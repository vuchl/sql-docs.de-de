---
title: Tools und Ansätze zum Verarbeiten (Analysis Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- process [Analysis Services]
- processing [Analysis Services]
ms.assetid: 82347a16-4145-4655-8adf-2a300f1fdf99
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f00c1a31869bdfb9375d1e97822c98a0e4f9f914
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261403"
---
# <a name="tools-and-approaches-for-processing-analysis-services"></a>Tools und Ansätze zum Verarbeiten (Analysis Services)
  Die Verarbeitung ist ein Vorgang, bei dem Analysis Services Daten aus einer relationalen Datenquelle abfragt und Analysis Services-Objekte mit diesen Daten auffüllt.  
  
 Als Analysis Services-Systemadministrator können Sie die Verarbeitung der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekte mithilfe der folgenden Ansätze ausführen und überwachen:  
  
-   Ausführen der Auswirkungsanalyse, um Objektabhängigkeiten und den Umfang von Vorgängen zu verstehen  
  
-   Verarbeiten von einzelnen Objekten in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   Verarbeiten von einzelnen oder mehreren Objekten in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   Führen Sie die Auswirkungsanalyse aus, um eine Liste von verbundenen Objekten zu überprüfen, die als Ergebnis der aktuellen Aktion nicht verarbeitet sind.  
  
-   Generieren und Ausführen eines Skripts in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -XMLA-Abfragefenster in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , um einzelne oder mehrere Objekte zu verarbeiten  
  
-   Verwenden von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -PowerShell-Cmdlets  
  
-   Verwenden von Ablaufsteuerungen und Tasks in [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketen  
  
-   Überwachen von Verarbeitung mit SQL Server Profiler  
  
-   Programmieren Sie mit AMO eine benutzerdefinierte Lösung. Weitere Informationen finden Sie unter [Programming AMO OLAP Basic Objects](analysis-management-objects/programming-amo-olap-basic-objects.md).  
  
 Die Verarbeitung ist ein stark konfigurierbarer Vorgang. Selbiger wird von einem Satz von Verarbeitungsoptionen gesteuert, die bestimmen, ob vollständige oder inkrementelle Verarbeitung auf Objektebene auftritt. Weitere Informationen zu Verarbeitungsoptionen und -objekten finden Sie unter [Verarbeiten von Optionen und Einstellungen &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) und [Verarbeiten von Analysis Services-Objekten](processing-analysis-services-objects.md).  
  
> [!NOTE]  
>  In diesem Thema werden die Tools und die Ansätze zum Verarbeiten von mehrdimensionalen Modellen beschrieben. Weitere Informationen zur Verarbeitung von tabellarischer Models finden Sie unter [Verarbeiten von Datenbank, Tabelle oder Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) und [Verarbeitungsdaten &#40;SSAS – tabellarisch&#41;](../process-data-ssas-tabular.md).  
  
### <a name="processing-objects-in-sql-server-management-studio"></a>Verarbeiten von Objekten in SQL Server Management Studio  
  
1.  Starten Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , und stellen Sie eine Verbindung mit Analysis Services her.  
  
2.  Klicken Sie mit der rechten Maustaste auf das Analysis Services-Objekt, das Sie verarbeiten möchten, und klicken Sie auf **Verarbeiten**. Sie können Daten auf einer dieser Ebenen verarbeiten:  
  
    -   Datenbanken  
  
    -   Cubes  
  
    -   Measuregruppen oder einzelne Partitionen in der Measuregruppe  
  
    -   Dimensionen  
  
    -   Miningmodelle  
  
    -   Miningstrukturen  
  
     Analysis Services-Objekte sind hierarchisch. Wenn Sie die Datenbank wählen, kann die Verarbeitung für alle in der Datenbank enthaltenen Objekte durchgeführt werden. Ob die Verarbeitung tatsächlich durchgeführt wird, hängt von der ausgewählten Verarbeitungsoption und vom Status des Objekts ab. Insbesondere gilt: Wenn ein Objekt noch nicht verarbeitet wurde, führt die Verarbeitung seines übergeordneten Elements dazu, dass das Objekt selbst auch verarbeitet wird. Weitere Informationen zu Objektabhängigkeiten finden Sie unter [Processing Analysis Services Objects](processing-analysis-services-objects.md).  
  
3.  Verwenden Sie im Dialogfeld **Verarbeiten** unter **Verarbeitungsoptionen**den bereitgestellten Standardwert, oder wählen Sie in der Liste eine andere Option aus. Weitere Informationen finden Sie unter [Verarbeiten von Optionen und Einstellungen &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md).  
  
4.  Klicken Sie auf **Auswirkungsanalyse** , um abhängige Objekte zu identifizieren und optional zu verarbeiten, die betroffen sind, wenn die im Dialogfeld Verarbeiten aufgeführten Objekte verarbeitet werden.  
  
5.  Klicken Sie optional auf **Einstellungen ändern** , um die Verarbeitungsreihenfolge, das Verarbeitungsverhalten relativ zu bestimmten Typen von Fehlern und andere Einstellungen zu ändern.  
  
6.  Klicken Sie auf **OK**.  
  
     Im Dialogfeld Verarbeitungsstatus wird für jeden Befehl fortlaufend der Status angezeigt. Wenn eine Statusmeldung abgeschnitten ist, können Sie auf **Details anzeigen** klicken, um die ganze Meldung zu lesen.  
  
### <a name="processing-objects-in-sql-server-data-tools"></a>Verarbeiten von Objekten in SQL Server Data Tools  
  
1.  Starten Sie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , und öffnen Sie ein Projekt, das bereitgestellt wurde.  
  
2.  Erweitern Sie im Projektmappen-Explorer den Ordner **Dimensionen** unter dem bereitgestellten Projekt.  
  
3.  Klicken Sie mit der rechten Maustaste auf eine Dimension, und klicken Sie dann auf **Verarbeiten**. Sie können mit der rechten Maustaste auf mehrere Dimensionen klicken, um mehrere Objekte auf einmal zu verarbeiten. Weitere Informationen finden Sie unter [Batchverarbeitung &#40;Analysis Services&#41;](batch-processing-analysis-services.md).  
  
4.  Überprüfen Sie im Dialogfeld **Dimension aufbereiten** in der Spalte **Verarbeitungsoptionen** unter **Objektliste**, ob die Option für diese Spalte **Vollständig verarbeiten**lautet. Sollte dies nicht der Fall sein, klicken Sie unter **Verarbeitungsoptionen**auf die Option, und wählen Sie aus der Dropdownliste **Vollständig verarbeiten** aus.  
  
5.  Klicken Sie auf **Ausführen**.  
  
6.  Klicken Sie nach Abschluss der Verarbeitung auf **Schließen**.  
  
##  <a name="bkmk_impactanalysis"></a> Ausführen der Auswirkungsanalyse, um Objektabhängigkeiten und den Umfang von Vorgängen zu verstehen  
  
1.  Bevor Sie ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Objekt in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] oder [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]verarbeiten, können Sie die Auswirkung auf die verbundenen Objekte analysieren, indem Sie auf **Auswirkungsanalyse** in einem der **Objekte verarbeiten** -Dialogfelder klicken.  
  
2.  Klicken Sie mit der rechten Maustaste auf eine Dimension, einen Cube, eine Measuregruppe oder eine Partition, um ein Dialogfeld **Objekte verarbeiten** zu öffnen.  
  
3.  Klicken Sie auf **Auswirkungsanalyse**. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] scannt das Modell und berichtet über Neuverarbeitungsanforderungen für Objekte, die auf das für die Verarbeitung ausgewählte verweisen.  
  
### <a name="processing-objects-using-xmla"></a>Verarbeiten von Objekten mit XMLA  
  
1.  Starten Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , und stellen Sie eine Verbindung mit Analysis Services her.  
  
2.  Klicken Sie mit der rechten Maustaste auf das Objekt, und klicken Sie dann auf **Verarbeiten**.  
  
3.  Wählen Sie im Dialogfeld **Verarbeiten** die Verarbeitungsoption aus, die Sie verwenden möchten. Ändern Sie beliebige andere Einstellungen. Führen Sie die Auswirkungsanalyse aus, um die Änderungen zu identifizieren, die ggf. vorgenommen werden müssen.  
  
4.  Klicken Sie im Bildschirm zum **Verarbeiten von Objekten** auf **Skript** .  
  
     Mit diesem Schritt wird ein XMLA-Skript generiert und ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -XMLA-Abfragefenster geöffnet.  
  
5.  Schließen Sie das Dialogfeld. Das Skript enthält den Verarbeitungsbefehl und die Optionen, die im Dialogfeld angegeben wurden.  
  
6.  Sie können optional dem Skript weiterhin Elemente hinzufügen, wenn Sie zusätzliche Objekte im gleichen Batch verarbeiten möchten. Wiederholen Sie zum Fortfahren die vorherigen Schritte, und fügen Sie das generierte Skript an, damit Sie über ein einzelnes Skript für alle Verarbeitungsvorgänge verfügen. Ein Beispiel finden Sie unter [Schedule SSAS Administrative Tasks with SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md).  
  
7.  Klicken Sie in der Menüleiste auf **Abfrage**, und klicken Sie dann auf **Ausführen**.  
  
### <a name="processing-objects-using-powershell"></a>Verarbeiten von Objekten mit PowerShell  
  
1.  Ab dieser Version von SQL Server können Sie Analysis Services PowerShell-Cmdlets zum Verarbeiten von Objekten verwenden. Die folgenden Cmdlets können interaktiv oder per Skript ausgeführt werden:  
  
    -   [Invoke-ProcessCube cmdlet (Invoke-ProcessCube-Cmdlet)](/sql/analysis-services/powershell/invoke-processcube-cmdlet)  
  
    -   [Invoke-ProcessDimension cmdlet (Invoke-ProcessDimension-Cmdlet)](/sql/analysis-services/powershell/invoke-processdimension-cmdlet)  
  
    -   [Invoke-ProcessPartition cmdlet (Invoke-ProcessPartition-Cmdlet)](/sql/analysis-services/powershell/invoke-processpartition-cmdlet)  
  
    -   [Invoke-ASCmd-Cmdlet](/sql/analysis-services/powershell/invoke-ascmd-cmdlet), das verwendet werden kann, um ein XMLA-, MDX- oder DMX-Skript mit Verarbeitungsbefehlen auszuführen.  
  
### <a name="monitoring-object-processing-using-sql-server-profiler"></a>Überwachungsobjektverarbeitung mit SQL Server Profiler  
  
1.  Stellen Sie in SQL Server Profiler eine Verbindung zu einer Analysis Services-Instanz her.  
  
2.  Klicken Sie unter **Ereignisauswahl** aufAlle Ereignisse anzeigen, um der Liste alle Ereignisse hinzuzufügen.  
  
3.  Wählen Sie eines der folgenden Ereignisse aus:  
  
    -   **Command Begin** und **Command End** , um anzuzeigen, wenn die Verarbeitung gestartet und angehalten wird  
  
    -   **Error** , um sämtliche Fehler aufzuzeichnen  
  
    -   **Progress Report Begin**, **Progress Report Current**und **Progress Report End** , um über den Verarbeitungsstatus zu berichten und die SQL-Abfragen anzuzeigen, die verwendet wurden, um die Daten abzurufen  
  
    -   **Execute MDX Script Begin** und **Execute MDX Script End** , um die Cubeberechnungen anzuzeigen  
  
    -   Fügen Sie alternativ Sperrereignisse hinzu, wenn Sie auf Verarbeitung bezogene Leistungsprobleme diagnostizieren  
  
### <a name="process-analysis-services-objects-using-integration-services"></a>Verarbeiten von Analysis Services-Objekten mit Integration Services  
  
1.  Erstellen Sie in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]ein Paket, das den Analysis Services-Verarbeitungstask verwendet, um Objekte automatisch mit neuen Daten aufzufüllen wenn Sie regelmäßige Updates an der relationalen Quelldatenbank vornehmen.  
  
2.  Doppelklicken Sie in der **SSIS-Toolbox**auf **Analysis Services-Verarbeitung** , um den Task zum Paket hinzuzufügen.  
  
3.  Bearbeiten Sie den Task, um eine Verbindung zur Datenbank anzugeben und um zu bestimmen, welche Objekte verarbeitet werden sollen und um die Verarbeitungsoption zu bestimmen. Weitere Informationen zum Implementieren dieses Tasks finden Sie unter [Analysis Services Processing Task](../../integration-services/control-flow/analysis-services-processing-task.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeitung von mehrdimensionalen Modellobjekten](processing-a-multidimensional-model-analysis-services.md)  
  
  
