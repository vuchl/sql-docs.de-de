---
title: MSSQLSERVER_11409 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 58a77d030a59580fd03a8ac9c7160cede94d8914
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34322431"
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|11409|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|ALTERCOL_COLSET_DROP|  
|Meldungstext|Der '%.*ls'-Spaltensatz in der '%.\*ls'-Tabelle kann nicht entfernt werden, da die Tabelle mehr als 1025 Spalten enthält.|  
  
## <a name="explanation"></a>Erklärung  
Tabellen können maximal 1024 Spalten enthalten, die nicht als Spalte mit geringer Dichte oder berechnete Spalte festgelegt sind. Wenn die Tabelle aufgrund von Sparsespalten mehr als 1024 Spalten aufweist, muss für die Tabelle ein Spaltensatz definiert werden. Die Tabelle, auf die verwiesen wird, weist mehr als 1024 Spalten auf, und Sie haben versucht, den Spaltensatz zu entfernen.  
  
## <a name="user-action"></a>Benutzeraktion  
Mit den aktuellen Spalten in der Tabelle müssen Sie den Spaltensatz beibehalten.  
  
Zum Entfernen des Spaltensatzes entfernen Sie zunächst Spalten aus der Tabelle, bis nur noch 1024 Spalten enthalten sind. Dann können Sie den Spaltensatz entfernen.  
  
