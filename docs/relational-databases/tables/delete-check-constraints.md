---
title: Löschen von CHECK-Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3a5bb0cb89714fd1cc567a9dc7858671afe8c3a7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43060292"
---
# <a name="delete-check-constraints"></a>Löschen von CHECK-Einschränkungen
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Sie können mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] eine CHECK-Einschränkung in [!INCLUDE[tsql](../../includes/tsql-md.md)]löschen. Durch das Löschen von CHECK-Einschränkungen werden die Beschränkungen für die Datenwerte entfernt, die in der Spalte oder den Spalten im Einschränkungsausdruck zulässig sind.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So löschen Sie eine CHECK-Einschränkung mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Tabelle.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-delete-a-check-constraint"></a>So löschen Sie eine CHECK-Einschränkung  
  
1.  Erweitern Sie im **Objekt-Explorer**die Tabelle mit der CHECK-Einschränkung.  
  
2.  Erweitern Sie  **Einschränkungen**.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Einschränkung, und klicken Sie dann auf **Löschen**.  
  
4.  Klicken Sie im Dialogfeld **Objekt löschen** auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-delete-a-check-constraint"></a>So löschen Sie eine CHECK-Einschränkung  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
  
