---
title: SetEOS-Methode | Microsoft Docs
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
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8821b58e5e111ad879c34f0d3d8177404945a72f
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281609"
---
# <a name="seteos-method"></a>SetEOS-Methode
Legt die Position, die das Ende des Streams fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Hinweise  
 **SetEOS** aktualisiert den Wert der [EOS](../../../ado/reference/ado-api/eos-property.md) Eigenschaft, indem Sie die aktuelle [Position](../../../ado/reference/ado-api/position-property-ado.md) das Ende des Streams. Alle Bytes oder Zeichen nach der aktuellen Position werden abgeschnitten.  
  
 Da [schreiben](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), und [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) in vorhandenen zusätzlichen Werte werden nicht abgeschnitten **Stream** Objekte aufweist, können Sie diese kürzen Byte- oder Zeichensequenz durch Festlegen der neuen Position der End-of-Stream mit **SetEOS**.  
  
> [!CAUTION]
>  Wenn Sie festlegen, **EOS** auf eine Position vor dem tatsächlichen Ende des Streams, alle Daten verloren nach neuen **EOS** Position.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
