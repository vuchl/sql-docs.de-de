---
title: Sortieren mit ORDER BY (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 98e5927c691cb1d9b4811cf308b139b205ed3058
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997652"
---
# <a name="sort-with-order-by-visual-database-tools"></a>Sortieren mit ORDER BY (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Sie können mithilfe einer ORDER BY-Klausel die Abfrageergebnisse nach einer oder mehreren Spalten in den zurückgegebenen Zeilen sortieren. Sie können eine ORDER BY-Klausel definieren, indem Sie Optionen im Kriteriendetailbereich auswählen.  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>So sortieren Sie eine Abfrage mit einer ORDER BY-Klausel  
  
1.  Öffnen Sie eine Abfrage, oder erstellen Sie eine neue.  
  
2.  Klicken Sie im [Kriterienbereich](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)auf die Spalte **Sortierungsart** für die Zeile, die der Spalte entspricht, nach der die Abfrageergebnisse sortiert werden sollen.  
  
3.  Wählen Sie *Aufsteigend* oder *Absteigend* aus der Dropdownliste aus.  
  
> [!NOTE]  
> Durch das Entfernen des Eintrags **Sortierungsart** für eine Spalte wird diese aus der ORDER BY-Klausel entfernt.  
  
Beachten Sie beim Arbeiten im Kriterienbereich, dass die UNION-Klausel der Abfrage entsprechend der zuletzt ausgeführten Aktionen geändert wird.  
  
> [!NOTE]  
> Geben Sie beim Sortieren mehrerer Spalten mithilfe der Spalte **Sortierreihenfolge** die Reihenfolge an, in der die Spalten relativ zueinander durchsucht werden. Weitere Informationen finden Sie unter **Gewusst wie: Sortieren mehrerer Spalten in Abfragen**.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Sortieren und Gruppieren von Abfrageergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Zusammenfassen von Abfrageergebnissen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
