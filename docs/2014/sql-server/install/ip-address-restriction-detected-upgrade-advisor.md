---
title: IP-adresseinschränkung erkannt (Upgrade Advisor) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: 9a154455-c68f-4403-a3a7-b90f4d35eecb
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9dd20d23fbb18f67116d021b725796418ea2ccca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323750"
---
# <a name="ip-address-restriction-detected-upgrade-advisor"></a>IP-Adresseinschränkung erkannt (Upgrade Advisor)
  Der Upgrade Advisor hat mindestens eine IP-Adresseinschränkung auf der IIS-Website gefunden, die den Berichtsserver bzw. die virtuellen Verzeichnisse des Berichts-Managers hostet. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt keine systeminterne Unterstützung für IP-Adresseinschränkungen bereit.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native.|  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Das Setup kann keine IP-Adresseinschränkungen für URLs definieren, die für einen aktualisierten Berichtsserver erstellt wurden. Das Upgrade kann fortgesetzt werden, jedoch werden keine IP-Adresseinschränkungen für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-URLs definiert.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Verwenden Sie nach dem Upgrade ISA Server, Ihre Firewallsoftware oder eine andere Lösung, um Anforderungen spezifischer IP-Adressen an den Berichtsserver zuzulassen oder abzuweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Upgradeprobleme bei Reporting Services &#40;Upgrade Advisor&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
