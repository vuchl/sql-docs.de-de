---
title: STRelate (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STRelate (geometry Data Type)
- STRelate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRelate (geometry Data Type)
ms.assetid: 9dcb5f58-35ab-4bb3-86ee-2d29eefba6d3
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 42391c371038037ce474052e5f293db82b71f831
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38039698"
---
# <a name="strelate-geometry-data-type"></a>STRelate (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt 1 zurück, wenn eine **geometry** -Instanz auf eine andere **geometry** -Instanz bezogen ist, wobei die Beziehung durch einen Mustermatrizenwert eines DE-9IM-Modells (Dimensionally Extended 9 Intersection Model) definiert wird. Andernfalls wird 0 zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STRelate ( other_geometry, intersection_pattern_matrix )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geometry*  
 Eine andere **geometry** -Instanz zum Vergleich mit der Instanz, in der `STRelate()` aufgerufen wird.  
  
 *intersection_pattern_matrix*  
 Eine Zeichenfolge vom Typ **nchar(9)** , die akzeptable Werte für das DE-9IM-Mustermatrizengerät zwischen den beiden **geometry** -Instanzen codiert.  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt immer NULL zurück, wenn die SRIDs (Spatial Reference IDs) der **geometry** -Instanzen nicht übereinstimmen. Diese Methode löst eine **ArgumentException** aus, wenn die Matrix nicht wohlgeformt ist.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STRelate()` verwendet, um mithilfe eines expliziten DE-9IM-Musters zwei **geometry** -Instanzen auf räumliche Disjunktion zu testen.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 2, 2 0, 4 2)', 0);  
SET @h = geometry::STGeomFromText('POINT(5 5)', 0);  
SELECT @g.STRelate(@h, 'FF*FF****');  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
