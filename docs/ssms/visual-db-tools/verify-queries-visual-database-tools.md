---
title: Überprüfen von Abfragen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3848b8cc758dde890c06711b4bea4e70cd137bb2
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38052988"
---
# <a name="verify-queries-visual-database-tools"></a>Überprüfen von Abfragen (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Um Probleme zu vermeiden, können Sie die erstellte Abfrage auf richtige Syntax überprüfen. Diese Option ist insbesondere dann nützlich, wenn Sie Anweisungen im [SQL-Bereich](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)eingeben.  
  
Einige Hinweise, die beim Überprüfen von Abfragen bedacht werden sollten:  
  
-   Eine Anweisung kann gültig und daher problemlos überprüfbar sein, auch wenn sie sich im **Diagrammbereich** und **Kriterienbereich**nicht darstellen lässt.  
  
-   Bei einer SQL-Überprüfung werden einige, aber möglicherweise nicht alle SQL-Fehler erkannt. Wenn eine Abfrage einen bei der SQL-Überprüfung nicht erkannten Fehler enthält, erkennt die Datenbank den Fehler beim Ausführen der Abfrage.  
  
-   Abfragen, die Parameter enthalten, können nicht überprüft werden.  
  
### <a name="to-verify-an-sql-statement"></a>So überprüfen Sie eine SQL-Anweisung  
  
-   Klicken Sie mit der rechten Maustaste in den **SQL-Bereich**, und wählen Sie im Kontextmenü den Befehl **SQL-Syntax überprüfen** aus.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Ausführen von Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
