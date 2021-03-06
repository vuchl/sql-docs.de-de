---
title: Benachrichtigen eines Operators über den Auftragsstatus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- status information [SQL Server], jobs
- jobs [SQL Server Agent], notification options
- SQL Server Agent jobs, status
- jobs [SQL Server Agent], status
- SQL Server Agent jobs, notification options
- notifications [SQL Server], job status
ms.assetid: e7399505-27ac-48d9-a637-73bf92b9df49
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cfb89cfa76ee5b64634c8f5c35f8c1619a0185e0
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43819376"
---
# <a name="notify-an-operator-of-job-status"></a>Benachrichtigen eines Operators über den Auftragsstatus
  In diesem Thema wird beschrieben, wie Sie Benachrichtigungsoptionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects festlegen können, damit der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent den Operatoren Benachrichtigungen über Aufträge senden kann.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So benachrichtigen Sie einen Operator über einen Auftragsstatus mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-notify-an-operator-of-job-status"></a>So benachrichtigen Sie einen Operator über einen Auftragsstatus  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie bearbeiten möchten, und wählen Sie **Eigenschaften**aus.  
  
3.  Wählen Sie im Dialogfeld **Auftragseigenschaften** die Seite **Benachrichtigungen** aus.  
  
4.  Wenn ein Operator per E-Mail benachrichtigt werden soll, aktivieren Sie die Option **E-Mail**, wählen Sie aus der Liste einen Operator aus, und wählen Sie dann eine der folgenden Optionen aus:  
  
    -   **Bei erfolgreicher Auftragsausführung** , um den Operator zu benachrichtigen, wenn der Auftrag erfolgreich abgeschlossen wurde.  
  
    -   **Bei Auftragsfehler** , um den Operator zu benachrichtigen, wenn der Auftrag fehlgeschlagen ist.  
  
    -   **Beim Abschluss des Auftrags** , um den Operator unabhängig vom Abschlussstatus zu benachrichtigen.  
  
5.  Wenn ein Operator per Pager benachrichtigt werden soll, aktivieren Sie die Option **Pager**, wählen Sie aus der Liste einen Operator aus, und wählen Sie dann eine der folgenden Optionen aus:  
  
    -   **Bei erfolgreicher Auftragsausführung** , um den Operator zu benachrichtigen, wenn der Auftrag erfolgreich abgeschlossen wurde.  
  
    -   **Bei Auftragsfehler** , um den Operator zu benachrichtigen, wenn der Auftrag fehlgeschlagen ist.  
  
    -   **Beim Abschluss des Auftrags** , um den Operator unabhängig vom Abschlussstatus zu benachrichtigen.  
  
6.  Wenn ein Operator per NET SEND benachrichtigt werden soll, aktivieren Sie die Option **NET SEND**, wählen Sie aus der Liste einen Operator aus, und wählen Sie dann eine der folgenden Optionen aus:  
  
    -   **Bei erfolgreicher Auftragsausführung** , um den Operator zu benachrichtigen, wenn der Auftrag erfolgreich abgeschlossen wurde.  
  
    -   **Bei Auftragsfehler** , um den Operator zu benachrichtigen, wenn der Auftrag fehlgeschlagen ist.  
  
    -   **Beim Abschluss des Auftrags** , um den Operator unabhängig vom Abschlussstatus zu benachrichtigen.  
  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-notify-an-operator-of-job-status"></a>So benachrichtigen Sie einen Operator über einen Auftragsstatus  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- adds an e-mail notification for the specified alert (Test Alert).  
    -- This example assumes that Test Alert already exists and that François Ajenstat is a valid operator name.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_notification   
    @alert_name = N'Test Alert',   
    @operator_name = N'François Ajenstat',   
    @notification_method = 1 ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_add_notification &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql).  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So benachrichtigen Sie einen Operator über einen Auftragsstatus**  
  
 Verwenden der `Job` Klasse, indem Sie eine Programmiersprache, die Sie, wie z. B. Visual Basic, Visual c# oder PowerShell auswählen. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
