---
title: Simulieren einer IF-WHILE EXISTS-Anweisung in einem nativ kompilierten Modul | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0e187c1-cbd9-463c-b417-8a734574f102
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3faef8fa02957cc2e05d336918f5f1b5651ac3bd
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110892"
---
# <a name="simulating-an-if-while-exists-statement-in-a-natively-compiled-module"></a>Simulieren einer IF-WHILE EXISTS-Anweisung in einem nativ kompilierten Modul
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Nativ kompilierte gespeicherte Prozeduren unterstützen in bedingten Anweisungen nicht die **EXISTS** -Klausel, z. B. IF und WHILE.  
  
 Das folgende Beispiel veranschaulicht eine Behelfslösung unter Verwendung einer BIT-Variablen mit einer SELECT-Anweisung zum Simulieren einer EXISTS-Klausel:  
  
```sql  
DECLARE @exists BIT = 0  
SELECT TOP 1 @exists = 1 FROM MyTable WHERE …  
IF @exists = 1  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](../../relational-databases/in-memory-oltp/migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
