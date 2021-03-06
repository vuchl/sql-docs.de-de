---
title: Datamining (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
caps.latest.revision: 28
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ff1d223cee1ce86851b3021bad15582db156639
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163431"
---
# <a name="data-mining-ssas"></a>Data Mining (SSAS)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt eine integrierte Plattform für Lösungen bereit, die Data Mining integrieren. Sie können entweder relationale oder Cubedaten verwenden, um Business Intelligence-Lösungen mit Vorhersageanalysen zu erstellen.  
  
## <a name="benefits-of-data-mining"></a>Vorteile des Data Minings  
 Beim Data Mining werden Daten unter Verwendung durchdachter statistischer Grundlagen auf Muster untersucht, um Ihnen bei komplexen Problemstellungen eine intelligente Entscheidungsfindung zu ermöglichen. Indem die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthaltenen Data Mining-Algorithmen auf Daten angewendet werden, können Trends vorhergesagt, Muster identifiziert, Regeln und Empfehlungen aufgestellt, die Abfolge von Ereignissen in komplexen Datasets analysiert und neue Einblicke gewonnen werden.  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ist Data Mining leistungsstark, zugreifbar und integriert in die Tools, die viele für Analyse und Berichtswesen bevorzugen. Um Ihr Hintergrundwissen für die ersten Schritte mit Data Mining-Funktionen zu vertiefen, informieren Sie sich in den Links in diesem Abschnitt.  
  
## <a name="key-data-mining-features"></a>Wichtige Data Mining-Funktionen  
 SQL Server stellt die folgenden Funktionen zur Unterstützung integrierter Data Mining-Lösungen bereit:  
  
-   Mehrere Datenquellen: Sie müssen kein Data Warehouse oder einen OLAP-Cube erstellen, um Data Mining-Funktionen zu nutzen. Sie können Tabellendaten externer Anbieter, aus Arbeitsblättern und sogar aus Textdateien verwenden. Darüber hinaus können Sie leicht für OLAP-Cubes, die in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]erstellt wurden, Data Mining durchführen. Sie können jedoch keine Daten aus einer speicherinternen Datenbank verwenden.  
  
-   Integrierte Datenbereinigung, Datenverwaltung und ETL: Data Quality Services stellen erweiterte Tools zur Profilerstellung und zum Bereinigen von Daten bereit. Integration Services können zum Erstellen von ETL-Prozessen zum Bereinigen von Daten sowie zum Erstellen, Verarbeiten, Trainieren und Aktualisieren von Modellen verwendet werden.  
  
-   Mehrere anpassbare Algorithmen: Neben Algorithmen, beispielsweise für das Clustering, neuronale Netzwerke und Entscheidungsstrukturen, unterstützt die Plattform die Entwicklung eigener benutzerdefinierter Plug-In-Algorithmen.  
  
-   Infrastruktur zum Testen von Modellen: Testen Sie die Modelle und Datasets unter Verwendung wichtiger Statistiktools, wie Kreuzvalidierung, Klassifikationsmatrizen, Prognosegütediagramme und Punktdiagramme. Erstellen und verwalten Sie einfach Test- und Trainingssätze.  
  
-   Abfragen und Drillthrough: Erstellen Sie Vorhersageabfragen, rufen Sie Modellmuster und Statistiken ab, und führen Sie einen Drillthrough zu Falldaten aus.  
  
-   Clienttools: Neben den Entwicklungs- und Entwurfsoberflächen von SQL Server können Sie mithilfe der Data Mining-Add-Ins für Excel Modelle erstellen, abfragen und durchsuchen. Alternativ können Sie benutzerdefinierte Clients, einschließlich Webdienste, erstellen.  
  
-   Unterstützung von Skriptsprachen und verwaltete API: Alle Data Mining-Objekte sind vollständig programmierbar. Skripts können mithilfe von MDX, XMLA oder der PowerShell-Erweiterungen für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]erstellt werden. Verwenden Sie die DMX-Sprache (Data Mining Extensions, Data Mining-Erweiterungen) für die schnelle Abfrageausführung und Skripterstellung.  
  
-   Sicherheit und Bereitstellung: Bietet rollenbasierte Sicherheit durch [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], einschließlich separater Berechtigungen für Drillthroughs zu Modell- und Strukturdaten. Einfache Bereitstellung von Modellen auf anderen Servern, damit Benutzer auf die Muster zugreifen oder Vorhersagen ausführen können  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den Themen in diesem Abschnitt werden die Hauptfunktionen von SQL Server Data Mining sowie verwandte Tasks eingeführt.  
  
-   [Data Mining-Konzepte](data-mining-concepts.md)  
  
-   [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Miningstrukturen &#40;Analysis Services – Datamining&#41;](mining-structures-analysis-services-data-mining.md)  
  
-   [Miningmodelle &#40;Analysis Services – Datamining&#41;](mining-models-analysis-services-data-mining.md)  
  
-   [Tests und Überprüfung &#40;Datamining&#41;](testing-and-validation-data-mining.md)  
  
-   [Data Mining-Abfragen](data-mining-queries.md)  
  
-   [Data Mining-Projektmappen](data-mining-solutions.md)  
  
-   [Data Mining-Tools](data-mining-tools.md)  
  
-   [Data Mining-Architektur](data-mining-architecture.md)  
  
-   [Übersicht über die Sicherheit &#40;Datamining&#41;](security-overview-data-mining.md)  
  
  
