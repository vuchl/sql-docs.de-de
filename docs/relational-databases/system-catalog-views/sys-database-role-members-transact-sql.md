---
title: database_role_members (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_role_members_TSQL
- sys.database_role_members
- database_role_members_TSQL
- database_role_members
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_role_members catalog view
ms.assetid: ed1b019d-ca48-4db3-85df-cf6d2db591cf
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a310472e8bb8f82845b6af83e7b9b09ee812cb4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43059954"
---
# <a name="sysdatabaserolemembers-transact-sql"></a>sys.database_role_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jedes Mitglied jeder Datenbankrolle zurück.  Datenbankbenutzer, anderen Datenbankrollen und Anwendungsrollen können Mitglieder einer Datenbankrolle sein. Um Mitglieder einer Rolle hinzuzufügen, verwenden Sie die [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md) -Anweisung mit der `ADD MEMBER` Option. Verknüpfen mit [Sys. database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md) die Namen der zurückzugebenden der `principal_id` Werte.
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**role_principal_id**|**int**|Datenbankprinzipal-ID der Rolle.|  
|**member_principal_id**|**int**|Datenbankprinzipal-ID des Elements.|  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann die eigenen Rollenmitgliedschaften anzeigen. Andere Rolle an Mitgliedschaften erfordert die Mitgliedschaft in der `db_securityadmin` feste Datenbankrolle oder `VIEW DEFINITION` für die Datenbank.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage gibt die Mitglieder der Datenbankrollen zurück.  
  
```  
SELECT DP1.name AS DatabaseRoleName,   
   isnull (DP2.name, 'No members') AS DatabaseUserName   
 FROM sys.database_role_members AS DRM  
 RIGHT OUTER JOIN sys.database_principals AS DP1  
   ON DRM.role_principal_id = DP1.principal_id  
 LEFT OUTER JOIN sys.database_principals AS DP2  
   ON DRM.member_principal_id = DP2.principal_id  
WHERE DP1.type = 'R'
ORDER BY DP1.name;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Prinzipale &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
[ALTER ROLE (Transact-SQLL)](../../t-sql/statements/alter-role-transact-sql.md)      
[Sys. server_role_members (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
  


