---
title: InstanceOf (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52e6d5e3bf8aa433d7956d758ae20174fd9e71c0
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36258192"
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Eine Methode, die die Übereinstimmung der **geometry**-Instanz mit dem angegebenen Typ überprüft. Gibt 1 zurück, wenn der Typ einer **geometry**-Instanz mit dem angegebenen Typ übereinstimmt oder der angegebene Typ ein Vorgänger des Instanztyps ist. Andernfalls wird 0 zurückgegeben.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>Argumente  
 *geometry_type*  
 Eine **nvarchar(4000)**-Zeichenfolge, die einen von 15 Typen angibt, die in der **geometry**-Typhierarchie verfügbar gemacht werden.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Die Eingabe für die Methode muss einem der folgenden Typen entsprechen: **Geometry**, **Point**, **Curve**, **LineString**, **CircularString**, **CompoundCurve**, **Surface**, **Polygon**, **CurvePolygon**, **GeometryCollection**, **MultiSurface**, **MultiPolygon**, **MultiCurve**, **MultiLineString** oder **MultiPoint**. Diese Methode löst eine **ArgumentException** aus, wenn andere Zeichenfolgen für die Eingabe verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `MultiPoint`-Instanz erstellt und `InstanceOf()` verwendet, um zu überprüfen, ob die Instanz eine `GeometryCollection` ist.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

