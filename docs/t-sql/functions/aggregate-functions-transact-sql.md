---
title: Aggregatfunktionen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bb2c15fa21847f8306d54213208e99e5da87f25a
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43082122"
---
# <a name="aggregate-functions-transact-sql"></a>Aggregatfunktionen (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Aggregatfunktionen führen Berechnungen für verschiedene Werte durch und geben einen einzelnen Wert zurück. Alle Aggregatfunktionen, außer `COUNT`, ignorieren NULL-Werte. Aggregatfunktionen werden häufig mit der GROUP BY-Klausel der SELECT-Anweisung verwendet.
  
Alle Aggregatfunktionen sind deterministisch. Dies bedeutet, dass Aggregatfunktionen bei jedem Aufruf mit bestimmten Eingabewerten immer den gleichen Wert zurückgeben. Weitere Informationen zu Funktionsdeterminismus finden Sie unter [Deterministische und nicht deterministische Funktionen](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). Die [OVER-Klausel](../../t-sql/queries/select-over-clause-transact-sql.md) folgt möglicherweise allen Aggregatfunktionen außer den Funktionen GROUPING oder GROUPING_ID.
  
Verwenden Sie Aggregatfunktionen nur in folgenden Fällen als Ausdrücke:
-   In der Auswahlliste einer SELECT-Anweisung (Unterabfrage oder äußere Abfrage)  
-   In einer HAVING-Klausel  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] stellt die folgenden Aggregatfunktionen bereit:
  
|||
|-|-|
|[APPROX_COUNT_DISTINCT](../../t-sql/functions/approx-count-distinct-transact-sql.md)| [MIN](../../t-sql/functions/min-transact-sql.md)|
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[STDEV](../../t-sql/functions/stdev-transact-sql.md)|
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|
|[COUNT](../../t-sql/functions/count-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[SUM](../../t-sql/functions/sum-transact-sql.md)|
|[GROUPING](../../t-sql/functions/grouping-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|
|[MAX](../../t-sql/functions/max-transact-sql.md)||
  
## <a name="see-also"></a>Siehe auch
[Integrierte Funktionen &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)  
[OVER-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
