---
title: Zugriff auf die aktuelle Transaktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- current transaction access
- Current property
- Transaction class
ms.assetid: 1a4e2ce5-f627-4c81-8960-6a9968cefda2
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dad95c2d2fc02e46b139f29889315873f21887e7
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351812"
---
# <a name="accessing-the-current-transaction"></a>Zugriff auf die aktuelle Transaktion
  Wenn eine Transaktion aktiv ist, an dem Punkt, an die common Language Runtime (CLR)-Code auf ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird eingegeben haben, wird die Transaktion über verfügbar gemacht der `System.Transactions.Transaction` Klasse. Die `Transaction.Current` Eigenschaft wird verwendet, um die aktuelle Transaktion zugegriffen. In den meisten Fällen ist es nicht notwendig, explizit auf die Transaktion zuzugreifen. Bei Datenbankverbindungen überprüft ADO.NET `Transaction.Current` automatisch, wenn die `Connection.Open` Methode wird aufgerufen, und trägt die Verbindung in dieser Transaktion (es sei denn, die `Enlist` Schlüsselwort in der Verbindungszeichenfolge nicht false festgelegt ist).  
  
 Möglicherweise möchten Sie verwenden die `Transaction` Objekt direkt in den folgenden Szenarien:  
  
-   Wenn Sie eine Ressource eintragen möchten, die nicht automatisch eingetragen wird oder die aus irgendeinem Grund während der Initialisierung nicht eingetragen wurde.  
  
-   Wenn Sie eine Ressource explizit in die Transaktion eintragen möchten.  
  
-   Wenn Sie die externe Transaktion aus einer gespeicherten Prozedur oder Funktion heraus beenden möchten. In diesem Fall verwenden Sie <xref:System.Transactions.TransactionScope>. Beispielsweise wird mit dem folgenden Code die aktuelle Transaktion rückgängig gemacht.  
  
    ```  
    using(TransactionScope transactionScope = new TransactionScope(TransactionScopeOptions.Required)) { }  
    ```  
  
 Im weiteren Verlauf dieses Themas werden andere Möglichkeiten beschrieben, eine externe Transaktion abzubrechen.  
  
## <a name="canceling-an-external-transaction"></a>Abbrechen einer externen Transaktion  
 Sie können externe Transaktionen wie folgt von einer verwalteten Prozedur oder einer Funktion aus abbrechen:  
  
-   Die verwaltete Prozedur oder die Funktion kann in einem Ausgabeparameter einen Wert zurückgeben. Die aufrufende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozedur kann den zurückgegebenen Wert überprüfen und gegebenenfalls `ROLLBACK TRANSACTION` ausführen.  
  
-   Die verwaltete Prozedur oder die Funktion kann eine benutzerdefinierte Ausnahme auslösen. Die aufrufende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur kann die Ausnahme, die von der verwalteten Prozedur oder Funktion in einem Try/Catch-Block ausgelöst, und führen Sie `ROLLBACK TRANSACTION`.  
  
-   Die verwaltete Prozedur oder Funktion Abbrechen die aktuelle Transaktion durch Aufrufen der `Transaction.Rollback` Methode, wenn eine bestimmte Bedingung erfüllt ist.  
  
 Wenn sie innerhalb einer verwalteten Prozedur oder Funktion aufgerufen wird die `Transaction.Rollback` Methode löst eine Ausnahme mit einer nicht eindeutigen Fehlermeldung aus und kann in einem Try/Catch-Block eingebunden werden. Die Fehlermeldung lautet wie folgt oder ähnlich:  
  
```  
Msg 3994, Level 16, State 1, Procedure uspRollbackFromProc, Line 0  
Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting.  
```  
  
 Diese Ausnahme wird erwartet und der try/catch-Block ist notwendig, damit die Codeausführung fortgesetzt wird. Wenn kein try/catch-Block vorhanden ist, wird die Ausnahme sofort der aufrufenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozedur übergeben und der verwaltete Code wird zu Ende ausgeführt. Wenn die Ausführung des verwalteten Codes beendet ist, wird eine andere Ausnahme ausgelöst.  
  
```  
Msg 3991, Level 16, State 1, Procedure uspRollbackFromProc, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate " uspRollbackFromProc " has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting. The statement has been terminated.  
```  
  
 Diese Ausnahme ist ebenfalls zu erwarten, und die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung, welche die den Trigger auslösenden Aktion ausführt, muss in einen try/catch-Block eingeschlossen werden, damit die Ausführung fortgesetzt wird. Trotz der zwei ausgelösten Ausnahmen wird ein Rollback für die Transaktion ausgeführt, und für die Änderungen in der Tabelle wird kein Commit ausgeführt.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird von der verwalteten Prozedur für eine Transaktion mit der `Transaction.Rollback`-Methode ein Rollback für die Transaktion ausgeführt. Beachten Sie den Try/Catch-Block, um die `Transaction.Rollback` -Methode in verwaltetem Code. Das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skript erstellt eine Assembly und eine verwaltete gespeicherte Prozedur. Beachten Sie, die die `EXEC uspRollbackFromProc` Anweisung in einem Try/Catch-Block umschlossen ist, sodass die Ausnahme wird ausgelöst, wenn die Ausführung der verwaltete Prozedur beendet abgefangen wird.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspRollbackFromProc()  
{  
   using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
   {  
      // Open the connection.  
      connection.Open();  
  
      bool successCondition = true;  
  
      // Success condition is met.  
      if (successCondition)  
      {  
         SqlContext.Pipe.Send("Success condition met in procedure.");   
         // Perform other actions here.  
      }  
  
      //  Success condition is not met, the transaction will be rolled back.  
      else  
      {  
         SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...");  
         try  
         {  
               // Get the current transaction and roll it back.  
               Transaction trans = Transaction.Current;  
               trans.Rollback();  
         }  
         catch (SqlException ex)  
         {  
            // Catch the expected exception.   
            // This allows the connection to close correctly.                      
         }    
      }  
  
      // Close the connection.  
      connection.Close();  
   }  
}  
};  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  uspRollbackFromProc ()  
   Using connection As New SqlConnection("context connection=true")  
  
   ' Open the connection.  
   connection.Open()  
  
   Dim successCondition As Boolean  
   successCondition = False  
  
   ' Success condition is met.  
   If successCondition Then  
  
      SqlContext.Pipe.Send("Success condition met in procedure.")  
  
      ' Success condition is not met, the transaction will be rolled back.  
  
   Else  
      SqlContext.Pipe.Send("Success condition not met in managed procedure. Transaction rolling back...")  
      Try  
         ' Get the current transaction and roll it back.  
         Dim trans As Transaction  
         trans = Transaction.Current  
         trans.Rollback()  
  
      Catch ex As SqlException  
         ' Catch the exception instead of throwing it.    
         ' This allows the connection to close correctly.                      
      End Try  
  
   End If  
  
   ' Close the connection.  
   connection.Close()  
  
End Using  
End Sub  
End Class  
```  
  
 **Transact-SQL**  
  
```  
--Register assembly.  
CREATE ASSEMBLY TestProcs FROM 'C:\Programming\TestProcs.dll'   
Go  
CREATE PROCEDURE uspRollbackFromProc AS EXTERNAL NAME TestProcs.StoredProcedures.uspRollbackFromProc  
Go  
  
-- Execute procedure.  
BEGIN TRY  
BEGIN TRANSACTION   
-- Perform other actions.  
Exec uspRollbackFromProc  
-- Perform other actions.  
PRINT N'Commiting transaction...'  
COMMIT TRANSACTION  
END TRY  
  
BEGIN CATCH  
SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
PRINT N'Exception thrown, rolling back transaction.'  
ROLLBACK TRANSACTION  
PRINT N'Transaction rolled back.'   
END CATCH  
Go  
  
-- Clean up.  
DROP Procedure uspRollbackFromProc;  
Go  
DROP ASSEMBLY TestProcs;  
Go  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Integration und -Transaktionen](../native-client-ole-db-transactions/transactions.md)  
  
  
