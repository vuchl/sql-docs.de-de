---
title: Sys. sql_logins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/20/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sql_logins_TSQL
- sql_logins_TSQL
- sys.sql_logins
- sql_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_logins catalog view
ms.assetid: 0d9c5b09-86fe-40ff-baab-00b7c051402f
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5740dbdf9961d0ab325b0fbfc023d4bd25045a08
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43073460"
---
# <a name="syssqllogins-transact-sql"></a>sys.sql_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  Gibt eine Zeile für jeden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Anmeldenamen zurück.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**\<geerbte Spalten >**|--|Erbt von **Sys. server_principals**.|  
|**is_policy_checked**|**bit**|Kennwortrichtlinie wird überprüft.|  
|**is_expiration_checked**|**bit**|Ablauf des Kennworts wird überprüft.|  
|**password_hash**|**varbinary(256)**|Hash des SQL-Anmeldekennworts. Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet.|  
  
 Eine Liste der Spalten, die in dieser Ansicht erbt, finden Sie unter [Sys. server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
## <a name="remarks"></a>Hinweise  
 Beides anzeigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldenamen für die Authentifizierung und Anmeldung für Windows-Authentifizierung, finden Sie unter [Sys. server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md).  
  
 Wenn eigenständige Datenbankbenutzer aktiviert sind, die Verbindungen hergestellt werden können, ohne Anmeldenamen. Um die Konten identifizieren zu können, finden Sie unter [Sys. database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierungsanmeldung werden der eigene Anmeldename und die sa-Anmeldung angezeigt. Zum Anzeigen anderer Anmeldenamen ist ALTER ANY LOGIN oder eine Berechtigung für den Anmeldenamen erforderlich.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
 [Prinzipale &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
