---
title: Zugriff auf die SOAP-API | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML Web service [Reporting Services], WSDL
- Web service [Reporting Services], SOAP
- calling Web service
- SOAP [Reporting Services], accessing
- Report Server Web service, SOAP
- Web service [Reporting Services], WSDL
- WSDL [Reporting Services]
- XML Web service [Reporting Services], SOAP
- Report Server Web service, WSDL
- referencing WSDL
ms.assetid: 63bb870a-4dbf-46bd-8921-78f8ebe5fd75
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d232c4014f6b6927d501057bdb6eff1996d623fb
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43271762"
---
# <a name="accessing-the-soap-api"></a>Accessing the SOAP API
  Der Berichtsserver-Webdienst verwendet SOAP (Simple Object Access Protocol) über HTTP und agiert als Kommunikationsschnittstelle zwischen den Clientprogrammen und dem Berichtsserver. Der Webdienst verfügt über zwei Endpunkte (einen für die Berichtsausführung und einen für die Berichtsverwaltung) und besteht aus Methoden und einer Reihe komplexer Typenobjekte, anhand derer Sie auf die kompletten Funktionen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] zugreifen können. Um den Dienst aufzurufen, müssen Sie auf die Reporting Services-WSDL (Web Services Description Language) verweisen.  
  
## <a name="referencing-the-reporting-services-wsdl"></a>Verweisen auf die Reporting Services-WSDL  
 Um einen Webdienst erfolgreich aufzurufen, müssen Sie wissen, wie auf den Dienst zugegriffen wird, welche Vorgänge der Dienst unterstützt, welche Parameter der Dienst benötigt und was der Dienst zurückgibt. WSDL stellt diese Informationen in einem XML-Dokument bereit, das von einem Computer gelesen oder verarbeitet werden kann.  
  
 Die Berichtsserver-Webdienste werden an drei unterschiedlichen Endpunkten verfügbar gemacht. Der Name der WSDL-Datei ist für jeden Endpunkt anders. Der <xref:ReportService2010>-Endpunkt enthält Methoden zum Verwalten von Objekten auf einem Berichtsserver im einheitlichen Modus oder integrierten SharePoint-Modus. Auf die WSDL für diesen Endpunkt wird über `ReportService2010.asmx?wsdl.` zugegriffen.  
  
> [!NOTE]  
>  Der <xref:ReportService2005>-Endpunkt und der <xref:ReportService2006>-Endpunkt sind in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] als veraltet markiert. Der <xref:ReportService2010>-Endpunkt schließt die Funktionen beider Endpunkte ein und beinhaltet zusätzliche Verwaltungsfunktionen.  
  
-   Der <xref:ReportExecution2005>-Endpunkt ermöglicht es Entwicklern, Berichte programmgesteuert auf einem Berichtsserver zu verarbeiten und zu rendern. Sie können über `ReportExecution2005.asmx?wsdl` auf die WSDL dieses Endpunkts zugreifen.  
  
 Die WSDL kann von Development Kits verwendet werden, die SOAP- und Webdienste unterstützen, wie z.B. das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
 Das folgende Beispiel zeigt das Format der URL zur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Verwaltungs-WSDL-Datei:  
  
```  
http://server/reportserver/ReportService2010.asmx?wsdl  
```  
  
 In der folgenden Tabelle werden die einzelnen Elemente in der URL beschrieben.  
  
|URL-Element|und Beschreibung|  
|-----------------|-----------------|  
|*server*|Der Name des Servers, auf dem der Berichtsserver eingesetzt wird.|  
|*berichtsserver*|Der Name des Ordners, der den XML-Webdienst enthält. Dieser wird während des Setups konfiguriert.|  
|*\<endpunktname>.asmx*|Der Name des Webdienst-Endpunkts.|  
  
 Weitere Informationen über das WSDL-Format finden Sie in der WSDL-Spezifikation von W3C (World Wide Web Consortium) unter http://www.w3.org/TR/wsdl.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erstellen von Anwendungen mit dem Webdienst und .NET Framework](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Report Server Web Service (Report Server-Webdienst)](../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
