---
title: MultiPolygon | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPolygon geometry subtype [SQL Server]
- geometry subtypes [SQL Server]
ms.assetid: 2c5db358-2a16-49d9-aac5-a74e86813932
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3ae25be65e0fdf0cf88bf8dec6cf5c3f59f9c9e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311402"
---
# <a name="multipolygon"></a>MultiPolygon
  Ein `MultiPolygon` -Instanz ist eine Sammlung von NULL oder mehr `Polygon` Instanzen.  
  
## <a name="polygon-instances"></a>Polygon-Instanzen  
 Die nachfolgende Abbildung enthält Beispiele für `MultiPolygon` Instanzen.  
  
 ![Beispiele für MultiPolygon-Geometrieinstanzen](../../database-engine/media/multipolygon.gif "Examples of geometry MultiPolygon instances")  
  
 Folgendes wird dargestellt:  
  
-   Abbildung 1 zeigt eine `MultiPolygon` -Instanz mit zwei `Polygon` Elemente. Die Begrenzung wird durch die beiden äußeren Ringe und die drei inneren Ringe definiert.  
  
-   Abbildung 2 zeigt eine `MultiPolygon`-Instanz mit zwei `Polygon`-Elementen. Die Begrenzung wird durch die beiden äußeren Ringe und die drei inneren Ringe definiert. Die beiden `Polygon`-Elemente überschneiden sich an einem Tangentenpunkt.  
  
### <a name="accepted-instances"></a>Akzeptierte Instanzen  
 Ein `MultiPolygon` -Instanz wird akzeptiert, eine der folgenden Bedingungen erfüllt ist.  
  
-   Es ist eine leere `MultiPolygon` Instanz.  
  
-   Alle Instanzen, die mit der `MultiPolygon` Instanz akzeptiert `Polygon` Instanzen. Weitere Informationen über akzeptierte `Polygon` -Instanzen finden Sie unter [Polygon](../spatial/polygon.md).  
  
 Die folgenden Beispiele zeigen, akzeptierte `MultiPolygon` Instanzen.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
```  
  
 Das folgende Beispiel zeigt eine MultiPolygon-Instanz, die eine `System.FormatException`auslöst.  
  
```  
DECLARE @g geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3)))';  
```  
  
 Die zweite Instanz im MultiPolygon ist eine LineString-Instanz und keine akzeptierte Polygon-Instanz.  
  
### <a name="valid-instances"></a>Gültige Instanzen  
 Eine `MultiPolygon`-Instanz ist gültig, wenn es sich um eine leere `MultiPolygon`-Instanz handelt bzw. wenn die folgenden Kriterien erfüllt werden.  
  
1.  Alle Instanzen, aus denen die `MultiPolygon`-Instanz besteht, sind gültige `Polygon`-Instanzen. Für gültige `Polygon` -Instanzen finden Sie unter [Polygon](../spatial/polygon.md).  
  
2.  Die `Polygon`-Instanzen, aus denen die `MultiPolygon`-Instanz besteht, überschneiden sich nicht.  
  
 Im folgende Beispiel werden zwei gültige `MultiPolygon`-Instanzen und eine ungültige `MultiPolygon`-Instanz veranschaulicht.  
  
```  
DECLARE @g1 geometry = 'MULTIPOLYGON EMPTY';  
DECLARE @g2 geometry = 'MULTIPOLYGON(((1 1, 1 -1, -1 -1, -1 1, 1 1)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
DECLARE @g3 geometry = 'MULTIPOLYGON(((2 2, 2 -2, -2 -2, -2 2, 2 2)),((1 1, 3 1, 3 3, 1 3, 1 1)))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 `@g2` gültig ist da die beiden `Polygon` -Instanzen nur an einem tangenspunkt berühren. `@g3` gilt nicht da die Innenbereiche der zwei `Polygon` -Instanzen überlappen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Erstellung einer `geometry``MultiPolygon` -Instanz veranschaulicht und das WKT-Format (Well-Known Text) der zweiten Komponente zurückgegeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON(((0 0, 0 3, 3 3, 3 0, 0 0), (1 1, 1 2, 2 1, 1 1)), ((9 9, 9 10, 10 9, 9 9)))');  
SELECT @g.STGeometryN(2).STAsText();  
```  
  
 In diesem Beispiel wird eine leere `MultiPolygon` -Instanz instantiiert.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::Parse('MULTIPOLYGON EMPTY');  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Polygon](../spatial/polygon.md)   
 [STArea &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/starea-geometry-data-type)   
 [STCentroid &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stcentroid-geometry-data-type)   
 [STPointOnSurface &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [Räumliche Daten &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)  
  
  
