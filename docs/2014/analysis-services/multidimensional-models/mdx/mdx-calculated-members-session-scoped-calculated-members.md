---
title: Erstellen im Bereich einer Sitzung berechnete Elemente (MDX) | Microsoft-Dokumentation
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
- CREATE MEMBER statement
- session-scoped calculated members [MDX]
ms.assetid: 2875ed89-2c26-4645-8ed9-8848479d110f
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 79e6466c7f514b3453f8840a72dc0028a215259b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249860"
---
# <a name="creating-session-scoped-calculated-members-mdx"></a>Erstellen berechneter Elemente im Bereich einer Sitzung (MDX)
  Zum Erstellen eines berechneten Elements, das während einer gesamten MDX-Sitzung (Multidimensional Expressions) verfügbar ist, verwenden Sie die [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member)-Anweisung. Ein berechnetes Element, das mit der CREATE MEMBER-Anweisung erstellt wurde, wird erst entfernt, nachdem die MDX-Sitzung geschlossen wurde.  
  
 Wie in diesem Thema erläutert wird, ist die Syntax der CREATE MEMBER-Anweisung unkompliziert und einfach zu verwenden.  
  
> [!NOTE]  
>  Weitere Informationen zu berechneten Elementen finden Sie unter [Erstellen von berechneten Elementen in MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
## <a name="create-member-syntax"></a>Syntax von CREATE MEMBER  
 Verwenden Sie die folgende Syntax, um der MDX-Anweisung die CREATE MEMBER-Anweisung hinzuzufügen:  
  
```  
CREATE [SESSION] MEMBER [<cube-name>.]<fully-qualified-member-name> AS <expression> [,<property-definition-list>]  
<cube name> ::= CURRENTCUBE | <Cube Name>  
<property-definition-list> ::= <property-definition>  
  | <property-definition>, <property-definition-list>  
<property-definition> ::= <property-identifier> = <property-value>  
<property-identifier> ::= VISIBLE | SOLVEORDER | SOLVE_ORDER | FORMAT_STRING | NON_EMPTY_BEHAVIOR <ole db member properties>  
```  
  
 In der Syntax für die CREATE MEMBER-Anweisung entspricht der `fully-qualified-member-name` -Wert dem vollqualifizierten Namen des berechneten Elements. Der vollqualifizierte Name enthält die Dimension oder Ebene, der das berechnete Element zugeordnet ist. Der `expression` -Wert gibt den Wert des berechneten Elements zurück, nachdem der Wert des Ausdrucks ausgewertet wurde.  
  
## <a name="create-member-example"></a>Beispiel zu CREATE MEMBER  
 Im folgenden Beispiel wird die CREATE MEMBER-Anweisung dazu verwendet, das berechnete Element `LastFourStores` zu erstellen. Dieses berechnete Element gibt die Summe der verkauften Einheiten für die letzten vier Filialen zurück und ist während der gesamten Cubesitzung verfügbar.  
  
```  
Create Session Member [Store].[Measures].LastFourStores as   
sum(([Stores].[ByLocation].Lag(3) :  
[Stores].[ByLocation].NextMember), [Measures].[Units Sold])  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen im Bereich einer Abfrage berechnete Elemente &#40;MDX&#41;](mdx-calculated-members-query-scoped-calculated-members.md)  
  
  
