---
title: 'Optionen (Seite "Text-Editor: XML:Tabs") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
ms.assetid: 13bf5f8c-aba3-4c05-b8bb-eb475797c9bd
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2843acbc8935d8bd9f505a9265c704a342ddee3d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324920"
---
# <a name="options-text-editorxmltabs-page"></a>Optionen (Text-Editor: XML:Tabs Seite)
  Mithilfe dieses Dialogfelds können Sie das Tabulatorverhalten des XML-Editors ändern, der für die Bearbeitung von XML-Dokumenten verwendet wird. Zum Anzeigen dieser Einstellungen klicken Sie im Menü **Extras** auf **Optionen** , und erweitern Sie anschließend den Ordner **Text-Editor** , dann den Unterordner **XML** , und klicken Sie dann auf **Tabstopps**.  
  
## <a name="setting-options-in-multiple-locations"></a>Festlegen der Optionen an mehreren Stellen  
 Optionen für den XML-Editor können auch im Dialogfeld **Alle Sprachen/Allgemein** festgelegt werden. Wenn Sie die Dialogfelder **Alle Sprachen** verwenden, um unterschiedliche Optionen für die anderen [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] -Editoren, z. B. den DMX- oder den MDX-Editor, festzulegen, müssen Sie die Optionen des XML-Editors mithilfe dieses Dialogs zurücksetzen.  
  
## <a name="indenting"></a>Einzug  
 **Keine**  
 Wenn diese Option ausgewählt ist, wird die neue Zeile, die nach dem Drücken der EINGABETASTE erstellt wird, nicht eingerückt. Der Cursor wird in der ersten Spalte der neuen Zeile platziert.  
  
 **Block**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile automatisch so weit eingerückt wie die vorige Zeile.  
  
 **Intelligente**  
 Wenn diese Option ausgewählt ist, wird die nach dem Drücken der Eingabetaste erstellte Zeile je nach Kontext eingerückt. Nach einer öffnenden geschweiften Klammer ({) werden beispielsweise die eingeschlossenen Zeilen automatisch um einen zusätzlichen Tabstopp eingerückt. Die dazugehörige schließende geschweifte Klammer (}) wird wieder auf die öffnende Klammer ausgerichtet.  
  
## <a name="tabs"></a>Tabstopps  
 **Tabulatorgröße**  
 Legt den Abstand zwischen den Tabstopps fest. Der Standardwert ist vier Leerzeichen.  
  
 **Einzugsgröße**  
 Legt die Größe des automatischen Einzugs in Leerzeichen fest. Der Standardwert ist vier Leerzeichen. Es werden entweder Tabstopps, Leerzeichen oder beide verwendet, um den angegebenen Raum zu füllen.  
  
 **Leerzeichen einfügen**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen nur Leerzeichen eingefügt, keine Tabulatorzeichen. Wenn die **Einzugsgröße** z. B. auf 5 festgelegt ist, werden fünf Leerzeichen eingefügt, wenn Sie die TAB-Taste drücken oder im Hauptfenster von **auf der Symbolleiste auf die Schaltfläche** Einzug vergrößern [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] klicken.  
  
 **Tabstopps beibehalten**  
 Wenn diese Option ausgewählt ist, werden bei Einzugsfunktionen so viele Tabulatorzeichen wie möglich eingefügt. Jedes Tabulatorzeichen nimmt den Platz so vieler Leerzeichen ein, wie im Feld **Tabulatorgröße**definiert wurden. Wenn die **Einzugsgröße** kein ganzes Vielfaches der **Tabulatorgröße**ist, werden zum Auffüllen der Differenz Leerzeichen verwendet.  
  
  
