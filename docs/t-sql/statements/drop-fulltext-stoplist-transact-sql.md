---
title: DROP FULLTEXT STOPLIST (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP_FULLTEXT_STOPLIST_TSQL
- DROP FULLTEXT STOPLIST
dev_langs:
- TSQL
helpviewer_keywords:
- DROP FULLTEXT STOPLIST statement
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 3ee2a2bb-1dfb-4e7c-90e9-9d917cd84a15
caps.latest.revision: 24
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 3792a7c675b8a0121908a942dc0e58e61efc074e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37788871"
---
# <a name="drop-fulltext-stoplist-transact-sql"></a>DROP FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Löscht eine Volltext-Stoppliste aus der Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!IMPORTANT]  
>  CREATE FULLTEXT STOPLIST wird nur bei einem Kompatibilitätsgrad von mindestens 100 unterstützt. Bei Kompatibilitätsgraden von 80 und 90 wird die Systemstoppliste immer der Datenbank zugewiesen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP FULLTEXT STOPLIST stoplist_name  
;  
```  
  
## <a name="arguments"></a>Argumente  
 *stoplist_name*  
 Der Name der Volltextstoppliste, die aus der Datenbank gelöscht werden soll.  
  
## <a name="remarks"></a>Remarks  
 DROP FULLTEXT STOPLIST schlägt fehl, wenn Volltextindizes auf die Volltextstoppliste verweisen, die gelöscht wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Löschen einer Stoppliste ist eine DROP-Berechtigung für die Stoppliste oder eine Mitgliedschaft in der festen Datenbankrolle **db_owner** oder **db_ddladmin** erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Volltextstoppliste mit dem Namen `myStoplist` gelöscht.  
  
```  
DROP FULLTEXT STOPLIST myStoplist;  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)  
  
  
