---
title: Benutzeroberfläche des MDX-Abfrage-Designers für Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- MDX [Reporting Services], creating datasets
- query designers [Reporting Services]
ms.assetid: d9c7c0b3-fce4-4a65-b679-408273e6a925
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: f322526680b3a91f2fcb7e93e3159f79b79793a6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323850"
---
# <a name="analysis-services-mdx-query-designer-user-interface"></a>Benutzeroberfläche des MDX-Abfrage-Designers für Analysis Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Stellt grafische Abfrage-Designer zum Erstellen von Abfragen (Multidimensional Expression) und Data Mining-Ausdrücke (DMX) Abfragen für ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquelle. In diesem Thema wird der MDX-Abfrage-Designer beschrieben. Weitere Informationen zu den DMX-Abfrage-Designer, finden Sie unter [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md).  
  
 Der grafische MDX-Abfrage-Designer verfügt über zwei Modi: Entwurfsmodus und Abfragemodus. Jeder Modus stellt einen Metadatenbereich bereit, in dem Sie Elemente aus den ausgewählten Cubes ziehen können, um eine MDX-Abfrage zu erstellen, die beim Verarbeiten des Berichts Daten abruft.  
  
> [!IMPORTANT]  
>  Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen. Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a>Grafischer MDX-Abfrage-Designer im Entwurfsmodus  
 Wenn Sie eine MDX-Abfrage für ein Berichtsdataset bearbeiten, wird der grafische MDX-Abfrage-Designer im Entwurfsmodus geöffnet.  
  
 In der folgenden Abbildung werden die Bereiche für den Entwurfsmodus bezeichnet.  
  
 ![Analysis Services-MDX-Abfrage-Designer, Entwurfsansicht](../../analysis-services/media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX query designer, design view")  
  
 In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Cube auswählen (Schaltfläche **...**)|Zeigt den aktuell ausgewählten Cube an.|  
|Metadaten (Bereich)|Zeigt eine hierarchische Liste von Measures, KPIs (Key Performance Indicators) und Dimensionen an, die für den ausgewählten Cube definiert sind.|  
|Berechnete Elemente (Bereich)|Zeigt die aktuell definierten berechneten Elemente an, die für eine Verwendung in der Abfrage verfügbar sind.|  
|Filter (Bereich)|Wird zum Auswählen von Dimensionen und zugehörigen Hierarchien verwendet, um Daten an der Quelle zu filtern und die an den Bericht zurückgegebenen Daten zu beschränken.|  
|Daten (Bereich)|Zeigt die Spaltenüberschriften für das Resultset an, während Sie Elemente aus dem Metadatenbereich und dem Bereich für berechnete Elemente ziehen. Aktualisiert automatisch das Resultset, wenn die Schaltfläche **Automatisch ausführen** ausgewählt wird. zugreifen.|  
  
 Sie können Dimensionen, Measures und KPIs aus dem Metadatenbereich sowie berechnete Elemente aus dem Bereich für berechnete Elemente in den Datenbereich ziehen. Im Filterbereich können Sie Dimensionen und zugehörige Hierarchien auswählen sowie Filterausdrücke festlegen, um die für eine Abfrage zur Verfügung stehenden Daten zu beschränken. Wenn die Umschaltfläche **AutoExecute** (![Automatisches Ausführen der Abfrage](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")) auf der Symbolliste ausgewählt wird, führt der Abfrage-Designer die Abfrage jedes Mal aus, wenn Sie ein Metadatenobjekt im Datenbereich ablegen. Sie können die Abfrage mithilfe der Schaltfläche **Ausführen** (![Ausführen der Abfrage](../../analysis-services/media/rsqdicon-run.gif "Run the query")) auf der Symbolleiste manuell ausführen.  
  
 Wenn Sie in diesem Modus eine MDX-Abfrage erstellen, werden die folgenden zusätzlichen Eigenschaften automatisch in die Abfrage eingeschlossen:  
  
 **Elementeigenschaften** MEMBER_CAPTION, MEMBER_UNIQUE_NAME  
  
 **Zelleigenschaften** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
  
 Um eigene zusätzliche Eigenschaften anzugeben, müssen Sie die MDX-Abfrage im Abfragemodus manuell bearbeiten.  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>Symbolleiste des grafischen MDX-Abfrage-Designers im Entwurfsmodus  
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen. In der folgenden Tabelle sind die Schaltflächen und ihre Funktionen aufgeführt.  
  
|Schaltfläche|Description|  
|------------|-----------------|  
|**Als Text bearbeiten**|Nicht aktiviert für diesen Datenquellentyp.|  
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Wechseln zur MDX-Abfrageansicht](../../analysis-services/media/rsqdicon-commandtypemdx.gif "Change to MDX query view")|Wechselt zum MDX-Befehlstyp.|  
|![Wechseln zur DMX-Abfragesprachenansicht](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")|Wechselt zum DMX-Befehlstyp.|  
|![Aktualisieren der Ergebnisdaten](../../analysis-services/media/rsqdicon-refresh.gif "Refresh result data")|Aktualisieren von Metadaten aus der Datenquelle.|  
|![Berechnetes Element hinzufügen](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "berechnetes Element hinzufügen")|Zeigt das Dialogfeld **Generator für berechnete Elemente** an.|  
|![Umschalten zum Anzeigen von leeren Zellen](../../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells")|Schaltet zwischen dem Anzeigen und Nichtanzeigen von leeren Zellen im Datenbereich um. (Dies entspricht dem Verwenden der NON EMPTY-Klausel in MDX.)|  
|![Automatisches Ausführen der Abfrage](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query")|Bei jeder Änderung wird die Abfrage automatisch ausgeführt, und das Ergebnis wird angezeigt. Die Ergebnisse werden im Datenbereich angezeigt.|  
|![Anzeigen der Schaltfläche „Aggregationen“](../../analysis-services/media/rsqdicon-showaggregations.gif "Show Aggregations button")|Zeigt Aggregationen im Datenbereich an.|  
|![Löschen Sie](../../analysis-services/media/rsqdicon-delete.gif "löschen")|Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.|  
|![Symbol für das Dialogfeld „Abfrageparameter“](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")|Anzeigen des Dialogfelds **Abfrageparameter** . Bei der Angabe von Werten für einen Abfrageparameter wird automatisch ein Berichtsparameter mit demselben Namen erstellt. Der Wert des Abfrageparameters wird auf einen Ausdruck festgelegt, der auf den Berichtsparameter verweist.|  
|![Schaltfläche „Abfrage vorbereiten“](../../analysis-services/media/rsqdicon-preparequery.gif "Prepare Query button")|Bereitet die Abfrage vor.|  
|![Führen Sie die Abfrage aus](../../analysis-services/media/rsqdicon-run.gif "Run the query")|Führt die Abfrage aus und zeigt die Ergebnisse im Datenbereich an.|  
|![Abbrechen der Abfrage](../../analysis-services/media/rsqdicon-cancel.gif "Cancel the query")|Abbrechen der Abfrage.|  
|![In Entwurfsmodus wechseln](../../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")|Umschalten zwischen Entwurfsmodus und Abfragemodus.|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a>Grafischer MDX-Abfrage-Designer im Abfragemodus  
 Wenn Sie vom grafischen Abfrage-Designer in den **Abfragemodus** wechseln möchten, klicken Sie auf der Symbolleiste auf die Schaltfläche **Entwurfsmodus** .  
  
 In der folgenden Abbildung sind die Bereiche für den Abfragemodus veranschaulicht.  
  
 ![Analysis Services-MDX-Abfrage-Designer, Abfrageansicht](../../analysis-services/media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX query designer, query view")  
  
 In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Cube auswählen (Schaltfläche **...**)|Zeigt den aktuell ausgewählten Cube an.|  
|Metadaten/Funktionen/Vorlagen (Bereich)|Zeigt eine hierarchische Liste von Measures, KPIs und Dimensionen an, die für den ausgewählten Cube definiert sind.|  
|Abfragebereich|Zeigt den Abfragetext an.|  
|Ergebnisbereich|Zeigt die Ergebnisse des Ausführens der Abfrage an.|  
  
 Im Metadatenbereich werden Registerkarten für **Metadaten**, **Funktionen**und **Vorlagen**angezeigt. Auf der Registerkarte **Metadaten** können Sie Dimensionen, Hierarchien, KPIs und Measures in den MDX-Abfragebereich ziehen. Auf der Registerkarte **Funktionen** können Sie Funktionen in den MDX-Abfragebereich ziehen. Auf der Registerkarte **Vorlagen** können Sie dem MDX-Abfragebereich MDX-Vorlagen hinzufügen. Wenn Sie die Abfrage ausführen, werden im Ergebnisbereich die Ergebnisse für die MDX-Abfrage angezeigt.  
  
 Sie können die im Entwurfsmodus erstellte Standard-MDX-Abfrage um zusätzliche Elementeigenschaften und Zelleigenschaften erweitern. Wenn Sie die Abfrage ausführen, werden diese Werte nicht im Resultset angezeigt. Sie werden jedoch an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] zurückgegeben, und Sie können diese Werte in einem Bericht verwenden. Weitere Informationen finden Sie unter Erweiterte Feldeigenschaften für eine Analysis Services (SSRS)-Datenbank.  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a>Symbolleiste für den grafischen Abfrage-Designer im Abfragemodus  
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen.  
  
 Die Schaltflächen der Symbolleiste sind im Entwurfs- und Abfragemodus identisch, aber die folgenden Schaltflächen sind für den Abfragemodus nicht aktiviert:  
  
-   **Als Text bearbeiten**  
  
-   **Berechnetes Element hinzufügen** (![berechnetes Element hinzufügen](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "berechnetes Element hinzufügen"))  
  
-   **Leere Zellen anzeigen** (![Umschalten zum Anzeigen von leeren Zellen](../../analysis-services/media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))  
  
-   **AutoExecute** (![Automatisches Ausführen der Abfrage](../../analysis-services/media/rsqdicon-autoexecute.gif "AutoExecute the query"))  
  
-   **Aggregationen anzeigen** (![Anzeigen der Schaltfläche „Aggregationen“](../../analysis-services/media/rsqdicon-showaggregations.gif "Show Aggregations button"))  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services &#40;Berichts-Generator und SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)   
 [RSReportDesigner-Konfigurationsdatei](../report-server/rsreportdesigner-configuration-file.md)   
 [Analysis Services-Verbindungstyp für MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md)  
  
  
