---
title: SSIS-Paketformat | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cfe0e5dc-5be3-4222-b721-fe83665edd94
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c025877f39e66fcf25e6ed2b27d6e1b422a299d9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37237120"
---
# <a name="ssis-package-format"></a>SSIS-Paketformat
  In der aktuellen Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] wurden wichtige Änderungen am Paketformat (DTSX-Datei) vorgenommen, um das Format besser lesbar zu machen und Pakete besser vergleichen zu können. Außerdem wurde das Zusammenführen von Paketen verbessert, die keine miteinander in Konflikt stehenden Änderungen oder im Binärformat gespeicherte Änderungen enthalten.  
  
 Um das aktuelle DTSX-Paketdateiformat anzuzeigen, finden Sie weitere Informationen unter [\[MS-DTSX\]: XML-Dateiformatspezifikation für das Data Transformation Services-Paket](http://go.microsoft.com/fwlink/?LinkId=233251).  
  
 In der folgenden Liste werden die Dateiformatänderungen beschrieben. Um Codebeispiele für diese Änderungen anzuzeigen, finden Sie weitere Informationen unter [Paketformatänderungen in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=233255).  
  
-   Formatierungskonventionen wurden übernommen, um die DTSX-Datei besser lesbar und verständlicher zu machen.  
  
-   Das Format ist präziser. Separate Elemente für jede Eigenschaft wurden als Attribute beibehalten, mit Ausnahme von PackageFormatVersion. Attribute sind alphabetisch aufgeführt, und Eigenschaften, die über Standardwerte verfügen, werden nicht mehr beibehalten. Außerdem sind Elemente, die mehrmals angezeigt werden können, jetzt innerhalb eines übergeordneten Elements enthalten.  
  
-   Die meisten Objekte in einem Paket, auf die von anderen Objekten verwiesen werden kann, verfügen jetzt über ein im Paket-XML definiertes `refId`-Attribut. Statt persistenter Herkunfts-IDs wird die `refID` jetzt beibehalten. Herkunfts-IDs werden immer noch zur Laufzeit verwendet und neu generiert, wenn das Paket geladen wird.  
  
     Die `refId` Wert ist eine eindeutige Zeichenfolge, die lesbar und verständlich ist im Vergleich zu GUIDs oder ganzzahligen Werten. Die Zeichenfolge ist ähnlich wie Pfadwerte, die in vorherigen Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]für die Paketkonfigurationen verwendet wurden.  
  
     Wenn Sie Änderungen zwischen zwei Versionen eines Pakets Zusammenführen der `refId` kann in Such-/Ersetzungsvorgängen verwendet werden, um sicherzustellen, dass alle Verweise auf dieses Objekt ordnungsgemäß aktualisiert wurden.  
  
-   Die Layoutinformationen sind in einem CDATA-Abschnitt enthalten.  
  
-   Anmerkungen werden in Klartext beibehalten. Dies erleichtert es, die Informationen für die automatisierte Generierung der Dokumentation zu extrahieren.  
  
  
