---
title: LockTypeEnum | Microsoft Docs
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
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4137ced62a083bb355a685222a044fdd9efacdf
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279219"
---
# <a name="locktypeenum"></a>LockTypeEnum
Gibt den Typ der Sperre, die auf Datensätze, die während der Bearbeitung platziert werden.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Gibt die vollständige BatchUpdates an. Für Batchmodus-Update erforderlich.|  
|**adLockOptimistic**|3|Gibt an, Parallelität, Datensatz nach dem anderen. Der Anbieter verwendet eingeschränktes Sperren, Sperren von Datensätzen nur bei Aufruf der [Update](../../../ado/reference/ado-api/update-method.md) Methode.|  
|**adLockPessimistic**|2|Gibt das pessimistische Sperren, Datensatz nach dem anderen an. Der Anbieter unterstützt, was erforderlich ist, um sicherzustellen, dass erfolgreiche Bearbeitung der Datensätze in der Regel durch Sperren von Datensätzen in der Datenquelle sofort nach der Bearbeitung ist.|  
|**adLockReadOnly**|1|Gibt an, nur-Lese Datensätze. Sie können die Daten nicht ändern.|  
|**adLockUnspecified**|-1|Gibt einen Typ von Sperre keine. Für Klone wird der Klon mit demselben Sperrentyp wie die ursprüngliche erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Clone-Methode (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType-Eigenschaft (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute-Ereignis (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
