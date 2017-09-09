---
title: STDifference (Geography-Datentyp) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STDifference_TSQL
- STDifference (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDifference (geography Data Type)
ms.assetid: 1cde5054-b91a-41bb-812a-08c9308738af
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5afb37eb29e63d8cf08e9c158b94385a66d4c41f
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="stdifference-geography-data-type"></a>STDifference (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt ein Objekt zurück, das die Punktmenge einer **geography** -Instanz darstellt, die sich außerhalb einer anderen **geography** -Instanz befindet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STDifference ( other_geography )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geography*  
 Eine andere **Geography** Instanz, der angibt, welche Punkte aus der Instanz entfernen, auf dem STDifference() aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Rückgabetyp: **Geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="exceptions"></a>Ausnahmen  
 Diese Methode löst eine **ArgumentException** aus, wenn die Instanz eine gegenüberliegende Kante enthält.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt immer NULL zurück, wenn die SRIDs (Spatial Reference IDs) der **geography** -Instanzen nicht übereinstimmen.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], der Satz von möglichen Ergebnissen, die auf dem Server zurückgegeben wurde erweitert und **FullGlobe** Instanzen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt räumliche Instanzen, die größer als eine Hemisphäre sind. Im Ergebnis können nur dann Kreisbogensegmente enthalten sein, wenn die Eingabeinstanzen auch Kreisbogensegmente enthalten. Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-computing-the-difference-between-two-geography-instances"></a>A. Berechnen des Unterschiedes zwischen zwei geography-Instanzen  
 Im folgenden Beispiel wird `STDifference()` zum Berechnen der Differenz zwischen zwei **geography** -Instanzen erweitert.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STDifference(@h).ToString();  
```  
  
### <a name="b-using-a-fullglobe-with-stdifference"></a>B. Verwenden eines FullGlobe mit STDifference()  
 Im folgenden Beispiel wird eine Instanz von `FullGlobe` verwendet. Das erste Ergebnis ist eine leere `GeometryCollection` , und das zweite Ergebnis ist eine `Polygon` -Instanz. `STDifference()`Gibt ein leeres `GeometryCollection` bei einem `FullGlobe` Instanz ist der Parameter. Alle Punkte in einer aufrufenden Instanz von `geography` sind in einer Instanz von `FullGlobe` enthalten.  
  
 `DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';`  
  
 `DECLARE @h geography = 'FULLGLOBE';`  
  
 `SELECT @g.STDifference(@h).ToString(),`  
  
 `@h.STDifference(@g).ToString();`  
  
## <a name="see-also"></a>Siehe auch  
 [OGC-Methoden für Geography-Instanzen](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  