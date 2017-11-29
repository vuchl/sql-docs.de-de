---
title: Sp_helprolemember (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helprolemember_TSQL
- sp_helprolemember
dev_langs: TSQL
helpviewer_keywords: sp_helprolemember
ms.assetid: 42797510-aa5d-4564-85ac-27418419af9c
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: afdfcf6f89a398f20f4281249662e5c7b52852d3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="sphelprolemember-transact-sql"></a>sp_helprolemember (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu den direkten Mitgliedern einer Rolle in der aktuellen Datenbank zurück.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis zur [aktuellen Version](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helprolemember [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@rolename =** ] **"** *Rolle* **"**  
 Der Name der Datenbankrolle in der aktuellen Datenbank. *role* ist vom Datentyp **sysname**und hat den Standardwert NULL. *role* muss in der aktuellen Datenbank vorhanden sein. Wenn *role* nicht angegeben wird, werden alle Rollen zurückgegeben, die mindestens ein Mitglied aus der aktuellen Datenbank enthalten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**DbRole**|**sysname**|Name der Rolle in der aktuellen Datenbank.|  
|**MemberName**|**sysname**|Name eines Mitglieds von **DbRole**.|  
|**MemberSID**|**varbinary (85)**|Sicherheits-ID von **MemberName**.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Datenbank geschachtelte Rollen enthält, ist **MemberName** möglicherweise der Name einer Rolle. **sp_helprolemember** zeigt keine Mitgliedschaft an, die über geschachtelte Rollen erworben wurde. Beispiel: Wenn User1 Mitglied von Role1 und Role1 Mitglied von Role2 ist, gibt `EXEC sp_helprolemember 'Role2'`; Role1, aber nicht die Mitglieder von Role1 (in diesem Beispiel User1) zurück. Um geschachtelte Mitgliedschaften zurückzugeben, müssen Sie **sp_helprolemember** wiederholt für jede geschachtelte Rolle ausführen.  
  
 Mithilfe von **sp_helpsrvrolemember** zeigen Sie die Mitglieder einer festen Serverrolle an.  
  
 Verwendung [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md) zum Überprüfen der Mitgliedschaft in Datenbankrolle für einen angegebenen Benutzer.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die Mitglieder der `Sales` -Rolle angezeigt.  
  
```  
EXEC sp_helprolemember 'Sales';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [Sp_droprolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [Sp_helprole &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [Sp_helpsrvrolemember &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  