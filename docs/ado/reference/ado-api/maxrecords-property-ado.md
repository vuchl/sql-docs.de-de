---
title: MaxRecords-Eigenschaft (ADO) | Microsoft Docs
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
- Recordset15::MaxRecords
helpviewer_keywords:
- MaxRecords property [ADO]
ms.assetid: 20c76571-8c9a-482c-a99e-726ab1d93f8b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b83fad35d6bc237e932dad9ed40ab2ae6f4ea279
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35279239"
---
# <a name="maxrecords-property-ado"></a>MaxRecords-Eigenschaft (ADO)
Gibt die maximale Anzahl von Datensätzen, die zum Zurückgeben einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) aus einer Abfrage.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **lange** Wert, der die maximale Anzahl der zurückzugebenden Datensätze angibt. Standard ist 0 (null) (**0**), was bedeutet keine Beschränkung.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **MaxRecords** -Eigenschaft können Sie die Anzahl der Datensätze zu begrenzen, die aus der Datenquelle des Anbieters zurückgibt. Die Standardeinstellung dieser Eigenschaft ist 0 (null), was bedeutet, dass der Anbieter gibt alle angeforderten Datensätze zurück.  
  
 Die **MaxRecords** Eigenschaft gilt Lese-/Schreibzugriff bei der **Recordset** geschlossen ist, und schreibgeschützt, wenn er geöffnet ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für MaxRecords-Eigenschaft (VB)](../../../ado/reference/ado-api/maxrecords-property-example-vb.md)   
 [MaxRecords-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/maxrecords-property-example-vc.md)   
