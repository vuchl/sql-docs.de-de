---
title: APP_NAME (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 46e34f32e26c847abb4ad30b1bc41aabd0c10f28
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785871"
---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Diese Funktion gibt den Anwendungsnamen der aktuellen Sitzung zurück, falls die Anwendung diesen Namenswert festlegt.
  
> [!IMPORTANT]  
>  Der Client stellt den Anwendungsnamen zur Verfügung. `APP_NAME` überprüft den Anwendungsnamenswert nicht. Verwenden Sie `APP_NAME` nicht als Teil einer Sicherheitsprüfung.  
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
**nvarchar(128)**
  
## <a name="remarks"></a>Remarks  
Verwenden Sie `APP_NAME`, um zwischen den verschiedenen Anwendungen zu unterscheiden, damit Sie verschiedene Aktionen für diese Anwendung durchführen können. `APP_NAME` kann beispielsweise zwischen verschiedenen Anwendungen unterscheiden, damit für jede Anwendung ein anderes Datumsformat verwendet werden kann. Außerdem kann durch diese Funktion eine Nachricht mit Informationen an bestimmte Anwendungen zurückgegeben werden.
  
Klicken Sie zum Festlegen eines Anwendungsnamens in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] im Dialogfeld **Verbindung mit Datenbank-Engine** herstellen auf **Optionen**. Geben Sie auf der Registerkarte **Zusätzliche Verbindungsparameter** das Attribut **app** im Format `;app='application_name'` an.
  
## <a name="example"></a>Beispiel  
Im folgenden Beispiel wird geprüft, ob die Clientanwendung, die diesen Prozess initiiert hat, eine `SQL Server Management Studio`-Sitzung ist. Dann wird ein Datumswert im US- oder ANSI-Format bereitgestellt.
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch
[Systemfunktionen &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[Funktionen](../../t-sql/functions/functions.md)
  
  
