---
title: ProtocolDLL-Eigenschaft (ServerNetworkProtocol-Klasse) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ProtocolDLL Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: ac386558-392e-46f3-97f8-382f267b7fca
caps.latest.revision: 31
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 498fea8f2c2d4b06934b36485decf0cbdd33ddda
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "33010087"
---
# <a name="protocoldll-property-servernetworkprotocol-class"></a>ProtocolDLL-Eigenschaft (ServerNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Namen der .dll-Datei ab, die von einem Servernetzwerkprotokoll benötigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 A [ServerNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , das das Netzwerkprotokoll darstellt, das von der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgewert, der den Namen der -dll-Datei angibt, die vom Server-Netzwerkprotokoll benötigt wird.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
