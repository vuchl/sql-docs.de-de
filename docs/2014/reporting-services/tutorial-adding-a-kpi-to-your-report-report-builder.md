---
title: 'Tutorial: Hinzufügen einer KPI zu einem Bericht (Berichts-Generator) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1bf77859-0b33-4f40-abaf-ebeeb6ebb1f8
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: f06fa546153ef62edda97c173a8c4fb9cc4d9362
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276166"
---
# <a name="tutorial-adding-a-kpi-to-your-report-report-builder"></a>Lernprogramm: Hinzufügen eines KPIs zu einem Bericht (Berichts-Generator)
  Ein Key Performance Indicator (KPI) ist ein messbarer Wert mit einer Aussagekraft für das Geschäft. In diesem Lernprogramm erfahren Sie, wie ein (KPI) in einen Bericht eingeschlossen wird. In diesem Szenario ist die Verkaufszusammenfassung nach Produktunterkategorien der KPI. Der aktuelle Status des KPI wird mit Farben, Messgeräten und Indikatoren angezeigt.  
  
 Die folgende Abbildung zeigt den Bericht, den Sie erstellen.  
  
 ![Rs_AddKPITutorial](../../2014/tutorials/media/rs-addkpitutorial.gif "Rs_AddKPITutorial")  
  
##  <a name="BackToTop"></a> Lernziele  
 In diesem Lernprogramm erfahren Sie, wie ein KPI hinzugefügt wird, indem Sie die Hintergrundfarbe von Tabellenzellen basierend auf dem Zellenwert festlegen und ein Messgerät und einen Indikator hinzufügen und konfigurieren. Sie erfahren auch, wie der Ausdruck zum Festlegen der Hintergrundfarbe der Tabellenzellen geschrieben wird.  
  
 Dieses Lernprogramm enthält die folgenden Verfahren:  
  
1.  [Erstellen eines Tabellenberichts und eines Datasets mit dem Tabellen- oder Matrix-Assistenten](#Table)  
  
2.  [Organisieren von Daten, Auswählen des Layouts und Formats mit dem Tabellen- oder Matrixassistenten](#CompleteWizard)  
  
3.  [Anzeigen einen KPI mithilfe von Hintergrundfarben](#BackgroundColors)  
  
4.  [Anzeigen eines KPI mit einem Messgerät](#Gauge)  
  
5.  [Anzeigen eines KPI mit einem Indikator](#Indicator)  
  
6.  [Hinzufügen eines Berichtstitels](#Title)  
  
7.  [Speichern des Berichts](#Save)  
  
> [!NOTE]  
>  In diesem Lernprogramm werden die Schritte für den Assistenten in zwei Verfahren zusammengefasst: ein Verfahren zum Erstellen des Datasets und ein Verfahren zum Erstellen einer Tabelle. Im ersten Tutorial dieser Reihe erhalten Sie ausführliche Anweisungen zum Navigieren zu einem Berichtsserver, Auswählen einer Datenquelle, Erstellen eines Datasets und Ausführen des Assistenten: [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
 Geschätzte Zeit zum Bearbeiten dieses Tutorials: 15 Minuten.  
  
## <a name="requirements"></a>Anforderungen  
 Weitere Informationen zu den Anforderungen finden Sie unter [Voraussetzungen für Tutorials &#40;Berichts-Generator&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="Table"></a> 1. Erstellen eines Tabellenberichts und eines Datasets mit dem Tabellen- oder Matrix-Assistenten  
 Von der **Einstieg** im Dialogfeld Wählen Sie eine freigegebene Datenquelle, erstellen Sie ein eingebettetes Dataset und zeigen Sie die Daten in einer Tabelle.  
  
> [!NOTE]  
>  In diesem Lernprogramm sind die Datenwerte in der Abfrage enthalten, sodass keine externe Datenquelle benötigt wird. Die Abfrage ist daher relativ lang. In einer Geschäftsumgebung wären die Daten nicht in der Abfrage enthalten. Dieses Szenario dient nur zu Lernzwecken.  
  
#### <a name="to-create-a-new-table"></a>So erstellen Sie eine neue Tabelle  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, zeigen Sie auf **Microsoft SQL Server 2012 Berichts-Generator**, und klicken Sie dann auf **Berichts-Generator**.  
  
     Das Dialogfeld **Erste Schritte** wird angezeigt.  
  
    > [!NOTE]  
    >  Wenn die **Einstieg** klicken Sie auf die Schaltfläche "Berichts-Generator" und das Dialogfeld nicht angezeigt wird, **neu**.  
  
2.  Vergewissern Sie sich, dass im linken Bereich **Neuer Bericht** ausgewählt ist.  
  
3.  Klicken Sie im rechten Bereich auf **Tabellen- oder Matrix-Assistent**.  
  
4.  Klicken Sie auf der Seite Dataset auswählen auf **erstellen Sie ein Dataset**.  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Verbindung mit einer Datenquelle auswählen** eine vorhandene Datenquelle aus, oder navigieren Sie zum Berichtsserver, und wählen Sie eine Datenquelle aus. Falls dort keine Datenquelle verfügbar ist oder Sie keinen Zugriff auf einen Berichtsserver haben, können Sie stattdessen eine eingebettete Datenquelle verwenden. Weitere Informationen finden Sie unter [Tutorial: Erstellen eines einfachen Tabellenberichts (Berichts-Generator)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der Seite **Abfrage entwerfen** auf **Als Text bearbeiten**.  
  
9. Kopieren Sie die folgende Abfrage, und fügen Sie sie in den Abfragebereich ein:  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Accessories' as Subcategory,  
       'Mini Battery Charger' as Product, CAST(1056.00 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Accessories' as Subcategory,  
       'Telephoto Conversion Lens' as Product, CAST(1380.00 AS money) AS Sales, 18 as Quantity  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,'Accessories' as Subcategory,    
       'USB Cable' as Product, CAST(780.00 AS money) AS Sales, 26 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate, 'Accessories' as Subcategory,   
       'Budget Movie-Maker' as Product, CAST(3798.00 AS money) AS Sales, 9 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Business Videographer' as Product, CAST(10400.00 AS money) AS Sales, 13 as Quantity  
    UNION SELECT CAST('2009-01-10' AS date) as SalesDate, 'Camcorders' as Subcategory,   
       'Social Videographer' as Product, CAST(3000.00 AS money) AS Sales, 60 as Quantity  
    UNION SELECT CAST('2009-01-11' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Advanced Digital' as Product, CAST(7234.50 AS money) AS Sales, 39 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Compact Digital' as Product, CAST(10836.00 AS money) AS Sales, 84 as Quantity  
    UNION SELECT CAST('2009-01-08' AS date) as SalesDate,  'Digital' as Subcategory,   
       'Consumer Digital' as Product, CAST(2550.00 AS money) AS Sales, 17 as Quantity  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Digital' as Subcategory,   
       'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity  
    UNION SELECT CAST('2009-01-09' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera 35mm' as Product, CAST(18530.00 AS money) AS Sales, 34 as Quantity  
    UNION SELECT CAST('2009-01-07' AS date) as SalesDate, 'Digital SLR' as Subcategory,   
       'SLR Camera' as Product, CAST(26576.00 AS money) AS Sales, 88 as Quantity  
    ```  
  
10. Klicken Sie auf **Weiter**.  
  
##  <a name="CompleteWizard"></a> 2. Organisieren von Daten, Auswählen des Layouts und Formats mit dem Tabellen- oder Matrix-Assistenten  
 Stellen Sie mithilfe des Assistenten einen Startentwurf für die Anzeige von Daten bereit. Im Vorschaufenster des Assistenten können Sie das Ergebnis der Datengruppierung visualisieren, bevor Sie den Tabellen- oder Matrixentwurf abschließen.  
  
#### <a name="to-organize-data-into-groups-choose-a-layout-and-a-style"></a>Um Daten in Gruppen organisieren möchten, wählen Sie ein Layout und einen Stil  
  
1.  Ziehen Sie auf der Seite „Felder anordnen“ das Feld „Product“ in **Werte**.  
  
2.  Ziehen Sie „Quantity“ in **Werte** , und platzieren Sie es unter „Product“.  
  
     Die Menge wird mit der Sum-Funktion zusammengefasst, der Standardfunktion zum Summieren numerischer Felder.  
  
3.  Ziehen Sie „Sales“ in **Werte** , und fügen Sie dieses Feld unter „Quantity“ ein.  
  
     In Schritt 1, 2 und 3 werden die Daten angegeben, die in der Tabelle angezeigt werden sollen.  
  
4.  Ziehen Sie „SalesDate“ in **Zeilengruppen**.  
  
5.  Ziehen Sie „Subcategory“ in **Zeilengruppen** , und fügen Sie dieses Feld unter „SalesDate“ ein.  
  
     Durch die Schritte 4 und 5 werden die Werte für die Felder zuerst nach Datum und dann nach allen Umsätzen für dieses Datum angeordnet.  
  
6.  Klicken Sie auf **Weiter**.  
  
     Bei der Ausführung des Berichts werden in der Tabelle jedes Datum, alle Aufträge für jedes Datum sowie alle Produkte, Mengen und Umsatzsummen für jeden Auftrag angezeigt.  
  
7.  Vergewissern Sie sich auf der Seite „Layout auswählen“, dass unter **Optionen**die Option **Teil- und Gesamtergebnisse anzeigen** ausgewählt ist.  
  
8.  Überprüfen Sie, ob **Als Block, Teilergebnis unterhalb** ausgewählt ist.  
  
9. Deaktivieren Sie die Option **Gruppen erweitern/reduzieren**.  
  
     In diesem Lernprogramm enthält der erstellte Bericht keine Drilldownfunktion, mit der ein Benutzer eine übergeordnete Gruppenhierarchie einblenden kann, um untergeordnete Gruppenzeilen und Detailzeilen anzuzeigen.  
  
10. Klicken Sie auf **Weiter**.  
  
11. Wählen Sie auf der Seite "Format auswählen" im Bereich "Formate" ein Format aus.  
  
     Die Abbildung des fertig gestellten Berichts zeigt den Bericht im Format "Ozean".  
  
12. Klicken Sie auf **Fertig stellen**.  
  
     Die Tabelle wird der Entwurfsoberfläche hinzugefügt. Die Tabelle enthält fünf Spalten und fünf Zeilen. Im Bereich "Zeilengruppen" werden drei Zeilengruppen angezeigt: "SalesDate", "Subcategory" und "Details". Detaildaten sind alle Daten, die von der Datasetabfrage abgerufen werden.  
  
13. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 Für jedes an einem bestimmten Datum verkaufte Produkt werden in der Tabelle der Produktname, die verkaufte Menge und der Gesamtumsatz angezeigt. Die Daten sind zuerst nach Verkaufsdatum und dann nach Unterkategorie organisiert.  
  
##  <a name="BackgroundColors"></a> 3. Anzeigen eines KPI mithilfe von Hintergrundfarben  
 Hintergrundfarben können für einen Ausdruck festgelegt werden, der beim Ausführen des Berichts ausgewertet wird.  
  
#### <a name="to-display-the-present-state-of-a-kpi-by-using-background-colors"></a>So zeigen Sie den aktuellen Status eines KPI mit Hintergrundfarben an  
  
1.  In der Tabelle mit der rechten Maustaste zwei Zellen nach unten aus dem `[Sum(Sales)]` Zelle (die Teilergebniszeile mit dem Umsatz für eine Unterkategorie), und klicken Sie dann auf **Textfeldeigenschaften**.  
  
2.  In **füllen**, klicken Sie auf die **fx** neben der **Füllfarbe** aus und geben Sie den folgenden Ausdruck in der **Ausdruck festlegen für: BackgroundColor** Feld:  
  
 `=IIF(Sum(Fields!Sales.Value) >= 5000 ,"Lime", IIF(Sum(Fields!Sales.Value) < 2500, "Red","Yellow"))`  
  
 Dadurch wird die Hintergrundfarbe für jede Zelle, die eine kombinierte Summe für `[Sum(Sales)]` enthält, die größer oder gleich 5.000 ist, mithilfe des Grüntons "Limonengrün" in Grün geändert. Werte von `[Sum(Sales)]` zwischen 2.500 und 5.000 werden gelb eingefärbt. Werte kleiner als 2.500 werden rot eingefärbt.  
  
1.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
2.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
 In der Teilergebniszeile, die den Umsatz für eine Unterkategorie anzeigt, ist die Hintergrundfarbe der Zelle abhängig vom Wert der Umsatzsumme rot, gelb oder grün.  
  
##  <a name="Gauge"></a> 4. Anzeigen eines KPI mit einem Messgerät  
 Ein Messgerät stellt einen einzelnen Wert in einem Dataset dar. In diesem Lernprogramm wird ein horizontales lineares Messgerät verwendet, da es aufgrund seiner Form und Einfachheit auch dann leicht zu lesen ist, wenn es klein ist und innerhalb einer Tabellenzelle verwendet wird. Weitere Informationen finden Sie unter [Gauges &#40;Report Builder and SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md).  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-a-gauge"></a>So zeigen Sie den aktuellen Status eines KPI mit einem Messgerät an  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  In der Tabelle mit der Maustaste des Handlers für die Spalte für die Zelle, die Sie in der vorherigen Prozedur geändert wird, zeigen Sie auf **Spalte einfügen**, und klicken Sie dann auf **rechts**. Eine neue Spalte wird der Tabelle hinzugefügt.  
  
3.  Typ **KPI** in der Spaltenüberschrift.  
  
4.  Auf der **einfügen** Registerkarte der **Datenbereiche** auf **Messgerät**, und klicken Sie dann auf die Entwurfsoberfläche außerhalb der Tabelle. Das Dialogfeld **Messgerättyp auswählen** wird angezeigt.  
  
5.  Klicken Sie auf **lineare**. Der erste lineare messgerättyp, **horizontale**, ausgewählt ist.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Der Entwurfsoberfläche wird ein Messgerät hinzugefügt.  
  
7.  Ziehen Sie "Sales" aus dem Berichtsdatenbereich in das Messgerät. Wenn Sie "Sales" über das Messgerät ziehen, wird der Bereich "Messgerätdaten" geöffnet.  
  
8.  Legen Sie Sales in der **Werte** Liste.  
  
     Wenn Sie das Feld auf dem Messgerät ablegen, wird das Feld anhand der integrierten Sum-Funktion aggregiert.  
  
9. Mit der rechten Maustaste des Zeigers im Messgerät, und klicken Sie auf **Zeigereigenschaften**.  
  
10. In **Zeigertyp**Option **Leiste**. Dadurch ändert sich der Zeiger von einem Marker in einen Balken, der besser zu sehen ist, wenn das Messgerät der Tabelle hinzugefügt wird.  
  
11. Klicken Sie auf **Zeigerfüllfarbe**. In **Sekundärfarbe** auswählen **gelben**. Das Farbverlaufsmuster verwandelt sich von Weiß in Gelb.  
  
12. Klicken Sie mit der rechten Maustaste auf die Skala im Messgerät, und klicken Sie auf **Skalierungseigenschaften**.  
  
13. Legen Sie die **maximale** Option auf 25000 fest.  
  
    > [!NOTE]  
    >  Anstelle einer Konstante wie 25.000 können Sie den Wert der Option **Maximum** auch mithilfe eines Ausdrucks dynamisch berechnen. Der Ausdruck würde das Aggregat der Aggregatfunktion verwenden und dem Ausdruck `=Max(Sum(Fields!Sales.value), "Tablix1")`ähneln.  
  
14. Ziehen Sie das Messgerät in der Tabelle in die dritte Zelle in der Teilergebniszeile, in der die Umsätze für eine Unterkategorie der von Ihnen eingefügten Spalte angezeigt werden.  
  
    > [!NOTE]  
    >  Möglicherweise müssen Sie die Größe der Spalte ändern, damit das horizontale lineare Messgerät in die Zelle passt. Klicken Sie dazu auf eine Spaltenkopfzeile, und passen Sie Höhe und Breite der Zellen mithilfe der entsprechenden Ziehpunkte an.  
  
15. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
     Die horizontale Länge der Leiste im Messgerät ändert sich je nach Wert des KPIs.  
  
16. (Optional) Fügen Sie einen maximalen Stift zur Behandlung des Überlaufs hinzu, damit Werte, die das Skalenmaximum überschreiten, stets auf den maximalen Stift verweisen:  
  
    1.  Öffnen Sie den Bereich Eigenschaften.  
  
    2.  Klicken Sie auf der Skala. Die Eigenschaften für die lineare Skala werden im Bereich "Eigenschaften" angezeigt.  
  
    3.  In der **Skalenpole** (Kategorie), erweitern Sie die **MaximumPin** Knoten.  
  
    4.  Legen Sie die **aktivieren** Eigenschaft `True`. Ein Stift wird nach dem maximalen Wert auf der Skala angezeigt.  
  
    5.  Legen Sie **BorderColor** zu `Lime`.  
  
17. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Indicator"></a> 5. Anzeigen eines KPI mit einem Indikator  
 Indikatoren sind kleine einfache Messgeräte, die Datenwerte auf einen Blick darstellen. Aufgrund ihrer Größe und Einfachheit werden Indikatoren oft in Tabellen und Matrizen verwendet. Weitere Informationen finden Sie unter [Indikatoren (Berichts-Generator und SSRS)](report-design/indicators-report-builder-and-ssrs.md).  
  
#### <a name="to-display-the-present-state-of-a-kpi-using-an-indicator"></a>So zeigen Sie den aktuellen Status eines KPI mit einem Indikator an  
  
1.  Wechseln Sie in die Entwurfsansicht.  
  
2.  In der Tabelle mit der Maustaste des Handlers für die Spalte für die Zelle, die Sie in der vorherigen Prozedur geändert wird, zeigen Sie auf **Spalte einfügen**, und klicken Sie dann auf **rechts**. Eine neue Spalte wird der Tabelle hinzugefügt.  
  
3.  Typ **KPI** in der Spaltenüberschrift.  
  
4.  Klicken Sie auf die Zelle für das Teilergebnis der Unterkategorie.  
  
5.  Auf der **einfügen** Registerkarte die **Datenbereiche** gruppieren, doppelklicken Sie auf **Indikator.**  
  
     Das Dialogfeld **Indikatortyp auswählen** wird geöffnet.  
  
6.  Klicken Sie auf **Formen**. Der erste Formtyp, **3 Ampeln (ohne Rand),** ausgewählt ist.  
  
     In diesem Lernprogramm verwenden Sie diesen Indikator.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     Der Indikator wird der Entwurfsoberfläche hinzugefügt.  
  
8.  Klicken Sie mit der rechten Maustaste auf den Indikator, und klicken Sie auf **Indikatoreigenschaften**.  
  
9. Klicken Sie auf **Werte und Status**.  
  
10. Wählen Sie in der Dropdown-Werteliste, **[SUM(Sales)"angezeigt]**, jedoch keine weiteren Optionen nicht ändern.  
  
     Standardmäßig findet eine Datensynchronisierung im Datenbereich statt, und der Wert **Tablix1**, der Name des Tabellendatenbereichs im Bericht, wird im Feld **Synchronisierungsbereich** angezeigt.  
  
     In diesem Bericht können Sie auch den Bereich eines Indikators ändern, der in der Zelle für das Teilergebnis der Unterkategorie eingefügt wurde, um das Feld "SalesDate" zu synchronisieren.  
  
11. Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Title"></a> 6. Hinzufügen eines Berichtstitels  
 Ein Berichtstitel wird oben im Bericht angezeigt. Sie können den Berichtstitel in eine Berichtskopfzeile einfügen oder, wenn der Bericht keine Kopfzeile enthält, in einem Textfeld am oberen Rand des Berichtshauptteils. Sie verwenden das Textfeld, das automatisch am oberen Rand des Berichtshauptteils platziert wird.  
  
 Die Darstellung des Texts kann weiter verbessert werden, indem andere Schriftschnitte, Größen und Farben für Ausdrücke und einzelne Zeichen des Texts angewendet werden. Weitere Informationen finden Sie unter [Formatieren von Text in einem Textfeld (Berichts-Generator und SSRS)](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md).  
  
#### <a name="to-add-a-report-title"></a>So fügen Sie einen Berichtstitel hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf **Zum Hinzufügen eines Titels klicken**.  
  
2.  Typ **Product Sales KPI**, und klicken Sie dann außerhalb des Textfelds auf.  
  
3.  Optional, wird mit das Textfeld mit der rechten Maustaste **Product Sales KPI**, klicken Sie auf **Textfeldeigenschaften**, und wählen Sie dann auf der Registerkarte Schriftart der andere Schriftschnitte, Größen und Farben.  
  
4.  Klicken Sie auf **Ausführen** , um eine Vorschau des Berichts anzuzeigen.  
  
##  <a name="Save"></a> 7. Speichern des Berichts  
 Speichern Sie den Bericht auf einem Berichtsserver oder auf Ihrem Computer. Wenn Sie den Bericht nicht auf dem Berichtsserver speichern, ist eine Reihe von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Funktionen nicht verfügbar, z. B. Berichtsteile und Unterberichte.  
  
#### <a name="to-save-the-report-on-a-report-server"></a>So speichern Sie den Bericht auf einem Berichtsserver  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Letzte Sites und Server**.  
  
3.  Wählen Sie den Namen des Berichtsservers aus, auf dem Sie zum Speichern von Berichten berechtigt sind, oder geben Sie ihn ein.  
  
     Die Meldung "Verbindung mit Berichtsserver wird hergestellt" wird angezeigt. Nachdem die Verbindung hergestellt wurde, sehen Sie den Inhalt des Berichtsordners, den der Berichtsserveradministrator als Standardspeicherort für Berichte angegeben hat.  
  
4.  Ersetzen Sie im Feld **Name**den Standardnamen durch **Produktumsatz-KPI**.  
  
5.  Klicken Sie auf **Speichern**.  
  
 Der Bericht wird auf dem Berichtsserver gespeichert. Der Name des Berichtsservers, mit dem Sie verbunden sind, wird in der Statusleiste unten im Fenster angezeigt.  
  
#### <a name="to-save-the-report-on-your-computer"></a>So speichern Sie den Bericht auf dem Computer  
  
1.  Klicken Sie auf die Schaltfläche **Berichts-Generator** und anschließend auf **Speichern unter**.  
  
2.  Klicken Sie auf **Desktop**, **Eigene Dokumente**oder **Computer**, und navigieren Sie zu dem Ordner, in dem Sie den Bericht speichern möchten.  
  
> [!NOTE]  
>  Wenn Sie keinen Zugriff auf einen Berichtsserver haben, klicken Sie auf **Desktop**&gt; **Eigene Dokumente**oder **Arbeitsplatz** , und speichern Sie den Bericht auf dem Computer.  
  
1.  Ersetzen Sie im Feld **Name**den Standardnamen durch **Produktumsatz-KPI**.  
  
2.  Klicken Sie auf **Speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie haben das Lernprogramm "Hinzufügen eines KPI zu einem Bericht" erfolgreich abgeschlossen. Weitere Informationen finden Sie unter Messgeräte (Berichts-Generator) [Indikatoren &#40;Berichts-Generator und SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Lernprogramme &#40;Berichts-Generator&#41;](report-builder-tutorials.md)   
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
