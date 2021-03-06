---
title: 'Vorgehensweise: Debuggen von benutzerdefinierten Assemblys | Microsoft-Dokumentation'
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-assemblies
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ec398599747218d8764bc21ba977dbed2ecf72b8
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43275665"
---
# <a name="how-to-debug-custom-assemblies"></a>Vorgehensweise: Debuggen von benutzerdefinierten Assemblys
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] stellt mehrere hilfreiche Tools zum Debuggen zur Verfügung, die Sie bei der Analyse des Codes in benutzerdefinierten Assemblys und bei der Fehlersuche im Code unterstützen. Welches Tool dafür am besten geeignet ist, hängt von Ihrer Zielsetzung ab. In diesem Beispiel wird [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]verwendet.  
  
 Am besten können Sie benutzerdefinierte Assemblys für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] entwerfen, entwickeln und testen, wenn Sie eine Projektmappe erstellen, die sowohl Ihre Testberichte als auch Ihre benutzerdefinierte Assembly enthält.  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>So debuggen Sie Assemblys mithilfe einer Instanz von Visual Studio  
  
1.  So legen Sie ein neues Berichtsmodellprojekt mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] an.  
  
     Während Sie ein Berichtsprojekt erstellen, wird von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] auch eine Projektmappe für das Projekt angelegt.  
  
2.  Fügen Sie der vorhandenen Projektmappe ein neues Klassenbibliotheksprojekt hinzu. Stellen Sie sicher, dass das Berichtsprojekt als Startprojekt festgelegt wird. Weitere Informationen hierzu finden Sie in Ihrer [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Dokumentation.  
  
3.  Wählen Sie die Projektmappe im Projektmappen-Explorer aus.  
  
4.  Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.  
  
     Das Dialogfeld **Eigenschaftenseiten** der Projektmappe wird geöffnet.  
  
5.  Wenn nötig, öffnen Sie im linken Bereich **Allgemeine Eigenschaften**, und klicken Sie auf **Projektabhängigkeiten**. Wählen Sie das Berichtsprojekt aus der Dropdownliste **Projekt** aus. Wählen Sie das Assemblyprojekt in der Liste der **Abhängigkeiten** aus.  
  
6.  Klicken Sie auf **OK**, um die Änderungen zu speichern, und schließen Sie das Dialogfeld **Eigenschaftenseiten**.  
  
7.  Wählen Sie im Projektmappen-Explorer Ihr benutzerdefiniertes Assemblyprojekt aus.  
  
8.  Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.  
  
     Das Dialogfeld der **Eigenschaftenseite des Projekts** wird geöffnet.  
  
9. Klicken Sie in einem C#-Projekt auf die Registerkarte **Erstellen** und in einem [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Projekt auf die Registerkarte **Kompilieren**.  
  
10. Geben Sie auf der Seite **Erstellen**/**Kompilieren** den Pfad zum Ordner des Berichts-Designers ein. Standardmäßig ist dies C:\Programme\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) im Textfeld **Ausgabepfad**. Damit wird eine aktualisierte Version der benutzerdefinierten Assembly erstellt und direkt im Berichts-Designer bereitgestellt, bevor der Bericht ausgeführt wird.  
  
11. Wenn Sie den Bericht entworfen und die benutzerdefinierte Assembly entwickelt haben, legen Sie die Breakpoints im Code der benutzerdefinierten Assembly fest.  
  
12. Führen Sie den Bericht unter dem **DebugLocal**-Modus aus, indem Sie die F5-TASTE drücken. Wenn der Bericht in der Popup-Vorschau ausgeführt wird, sucht der Debugger alle Breakpoints, die dem ausführbaren Code in Ihrer Assembly entsprechen. Verwenden Sie F11, um den Code der benutzerdefinierten Assembly schrittweise zu durchlaufen.  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>So debuggen Sie Assemblys mithilfe von zwei Instanzen in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], und öffnen Sie das Projekt der benutzerdefinierten Assembly.  
  
2.  Erstellen Sie das Projekt, und stellen Sie die benutzerdefinierte Assembly und die dazugehörige PDB-Datei im Berichts-Designer bereit. Weitere Informationen zur Bereitstellung finden Sie unter [Deploying a Custom Assembly (Bereitstellen einer benutzerdefinierten Assembly)](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md).  
  
3.  Öffnen Sie ein Berichtsprojekt, das Ihre benutzerdefinierte Assembly verwendet, ohne den Code der benutzerdefinierten Assembly in einer anderen Instanz von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zu schließen.  
  
4.  Wechseln Sie zur [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Instanz, die das Projekt für die benutzerdefinierte Assembly enthält, und legen Sie einige Breakpoints im Code fest.  
  
5.  Während das Projekt der benutzerdefinierten Assembly noch immer das aktive Fenster ist, klicken Sie im Menü **Debuggen** auf **An den Prozess anhängen**.  
  
     Das Dialogfeld **An den Prozess anhängen** wird geöffnet.  
  
6.  Wählen Sie aus der Liste der Prozesse den Prozess „devenv.exe“ aus, der dem Berichtsprojekt entspricht, und klicken Sie auf **Anfügen**.  
  
7.  Definieren Sie die Ausdrücke, die Sie im Bericht aus der benutzerdefinierten Assembly verwenden möchten, und entwerfen Sie Ihren Bericht.  
  
8.  Wenn Sie den Bericht entworfen haben, klicken Sie auf die Registerkarte **Vorschau**.  
  
     Der Bericht wird ausgeführt, und der Code der benutzerdefinierten Assembly sollte an den vordefinierten Breakpoints unterbrochen werden.  
  
    > [!NOTE]  
    >  Bei Verwendung der Registerkarte **Vorschau** werden keine Codeberechtigungen für die Assembly erzwungen. Sie können einen vollständigen Test, der alle Fehler der Codezugriffssicherheit enthält, durchführen, indem Sie das Berichtsprojekt unter der Konfigurationseinstellung **DebugLocal** starten.  
  
9. Gehen Sie den Code schrittweise mit der F11-Taste durch. Weitere Informationen zum Debuggen mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] finden Sie in der Dokumentation zu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verwenden benutzerdefinierter Assemblys mit Berichten](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
