---
title: IF-Anweisung (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4975c455b942f053287b344a956a0083c8ca4e1a
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741659"
---
# <a name="mdx-scripting---if"></a>MDX-Skripts - IF


  Führt eine Anweisung aus, wenn die Bedingung erfüllt ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
IF expression THEN assignment END IF  
```  
  
## <a name="arguments"></a>Argumente  
 *expression*  
 Ein MDX-Ausdruck (Multidimensional Expressions), der zu einem booleschen Wert ausgewertet wird, der TRUE oder FALSE zurückgibt.  
  
 *Zuweisung*  
 Ein MDX-Ausdruck, der entweder einem Teilcube oder einer berechneten Eigenschaft einen Wert zuweist.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die IF-Anweisung für die ablaufsteuerung, also im Gegensatz zu den [IIf &#40;MDX&#41; ](../mdx/iif-mdx.md) Funktion und die [CASE-Anweisung &#40;MDX&#41; ](../mdx/case-statement-mdx.md) , nur zum Zurückgeben von Werten oder Objekten verwendet werden kann.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel ist der Gültigkeitsbereich auf die Country-Ebene der Customer Geography-Hierarchie in der Customer-Dimension beschränkt. Wenn das aktuelle Measure „Betrag der Internetsteuern“ ist, dann wird „Betrag der Internetsteuern“ auf 10 festgelegt:  
  
 `SCOPE ([Customer].[Customer Geography].[Country].MEMBERS);`  
  
 `IF Measures.CurrentMember IS [Measures].[Internet Sales Amount] THEN this = 10 END IF;`  
  
 `END SCOPE`;  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
