---
title: Sys. server_permissions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.server_permissions_TSQL
- sys.server_permissions
- server_permissions
- server_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_permissions catalog view
ms.assetid: 7d78bf17-6c64-4166-bd0b-9e9e20992136
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b8340a2e0f71d656f5137f4783d4673b81e1459
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43098658"
---
# <a name="sysserverpermissions-transact-sql"></a>sys.server_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Gibt eine Zeile für jede Berechtigung auf Serverebene zurück.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|Identifiziert die Klasse, in der die Berechtigung vorhanden ist.<br /><br /> 100 = Server<br /><br /> 101 = Serverprinzipal<br /><br /> 105 = Endpunkt|  
|**class_desc**|**nvarchar(60)**|Beschreibung der Klasse, in der die Berechtigung vorhanden ist. Einer der folgenden Werte:<br /><br /> **SERVER**<br /><br /> **SERVER_PRINCIPAL**<br /><br /> **ENDPOINT**|  
|**major_id**|**int**|ID des sicherbaren Elements, für das die Berechtigung vorhanden ist. Der Wert wird gemäß der Klasse interpretiert. Bei den meisten Elementen ist dies die ID, die die Klasse darstellt. Die Interpretation für Elemente, die nicht dem Standard entsprechen, lautet wie folgt:<br /><br /> 100 = immer 0|  
|**minor_id**|**int**|Sekundäre ID des Elements, für das die Berechtigung vorhanden ist. Der Wert wird gemäß der Klasse interpretiert.|  
|**grantee_principal_id**|**int**|Serverprinzipal-ID, der die Berechtigungen erteilt werden.|  
|**grantor_principal_id**|**int**|Serverprinzipal-ID des Berechtigenden dieser Berechtigungen.|  
|**type**|**char(4)**|Typ der Serverberechtigung. Eine Liste der Berechtigungstypen finden Sie in der folgenden Tabelle.|  
|**permission_name**|**nvarchar(128)**|Berechtigungsname.|  
|**state**|**char(1)**|Der Berechtigungsstatus:<br /><br /> D = Verweigern<br /><br /> R = Aufheben<br /><br /> G = Erteilen<br /><br /> W = Mit Grant-Option erteilen|  
|**state_desc**|**nvarchar(60)**|Beschreibung des Berechtigungsstatus:<br /><br /> DENY<br /><br /> REVOKE<br /><br /> GRANT<br /><br /> GRANT_WITH_GRANT_OPTION|  
  
|Berechtigungstyp|Berechtigungsname|Betroffenes sicherungsfähiges Element|  
|---------------------|---------------------|--------------------------|  
|ADBO|ADMINISTER BULK OPERATIONS|SERVER|  
|AL|ALTER|ENDPOINT, LOGIN|  
|ALCD|ALTER ANY CREDENTIAL|SERVER|  
|ALCO|ALTER ANY CONNECTION|SERVER|  
|ALDB|ALTER ANY DATABASE|SERVER|  
|ALES|ALTER ANY EVENT NOTIFICATION|SERVER|  
|ALHE|ALTER ANY ENDPOINT|SERVER|  
|ALLG|ALTER ANY LOGIN|SERVER|  
|ALLS|ALTER ANY LINKED SERVER|SERVER|  
|ALRS|ALTER RESOURCES|SERVER|  
|ALSS|ALTER SERVER STATE|SERVER|  
|ALST|ALTER SETTINGS|SERVER|  
|ALTR|ALTER TRACE|SERVER|  
|AUTH|AUTHENTICATE SERVER|SERVER|  
|CL|CONTROL|ENDPOINT, LOGIN|  
|CL|CONTROL SERVER|SERVER|  
|CO|CONNECT|ENDPOINT|  
|COSQ|CONNECT SQL|SERVER|  
|CRDB|CREATE ANY DATABASE|SERVER|  
|CRDE|CREATE DDL EVENT NOTIFICATION|SERVER|  
|CRHE|CREATE ENDPOINT|SERVER|  
|CRTE|CREATE TRACE EVENT NOTIFICATION|SERVER|  
|IM|IMPERSONATE|Anmeldung|  
|SHDN|SHUTDOWN|SERVER|  
|TO|TAKE OWNERSHIP|ENDPOINT|  
|VW|VIEW DEFINITION|ENDPOINT, LOGIN|  
|VWAD|VIEW ANY DEFINITION|SERVER|  
|VWDB|VIEW ANY DATABASE|SERVER|  
|VWSS|VIEW SERVER STATE|SERVER|  
|XA|EXTERNAL ACCESS|SERVER|  
  
## <a name="permissions"></a>Berechtigungen  
 Jedem Benutzer werden die eigenen Berechtigungen angezeigt. Zum Anzeigen der Berechtigungen für andere Anmeldungen ist die VIEW DEFINITION-Berechtigung, die ALTER ANY LOGIN-Berechtigung oder eine beliebige Berechtigung für die betreffende Anmeldung erforderlich. Zum Anzeigen benutzerdefinierter Serverrollen ist ALTER ANY SERVER ROLE oder die Mitgliedschaft in der Rolle erforderlich.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Mit der folgenden Abfrage werden die Berechtigungen aufgelistet, die Serverprinzipalen ausdrücklich gewährt oder verweigert wurden.  
  
> [!IMPORTANT]  
>  Die Berechtigungen von festen Serverrollen werden nicht in sys.server_permissions aufgeführt. Daher können Serverprinzipale über zusätzliche Berechtigungen verfügen, die hier nicht aufgeführt werden.  
  
```  
SELECT pr.principal_id, pr.name, pr.type_desc,   
    pe.state_desc, pe.permission_name   
FROM sys.server_principals AS pr   
JOIN sys.server_permissions AS pe   
    ON pe.grantee_principal_id = pr.principal_id;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 
  [Berechtigungen &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Berechtigungshierarchie &amp;#40;Datenbank-Engine&amp;#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
  
  
