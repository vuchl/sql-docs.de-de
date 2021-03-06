---
title: Unterstützt Methode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5788431361aa73999b819a09f76a0c4bef268c83
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282579"
---
# <a name="supports-method"></a>Unterstützt-Methode
Bestimmt, ob ein angegebener [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt unterstützt eine bestimmte Art von Funktionen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **booleschen** Wert, der angibt, ob alle Funktionen von identifiziert die *CursorOptions* Argument vom Anbieter unterstützt werden.  
  
#### <a name="parameters"></a>Parameter  
 *CursorOptions*  
 Ein **lange** Ausdruck, der eine oder mehrere besteht [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) Werte.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **unterstützt** Methode, um zu bestimmen, welche Arten von Funktionen einer **Recordset** -Objekt unterstützt. Wenn die **Recordset** Objekt unterstützt die Funktionen, deren entsprechenden Konstanten in sind *CursorOptions*, **unterstützt** -Methode zurückkehrt **"true"**. Andernfalls wird zurückgegeben **"false"**.  
  
> [!NOTE]
>  Obwohl die **unterstützt** Methode gelegten **"true"** für eine bestimmte Funktionalität kann nicht garantiert, dass der Anbieter das Feature unter allen Umständen verfügbar machen kann. Die **unterstützt** Methode gibt einfach auftragsantwortnachrichten zurück, ob der Anbieter unterstützt den angegebenen Funktionen können unter bestimmten Bedingungen erfüllt sind. Z. B. die **unterstützt** Methode hinweisen, die eine **Recordset** Objekt Updates unterstützt, auch wenn der Cursor auf einer Verknüpfung mit mehreren Tabellen basiert einige Spalten der sind nicht aktualisierbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützt-Methode (Beispiel) (VB)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Unterstützt-Methode (VC++-Beispiel)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [CursorType-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
