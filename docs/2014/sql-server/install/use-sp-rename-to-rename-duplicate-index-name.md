---
title: Verwenden Sie Sp_rename, benennen Sie die doppelten Indexnamen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 522fcd712882d031a5febe4766946a31d5696859
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37232510"
---
# <a name="use-sprename-to-rename-duplicate-index-name"></a>Verwenden Sie bei doppelten Indexnamen 'sp_rename' zum Umbenennen
  Der Upgrade Advisor hat doppelte Tabellen- oder Sichtindexnamen erkannt. Vor dem Upgrade müssen Sie die Indizes umbenennen, um Duplikate zu entfernen.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
  
1.  Suchen Sie die doppelten Indizes durch Ausführen der folgenden Abfrage.  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  Verwendung **Sp_rename** ändern Sie einen der Indexnamen. Da die Indexnamen identisch sind, können Sie nicht bestimmen, welcher Index umbenannt wird. Durch diesen Schritt können Sie die Indizes unterscheiden.  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  Überprüfen Sie durch Ausführen der folgenden Abfrage, welcher Index umbenannt wurde. Diese Abfrage gibt alle Indizes (einschließlich der Schlüsselspaltennamen) für die angegebene Tabelle oder Sicht zurück.  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  Verwenden Sie bei Bedarf **Sp_rename** erneut aus, um die Indexnamen zu korrigieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
