---
title: sp_cdc_disable_table (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9450d80191ac611004cc39528820f49949232823
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028328"
---
# <a name="sysspcdcdisabletable-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Deaktiviert Change Data Capture für die angegebene Quelltabelle und die Aufzeichnungsinstanz in der aktuellen Datenbank. Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@source_schema=** ] **"***Source_schema***"**  
 Der Name des Schemas, in dem die Quelltabelle enthalten ist. *Source_schema* ist **Sysname**, hat keinen Standardwert und darf nicht NULL sein.  
  
 *Source_schema* muss in der aktuellen Datenbank vorhanden sein.  
  
 [  **@source_name=** ] **"***Source_name***"**  
 Ist der Name der Quelltabelle, von dem Change Data Capture deaktiviert werden sollte. *Source_name* ist **Sysname**, hat keinen Standardwert und darf nicht NULL sein.  
  
 *Source_name* muss in der aktuellen Datenbank vorhanden sein.  
  
 [  **@capture_instance=** ] **"***Capture_instance***"** | **"** alle **"**  
 Ist der Name der Aufzeichnungsinstanz, der für die angegebene Quelltabelle deaktiviert werden muss. *Capture_instance* ist **Sysname** und darf nicht NULL sein.  
  
 Wenn 'all' angegeben ist, sind alle aufzeichnungsinstanzen für definierten *Source_name* sind deaktiviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 **sp_cdc_disable_table** löscht die Change Data Capture zu ändern und Systemfunktionen, die der angegebenen Quellinstanz und die Aufzeichnungsinstanz zugeordnet. Löscht alle Zeilen verknüpft ist, mit der angegebenen Aufzeichnungsinstanz der Change Data Capture-Systemtabellen und legt die **Is_tracked_by_cdc** Spalte für den Tabelleneintrag in der [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) Katalogsicht auf 0.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Db_owner** festen Datenbankrolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird Change Data Capture für die `HumanResources.Employee`-Tabelle deaktiviert.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
