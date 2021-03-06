---
title: 'Analysis Services-Tutorial, Lektion 8: Erstellen von Perspektiven | Microsoft-Dokumentation'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 080b20dbcf7438d26102a3bf906256343271af45
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085321"
---
# <a name="create-perspectives"></a>Erstellen von Perspektiven

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion erstellen Sie eine Internet Sales-Perspektive. Eine Perspektive definiert eine sichtbare Teilmenge eines Modells, die fokussierte, unternehmensspezifische oder anwendungsspezifische Blickpunkte bereitstellt. Wenn ein Benutzer auf ein Modell mithilfe einer Perspektive herstellt, sehen sie nur die Modellobjekte (Tabellen, Spalten, Measures, Hierarchien und KPIs) als in dieser Perspektive definierten Felder. Weitere Informationen finden Sie unter [Perspektiven](../tabular-models/perspectives-ssas-tabular.md).
  
Die Internet Sales-Perspektive, die Sie in dieser Lektion erstellen, schließt das Objekt DimCustomer-Tabelle. Wenn Sie eine Perspektive, die bestimmte Objekte aus der Sicht ausschließt erstellen, ist das Objekt weiterhin im Modell vorhanden. Es ist jedoch nicht in der Feldliste einer berichterstellungsclients sichtbar. In berechneten Spalten und Measures können Berechnungen mit ausgeschlossenen Objektdaten ausgeführt werden, unabhängig davon, ob die Spalten und Measures in einer Perspektive enthalten sind.  
  
In dieser Lektion wird beschrieben, wie Sie Perspektiven erstellen und sich mit den Erstellungstools der Tabellenmodelle vertraut machen. Wenn Sie später dieses Modell um zusätzliche Tabellen erweitern, können Sie zusätzliche Perspektiven, um verschiedene Blickpunkte des Modells, z. B. Inventur- und Sales definieren erstellen.  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **fünf Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion an, Sie sollten die vorherige Lektion abgeschlossen haben: [Lektion 7: Erstellen von Key Performance Indicators](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Erstellen von Perspektiven  
  
#### <a name="to-create-an-internet-sales-perspective"></a>So erstellen Sie eine Internet Sales-Perspektive  
  
1.  Klicken Sie auf die **Modell** Menü > **Perspektiven** > **erstellen und verwalten**.  
  
2.  Klicken Sie im Dialogfeld **Perspektiven** auf **Neue Perspektive**.  
  
3.  Doppelklicken Sie auf die **neue Perspektive** Spaltenüberschrift, und klicken Sie dann benennen **Internetverkäufe**.  
  
4.  Wählen Sie alle Tabellen *außer* **DimCustomer**.  
  
    ![Perspektiven als Lektion 8](../tutorial-tabular-1400/media/as-lesson8-perspectives.png)
  
    In einer späteren Lektion verwenden Sie die Funktion in Excel analysieren dieser Perspektive zu testen. Der Excel-PivotTable-Feldliste enthält alle Tabellen außer DimCustomer-Tabelle.  

## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 9: Erstellen von Hierarchien](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).
  
  
  
  
