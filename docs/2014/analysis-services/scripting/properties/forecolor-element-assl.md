---
title: ForeColor-Element (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ForeColor Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeColor
helpviewer_keywords:
- ForeColor element
ms.assetid: 5125520c-3bce-40e6-a722-8d4d47306fed
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: efcd4c226743ec313e338eea4af83ba68792b675
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332830"
---
# <a name="forecolor-element-assl"></a>ForeColor-Element (ASSL)
  Beschreibt farbbezogene Anzeigeeigenschaften der [CalculationProperty](../objects/calculationproperty-element-assl.md) oder [Measure](../objects/measure-element-assl.md) übergeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <ForeColor>...</ForeColor>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[CalculationProperty](../objects/calculationproperty-element-assl.md), [Measure](../objects/measure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die `ForeColor` -Eigenschaft enthält einen Ausdruck für MDX (Multidimensional Expressions) und gilt für `CalculationProperty` Elemente mit einem [CalculationType](calculationtype-element-assl.md) von *Member* oder *Zellen* .  
  
 Die Elemente, die den übergeordneten Elementen von entsprechen `ForeColor` im Analysis Management Objects (AMO)-Objektmodell werden <xref:Microsoft.AnalysisServices.CalculationProperty> und <xref:Microsoft.AnalysisServices.Measure>.  
  
## <a name="see-also"></a>Siehe auch  
 [CalculationProperties-Element &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript-Element &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts-Element &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
