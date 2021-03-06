---
title: DefaultDatabase-Eigenschaft | Microsoft Docs
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
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b7fc72d99273428a1ab4a11f12a021079d8faac
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277459"
---
# <a name="defaultdatabase-property"></a>DefaultDatabase-Eigenschaft
Gibt an, die Standarddatenbank für einen [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der vom Anbieter den Namen einer verfügbaren Datenbank ergibt.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **DefaultDatabase** Eigenschaft so festlegen oder Zurückgeben der Name der Standarddatenbank für einen bestimmten **Verbindung** Objekt.  
  
 Ist eine Standarddatenbank, möglicherweise SQL-Zeichenfolgen eine unvollständige Syntax verwenden, den Zugriff auf Objekte in dieser Datenbank. Zum Zugreifen auf Objekte in einer anderen Datenbank als die der **DefaultDatabase** -Eigenschaft, müssen Sie mit dem gewünschten Datenbanknamen zu verwendenden Objektnamen qualifizieren. Beim Herstellen der Verbindung, wird der Anbieter Datenbank Standardinformationen zum Schreiben der **DefaultDatabase** Eigenschaft. Einige Anbieter ermöglichen, nur eine Datenbank pro Verbindung, in diesem Fall können Sie ändern die **DefaultDatabase** Eigenschaft.  
  
 Einige Datenquellen und Anbietern können dieses Feature wird nicht unterstützt und möglicherweise einen Fehler oder eine leere Zeichenfolge zurück.  
  
> [!NOTE]
>  **Remote Datendienstnutzung** diese Eigenschaft ist nicht verfügbar für eine clientseitige **Verbindung** Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Anbieter und DefaultDatabase-Eigenschaften-Beispiel (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider- und DefaultDatabase-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
