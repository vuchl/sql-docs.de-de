---
title: Operatoren für äußere Joins *= und =* werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 579565320855694166f57039402e3fbef14183d5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255442"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Operatoren für äußere Joins *= und =* werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt
  Der Upgrade Advisor hat festgestellt, dass Operatoren für äußere Joins * = und =\*. Diese Operatoren werden im Kompatibilitätsmodus 90 oder höher nicht unterstützt. Beim Upgrade behalten die Benutzerdatenbanken ihren Kompatibilitätsmodus bei. Anweisungen, die diese Operatoren verwenden, führen zu einem Fehler.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Bevor Sie die Datenbank-Kompatibilitätsmodus auf 90 oder höher ändern, ändern Sie Anweisungen, Operatoren für äußere Joins verwenden * = und =\* entsprechende OUTER JOIN-Schlüsselwörter verwenden. Im folgenden Beispiel wird eine Abfrage gezeigt, die den `*=`-Operator verwendet, sowie eine entsprechende Abfrage, die das `LEFT OUTER JOIN`-Schlüsselwort verwendet.  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 Weitere Informationen zu äußeren Joins finden Sie unter "Verwenden von äußeren Joins" in der SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
