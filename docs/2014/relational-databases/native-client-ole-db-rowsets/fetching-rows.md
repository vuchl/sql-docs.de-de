---
title: Abrufen von Zeilen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ef60069c801ed7000677122af6fba7b2e9f7c4a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415059"
---
# <a name="fetching-rows"></a>Abrufen von Zeilen
  Die **IRowset** Schnittstelle ist die grundlegende Rowset-Schnittstelle. Die **IRowset** Schnittstelle stellt Methoden zum sequenziellen Abrufen von Zeilen, die Daten aus diesen Zeilen abrufen und zum Verwalten der Zeilen bereit. Consumer verwenden die Methoden in **IRowset** für alle grundlegenden rowsetvorgänge. Dazu gehört das Abrufen und erneute Freigeben von Zeilen und das Einlesen von Spaltenwerten.  
  
 Wenn ein Consumer einen Schnittstellenzeiger für ein Rowset erhält, wird der erste Schritt normalerweise um zu bestimmen, das die Funktionen des Rowsets mithilfe der **IRowsetInfo:: GetProperties** Methode. Auf diese Weise werden Informationen über die durch das Rowset verfügbar gemachten Schnittstellen zurückgegeben sowie über andere Möglichkeiten des Rowsets, die nicht als eigentliche Schnittstellen zu betrachten sind, wie beispielsweise die maximale Anzahl aktiver Zeilen und die Anzahl der Zeilen, die gleichzeitig ausstehende Updates aufweisen können.  
  
 Der nächste, vom Consumer auszuführende Schritt besteht darin, die Charakteristika – oder Metadaten – der Spalten im Rowset zu ermitteln. Dafür verwendet er die **IColumnsInfo** Methode für die einfache Spalteninformationen oder **IColumnsRowset** Methode für die erweiterte Spalteninformationen. Die **GetColumnInfo** Methode die folgenden Informationen zurückgegeben:  
  
-   Die Anzahl der Spalten im Resultset.  
  
-   Ein Array von DBCOLUMNINFO-Strukturen; eines pro Spalte.  
  
     Die Reihenfolge der Strukturen entspricht der Reihenfolge, in der die Spalten im Rowset erscheinen. Jede DBCOLUMNINFO-Struktur enthält Spaltenmetadaten wie den Spaltennamen, die Ordnungszahl der Spalte, maximal mögliche Länge eines Werts in der Spalte, Datentyp, Genauigkeit und Länge der Spalte.  
  
-   Den Zeiger auf einen Speicher für alle Zeichenfolgenwerte innerhalb eines einzelnen Zuordnungsblocks.  
  
 Der Consumer bestimmt, welche Spalten erforderlich sind, entweder auf der Grundlage der Metadaten oder basierend auf den Textbefehl, mit dem das Rowset generiert wurde. Die Ordnungszahlen der benötigten Spalten über die Reihenfolge der zurückgegebenen Spalteninformationen **IColumnsInfo** oder von den Ordnungszahlen in dem von zurückgegebenen spaltenmetadatenrowset **IColumnsRowset**.  
  
 Die **IColumnsInfo** und **IColumnsRowset** Schnittstellen werden verwendet, um Informationen zu den Spalten im Rowset zu extrahieren. Die **IColumnsInfo** Schnittstelle gibt eine begrenzte Anzahl von Informationen zurück, wohingegen **IColumnsRowset** alle Metadaten bereitstellt.  
  
> [!NOTE]  
>  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Version 7.0 und früher die optionale Metadatenspalte DBCOLUMN_COMPUTEMODE zurückgegebenes **IColumnsInfo:: GetColumnsInfo** zurückgegeben wird, DBSTATUS_S_ISNULL (anstelle der Werte, die beschreibt, ob die Spalte berechnet), da nicht ermittelt werden kann, ob die zugrunde liegende Spalte berechnet ist.  
  
 Die Ordnungszahlen werden verwendet, um eine Bindung an eine Spalte anzugeben. Eine Bindung ist eine Struktur, die einer Spalte ein Element der Struktur des Consumers zuordnet. Die Bindung kann den Datenwert, die Länge und den Statuswert der Spalte binden.  
  
 Ein Satz von Bindungen wird zusammen in einem Accessor erfasst. Dieser wird erstellt, mit der **IAccessor:: CreateAccessor** Methode. Ein Accessor kann mehrere Bindungen enthalten, sodass die Daten für mehrere Spalten durch einen einzigen Aufruf abgerufen oder festgelegt werden können. Der Consumer kann mehrere Accessoren erstellen, um in verschiedenen Teilen der Anwendung auf verschiedene Verwendungsmuster zu antworten. Er kann Accessoren erstellen und freigeben, solange das Rowset besteht.  
  
 Um Zeilen aus der Datenbank abzurufen, ruft der Consumer eine Methode, wie z. B. **IRowset:: GetNextRows** oder **IRowsetLocate:: GetRowsAt**. Diese Abrufvorgänge platzieren Zeilendaten vom Server in den Zeilenpuffer des Anbieters. Der Consumer hat keinen Direktzugriff auf den Zeilenpuffer des Anbieters. Der Consumer verwendet **IRowset:: GetData** um Daten aus dem Puffer des Anbieters in den Consumerpuffer zu kopieren und **IRowsetChange:: SetData** datenänderungen vom Consumerpuffer in den Anbieterpuffer zu kopieren.  
  
 Der Consumer Ruft die **GetData** Methode und übergibt das Handle für eine Zeile, die das Handle für einen Accessor und einen Zeiger auf einen Consumer zugeordneten Puffer. **GetData** konvertiert die Daten und gibt die Spalten in die zum Erstellen des Accessors verwendeten Bindungen angegeben. Der Consumer kann Aufrufen **GetData** mehr als einmal für eine Zeile verwenden verschiedene Accessoren und Puffer und daher der Consumer mehrere Kopien derselben Daten erhalten kann.  
  
 Daten aus Spalten variabler Länge können auf mehrere Arten behandelt werden. Zunächst können solche Spalten an einen endlichen Abschnitt der Struktur des Consumers gebunden werden. Dies verursacht das Abschneiden von Daten, wenn die Länge der Daten die Länge des Puffers überschreitet. Der Consumer kann ermitteln, dass Daten abgeschnitten wurden, indem er den Status DBSTATUS_S_TRUNCATED überprüft. Die zurückgegebene Länge ist immer die wirkliche Länge in Byte, sodass der Consumer auch bestimmen kann, wie viele Daten abgeschnitten wurden.  
  
 Wenn der Consumer das Abrufen oder Aktualisieren von Zeilen abgeschlossen ist, gibt er sie mit der **ReleaseRows** Methode. Auf diese Weise werden Ressourcen von der Kopie der Zeilen im Rowset frei, und es wird Platz für neue Zeilen geschaffen. Der Consumer kann den Zyklus des Abrufens oder Erstellens von Zeilen sowie des Zugreifens auf Daten in den Zeilen beliebig wiederholen.  
  
 Wenn der Consumer mit dem Rowset fertig ist, ruft er die **ReleaseAccessor** Methode, um Accessoren freizugeben. Ruft die **IUnknown:: Release** Methode für alle Schnittstellen, die vom Rowset Freigeben des Rowsets verfügbar gemacht. Sobald das Rowset freigegeben ist, wird die Freigabe aller verbleibender Zeilen oder vom Consumer verwendeten Accessoren erzwungen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Nächste Abrufposition](fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Rowsets](rowsets.md)  
  
  
