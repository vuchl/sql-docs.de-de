---
title: STContains (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STContains method (geography)
ms.assetid: b10e8f0a-2926-449a-82ea-be42543420ca
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fe854f678ccbbce782f7b5d4efe2e807526077f4
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38061218"
---
# <a name="stcontains--geography-data-type"></a>STContains (geography-Datentyp)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Gibt an, ob die aufrufende **geography**-Instanz die an die Methode übergebene **geography**-Instanz räumlich enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.STContains ( other_geography )  
```  
  
## <a name="arguments"></a>Argumente  
 *other_geography*  
 Eine andere **geography**-Instanz zum Vergleich mit der Instanz, in der `STContains()` aufgerufen wird.  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **bit**  
  
 CLR-Rückgabetyp: **SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 Gibt 1 zurück, wenn die aufrufende **geography**-Instanz die an die Methode übergebene **geography**-Instanz räumlich enthält, und gibt andernfalls 0 (null) zurück. Gibt **NULL** zurück, wenn die SRID der beiden **geography**-Instanzen nicht übereinstimmt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird `STContains()` verwendet, um zwei `geography`-Instanzen daraufhin zu überprüfen, ob die erste Instanz die zweite Instanz enthält.  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::Parse('CURVEPOLYGON (COMPOUNDCURVE (CIRCULARSTRING (-122.200928 47.454094, -122.810669 47.00648, -122.942505 46.687131, -121.14624 45.786679, -119.119263 46.183634), (-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)))');  
SET @h = geography::Parse('POINT(-121.703796 46.893985)');  
```  
  
 `SELECT @g.STContains(@h);`  
  
  
