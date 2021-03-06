---
title: Flush-Methode (ADO) | Microsoft Docs
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
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 931d8a2546c9a4d5c41d6b2348a7db5d9ad312ef
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278769"
---
# <a name="flush-method-ado"></a>Flush-Methode (ADO)
Erzwingt, dass der Inhalt des der [Stream](../../../ado/reference/ado-api/stream-object-ado.md) verbleiben in der ADO-Puffer, in der zugrunde liegenden Objekts, dem die **Stream** zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann verwendet werden, um den Inhalt des Streampuffers an das zugrunde liegende Objekt zu senden: z. B. den Knoten oder die Datei, die von der URL, die die Quelle der dargestellt die **Stream** Objekt. Diese Methode sollte aufgerufen werden, wenn Sie möchten, um sicherzustellen, dass alle Änderungen, die vorgenommen wurden, mit dem Inhalt des eine **Stream** geschrieben wurden. Allerdings mit ADO ist es nicht in der Regel erforderlich, rufen Sie **leeren**, wie ADO des Puffers so weit wie möglich im Hintergrund kontinuierlich wird geleert. Änderungen an den Inhalt einer **Stream** erfolgt automatisch, nicht zwischengespeichert, bis **leeren** aufgerufen wird.  
  
 Schließen einer **Stream** mit der [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode leert den Inhalt des eine **Stream** automatisch; es ist nicht erforderlich, explizit aufzurufen **leeren**unmittelbar vor dem **schließen**.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
