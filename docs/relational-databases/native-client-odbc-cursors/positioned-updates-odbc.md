---
title: Positionierte Updates (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 38f2dbc6106fb9a911f0ab2266d7eeefcd753167
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43058113"
---
# <a name="positioned-updates-odbc"></a>Positionierte Updates (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC unterstützt zwei Methoden für das Ausführen von positionierten Updates in einem Cursor:  
  
-   **SQLSetPos**  
  
-   WHERE CURRENT OF-Klausel  
  
 Gängigere Möglichkeit ist die Verwendung **SQLSetPos**. Es bietet die folgenden Optionen.  
  
 SQL_POSITION  
 Positioniert den Cursor in einer bestimmten Zeile im aktuellen Rowset.  
  
 SQL_REFRESH  
 Aktualisiert die an die Resultsetspalten gebundenen Programmvariablen mit den Werten aus der Zeile, in der der Cursor zurzeit positioniert ist.  
  
 SQL_UPDATE  
 Aktualisiert die aktuelle Zeile im Cursor mit den Werten aus den an die Resultsetspalten gebundenen Programmvariablen.  
  
 SQL_DELETE  
 Löscht die aktuelle Zeile im Cursor.  
  
 **SQLSetPos** mit einem anweisungsresultset, wenn die Anweisungshandle-Cursorattribute festgelegt sind, auf die Verwendung von Servercursorn verwendet werden kann. Die Resultsetspalten müssen an Programmvariablen gebunden sein. Sobald die Anwendung eine Zeile abgerufen hat aufgerufen **SQLSetPos**(SQL_POSTION) auf, um den Cursor in der Zeile zu positionieren. Die Anwendung könnte dann SQLSetPos(SQL_DELETE) aufrufen, um die aktuelle Zeile zu löschen, oder neue Datenwerte in die gebundenen Programmvariablen verschieben und SQLSetPos(SQL_UPDATE) aufrufen, um die aktuelle Zeile zu aktualisieren.  
  
 Anwendungen können aktualisieren oder löschen Sie eine beliebige Zeile im Rowset mit **SQLSetPos**. Aufrufen von **SQLSetPos** ist eine praktische Alternative zum Erstellen und Ausführen einer SQL-Anweisung. **SQLSetPos** greift auf das aktuelle Rowset und kann verwendet werden, nur nach einem Aufruf von [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Rowsetgröße wird durch einen Aufruf von [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) mit einem attributsargument von SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** verwendet eine neue Rowsetgröße, aber nur nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**. Wenn die Rowsetgröße geändert wird, z. B. **SQLSetPos** wird aufgerufen, und klicken Sie dann **SQLFetch** oder **SQLFetchScroll** aufgerufen wird. Der Aufruf von **SQLSetPos** verwendet die alte Rowsetgröße, aber **SQLFetch** oder **SQLFetchScroll** die neue Rowsetgröße verwendet.  
  
 Die erste Zeile im Rowset ist die Zeile 1. Das RowNumber-Argument in **SQLSetPos** muss eine Zeile im Rowset identifizieren, also muss sein Wert im Bereich zwischen 1 und die Anzahl der Zeilen, die zuletzt abgerufen wurden. Diese ist eventuell kleiner als die Rowsetgröße. Wenn RowNumber 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Beim Löschvorgang von **SQLSetPos** macht die Datenquelle, die eine oder mehrere ausgewählte Zeilen einer Tabelle zu löschen. Zum Löschen von Zeilen mit **SQLSetPos**, die Anwendung ruft **SQLSetPos** mit Operation auf SQL_DELETE und RowNumber auf die Nummer der Zeile zu löschen. Wenn RowNumber 0 ist, werden alle Zeilen im Rowset gelöscht.  
  
 Nach dem **SQLSetPos** zurückgegeben wird, die gelöschte Zeile wird die aktuelle Zeile und des Status SQL_ROW_DELETED. Die Zeile kann nicht verwendet werden, in weiteren positionierten Vorgängen, z. B. Aufrufe von [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) oder **SQLSetPos**.  
  
 Wenn Sie alle Zeilen des Rowsets löschen (' RowNumber ' ist gleich 0), die Anwendung kann verhindern, dass den Treiber bestimmte Zeilen löscht, unter Verwendung des Zeile Vorgang wie für den Updatevorgang des **SQLSetPos**.  
  
 Jede Zeile, die gelöscht wird, sollte eine Zeile sein, die im Resultset vorhanden ist. Wenn die Anwendungspuffer beim Abrufen gefüllt werden und ein Zeilenstatusarray beibehalten wurde, sollten die Werte an jeder Zeilenposition nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.  
  
 Positionierte Updates können auch mit der WHERE CURRENT OF-Klausel für UPDATE-, DELETE- und INSERT-Anweisungen durchgeführt werden. In denen CURRENT OF erfordert ein Cursor zu benennen, der von ODBC generiert wird, wenn die [SQLGetCursorName](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) Funktion aufgerufen wird, oder geben Sie an, durch den Aufruf **SQLSetCursorName**. Im Folgenden finden Sie allgemeine Schritte zum Durchführen eines WHERE CURRENT OF-Updates in einer ODBC-Anwendung:  
  
-   Rufen Sie **SQLSetCursorName** um einen Cursornamen für das Anweisungshandle einzurichten.  
  
-   Erstellen Sie eine SELECT-Anweisung mit einer FOR UPDATE OF-Klausel, und führen Sie sie aus.  
  
-   Rufen Sie **SQLFetchScroll** zum Abrufen eines Rowsets oder **SQLFetch** um eine Zeile abzurufen.  
  
-   Rufen Sie **SQLSetPos** (SQL_POSITION) auf, um den Cursor in der Zeile zu positionieren.  
  
-   Erstellen und Ausführen eine UPDATE-Anweisung mit einer WHERE CURRENT OF-Klausel mit dem cursornamensset mit **SQLSetCursorName**.  
  
 Sie können alternativ Aufrufen **SQLGetCursorName** nach dem Ausführen der SELECT-Anweisung statt **SQLSetCursorName** vor der Ausführung der SELECT-Anweisung. **SQLGetCursorName** ein Standardname-Cursor von ODBC zugewiesen wird, wenn Sie keinen Cursor mit festlegen, gibt **SQLSetCursorName**.  
  
 **SQLSetPos** über WHERE CURRENT OF bevorzugt wird, bei Verwendung von Servercursorn. Wenn Sie einen statischen, aktualisierbaren Cursor mit der ODBC-Cursorbibliothek verwenden, implementiert die Cursorbibliothek die WHERE CURRENT OF-Updates, indem eine WHERE-Klausel mit den Schlüsselwerten für die zugrunde liegende Tabelle hinzugefügt wird. Dies kann zu nicht beabsichtigten Updates führen, wenn die Schlüssel in der Tabelle nicht eindeutig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Cursorn &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
