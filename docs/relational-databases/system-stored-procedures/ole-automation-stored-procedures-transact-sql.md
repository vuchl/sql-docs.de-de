---
title: OLE Automation gespeicherte Prozeduren (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system stored procedures [SQL Server], OLE Automation
- OLE Automation [SQL Server], stored procedures
ms.assetid: ff16a833-01fe-4877-8aa6-55b72603ec2e
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 015dfe6c9e296a839ea9b558336b0f7e572bc192
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020178"
---
# <a name="ole-automation-stored-procedures-transact-sql"></a>Gespeicherte OLE-Automatisierungsprozeduren (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt die folgenden gespeicherten Systemprozeduren, die die Verwendung von OLE-Automatisierungsobjekten in einem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch zulassen. Standardmäßig blockiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Zugriff auf gespeicherte OLE-Automatisierungsprozeduren, da diese Komponente im Rahmen der Sicherheitskonfiguration für diesen Server deaktiviert wird. Ein Systemadministrator kann den Zugriff auf OLE-Automatisierungsprozeduren mit sp_configure aktivieren. Weitere Informationen finden Sie unter [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
|||  
|-|-|  
|[sp_OACreate](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md)|[sp_OAMethod](../../relational-databases/system-stored-procedures/sp-oamethod-transact-sql.md)|  
|[sp_OADestroy](../../relational-databases/system-stored-procedures/sp-oadestroy-transact-sql.md)|[sp_OASetProperty](../../relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql.md)|  
|[sp_OAGetErrorInfo](../../relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql.md)|[sp_OAStop](../../relational-databases/system-stored-procedures/sp-oastop-transact-sql.md)|  
|[sp_OAGetProperty](../../relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql.md)|[Objekthierarchiesyntax &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsprozeduren (Serverkonfigurationsoption)](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
