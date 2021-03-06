---
title: 'Schritt 2: Hinzufügen und Konfigurieren der Protokollierung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7c8aeee9c6d0d11ba5dbb482e02595802c5d76fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281366"
---
# <a name="step-2-adding-and-configuring-logging"></a>Schritt 2: Hinzufügen und Konfigurieren der Protokollierung
  In dieser Aufgabe aktivieren Sie die Protokollierung für den Datenfluss im Paket Lesson 3.dtsx. Sie konfigurieren dann einen Protokollanbieter für Textdateien, um die Ereignisse PipelineExecutionPlan und PipelineExecuteTrees zu protokollieren. Der Protokollanbieter für Textdateien erstellt Protokolle, die auf einfache Weise angezeigt werden können und portabel sind. Die Einfachheit dieser Protokolldateien ist besonders während der grundlegenden Testphase eines Pakets nützlich. Sie können die Protokolleinträge auch im Fenster Protokollereignisse des [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designers anzeigen.  
  
### <a name="to-add-logging-to-the-package"></a>So fügen Sie die Protokollierung zum Paket hinzu  
  
1.  Klicken Sie im Menü **SSIS** auf **Protokollierung**.  
  
2.  Stellen Sie im Dialogfeld **SSIS-Protokolle konfigurieren** im **Container** -Bereich sicher, dass das oberste Objekt, das das Paket aus Lektion 3 darstellt, ausgewählt ist.  
  
3.  Wählen Sie auf der Registerkarte **Anbieter und Protokolle** im Feld **Anbietertyp** die Option **SSIS-Protokollanbieter für Textdateien**aus, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Von Integration Services wird ein neuer Protokollanbieter für Textdateien mit dem Standardnamen **SSIS-Protokollanbieter für Textdateien**zum Paket hinzugefügt. Sie können jetzt den neuen Protokollanbieter konfigurieren.  
  
4.  In der **Namen** Spalte, Datentyp `Lesson 3 Log File`.  
  
5.  Ändern Sie optional **Beschreibung**.  
  
6.  In der **Konfiguration** Spalte, klicken Sie auf  **\<neue Verbindung >** um das Ziel anzugeben, wohin die Protokollinformationen geschrieben.  
  
     Wählen Sie im Dialogfeld **Dateiverbindungs-Manager-Editor** für **Verwendungstyp**die Option **Datei erstellen**aus, und klicken Sie anschließend auf **Durchsuchen**. Standardmäßig wird vom Dialogfeld **Dateien auswählen** der Projektordner geöffnet, aber Sie können Protokollinformationen an beliebiger Stelle speichern.  
  
7.  In der **Datei auswählen** Dialogfeld die **Dateiname** geben `TutorialLog.log`, und klicken Sie auf **öffnen**.  
  
8.  Klicken Sie auf **OK** , um das Dialogfeld **Dateiverbindungs-Manager-Editor** zu schließen.  
  
9. Erweitern Sie im **Container** -Bereich alle Knoten der Paketcontainerhierarchie, und deaktivieren Sie anschließend alle Kontrollkästchen, einschließlich des Kontrollkästchens für **Extract Sample Currency Data** . Aktivieren Sie jetzt das Kontrollkästchen für **Extract Sample Currency Data** , um nur die Ereignisse für diesen Knoten abzurufen.  
  
    > [!IMPORTANT]  
    >  Wenn der Status des Kontrollkästchens **Extract Sample Currency Data** abgeblendet anstatt ausgewählt ist, verwendet der Task die Protokolleinstellungen des übergeordneten Containers. In diesem Fall können Sie die taskspezifischen Protokollereignisse nicht aktivieren.  
  
10. Wählen Sie auf der Registerkarte **Details** in der Spalte **Ereignisse** die Ereignisse **PipelineExecutionPlan** und **PipelineExecutionTrees** aus.  
  
11. Klicken Sie auf **Erweitert** , um die Details zu überprüfen, die vom Protokollanbieter für jedes Ereignis in das Protokoll geschrieben werden. Standardmäßig werden alle Informationskategorien für die Ereignisse ausgewählt, die Sie angeben.  
  
12. Klicken Sie auf **Standard** , um die Informationskategorien auszublenden.  
  
13. Auf der **Anbieter und Protokolle** Registerkarte die **Namen** Spalte `Lesson 3 Log File`. Nach dem Erstellen eines Protokollanbieters für Ihr Paket können Sie diesen optional deaktivieren, um die Protokollierung zeitweise zu deaktivieren, ohne dass Sie einen Protokollanbieter löschen und dann erneut erstellen müssen.  
  
14. Klicken Sie auf **OK**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Schritt 3: Testen des Tutorialpakets aus Lektion 3](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  
