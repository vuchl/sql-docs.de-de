---
title: GetRoot (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- GetRoot
- GetRoot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetRoot [Database Engine]
ms.assetid: 240b70f1-eeda-44ab-b4bb-9e4af80fa7c0
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4b654e40e947603518ac53e28a7d5a1b9213aa7d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427399"
---
# <a name="getroot-database-engine"></a>GetRoot (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Gibt den Stamm der Hierarchiestruktur zurück. GetRoot() ist eine statische Methode.
  
## <a name="syntax"></a>Syntax  
  
```sql
-- Transact-SQL syntax  
hierarchyid::GetRoot ( )   
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId GetRoot ( )   
```  
  
## <a name="return-types"></a>Rückgabetypen  
**SQL Server-Rückgabetyp: hierarchyid**
  
**CLR-Rückgabetyp: SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
Wird verwendet, um den Stammknoten in einer Hierarchiestruktur zu bestimmen.
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-transact-sql-example"></a>A. Beispiel für Transact-SQL  
Im folgenden Beispiel wird der Stamm der Hierarchiestruktur zurückgegeben.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = hierarchyid::GetRoot()  
```  
  
### <a name="b-clr-example"></a>B. CLR-Beispiel  
Im folgenden Codeausschnitt wird die GetRoot()-Methode aufgerufen:
  
```sql
SqlHierarchyId.GetRoot()  
```  
  
## <a name="see-also"></a>Siehe auch
[hierarchyid-Datentyp-Methodenverweis](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Hierarchische Daten &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
