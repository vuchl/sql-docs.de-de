---
title: Sp_browsemergesnapshotfolder (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_browsemergesnapshotfolder
- sp_browsemergesnapshotfolder_TSQL
helpviewer_keywords:
- sp_browsemergesnapshotfolder
ms.assetid: e248642f-5fea-4ed7-be1a-36ff75abcfde
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 153abe2a9466c6f0496dfe86b852571828111a43
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020998"
---
# <a name="spbrowsemergesnapshotfolder-transact-sql"></a>sp_browsemergesnapshotfolder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den vollständigen Pfad für die aktuellste Momentaufnahme zurück, der für eine Mergeveröffentlichung generiert wurde. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_browsemergesnapshotfolder [@publication= ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publication=**] **'***publication***'**  
 Der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**snapshot_folder**|**Datentyp nvarchar(2000)**|Vollständiger Pfad zum Momentaufnahmeverzeichnis.|  
  
## <a name="remarks"></a>Hinweise  
 **Sp_browsemergesnapshotfolder** wird bei der Mergereplikation verwendet.  
  
 Wenn die Veröffentlichung so eingerichtet ist, dass sie Momentaufnahmedateien sowohl im Arbeitsverzeichnis als auch im Momentaufnahmeordner des Verlegers generiert, dann enthält das Resultset zwei Zeilen: Die erste Zeile enthält den Momentaufnahmeordner der Veröffentlichung, und die zweite Zeile enthält das Arbeitsverzeichnis des Verlegers.  
  
 **Sp_browsemergesnapshotfolder** eignet sich zum Ermitteln des Verzeichnisses, in dem die momentaufnahmedateien generiert werden. Dieser Ordner/Pfad und sein Inhalt können dann auf Wechselmedien kopiert werden. Die Momentaufnahme kann dann dazu verwendet werden, ein Abonnement von einer alternativen Momentaufnahmeposition zu synchronisieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_browsemergesnapshotfolder**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
