---
title: Ausführen von Anweisungen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b50d6e9cc46e9abdf46e2b3b0a184654d9074b8f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410769"
---
# <a name="executing-statements-odbc"></a>Ausführen von Anweisungen (ODBC)
  Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber bietet verschiedene Möglichkeiten zum Ausführen von SQL-Anweisungen in einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank:  
  
-   Direkte Ausführung  
  
-   Die vorbereitete Ausführung  
  
 Direkte Ausführung erfordert die Bildung einer Zeichenfolge Zeichen mit einem [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisung und die Übermittlung dieser für die Ausführung mit der **SQLExecDirect** Funktion. Die vorbereitete Ausführung erfordert die Bildung einer Zeichenfolge, die eine [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisung enthält, und die Ausführung dieser Anweisung in zwei Phasen. Der ersten Phase wird die [SQLPrepare-Funktion](http://go.microsoft.com/fwlink/?LinkId=59360) zu analysieren und Kompilieren den Ausführungsplan für die Anweisung in der [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Der zweiten Phase wird die **SQLExecute** Funktion, um den zuvor vorbereiteten Ausführungsplan auszuführen. Dadurch wird bei jeder Ausführung der mit der Analyse und Kompilierung verbundene Aufwand reduziert. Die vorbereitete Ausführung wird in Anwendungen häufig verwendet, um dieselbe parametrisierte SQL-Anweisung mehrfach auszuführen.  
  
 Sowohl bei der direkten als auch bei der vorbereiteten Ausführung können einzelne [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen oder Batches von SQL-Anweisungen ausgeführt oder gespeicherte Prozeduren aufgerufen werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Direkte Ausführung](direct-execution.md)  
  
-   [Vorbereitete Ausführung](prepared-execution.md)  
  
-   [Vorgehensweisen](procedures.md)  
  
-   [Batches von Anweisungen](batches-of-statements.md)  
  
-   [Effekte von ISO-Optionen](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Abfragen &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
