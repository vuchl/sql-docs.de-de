---
title: SET OFFSETS (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
caps.latest.revision: 25
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b40204e252142b7b72962326ccc37e2174d3a811
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38045828"
---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt den Offset (die relative Position zum Start einer Anweisung) der angegebenen Schlüsselwörter in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen an DB-Library-Anwendungen zurück.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>Argumente  
 *keyword_list*  
 Eine durch Trennzeichen getrennte Liste von [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukten, einschließlich SELECT, FROM, ORDER, TABLE, PROCEDURE, STATEMENT, PARAM und EXECUTE.  
  
## <a name="remarks"></a>Remarks  
 SET OFFSETS wird nur in DB-Library-Anwendungen verwendet.  
  
 Die Einstellung von SET OFFSETS wird zur Ausführungszeit und nicht zur Analysezeit festgelegt. Ein Festlegen zur Analysezeit bedeutet Folgendes: Befindet sich die SET-Anweisung im Batch oder in der gespeicherten Prozedur, wird die Einstellung unabhängig davon wirksam, ob die Codeausführung tatsächlich diesen Punkt erreicht, und die SET-Anweisung wird wirksam, bevor Anweisungen ausgeführt werden. Auch wenn sich die SET-Anweisung z. B. in einem IF...ELSE-Anweisungsblock befindet, der während der Ausführung niemals erreicht wird, ist die SET-Anweisung dennoch wirksam, da der IF...ELSE-Anweisungsblock analysiert wird.  
  
 Wird SET OFFSETS in einer gespeicherten Prozedur festgelegt, so wird der Wert von SET OFFSETS wiederhergestellt, nachdem die gespeicherte Prozedur die Steuerung zurückgegeben hat. Daher hat eine SET OFFSETS-Anweisung, die in einer dynamischem SQL-Anweisung angegeben wird, keine Auswirkung auf die Anweisungen, die der dynamischen SQL-Anweisung folgen.  
  
 SET PARSEONLY gibt Offsets zurück, wenn SET OFFSETS auf ON festgelegt ist und keine Fehler auftreten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SET-Anweisungen (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET PARSEONLY &#40;Transact-SQL&#41;](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  
