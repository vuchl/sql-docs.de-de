---
title: Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- URL access [Reporting Services], report history
- history snapshots [Reporting Services]
- historical data [Reporting Services]
- snapshots [Reporting Services], URL access
- snapshots [Reporting Services], rendering report history
ms.assetid: 3f87f82d-0e61-4492-9c4b-f5238c39e8cd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 44de81b48604356761ed855f4b765af60cb75103
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43279262"
---
# <a name="render-a-report-history-snapshot-using-url-access"></a>Rendern von Berichtsverlaufs-Momentaufnahmen mit URL-Zugriff
  Sie können einen Bericht auf der Grundlage einer Berichtsverlaufs-Momentaufnahme rendern, indem Sie den Parameter *rs:Snapshot* angeben und seinen Wert auf eine gültige Momentaufnahme-ID festlegen. Der Parameterwert hat das Format YYYY-MM-DDTHH:MM:SS und basiert auf dem ISO-Standard 8601 (Standard International Organization for Standardization).  
  
 Wenn Sie diesen Parameter weglassen, wird der Bericht gemäß den Optionseinstellungen für die Berichtsausführung und Cacheverwaltung des Berichtsservers gerendert. Weitere Informationen zur Ausführung von Berichten finden Sie unter [Festlegen von Berichtsverarbeitungseigenschaften](../reporting-services/report-server/set-report-processing-properties.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine URL, die eine Berichtsverlaufs-Momentaufnahme abruft:  
  
```  
http://myrshost/reportserver?/SampleReports/Company Sales&rs:Snapshot=2003-04-07T13:40:02  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [URL-Zugriff &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](../reporting-services/url-access-parameter-reference.md)  
  
  
