---
title: UpdateCells-Element (XMLA) | Microsoft-Dokumentation
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
- UpdateCells Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.updatecells
- urn:schemas-microsoft-com:xml-analysis#UpdateCells
- http://schemas.microsoft.com/analysisservices/2003/engine#UpdateCells
helpviewer_keywords:
- UpdateCells command
ms.assetid: 18336a35-8a46-4532-9ee7-71828b2982af
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 05b3b1dae8f409f367a88b696accb77484304b4e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219980"
---
# <a name="updatecells-element-xmla"></a>UpdateCells-Element (XMLA)
  Aktualisiert Zellen in einem Cube mit aktiviertem Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<Command>  
   <UpdateCells>  
      <Cell>...</Cell>  
   </UpdateCells>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|InclusionThresholdSetting|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-n: Optionales Element, das mehr als einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnete Elemente|[Befehl](../xml-elements-properties/command-element-xmla.md)|  
|Untergeordnete Elemente|[Zelle](../xml-elements-properties/cell-element-xmla.md)|  
  
## <a name="remarks"></a>Hinweise  
 Die `UpdateCells` Befehl aktualisiert Zellen in einem Cube, der Zellenrückschreiben unterstützt.  
  
 Weitere Informationen zum Aktualisieren von Zellen finden Sie unter [Aktualisieren von Zellen &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Drop-Element &#40;XMLA&#41;](drop-element-xmla.md)   
 [INSERT-Element &#40;XMLA&#41;](insert-element-xmla.md)   
 [Update-Element &#40;XMLA&#41;](update-element-xmla.md)   
 [Befehle &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
