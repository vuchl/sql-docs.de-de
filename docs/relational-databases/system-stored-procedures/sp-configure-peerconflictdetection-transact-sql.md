---
title: Sp_configure_peerconflictdetection (Transact-SQL) | Microsoft-Dokumentation
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
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords:
- sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07555d1f5e26538b1bdf980c65d5f08cfa546717
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031657"
---
# <a name="spconfigurepeerconflictdetection-transact-sql"></a>sp_configure_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Konfiguriert die Konflikterkennung für eine Veröffentlichung, die Teil einer Peer-zu-Peer-Transaktionsreplikationstopologie ist. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md). Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_configure_peerconflictdetection [ @publication = ] 'publication'  
    [ , [ @action = ] 'action']  
    [ , [ @originator_id = ] originator_id ]  
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @continue_onconflict = ] 'continue_onconflict']  
    [ , [ @local = ] 'local']  
    [ , [ @timeout = ] timeout ]  
  
```  
  
## <a name="arguments"></a>Argumente  
 [ @publication=] '*publication*'  
 Der Name der Veröffentlichung, für die die Konflikterkennung konfiguriert werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ @action=] '*Aktion*"  
 Gibt an, ob die Konflikterkennung für eine Veröffentlichung aktiviert oder deaktiviert werden soll. *Aktion* ist **nvarchar(5)**, und kann einen der folgenden Werte.  
  
|value|Description|  
|-----------|-----------------|  
|**Aktivieren**|Aktiviert die Konflikterkennung für eine Veröffentlichung.|  
|**disable**|Deaktiviert die Konflikterkennung für eine Veröffentlichung.|  
|NULL (Standard)||  
  
 [ @originator_id= ] *originator_id*  
 Gibt eine ID für einen Knoten in einer Peer-zu-Peer-Topologie an. *Originator_id* ist **Int**, hat den Standardwert NULL. Diese ID wird für die konflikterkennung verwendet, wenn *Aktion* nastaven NA hodnotu **aktivieren**. Geben Sie eine positive ID ungleich 0 an, die in der Topologie noch nicht verwendet wurde. Zum Anzeigen einer Liste der bereits verwendeten IDs fragen Sie die [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) -Systemtabelle ab.  
  
 [ @conflict_retention= ] *conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict=] '*Continue_onconflict*']  
 Legt fest, ob der Verteilungs-Agent nach Erkennung eines Konflikts die Verarbeitung von Änderungen fortsetzt. *Continue_onconflict* ist **nvarchar(5)** hat den Standardwert "false".  
  
> [!CAUTION]  
>  Es wird empfohlen, den Standardwert FALSE zu verwenden. Wenn diese Option auf TRUE festgelegt wird, versucht der Verteilungs-Agent, die Datenkonvergenz in der Topologie herbeizuführen, indem die konfliktverursachende Zeile von dem Knoten mit der höchsten Absender-ID angewendet wird. Bei dieser Methode ist keine Konvergenz garantiert. Sie sollten sicherstellen, dass die Topologie nach der Erkennung eines Konflikts konsistent ist. Weitere Informationen finden Sie im Abschnitt "Konfliktbehandlung" unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [ @local= ] '*local*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout= ] *timeout*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_configure_peerconflictdetection wird in der Peer-zu-Peer-Transaktionsreplikation verwendet. Um die Verwendung der konflikterkennung müssen auf allen Knoten ausgeführt werden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder späteren Versionen verwendet werden und die Erkennung muss für alle Knoten aktiviert sein.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle sysadmin oder in der festen Datenbankrolle db_owner.  
  
## <a name="see-also"></a>Siehe auch  
 [Konflikterkennung bei der Peer-zu-Peer-Replikation](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
