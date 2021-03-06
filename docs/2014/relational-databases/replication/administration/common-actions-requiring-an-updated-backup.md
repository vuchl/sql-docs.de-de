---
title: Häufige Aktionen, die eine aktualisierte Sicherung erfordern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- recovery [SQL Server replication], actions requiring a backup
- restoring [SQL Server replication], actions requiring a backup
- backups [SQL Server replication], actions requiring a backup
ms.assetid: a5975bf4-183e-42e3-b7d1-ad02f89d2e1d
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5d6065f17d65fc12a0c688625d4210b991c8fad0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203050"
---
# <a name="common-actions-requiring-an-updated-backup"></a>Häufige Aktionen, die eine aktualisierte Sicherung erfordern
  Wenn Sie regelmäßige Protokollsicherungen ausführen, sollten in den Protokollsicherungen auch alle replikationsrelevanten Änderungen erfasst werden. Wenn Sie keine Protokollsicherungen ausführen, sichern Sie die Veröffentlichung, die Verteilung, das Abonnement sowie die Datenbanken **msdb**und **master** nach Änderungen am Replikationsschema oder der Topologie.  
  
## <a name="publication-database"></a>Veröffentlichungsdatenbank  
 Sichern Sie die Veröffentlichungsdatenbank nach folgenden Aktionen:  
  
-   Erstellen neuer Veröffentlichungen.  
  
-   Ändern von Veröffentlichungseigenschaften, einschließlich des Filterns.  
  
-   Hinzufügen von Artikeln zu einer vorhandenen Veröffentlichung.  
  
-   Ausführen einer veröffentlichungsweiten erneuten Initialisierung der Abonnements.  
  
-   Vornehmen einer Schemaänderung an einer veröffentlichten Tabelle.  
  
-   Ausführen einer bedarfsgesteuerten Skriptausführung mit [sp_addscriptexec &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addscriptexec-transact-sql).  
  
-   Ändern von Artikeleigenschaften.  
  
-   Löschen von Veröffentlichungen.  
  
-   Löschen von Artikeln.  
  
-   Deaktivieren der Replikation.  
  
## <a name="distribution-database"></a>Verteilungsdatenbank  
 Sichern Sie die Verteilungsdatenbank nach folgenden Aktionen:  
  
-   Erstellen oder Ändern von Replikations-Agentprofilen.  
  
-   Ändern von Parametern für die Replikations-Agentprofile.  
  
-   Ändern der Eigenschaften von Replikations-Agents (einschließlich der Zeitpläne) für Pushabonnements.  
  
-   Ein neuer Identitätsbereich wird von der Funktion der automatischen Identitätsbereichsverwaltung zugewiesen.  
  
## <a name="subscription-database"></a>Abonnementdatenbank  
 Sichern Sie die Abonnementdatenbank nach folgenden Aktionen:  
  
-   Ändern von Abonnementeigenschaften.  
  
-   Ändern der Priorität eines Mergeabonnements auf dem Verleger.  
  
-   Löschen von Abonnements.  
  
-   Deaktivieren der Replikation.  
  
## <a name="msdb-database"></a>msdb-Datenbank  
 Sichern Sie die **msdb** -Systemdatenbank auf dem entsprechenden Knoten nach den folgenden Aktionen:  
  
-   Aktivieren oder Deaktivieren der Replikation.  
  
-   Hinzufügen oder Löschen einer Verteilungsdatenbank (auf dem Verteiler).  
  
-   Aktivieren oder Deaktivieren einer Datenbank für das Veröffentlichen (auf dem Verleger).  
  
-   Erstellen oder Ändern von Replikations-Agentprofilen (auf dem Verteiler).  
  
-   Ändern von Parametern für Replikations-Agentprofile (auf dem Verteiler).  
  
-   Ändern der Eigenschaften von Replikations-Agents (einschließlich der Zeitpläne) für Pushabonnements (auf dem Verteiler).  
  
-   Ändern der Eigenschaften von Replikations-Agents (einschließlich der Zeitpläne) für Pullabonnements (auf dem Abonnenten).  
  
-   Erstellen eines DTS-Pakets, das einer Transaktionsveröffentlichung zugewiesen ist, die transformierbare Abonnements verwendet (auf dem Verteiler und Abonnenten).  
  
-   Hinzufügen oder Löschen eines transformierbaren Abonnements (auf dem Verteiler und Abonnementen).  
  
## <a name="master-database"></a>master-Datenbank  
 Sichern Sie die **master** -Systemdatenbank auf dem entsprechenden Knoten nach den folgenden Aktionen:  
  
-   Aktivieren oder Deaktivieren der Replikation.  
  
-   Hinzufügen oder Löschen einer Verteilungsdatenbank (auf dem Verteiler).  
  
-   Aktivieren oder Deaktivieren einer Datenbank für das Veröffentlichen (auf dem Verleger).  
  
-   Hinzufügen der ersten Veröffentlichung oder Löschen der letzten Veröffentlichung in einer Datenbank (auf dem Verleger).  
  
-   Hinzufügen des ersten Abonnements oder Löschen des letzten Abonnements in einer Datenbank (auf dem Abonnenten).  
  
-   Aktivieren oder Deaktivieren eines Verlegers auf einem Verteilungsverleger (auf dem Verleger und dem Verteiler).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Sichern und Wiederherstellen von replizierten Datenbanken](back-up-and-restore-replicated-databases.md)  
  
  
