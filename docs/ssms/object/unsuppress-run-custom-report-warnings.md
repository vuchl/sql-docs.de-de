---
title: "Aufheben der Unterdrückung von Warnungen für das Ausführen von benutzerdefinierten Berichten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20c37528ddb6bc1c93d86135ddcdf1ed0b9e2aa1
ms.lasthandoff: 04/11/2017

---
# <a name="unsuppress-run-custom-report-warnings"></a>Aufheben der Unterdrückung von Warnungen für das Ausführen von benutzerdefinierten Berichten
Für benutzerdefinierte Berichte gibt es zwei Warndialogfelder. In diesem Thema wird beschrieben, wie die Unterdrückung der Anzeige dieser Felder in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]aufgehoben werden kann.  
  
Standardmäßig wird das Dialogfeld **Benutzerdefinierten Bericht ausführen** vor dem Ausführen eines benutzerdefinierten Berichts angezeigt. Wenn Sie das Kontrollkästchen **Diese Meldung nicht mehr anzeigen** aktivieren, wird das Dialogfeld nicht mehr angezeigt. Standardmäßig wird das Dialogfeld **Benutzerdefinierten Bericht ausführen** auch dann angezeigt, wenn Sie einen benutzerdefinierten Bericht öffnen und dann auf einen Link klicken, um einen anderen benutzerdefinierten Bericht zu öffnen. In diesem Dialogfeld wird der vollständige Pfad zur benutzerdefinierten Drillthroughberichtsdatei angezeigt. Wenn Sie das Kontrollkästchen **Diese Meldung nicht mehr anzeigen** aktivieren, wird das Dialogfeld nicht mehr angezeigt.  
  
## <a name="SSMSProcedure"></a>Verwenden von SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>So heben Sie die Unterdrückung des Warndialogfelds für den benutzerdefinierten Hauptbericht auf  
  
1.  Stellen Sie eine Verbindung mit \<*Server*>\\<*Freigabe*>|\<*Laufwerk*>\Dokumente und Einstellungen\\<UserProfile>\Anwendungsdaten\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml her.  
  
2.  Klicken Sie mit der rechten Maustaste auf **reports.xml**, und klicken Sie dann auf **Bearbeiten**.  
  
3.  Ändern Sie **<SuppressWarning>true\<\/Suppress Warning> in <SuppressWarning>false\<\/SupressWarning>**.  
  
4.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]neu.  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>So heben Sie die Unterdrückung des Warndialogfelds für den benutzerdefinierten Drillthroughbericht auf  
  
1.  Stellen Sie eine Verbindung mit \<*Server*>\\<*Freigabe*>|\<*Laufwerk*>\Dokumente und Einstellungen\\<UserProfile>\Anwendungsdaten\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml her.  
  
2.  Klicken Sie mit der rechten Maustaste auf **reports.xml**, und klicken Sie auf **Bearbeiten**.  
  
3.  Ändern Sie **<SuppressDrillthroughWarning>true\<\/SupressDrillthroughWarning> in <SuppressDrillthroughWarning>false\<\/SupressDrillthroughWarning>**.  
  
4.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]neu.  
  
## <a name="see-also"></a>Siehe auch  
[Benutzerdefinierte Berichte in Management Studio](../../ssms/object/custom-reports-in-management-studio.md)  
[Hinzufügen eines benutzerdefinierten Berichts zu Management Studio](../../ssms/object/add-a-custom-report-to-management-studio.md)  
[Verwenden benutzerdefinierter Berichte mit Eigenschaften von Objekt-Explorer-Knoten](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
  
