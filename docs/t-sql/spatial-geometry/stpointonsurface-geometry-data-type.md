---
title: STPointOnSurface (geometry-Datentyp) | Microsoft-Dokumentation
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
- STPointOnSurface (geometry Data Type)
- STPointOnSurface_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STPointOnSurface (geometry Data Type)
ms.assetid: 23b2b8eb-4176-49fb-ace0-92398928d60e
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9aa042a3f907c64c23c44aea3a88e91da94fa1f6
ms.sourcegitcommit: a6596c62f607041c4402f7d5b41a232fca257c14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36256342"
---
# <a name="stpointonsurface-geometry-data-type"></a>STPointOnSurface (geometry-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt einen beliebigen im Inneren einer **geometry** -Instanz enthaltenen Punkt zurück.
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STPointOnSurface ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geometry**  
  
 CLR-Rückgabetyp: **SqlGeometry**  
  
 Open Geospatial Consortium (OGC)-Typ: **Point**  
  
## <a name="remarks"></a>Remarks  
 Diese Methode gibt NULL zurück, wenn die Instanz leer ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `Polygon` -Instanz erstellt und `STPointOnSurface()` verwendet, um einen Punkt auf der Instanz zu finden.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STPointOnSurface().ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [OGC-Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

