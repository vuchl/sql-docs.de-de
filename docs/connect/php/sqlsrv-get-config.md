---
title: Sqlsrv_get_config | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60437df28456c949d3a03cb58cef89136acbdf2d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "37991282"
---
# <a name="sqlsrvgetconfig"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt den aktuellen Wert der angegebenen Konfigurationseinstellung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>Parameter  
*$setting*: Die Konfigurationseinstellung für die der Wert zurückgegeben wird. Eine Liste der konfigurierbaren Einstellungen finden Sie unter [sqlsrv_configure](../../connect/php/sqlsrv-configure.md).  
  
## <a name="return-value"></a>Rückgabewert  
Der Wert der Einstellung, angegeben durch den *$setting* -Parameter. Wenn eine ungültige Einstellung angegeben wird, wird **false** zurückgegeben und ein Fehler wird zur Fehlersammlung hinzugefügt.  
  
## <a name="remarks"></a>Remarks  
Wenn **false** von **sqlsrv_get_config**zurückgegeben wird, müssen Sie [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) aufrufen, um zu bestimmen, ob ein Fehler aufgetreten ist oder ob **false** der Wert der durch den *$setting* -Parameter.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  

[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
