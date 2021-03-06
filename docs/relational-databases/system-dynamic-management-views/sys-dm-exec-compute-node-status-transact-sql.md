---
title: dm_exec_compute_node_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DM_EXEC_COMPUTE_NODE_STATUS_TSQL
- DM_EXEC_COMPUTE_NODE_STATUS
dev_langs:
- TSQL
helpviewer_keywords:
- PolyBase,views
- PolyBase
- dm_exec_compute_node_status
- sys.dm_exec_compute_node_status management view
ms.assetid: b606f91f-3a08-4a4f-bb57-32ae155b3738
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cff2bc47e5ee29ede1e514937dd2e22626c6385c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43077793"
---
# <a name="sysdmexeccomputenodestatus-transact-sql"></a>dm_exec_compute_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Enthält zusätzliche Informationen über die Leistung und den Status aller PolyBase-Knoten. Enthält eine Zeile pro Knoten an.  
  
|Spaltenname|Datentyp|Description|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|compute_node_id|**int**|Eindeutige numerische Id, die dem Knoten zugeordnet.|Eindeutig erweiterungscluster unabhängig von der Art.|  
|process_id|**int**|||  
|process_name|**nvarchar(255)**|Logischer Name des Knotens.|Jede Zeichenfolge der Länge der entsprechenden.|  
|allocated_memory|**bigint**|Insgesamt zugeordneter Arbeitsspeicher auf diesem Knoten.||  
|available_memory|**bigint**|Gesamten verfügbaren Arbeitsspeichers auf diesem Knoten.||  
|process_cpu_usage|**bigint**|Gesamt-Prozess-CPU-Nutzung in Ticks.||  
|total_cpu_usage|**bigint**|Gesamte CPU-Auslastung in Ticks.||  
|Thread_Count|**bigint**|Die Gesamtanzahl der Threads auf diesem Knoten.||  
|handle_count|**bigint**|Gesamtanzahl der Handles in Verwendung auf diesem Knoten.||  
|total_elapsed_time|**bigint**|Insgesamt verstrichene Zeit seit System starten oder neu starten.|Insgesamt verstrichene Zeit seit System starten oder neu starten. Überschreitet Total_elapsed_time den maximalen Wert für eine ganze Zahl (rund 24,8 Tage in Millisekunden), wird es Materialisierung Fehler aufgrund einer zu einem Überlauf führen. Der maximale Wert in Millisekunden entspricht rund 24,8 Tage.|  
|is_available|**bit**|Flag, der angibt, ob dieser Knoten verfügbar ist.||  
|sent_time|**datetime**|Zeitpunkt der letzten wurde ein Netzwerk-Paket von diesem gesendet.||  
|received_time|**datetime**|Zeitpunkt der letzten ein das Paket wurde von diesem Knoten gesendet werden.||  
|error_id|**nvarchar(36)**|Eindeutiger Bezeichner des letzten Fehlers, der auf diesem Knoten aufgetreten ist.||  
  
## <a name="see-also"></a>Siehe auch  
 [PolyBase-Problembehandlung mit dynamischen Verwaltungssichten](http://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [Dynamische Verwaltungssichten und -funktionen &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Datenbank &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
