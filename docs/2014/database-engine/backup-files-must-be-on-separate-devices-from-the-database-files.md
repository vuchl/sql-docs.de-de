---
title: Sicherungsdateien und Datenbankdateien müssen auf separaten Medien gespeichert sein. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18b1f6d38f67dacc2a8da06a061d6bd76e055196
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818106"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Sicherungsdateien und Datenbankdateien müssen auf separaten Medien gespeichert sein
  Diese Regel überprüft, ob Datenbankdateien und Sicherungsdateien auf separaten Medien gespeichert sind. Wenn sich Datenbankdateien und Sicherungsdateien auf demselben Medium befinden und ein Fehler auftritt, stehen die Datenbank und die Sicherungen nicht mehr zur Verfügung. Wenn Sie die Daten und die Sicherungen auf separaten Medien speichern, wird auch die E/A-Leistung für die produktive Nutzung der Datenbank sowie für das Schreiben von Sicherungen optimiert.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Es empfiehlt sich dringend, Datenbank und Sicherungen auf separaten Sicherungsmedien zu speichern.  
  
> [!NOTE]  
>  Diese Richtlinie kann separate physische Geräte nicht durch Einbindungspunkte erkennen.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sicherungsmedien &#40;SQL Server&#41;](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [Sichern und Wiederherstellen von SQL Server-Datenbanken](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
