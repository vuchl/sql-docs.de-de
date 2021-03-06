---
title: Nach dem Upgrade neue reservierte Schlüsselwörter nicht als Bezeichner verwendet werden können | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- keywords [SQL Server], after upgrade
- keywords [SQL Server], reserved
- keywords [SQL Server]
ms.assetid: cb242081-54f8-4273-a8ef-52f3751c25ef
caps.latest.revision: 10
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bc7569837d0442b23e16c365ea1076b734f23892
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172117"
---
# <a name="after-upgrade-new-reserved-keywords-cannot-be-used-as-identifiers"></a>Nach dem Upgrade können neue reservierte Schlüsselwörter nicht als Bezeichner verwendet werden
  Der Upgrade Advisor hat die Verwendung von Wörtern erkannt, die als Schlüsselwörter reserviert sind. Ein reserviertes Schlüsselwort kann nicht als Bezeichner oder Objektname verwendet werden, es sei denn, der Name ist mit Trennzeichen versehen.  
  
## <a name="component"></a>Komponente  
 Datenbank-Engine  
  
## <a name="description"></a>Description  
 Bei Kompatibilitätsgrad 90 oder niedriger sind die folgenden Wörter keine reservierten Schlüsselwörter und können in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skripts als Bezeichner oder Objektnamen verwendet werden. Bei Kompatibilitätsgrad 100 sind diese Wörter vollständig reservierte Schlüsselwörter und sollten nicht als Bezeichner oder Objektnamen verwendet werden.  
  
-   EXTERNAL  
  
-   MERGE  
  
-   PIVOT  
  
-   REVERT  
  
-   STOPLIST  
  
-   TABLESAMPLE  
  
-   UNPIVOT  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Es wird empfohlen, das Objekt umzubenennen. Falls dies vor dem Upgrade nicht möglich ist, können Sie eine der folgenden Methoden verwenden, bis der Name geändert werden kann:  
  
-   Behalten Sie die Einstellung von 90 oder niedriger für den Datenbankkompatibilitätsgrad bei.  
  
-   Verweisen Sie mit Begrenzungsbezeichnern auf das Objekt. Z. B. die Anweisung `CREATE TABLE [MERGE] ([MERGE] int);` Klammern verwendet, um den Objektnamen MERGE zu begrenzen.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 [Reservierte Schlüsselwörter &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reserved-keywords-transact-sql)  
  
 [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql)  
  
 [Begrenzungsbezeichner (Datenbank-Engine)](http://go.microsoft.com/fwlink/?LinkId=112509)  
  
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
