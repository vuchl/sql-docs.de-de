---
title: Implementieren von Datenverarbeitungserweiterungen | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom data processing extensions [Reporting Services]
- data sources [Reporting Services], data processing extensions
- data processing extensions [Reporting Services]
- extensions [Reporting Services], data processing
ms.assetid: 8dc2b44e-5ad9-411d-a29f-7213e29321a9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b31e1adec1e975f7fbdda7c7b0f7e732a39eaa47
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43269120"
---
# <a name="implementing-a-data-processing-extension"></a>Implementieren von Datenverarbeitungserweiterungen
  Mithilfe von Datenverarbeitungserweiterungen in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] können Sie eine Verbindung zu einer Datenquelle herstellen und Daten abrufen. Sie dienen außerdem als Verbindung zwischen einer Datenquelle und einem Dataset. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterungen sind einer Teilmenge der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Datenanbieterschnittstellen nachgebildet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Data Processing Extensions Overview (Übersicht über Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)  
 Erläutert, wie eine benutzerdefinierte Datenverarbeitungserweiterung für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] geschrieben wird.  
  
 [Preparing to Implement a Data Processing Extension (Vorbereiten der Implementierung von Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/preparing-to-implement-a-data-processing-extension.md)  
 Beschreibt die verfügbaren Schnittstellen beim Implementieren einer [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung sowie den Fall, in dem Sie eine bestimmte Schnittstelle implementieren müssen.  
  
 [Creating a Data Processing Extension Library (Erstellen einer Bibliothek für Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/creating-a-data-processing-extension-library.md)  
 Beschreibt die Zuordnung eines Namespace für Ihre [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung und die Kompilierung Ihrer Datenverarbeitungserweiterung in eine DLL-Bibliothek.  
  
 [Implementing a Connection Class for a Data Processing Extension (Implementieren einer Connection-Klasse für Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/implementing-a-connection-class-for-a-data-processing-extension.md)  
 Beschreibt die Attribute einer Verbindung und die Implementierungsweise einer eigenen **Connection**-Klasse für Ihre Datenverarbeitungserweiterung  
  
 [Implementing a Command Class for a Data Processing Extension (Implementieren einer Command-Klasse für Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/implementing-a-command-class-for-a-data-processing-extension.md)  
 Beschreibt die Attribute eines Befehls und die Implementierungsweise einer eigenen **Command**-Klasse für Ihre Datenverarbeitungserweiterung  
  
 [Implementing a DataReader Class for a Data Processing Extension (Implementieren einer DataReader-Klasse für Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/implementing-a-datareader-class-for-a-data-processing-extension.md)  
 Beschreibt die Attribute eines Datenlesers und die Implementierungsweise einer eigenen **DataReader**-Klasse für Ihre Datenverarbeitungserweiterung  
  
 [Using an External Dataset with Reporting Services (Verwenden eines externen Datasets mit Reporting Services)](../../../reporting-services/extensions/data-processing/using-an-external-dataset-with-reporting-services.md)  
 Beschreibt, wie die benutzerdefinierten **Dataset**-Objekte für die Verwendung durch den Berichtsserver zur Verfügung gestellt werden  
  
 [Bereitstellen von Datenverarbeitungserweiterungen](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)  
 Beschreibt, wie Sie eine Datenverarbeitungserweiterung bereitstellen  
  
 [Debugging Data Processing Extension Code (Debuggen von Code für Datenverarbeitungserweiterungen)](../../../reporting-services/extensions/data-processing/debugging-data-processing-extension-code.md)  
 Beschreibt, wie Sie Code in Ihren Datenverarbeitungserweiterungen debuggen  
  
 Ein Beispiel für eine vollständig implementierte Datenverarbeitungserweiterung finden Sie unter [SQL Server Reporting Services-Produktbeispiele](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterungen für Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
