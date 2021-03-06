---
title: Kardinalitätsschätzung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cardinality estimator
- CE (cardinality estimator)
- estimating cardinality
ms.assetid: baa8a304-5713-4cfe-a699-345e819ce6df
caps.latest.revision: 11
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a7f4ed8039cbce77ae6f1350631cc0329c358af7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43073383"
---
# <a name="cardinality-estimation-sql-server"></a>Kardinalitätsschätzung (SQL Server)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Dieser Artikel veranschaulicht, wie Sie die beste Konfiguration für die Kardinalitätsschätzung (Cardinality Estimation, CE) für Ihr SQL-System bewerten und auswählen. Die meisten Systeme profitieren von der neuesten Kardinalitätsschätzung, da sie die genaueste ist. Die Kardinalitätsschätzung sagt vorher, wie viele Zeilen eine Abfrage wahrscheinlich zurückgibt. Die Vorhersage der Kardinalität wird vom Abfrageoptimierer verwendet, um einen optimalen Abfrageplan zu generieren. Mit genaueren Schätzungen kann der Abfrageoptimierer in der Regel einen besseren Abfrageplan erzeugen.  
  
Möglicherweise existiert in Ihrem Anwendungssystem eine wichtige Abfrage, deren Plan während einer neuen Kardinalitätsschätzung in einen langsameren Plan geändert wird. Hier einige Beispiele für eine solche Abfrage:  
  
- Eine OLTP-Abfrage (Onlinetransaktionsverarbeitung), die so häufig ausgeführt wird, dass oft mehrere Instanzen der Abfrage gleichzeitig ausgeführt werden.  
- Eine SELECT-Anweisung mit erheblicher Aggregation, die während der OLTP-Betriebszeiten ausgeführt wird.  
  
Sie verfügen über Techniken, um eine Abfrage zu identifizieren, die mit der neuen Kardinalitätsschätzung langsamer ausgeführt wird. Und Sie verfügen über Optionen, wie Sie das Leistungsproblem beheben.     
  
## <a name="versions-of-the-ce"></a>Versionen der Kardinalitätsschätzung  
1998 war ein großes Update der Kardinalitätsschätzung Teil von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0, dessen Kompatibilitätsgrad 70 betrug. Diese Version des Modells der Kardinalitätsschätzung baut auf vier grundlegenden Annahmen auf:

-  **Unabhängigkeit:** Es wird angenommen, dass Datenverteilungen in verschiedenen Spalten unabhängig voneinander sind, es sei denn, Korrelationsinformationen sind verfügbar und verwendbar.
-  **Einheitlichkeit:** DISTINCT-Werte haben denselben Abstand und dieselbe Häufigkeit. Genauer gesagt, sind DISTINCT-Werte innerhalb der Schritte eines [Histogramms](../../relational-databases/statistics/statistics.md#histogram) gleichmäßig verteilt, und jeder Wert weist dieselbe Häufigkeit auf. 
-  **Einschluss (einfach):** Benutzer fragen Daten ab, die bereits vorhanden sind. Bei einem Gleichheits-Join von zwei Tabellen sollten Sie z.B. die Selektivität<sup>1</sup> von Prädikaten in jedem Eingabehistogramm berücksichtigen, bevor Sie Histogramme verknüpfen, um die Joinselektivität zu schätzen. 
-  **Aufnahme:** Bei Filterprädikaten, in denen `Column = Constant` gilt, wird angenommen, dass sie für die zugeordnete Spalte tatsächlich vorhanden sind. Wenn ein entsprechender Histogrammschritt nicht leer ist, wird angenommen, dass einer der DISTINCT-Werte des Schritts dem Wert des Prädikats entspricht.

  <sup>1</sup> Zeilenanzahl, die dem Prädikat entspricht

Spätere Updates beginnen mit [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], also mit Kompatibilitätsgrad 120 und höher. Die Updates der Kardinalitätsschätzung für die Kompatibilitätsgrade 120 und höher umfassen aktualisierte Annahmen und Algorithmen, die für moderne Data Warehousing- und OLTP-Workloads gut funktionieren. Aus den Annahmen der Kardinalitätsschätzung 70 wurden ab Kardinalitätsschätzung 120 die folgenden Modellannahmen geändert:

-  **Unabhängigkeit** wird zu **Korrelation**: Die Kombination der verschiedenen Spaltenwerte ist nicht unbedingt unabhängig. Dies ähnelt eher einer realistischen Datenabfrage.
-  Der **einfache Einschluss** wird zum **Basiseinschluss**: Benutzer können Daten abfragen, die nicht vorhanden sind. Bei einem Gleichheits-Join von zwei Tabellen nutzen wir die Basistabellenhistogramme, um die Joinselektivität zu schätzen, und berücksichtigen anschließend die Selektivität der Prädikate.
  
**Kompatibilitätsgrad**: Sie können sicherstellen, dass ein bestimmter Grad für Ihre Datenbank gilt, indem Sie den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code für [COMPATIBILITY_LEVEL](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md) ausführen.  

```sql  
SELECT ServerProperty('ProductVersion');  
GO  
  
ALTER DATABASE <yourDatabase>  
SET COMPATIBILITY_LEVEL = 130;  
GO  
  
SELECT d.name, d.compatibility_level  
FROM sys.databases AS d  
WHERE d.name = 'yourDatabase';  
GO  
```  
  
In einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank, die mit dem Kompatibilitätsgrad 120 oder höher eingerichtet wurde, zwingt die Aktivierung des [Ablaufverfolgungsflags 9481](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) das System dazu, Version 70 der Kardinalitätsschätzung zu verwenden.  
  
**Ältere Kardinalitätsschätzung**: In einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank, die mit dem Kompatibilitätsgrad 120 oder höher eingerichtet wurde, kann Version 70 der Kardinalitätsschätzung aktiviert werden. Verwenden Sie dazu [ALTER DATABASE SCOPED CONFIGURATION](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) auf Datenbankebene.
  
```sql  
ALTER DATABASE SCOPED CONFIGURATION 
SET LEGACY_CARDINALITY_ESTIMATION = ON;  
GO  
  
SELECT name, value  
FROM sys.database_scoped_configurations  
WHERE name = 'LEGACY_CARDINALITY_ESTIMATION';  
GO
```  
 
Oder ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 den [Abfragehinweis](../../t-sql/queries/hints-transact-sql-query.md#use_hint) `USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION')`.
 
 ```sql  
SELECT CustomerId, OrderAddedDate  
FROM OrderTable  
WHERE OrderAddedDate >= '2016-05-01'; 
OPTION (USE HINT ('FORCE_LEGACY_CARDINALITY_ESTIMATION'));  
```
 
**Abfragespeicher:** Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ist der Abfragespeicher ein praktisches Tool zum Untersuchen der Leistung Ihrer Abfragen. In [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] wird im **Objekt-Explorer** unterhalb des Knotens Ihrer Datenbank ein Knoten **Abfragespeicher** angezeigt, wenn der Abfragespeicher aktiviert ist.  
  
```sql  
ALTER DATABASE <yourDatabase>  
SET QUERY_STORE = ON;  
GO  
  
SELECT q.actual_state_desc AS [actual_state_desc_of_QueryStore],  
        q.desired_state_desc,  
        q.query_capture_mode_desc  
FROM sys.database_query_store_options AS q;  
GO  
  
ALTER DATABASE <yourDatabase>  
SET QUERY_STORE CLEAR;  
```  
  
> [!TIP] 
> Es wird empfohlen, die neueste Version von [Management Studio](http://msdn.microsoft.com/library/mt238290.aspx) zu installieren und häufig zu aktualisieren.  
  
Eine andere Option zum Nachverfolgen des Prozesses der Kardinalitätsschätzung ist die Verwendung des erweiterten Ereignisses **query_optimizer_estimate_cardinality**. Das folgende [!INCLUDE[tsql](../../includes/tsql-md.md)]-Codebeispiel wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt. Es schreibt eine XEL-Datei in `C:\Temp\` (Sie können den Pfad ändern). Wenn Sie die XEL-Datei in [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] öffnen, werden die detaillierten Daten in einer von Benutzern gut lesbaren Weise angezeigt.  
  
```sql  
DROP EVENT SESSION Test_the_CE_qoec_1 ON SERVER;  
go  
  
CREATE EVENT SESSION Test_the_CE_qoec_1  
ON SERVER  
ADD EVENT sqlserver.query_optimizer_estimate_cardinality  
    (  
        ACTION (sqlserver.sql_text)  
            WHERE (  
                sql_text LIKE '%yourTable%'  
                and sql_text LIKE '%SUM(%'  
            )  
    )  
ADD TARGET package0.asynchronous_file_target   
        (SET  
            filename = 'c:\temp\xe_qoec_1.xel',  
            metadatafile = 'c:\temp\xe_qoec_1.xem'  
        );  
GO  
  
ALTER EVENT SESSION Test_the_CE_qoec_1  
ON SERVER  
STATE = START;  --STOP;  
GO  
```  
  
Informationen zu erweiterten Ereignissen, die speziell auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)] zugeschnitten sind, finden Sie unter [Erweiterte Ereignisse in SQL-Datenbank](http://azure.microsoft.com/documentation/articles/sql-database-xevent-db-diff-from-svr/).  
  
## <a name="steps-to-assess-the-ce-version"></a>Schritte für die Bewertung der Version der Kardinalitätsschätzung  
  
Mit den folgenden Schritten können Sie ermitteln, ob Ihre wichtigsten Abfragen mit der neuesten Kardinalitätsschätzung mit geringerer Leistung ausgeführt werden. In einigen der Schritte wird ein Codebeispiel ausgeführt, das im vorherigen Abschnitt vorgestellt wurde.  
  
1.  Öffnen Sie [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)]. Stellen Sie sicher, dass für Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank der höchste verfügbare Kompatibilitätsgrad festgelegt wurde.  
  
2.  Führen Sie die folgenden vorbereitenden Schritte aus:  
  
    1.  Öffnen Sie [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)].  
  
    2.  Führen Sie T-SQL aus, um sicherzustellen, dass für Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank der höchste verfügbare Kompatibilitätsgrad festgelegt wurde.  
  
    3.  Stellen Sie sicher, dass die `LEGACY_CARDINALITY_ESTIMATION`-Konfiguration Ihrer Datenbank deaktiviert ist.  
  
    4.  Bereinigen Sie Ihren Abfragespeicher (CLEAR). Natürlich müssen Sie auch sicherstellen, dass Ihr Abfragespeicher aktiviert ist.  
  
    5.  Führen Sie die Anweisung `SET NOCOUNT OFF;` aus.  
  
3.  Führen Sie die Anweisung `SET STATISTICS XML ON;` aus.  
  
4.  Führen Sie Ihre wichtige Abfrage aus.  
  
5.  Beachten Sie im Ergebnisbereich auf der Registerkarte **Meldungen** die tatsächliche Anzahl von betroffenen Zeilen.  
  
6.  Doppelklicken Sie im Ergebnisbereich auf der Registerkarte **Ergebnisse** auf die Zelle, die die Statistik im XML-Format enthält. Es wird ein grafischer Abfrageplan angezeigt.  
  
7.  Klicken Sie mit der rechten Maustaste auf das erste Feld im grafischen Abfrageplan, und klicken Sie dann auf **Eigenschaften**.  
  
8.  Notieren Sie die Werte für die folgenden Eigenschaften, um diese später mit einer anderen Konfiguration vergleichen zu können:  
  
    -   **CardinalityEstimationModelVersion**.  
  
    -   **Geschätzte Anzahl von Zeilen**.  
  
    -   **Geschätzte E/A-Kosten**sowie einige weitere ähnliche *geschätzte* Eigenschaften, die sich eher auf die tatsächliche Leistung als auf Vorhersagen zur Zeilenanzahl beziehen.  
  
    -   **Logische Operation** und **Physische Operation**. *Parallelität* ist ein guter Wert.  
  
    -   **Tatsächlicher Ausführungsmodus**. *Batch* ist ein guter Wert und besser als *Zeile*.  
  
9. Vergleichen Sie die geschätzte Anzahl von Zeilen mit der tatsächliche Zeilenanzahl. Ist die Kardinalitätsschätzung um 1% oder um 10% ungenau (höher oder niedriger)?  
  
10. Führen Sie `SET STATISTICS XML OFF;` aus.  
  
11. Führen Sie den T-SQL-Code aus, um den Kompatibilitätsgrad Ihrer Datenbank um eine Stufe zu senken (z.B. von 130 auf 120).  
  
12. Führen Sie alle Schritte erneut aus, die keine Vorbereitungsschritte sind.  
  
13. Vergleichen Sie die Eigenschaftswerte der Kardinalitätsschätzung der beiden Ausführungen.  
  
    - Ist der Prozentsatz der Ungenauigkeit mit der neuesten Kardinalitätsschätzung geringer als mit der älteren?  
  
14. Vergleichen Sie zum Schluss die verschiedenen Leistungswerte der beiden Ausführungen.  
  
    -   Hat Ihre Abfrage bei den beiden verschiedenen Kardinalitätsschätzungen unterschiedliche Abfragepläne verwendet?  
  
    -   Wurde Ihre Abfrage mit der neuesten Kardinalitätsschätzung langsamer ausgeführt?  
  
    -   Wenn Ihre Abfrage nicht mit der älteren Kardinalitätsschätzung besser und unter einem anderen Plan ausgeführt wird als mit der neuen Schätzung, sollten Sie mit größter Wahrscheinlichkeit die neueste Kardinalitätsschätzung verwenden.  
  
    -   Wenn Ihre Abfrage allerdings mit der älteren Kardinalitätsschätzung unter einem schnelleren Plan ausgeführt wird, sollten Sie erwägen, Ihr System zu zwingen, den schnelleren Plan zu verwenden und die Kardinalitätsschätzung zu ignorieren. Auf diese Weise können Sie die neueste Kardinalitätsschätzung allgemein im System verwenden, für Sonderfälle aber den schnelleren Plan beibehalten.  
  
## <a name="how-to-activate-the-best-query-plan"></a>Aktivieren des besten Abfrageplans  
  
Angenommen, mit der Kardinalitätsschätzung 120 oder höher wird ein langsamerer Abfrageplan für Ihre Abfrage generiert. Für diesen Fall finden Sie hier einige Optionen, mit denen Sie den besseren Plan aktivieren können:  
  
1. Sie können den Kompatibilitätsgrad für Ihre gesamte Datenbank auf einen niedrigeren Wert als den neuesten verfügbaren Grad festlegen.  
  
   - Wenn Sie z.B. den Kompatibilitätsgrad auf 110 oder niedriger festlegen, wird die Kardinalitätsschätzung 70 aktiviert, obwohl alle Abfragen dem vorherigen Kardinalitätsschätzungsmodell unterliegen.  
  
   - Beim Festlegen eines niedrigeren Kompatibilitätsgrads werden außerdem viele Verbesserungen des Abfrageoptimierers für die neuesten Versionen nicht genutzt.  
  
2. Sie können die Datenbankoption `LEGACY_CARDINALITY_ESTIMATION` verwenden, sodass die gesamte Datenbank die ältere Kardinalitätsschätzung verwendet, die Verbesserungen des Abfrageoptimierers jedoch beibehalten werden.   

3. Sie können den Abfragehinweis `LEGACY_CARDINALITY_ESTIMATION` verwenden, sodass eine einzelne Abfrage die ältere Kardinalitätsschätzung verwendet, die Verbesserungen des Abfrageoptimierers jedoch beibehalten werden.  
  
Die genaueste Steuerung erzielen Sie, indem Sie *erzwingen*, dass das System den Plan verwendet, der während der Testphase mit der Kardinalitätsschätzung 70 generiert wurde. Nachdem Sie den bevorzugten Plan *angeheftet* haben, können Sie die gesamte Datenbank für die Verwendung des neuesten Kompatibilitätsgrad und der neuesten Kardinalitätsschätzung einrichten. Diese Option wird im nächsten Abschnitt erläutert.  
  
### <a name="how-to-force-a-particular-query-plan"></a>Erzwingen eines bestimmten Abfrageplans  
  
Der Abfragespeicher bietet verschiedene Möglichkeiten, das System zur Verwendung eines bestimmten Abfrageplans zu zwingen:  
  
- Führen Sie **sp_query_store_force_plan**aus.  
  
- Erweitern Sie in [!INCLUDE[ssManStudio](../../includes/ssManStudio-md.md)] den Knoten für Ihren **Abfragespeicher**, klicken Sie mit der rechten Maustaste auf **Knoten mit dem höchsten Ressourcenverbrauch**, und klicken Sie dann auf **Knoten mit dem höchsten Ressourcenverbrauch anzeigen**. Es werden die Schaltflächen **Plan erzwingen** und **Erzwingung des Plans aufheben**angezeigt.  
  
Weitere Informationen zum Abfragespeicher finden Sie unter [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
## <a name="examples-of-ce-improvements"></a>Beispiele für Verbesserungen der Kardinalitätsschätzung  
  
Dieser Abschnitt enthält Beispielabfragen, die von den Erweiterungen der Kardinalitätsschätzung in neueren Versionen profitieren. Hierbei handelt es sich um Hintergrundinformationen, die keine bestimmte Aktion Ihrerseits erfordern.  
  
### <a name="example-a-ce-understands-maximum-value-might-be-higher-than-when-statistics-were-last-gathered"></a>Beispiel A. Die Kardinalitätsschätzung berücksichtigt, dass Maximalwerte höher sein können als bei der letzten Erfassung der Statistiken  
  
Angenommen, die Statistiken für `OrderTable` wurden zuletzt am `2016-04-30` erstellt, als der maximale Wert für `OrderAddedDate` `2016-04-30` entsprach. Bei der Kardinalitätsschätzung 120 (und höher) wird berücksichtigt, dass Spalten in `OrderTable` mit *ansteigenden* Daten Werte aufweisen können, die über dem von der Statistik aufgezeichneten Maximalwert liegen. Dies verbessert den Abfrageplan für [!INCLUDE[tsql](../../includes/tsql-md.md)]-SELECT-Anweisungen wie die folgende.  
  
```sql  
SELECT CustomerId, OrderAddedDate  
FROM OrderTable  
WHERE OrderAddedDate >= '2016-05-01';  
```  
  
### <a name="example-b-ce-understands-that-filtered-predicates-on-the-same-table-are-often-correlated"></a>Beispiel B. Die Kardinalitätsschätzung berücksichtigt, dass gefilterte Prädikate in der gleichen Tabelle häufig korrelieren.  
  
Die folgende SELECT-Anweisung zeigt gefilterte Prädikate für `Model` und `ModelVariant`. Wenn `Model` „Xbox“ ist, verstehen wir intuitiv, dass die Möglichkeit besteht, dass `ModelVariant` „One“ ist, da es von „Xbox“ eine Variante namens „One“ gibt.  
  
Ab der Kardinalitätsschätzung 120 berücksichtigt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dass eine Korrelation zwischen den Spalten `Model` und `ModelVariant` existieren kann, die sich in der gleichen Tabelle befinden. Die Kardinalitätsschätzung kann genauer einschätzen, wie viele Zeilen von der Abfrage zurückgegeben werden, und der [Abfrageoptimierer](../../relational-databases/query-processing-architecture-guide.md#optimizing-select-statements) generiert einen besseren Plan.  
  
```sql  
SELECT Model, Purchase_Price  
FROM dbo.Hardware  
WHERE Model = 'Xbox' AND  
      ModelVariant = 'One';  
```  
  
### <a name="example-c-ce-no-longer-assumes-any-correlation-between-filtered-predicates-from-different-tables"></a>Beispiel C. Die Kardinalitätsschätzung geht nicht mehr von einer Korrelation zwischen gefilterten Prädikaten aus verschiedenen Tabellen aus 
Umfangreiche neue Untersuchungen moderner Arbeitslasten und tatsächlicher Geschäftsdaten haben ergeben, dass Prädikatfilter aus unterschiedlichen Tabellen üblicherweise nicht korrelieren. In der folgenden Abfrage nimmt die Kardinalitätsschätzung an, dass zwischen `s.type` und `r.date` kein Zusammenhang besteht. Daher wird die Anzahl der zurückgegebenen Zeilen niedriger eingeschätzt.  
  
```sql  
SELECT s.ticket, s.customer, r.store  
FROM dbo.Sales    AS s  
CROSS JOIN dbo.Returns  AS r  
WHERE s.ticket = r.ticket AND  
      s.type = 'toy' AND  
      r.date = '2016-05-11';  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Optimieren der Leistung](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Optimizing Your Query Plans with the SQL Server 2014 Cardinality Estimator (Optimieren Ihrer Abfragepläne mit der SQL Server 2014-Kardinalitätsschätzung)](http://msdn.microsoft.com/library/dn673537.aspx)  
 [Abfragehinweise](../../t-sql/queries/hints-transact-sql-query.md)     
 [Abfragehinweise „USE HINT“](../../t-sql/queries/hints-transact-sql-query.md#use_hint)       
 [Überwachen der Leistung mit dem Abfragespeicher](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)    
 [Handbuch zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)   
