---
title: STAT-Methode | Microsoft Docs
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
- _Stream::Stat
helpviewer_keywords:
- Stat method [ADO]
ms.assetid: 99a2b2d4-e6b1-4205-b011-72d024ea7240
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b900386c1890d54ec61d3bfd2328f3d173c9300
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282019"
---
# <a name="stat-method"></a>STAT-Methode
Ruft Informationen zu einem [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Long stream.Stat(StatStg, StatFlag)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **lange** Wert, der angibt, des Status des Vorgangs.  
  
#### <a name="parameters"></a>Parameter  
 *StatStg*  
 Eine STATSTG-Struktur, die mit Informationen über den Stream ausgefüllt wird. Die Implementierung der **Stat** vom ADO-Stream-Objekt verwendete Methode ist nicht in alle Felder der Struktur aufgefüllt.  
  
 *StatFlag*  
 Gibt an, dass diese Methode nicht Teil der Mitglieder in der STATSTG-Struktur, und speichern daher ein speicherbelegungsvorgang zurückgibt. Werte werden aus der Enumeration STATFLAG aufgefasst. Die STATFLAG-Enumeration hat zwei Werte  
  
|Konstante|value|  
|--------------|-----------|  
|STATFLAG_DEFAULT|0|  
|STATFLAG_NONAME|1|  
  
## <a name="remarks"></a>Hinweise  
 Die Version der Stat-Methode für das ADO-Stream-Objekt implementiert füllt die folgenden Felder der STATSTG-Struktur:  
  
 *pwcsName*  
 Eine Zeichenfolge, die mit dem Namen des Streams, sofern verfügbar und den Wert StatFlag STATFLAG_NONAME wurde nicht angegeben.  
  
 *cbSize*  
 Gibt die Größe des Datenstroms oder Bytearrays in Bytes an.  
  
 *mtime*  
 Gibt den Zeitpunkt der letzten Änderung dieses Speichers, Datenstroms oder Bytearrays an.  
  
 *ctime*  
 Gibt die Erstellungszeit dieses Speichers, Datenstroms oder Bytearrays Array an.  
  
 *atime*  
 Gibt die Uhrzeit des Letztes Zugriffs für dieses Speichers, Datenstroms oder Bytearrays Array an.  
  
 Wenn STATFLAG_NONAME im StatFlag-Parameter angegeben wird, wird der Name des Datenstroms nicht zurückgegeben.  
  
 Wenn STATFLAG_NONAME im StatFlag-Parameter nicht angegeben wurde und kein Name für den aktuellen Stream verfügbar ist, wird dieser Wert E_NOTIMPL sein.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
