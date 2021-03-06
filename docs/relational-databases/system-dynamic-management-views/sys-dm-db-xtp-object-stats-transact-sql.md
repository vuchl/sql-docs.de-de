---
title: Sys. dm_db_xtp_object_stats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_xtp_object_stats_TSQL
- sys.dm_db_xtp_object_stats
- dm_db_xtp_object_stats
- sys.dm_db_xtp_object_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_xtp_object_stats dynamic management view
ms.assetid: 07300b59-3cab-4d3e-8138-5ea8f584f88f
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b1d4185fe00e3038a07cc6cd80c286375d865a96
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43063631"
---
# <a name="sysdmdbxtpobjectstats-transact-sql"></a>sys.dm_db_xtp_object_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Gibt die Anzahl der von Operationen auf allen betroffenen Zeilen die [!INCLUDE[hek_2](../../includes/hek-2-md.md)] Objekte seit dem letzten Neustart. Die Statistiken werden aktualisiert, wenn der Vorgang ausgeführt wird, und zwar unabhängig davon, ob für die Transaktion ein Commit oder Rollback ausgeführt wurde.  
  
 Mithilfe von sys.dm_db_xtp_object_stats können Sie ermitteln, welche speicheroptimierten Tabellen am häufigsten geändert werden. Sie können selten oder nicht verwendete Tabellenindizes entfernen, da jeder Index die Leistung beeinflusst. Bei Verwendung von Hashindizes sollte die Bucketanzahl regelmäßig neu ausgewertet werden. Weitere Informationen finden Sie unter [Determining the Correct Bucket Count for Hash Indexes](http://msdn.microsoft.com/library/6d1ac280-87db-4bd8-ad43-54353647d8b5).  
  
 Mithilfe von sys.dm_db_xtp_object_stats können Sie ermitteln, welche speicheroptimierten Tabellen Write-Write-Konflikte verursachen, die möglicherweise die Anwendungsleistung beeinträchtigen. Wenn Sie beispielsweise Wiederholungslogik für Transaktionen implementiert haben, muss ein und dieselbe Anweisung u. U. mehrfach ausgeführt werden. Außerdem können Sie anhand dieser Informationen die Tabellen (und folglich die Geschäftslogik) identifizieren, die eine Behandlung von Write-Write-Fehlern erfordern.  
  
 Diese Sicht enthält eine Zeile für jede speicheroptimierte Tabelle in der Datenbank.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|object_id|**bigint**|Die ID des Objekts.|  
|row_insert_attempts|**bigint**|Die Anzahl der Zeilen, die seit dem letzten Neustart der Datenbank von Transaktionen, für die ein Commit oder Abbruch ausgeführt wurde, in die Tabelle eingefügt wurden.|  
|row_update_attempts|**bigint**|Die Anzahl der Zeilen, die seit dem letzten Neustart der Datenbank von Transaktionen, für die ein Commit oder Abbruch ausgeführt wurde, in der Tabelle aktualisiert wurden.|  
|row_delete_attempts|**bigint**|Die Anzahl der Zeilen, die seit dem letzten Neustart der Datenbank von Transaktionen, für die ein Commit oder Abbruch ausgeführt wurde, aus der Tabelle gelöscht wurden.|  
|write_conflicts|**bigint**|Die Anzahl der Schreibkonflikte, die seit dem letzten Neustart der Datenbank aufgetreten sind.|  
|unique_constraint_violations|**bigint**|Die Anzahl der Verletzungen von UNIQUE-Einschränkungen, die seit dem letzten Neustart der Datenbank aufgetreten sind.|  
|object_address|**varbinary(8)**|Nur interne Verwendung.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW DATABASE STATE-Berechtigung für die aktuelle Datenbank.  
  
## <a name="see-also"></a>Siehe auch  
 [Eine Speicheroptimierte Tabelle dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
