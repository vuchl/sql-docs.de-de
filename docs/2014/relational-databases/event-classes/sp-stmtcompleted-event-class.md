---
title: Ereignisklasse „SP:StmtCompleted“ | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SP:StmtCompleted event class
ms.assetid: 9e8147a4-aeeb-49a6-80f8-df753d0f34cc
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 44191b710b96e5339649a783efbd7f9d27f7a09a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217380"
---
# <a name="spstmtcompleted-event-class"></a>SP:StmtCompleted-Ereignisklasse
  Die SP:StmtCompleted-Ereignisklasse gibt an, dass eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung in einer gespeicherten Prozedur abgeschlossen wurde.  
  
## <a name="spstmtcompleted-event-class-data-columns"></a>Datenspalten der SP:StmtCompleted-Ereignisklasse  
  
|Datenspaltenname|`Data type`|Description|Column ID|Filterbar|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|ja|  
|CPU|`int`|Die CPU-Zeit (in Millisekunden), die vom Ereignis verwendet wurde.|18|ja|  
|DatabaseID|`int`|ID der Datenbank, in der die gespeicherte Prozedur ausgeführt wird. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die gespeicherte Prozedur ausgeführt wird.|35|ja|  
|Duration|`bigint`|Die Zeit (in Mikrosekunden), die für das Ereignis benötigt wurde.|13|ja|  
|EndTime|`datetime`|Der Zeitpunkt, zu dem das Ereignis beendet wurde. Diese Spalte wird für Startereignisklassen (z. B. SQL:BatchStarting oder SP:Starting) nicht aufgefüllt.|15|ja|  
|EventClass|`int`|Ereignistyp = 45.|27|nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|ja|  
|IntegerData|`int`|Wert für eine ganze Zahl, der von der in der Ablaufverfolgung erfassten Ereignisklasse abhängt.|25|ja|  
|IntegerData2|`int`|Endoffset (in Bytes) der Anweisung, die gerade ausgeführt wird.|55|ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|ja|  
|LineNumber|`int`|Die Zeilennummer der Anweisung, die gerade ausgeführt wird.|5|ja|  
|LoginName|`nvarchar`|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|ja|  
|NestLevel|`int`|Ganze Zahl, die die von @@NESTLEVEL zurückgegebenen Daten darstellt.|29|ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|ja|  
|ObjectID|`int`|Vom System zugewiesene ID des Objekts.|22|ja|  
|ObjectName|`nvarchar`|Name des Objekts, auf das verwiesen wird|34|ja|  
|ObjectType|`int`|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in der sys.objects-Katalogsicht. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](objecttype-trace-event-column.md).|28|ja|  
|Offset|`int`|Der Startoffset der Anweisung in der gespeicherten Prozedur oder im Batch.|61|ja|  
|Reads|`bigint`|Die Anzahl der logischen Lesevorgänge auf dem Datenträger, die vom Server aufgrund dieses Ereignisses ausgeführt werden.|16|ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|ja|  
|RowCounts|`bigint`|Die Anzahl der von einem Ereignis betroffenen Zeilen.|48|ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|ja|  
|SourceDatabaseID|`int`|Die ID der Datenbank, in der das Objekt vorhanden ist.|62|ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|ja|  
|TextData|`ntext`|Textwert, der von der Ereignisklasse abhängt, die in der Ablaufverfolgung aufgezeichnet wurde.|1|ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|ja|  
|Writes|`bigint`|Die Anzahl physischer Schreibvorgänge auf dem Datenträger, die vom Server aufgrund des Ereignisses ausgeführt werden.|17|ja|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|ja|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
