---
title: MSSQLSERVER_3961 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3961 (Database Engine error)
ms.assetid: 3bbc6965-6445-400c-940a-2d85b037513f
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8552287ded720ed5aa66eb5675d1a96fb087a76
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34322951"
---
# <a name="mssqlserver3961"></a>MSSQLSERVER_3961
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3961|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|XACT_METADATA_INVALID|  
|Meldungstext|Fehler bei der Momentaufnahmeisolationstransaktion in der '%.*ls'-Datenbank, weil das von der Anweisung zugegriffene Objekt durch eine DDL-Anweisung in einer anderen gleichzeitigen Transaktion seit dem Beginn dieser Transaktion geändert wurde.  Dies ist unzulässig, weil die Metadaten nicht versionsspezifisch sind. Ein gleichzeitiges Update von Metadaten kann in Kombination mit der Momentaufnahmeisolation zu Inkonsistenzen führen.|  
  
## <a name="explanation"></a>Erklärung  
Dieser Fehler kann auftreten, wenn Sie Metadaten unter Momentaufnahmeisolation abfragen und gleichzeitig eine DDL-Anweisung vorhanden ist, die die Metadaten aktualisiert, auf die unter Momentaufnahmeisolation zugegriffen wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine Versionsverwaltung von Metadaten. Aus diesem Grund gibt es bezüglich der DDL-Vorgänge, die in einer unter Momentaufnahmeisolation ausgeführten expliziten Transaktion ausgeführt werden, Einschränkungen. Eine implizite Transaktion ist definitionsgemäß eine einzelne Anweisung, mit der die Semantik der Momentaufnahmeisolation auch in DDL-Anweisungen erzwungen werden kann. Die folgenden DDL-Anweisungen sind nach einer BEGIN TRANSACTION-Anweisung unter Momentaufnahmeisolation nicht zulässig: ALTER TABLE, CREATE INDEX, CREATE XML INDEX, ALTER INDEX, DROP INDEX, DBCC REINDEX, ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME sowie alle CLR (Common Language Runtime)-DDL-Anweisungen. Diese Anweisungen sind zulässig, wenn die Momentaufnahmeisolation in impliziten Transaktionen verwendet wird. Eine implizite Transaktion ist definitionsgemäß eine einzelne Anweisung, mit der die Semantik der Momentaufnahmeisolation auch in DDL-Anweisungen erzwungen werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
Ändern Sie die Momentaufnahmeisolationsstufe vor dem Abfragen von Metadaten in eine Isolationsstufe, bei der es sich nicht um eine Momentaufnahmeisolationsstufe handelt, z. B. Read Committed.  
  
