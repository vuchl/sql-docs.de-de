---
title: SetObjectOwner-Methode | Microsoft Docs
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
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a31ac477e2d0d316f1ddda7ebc60b81b6309f15
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286875"
---
# <a name="setobjectowner-method"></a>SetObjectOwner-Methode
Gibt den Besitzer eines Objekts in einem [Katalog](../../../ado/reference/adox-api/catalog-object-adox.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parameter  
 *ObjectName*  
 Ein **Zeichenfolge** Wert, der den Namen des Objekts, für das an den Besitzer angibt.  
  
 *ObjectType*  
 Ein **lange** Wert sein kann von der [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) Konstanten, der den Besitzertyp angibt.  
  
 *OwnerName*  
 Ein **Zeichenfolge** Wert, der angibt, die [Namen](../../../ado/reference/adox-api/name-property-adox.md) von der [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) oder [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) zum Besitzer des Objekts.  
  
 *ObjectTypeId*  
 Optional. Ein **Variant** Wert, der die GUID für einen Anbietertyp für das Objekt angibt, die nicht vom OLE DB-Spezifikation definiert ist. Dieser Parameter ist erforderlich, wenn *ObjectType* festgelegt ist, um **AdPermObjProviderSpecific**ist, andernfalls ist er nicht verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Wenn der Anbieter keine Angabe Objektbesitzer unterstützt wird, tritt ein Fehler auf.  
  
## <a name="applies-to"></a>Gilt für  
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>Siehe auch  
 [GetObjectOwner- und SetObjectOwner Methoden Beispiel (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner-Methode (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
