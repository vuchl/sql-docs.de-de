---
title: MSSQLSERVER_41301 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41301 (Database Engine error)
ms.assetid: c6127e1e-2846-4ee9-bc42-2d896ea9730e
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9281a679d49329faaee903dd1549c07e5dd88449
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37418779"
---
# <a name="mssqlserver41301"></a>MSSQLSERVER_41301
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41301|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|COMMIT_DEPENDENCY_FAILURE|  
|Meldungstext|Eine vorherige Transaktion, zu der die aktuelle Transaktion eine Abhängigkeit eingegangen war, wurde abgebrochen. Die aktuelle Transaktion kann keinen Commit mehr ausführen.|  
  
## <a name="explanation"></a>Erklärung  
 Bei der Transaktion trat ein Abhängigkeitsfehler auf, sie kann nicht abgeschlossen werden.  
  
 Dieser Fehler kann auch durch zu viele abhängige Transaktionen verursacht werden. Jede Schreibtransaktion kann über eine begrenzte Anzahl abhängiger Transaktionen verfügen. Dieser Fehler kann beispielsweise auftreten, wenn zu viele Lesetransaktionen versuchen, eine Abhängigkeit von der Updatetransaktion herzustellen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Erledigen Sie keine Bearbeitung der Transaktion. Rufen Sie ROLLBACK TRAN auf, um ein Rollback für die Transaktion auszuführen. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
  
