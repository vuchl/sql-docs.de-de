---
title: Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f0816ea29b873777c54d77e34d691c909c8e6208
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256132"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a>Zwischenspeichern, Aktualisieren und Leistung des Replikationsmonitors
  Der Replikationsmonitor von[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dient der effizienten Überwachung einer großen Zahl von Computern in einem Produktionssystem. Die Abfragen, mit denen der Replikationsmonitor Berechnungen ausführt und Daten erfasst, werden zwischengespeichert und regelmäßig aktualisiert. Das Zwischenspeichern verringert die Zahl der Abfragen und Berechnungen, die erforderlich sind, wenn Sie verschiedene Seiten im Replikationsmonitor anzeigen, und ermöglicht es, den Umfang der Überwachungen für mehrere Benutzer optimal anzupassen.  
  
 Die Aktualisierung des Cache wird durch einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agentauftrag ausgeführt: **Aktualisierung für die Replikationsüberwachung**. Der Auftrag wird fortlaufend ausgeführt. Der Zeitplan für die Aktualisierung des Cache hängt von einer bestimmten Wartedauer nach der vorhergehenden Aktualisierung ab:  
  
-   Wenn seit dem letzten Erstellen des Cache Änderungen des Agent-Verlaufs stattgefunden haben, beträgt die Wartezeit mindestens 4 Sekunden oder die Zeitspanne, die das Erstellen des vorherigen Cache gedauert hat.  
  
-   Wenn seit dem letzten Erstellen des Cache keine Änderungen des Agent-Verlaufs stattgefunden haben (es könnten andere Änderungen eingetreten sein), beträgt die Wartezeit maximal 30 Sekunden oder die Zeitspanne, die das Erstellen des vorherigen Cache gedauert hat.  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a>Aktualisieren der Benutzeroberfläche des Replikationsmonitors  
 Die Benutzeroberfläche des Replikationsmonitors kann folgendermaßen aktualisiert werden:  
  
-   Das Fenster des Replikationsmonitors (einschließlich aller Registerkarten) wird standardmäßig alle fünf Sekunden automatisch aktualisiert. Das automatische Aktualisieren erzwingt keine Aktualisierung des Cache. Die Benutzeroberfläche zeigt die aktuellste Version der Daten aus dem Cache an. Sie können die Aktualisierungsrate für alle Fenster anpassen, die mit einem Verleger zusammenhängen, indem Sie die Einstellungen für den Verleger bearbeiten. Sie können die automatischen Aktualisierungen für einen Verleger auch deaktivieren.  
  
-   Die im Replikationsmonitor gestarteten Detailfenster werden nicht standardmäßig automatisch aktualisiert, ausgenommen Fenster, die mit einem gerade synchronisierten Merge-Abonnement zusammenhängen. Wenn Sie das automatische Aktualisieren von Detailfenstern angeben, werden die Fenster nach demselben Zeitplan aktualisiert wie das Hauptfenster des Replikationsmonitors.  
  
-   Sie können alle Fenster manuell aktualisieren. Drücken Sie dazu F5, oder klicken Sie mit der rechten Maustaste auf einen Knoten in der Struktur des Replikationsmonitors, und klicken Sie dann auf **Aktualisieren**. Das manuelle Aktualisieren erzwingt eine Aktualisierung des Cache.  
  
 Weitere Informationen finden Sie unter [Aktualisieren von Daten im Replikationsmonitor](refresh-data-in-replication-monitor.md).  
  
## <a name="performance-considerations"></a>Leistungsaspekte  
 Der Replikationsmonitor ist zwar für ein effizientes Ausführen ausgelegt, jedoch sollten Sie Folgendes beachten:  
  
-   Legen Sie bei einer großen Zahl von Veröffentlichungen oder Abonnements einen Zeitplan fest, nach dem die Benutzeroberfläche weniger häufig automatisch aktualisiert wird.  
  
-   Vermeiden Sie das gleichzeitige Ausführen mehrerer Instanzen des Replikationsmonitors.  
  
-   Vermeiden Sie es, eine große Zahl von Verteilern zu registrieren und festzulegen, dass der Replikationsmonitor zu allen automatisch eine Verbindung herstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Aufträgen zur Replikationswartung &#40;SQL Server Management Studio&#41;](../../../ssms/sql-server-management-studio-ssms.md)   
 [Überwachen (Replikation)](../monitoring-replication.md)  
  
  
