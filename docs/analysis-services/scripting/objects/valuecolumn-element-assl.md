---
title: ValueColumn-Element (ASSL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ValueColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- ValueColumn element
ms.assetid: 6c2d6822-8ecc-46df-9fa9-bb92ac716c36
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c17b9dea933e1beee1f4957a9bb6f82c669963be
ms.contentlocale: de-de
ms.lasthandoff: 09/01/2017

---
# <a name="valuecolumn-element-assl"></a>ValueColumn-Element (ASSL)
  Identifiziert die Spalte, die den Wert des übergeordneten Elements bereitstellt.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <ValueColumn xsi:type="DataItem">...</ValueColumn>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Standardwert|Variiert (siehe Hinweise)|  
|Kardinalität|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md) Element des **DimensionAttribute** angegeben wird, die gleiche **DataItem** Werte dienen als Standardwerte für die **ValueColumn** Element. Wenn die **NameColumn** Element des **DimensionAttribute** nicht angegeben wird und die [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md) Auflistung von **DimensionAttribute** enthält ein einziges [KeyColumn](../../../analysis-services/scripting/objects/keycolumn-element-assl.md) Element, das eine Schlüsselspalte mit einem Zeichenfolgen-Datentyp, der darstellt **DataItem** Werte dienen als Standardwerte für die **ValueColumn** Element.  
  
 Weitere Informationen zu den **DataItem** Typ, einschließlich einer Tabelle von Analysis Services Scripting Language (ASSL)-Objekten und Eigenschaften der **DataItem** finden Sie unter [DataItem-Datentyp &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen **NameColumn** im Objektmodell von Analysis Management Objects (AMO) sind <xref:Microsoft.AnalysisServices.DimensionAttribute> und <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [Objekte &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  