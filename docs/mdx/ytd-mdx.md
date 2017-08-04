---
title: YTD (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- YTD
dev_langs:
- kbMDX
helpviewer_keywords:
- Ytd function
ms.assetid: b77fdba2-d4a9-4271-8c21-c1f12eba526d
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 99600f9684215a1147b5372c3e912040fb9f122f
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---
# <a name="ytd-mdx"></a>Ytd (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt einen Satz von gleichgeordneten Elementen aus der gleichen Ebene wie ein angegebenes Element aus, beginnend mit dem ersten gleichgeordneten Element und endend mit dem angegebenen Element, entsprechend der Einschränkung durch die *Jahr* in der Zeitdimension.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Elementausdruck nicht angegeben ist, wird die Standardeinstellung ist das aktuelle Element der ersten Hierarchie mit einer Ebene des Typs *Jahre* in der ersten Dimension des Typs *Zeit* in der Measuregruppe.  
  
 Die **Ytd** Funktion ist eine Verknüpfungsfunktion für die [PeriodsToDate](../mdx/periodstodate-mdx.md) Funktion, die Typeigenschaft der Attributhierarchie, auf dem die Ebene basiert, auf festgelegt ist *Jahre*. Somit ist `Ytd(Member_Expression)` äquivalent zu `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Beachten Sie, die diese Funktion nicht verwendet werden, wenn die Type-Eigenschaft, um festgelegt ist *FiscalYears*.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel gibt die Summe aus der `Measures.[Order Quantity]` Elements, aggregiert über die ersten acht Monate des Kalenderjahres 2003 in der `Date` Dimension, aus der **Adventure Works** Cube.  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **YTD** wird häufig in Kombination verwendet, ohne Parameter angegeben wird, was bedeutet, dass die [CurrentMember &#40; MDX &#41; ](../mdx/currentmember-mdx.md) -Funktion wird eine kumulative Summe der Jahr-bis-heute in einem Bericht anzeigen, wie in der folgenden Abfrage gezeigt:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
