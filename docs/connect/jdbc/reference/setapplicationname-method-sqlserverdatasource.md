---
title: SetApplicationName-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 661e8a31ad3fc240c1e8e51f03f2e4132e96fdc7
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784216"
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>setApplicationName-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Anwendungsnamen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *applicationName*  
  
 Ein **String-Objekt**, das den Namen der Anwendung enthält.  
  
## <a name="remarks"></a>Remarks  
 Anhand des Anwendungsnamens wird die jeweilige Anwendung in den verschiedenen Profilerstellungs- und Protokollierungstools von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identifiziert. Ist der Anwendungsname nicht festgelegt, wird von der getApplicationName-Methode die nicht lokalisierte Zeichenfolge "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]" zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
