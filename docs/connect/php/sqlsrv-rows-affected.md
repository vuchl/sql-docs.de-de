---
title: zu Sqlsrv_rows_affected | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_rows_affected
apitype: NA
helpviewer_keywords:
- sqlsrv_rows_affected
- API Reference, sqlsrv_rows_affected
ms.assetid: 6f43fbfc-fc92-449b-82d0-33fa780e8f09
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f416bf1633909e548572f8f90c7fac7e188ecf75
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991382"
---
# <a name="sqlsrvrowsaffected"></a>sqlsrv_rows_affected
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt die Anzahl von Zeilen zurück, die von der zuletzt ausgeführten Anweisung geändert wurden. Diese Funktion gibt nicht die Anzahl der von einer SELECT-Anweisung zurückgegebenen Zeilen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_rows_affected( resource $stmt)  
```  
  
#### <a name="parameters"></a>Parameter  
*$stmt*: Eine Anweisungsressource, die einer ausgeführten Anweisung entspricht.  
  
## <a name="return-value"></a>Rückgabewert  
Eine ganze Zahl, die die Anzahl der Zeilen angibt, die durch die zuletzt ausgeführte Anweisung geändert wurden. Wenn keine Zeilen geändert wurden, wird Null (0) zurückgegeben. Wenn keine Informationen über die Anzahl der geänderten Zeilen verfügbar sind, wird die negative Eins (-1) zurückgegeben. Wenn ein Fehler beim Abrufen der geänderten Zeilen aufgetreten ist, wird **false** zurückgegeben.  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel zeigt die Anzahl der Zeilen, die durch eine UPDATE-Anweisung geändert wurden. Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) -Datenbank auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET SpecialOfferID = ?   
         WHERE ProductID = ?";  
  
/* Set parameter values. */  
$params = array(2, 709);  
  
/* Execute the statement. */  
$stmt = sqlsrv_query( $conn, $tsql, $params);  
  
/* Get the number of rows affected and display appropriate message.*/  
$rows_affected = sqlsrv_rows_affected( $stmt);  
if( $rows_affected === false)  
{  
     echo "Error in calling sqlsrv_rows_affected.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
elseif( $rows_affected == -1)  
{  
      echo "No information available.\n";  
}  
else  
{  
      echo $rows_affected." rows were updated.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  

[Aktualisieren von Daten &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  

  
