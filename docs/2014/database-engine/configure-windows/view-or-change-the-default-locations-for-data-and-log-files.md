---
title: Anzeigen oder Ändern der Standardspeicherorte für Daten- und Protokolldateien (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b62c6264686efe2b117ca755fc291c784308fe9d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320780"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a>Anzeigen oder Ändern der Standardspeicherorte für Daten- und Protokolldateien (SQL Server Management Studio)
  In diesem Thema wird das Anzeigen und Ändern der Standardspeicherorte von neuen Daten- und Protokolldateien in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]beschrieben. Der Standardpfad wird aus der Registrierung abgerufen. Nachdem Sie den Speicherort geändert haben, verwenden alle neuen Datenbanken, die in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt werden, diesen Speicherort, sofern kein anderer Speicherort angegeben wird.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Empfehlungen](#Recommendations)  
  
-   **Zum Anzeigen oder ändern die Daten- und Protokolldateien Standardspeicherorte verwenden:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
-   **Nachverfolgung:** [Ändern der Standardspeicherorte](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Recommendations"></a> Empfehlungen  
 Als bewährte Methode zum Schutz der Datendateien und Protokolldateien sollten Sie sicherstellen, dass diese durch Zugriffssteuerungslisten (ACLs) geschützt sind. Die ACLs sollten für den Verzeichnisstamm eingerichtet werden, unter dem die Dateien erstellt werden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a>So zeigen Sie die Standardspeicherorte für Datenbankdateien an oder ändern diese  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf die Seite **Datenbankeinstellungen** .  
  
3.  Im Bereich **Standardspeicherorte für Datenbank**können Sie die aktuellen Standardspeicherorte für neue Datendateien und neue Protokolldateien anzeigen. Um einen Standardspeicherort zu ändern, geben Sie einen neuen Standardpfadnamen in das Feld **Daten** oder **Protokoll** ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen, um einen Pfadnamen zu suchen und auszuwählen.  
  
##  <a name="FollowUp"></a> Nachverfolgung: Nach dem Ändern der Standardspeicherorte  
 Sie müssen den SQL Server-Dienst beenden und wieder starten, um die Änderung abzuschließen.  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Erstellen einer Datenbank](../../relational-databases/databases/create-a-database.md)  
  
  
