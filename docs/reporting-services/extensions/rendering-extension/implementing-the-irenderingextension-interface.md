---
title: Implementieren der IRenderingExtension-Schnittstelle | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- IRenderingExtension interface
- rendering extensions [Reporting Services], IRenderingExtension interface
ms.assetid: 74b2f2b7-6796-42da-ab7d-b05891ad4001
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5526129418f454f7323add732458081f5db11869
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43274462"
---
# <a name="implementing-the-irenderingextension-interface"></a>Implementieren der IRenderingExtension-Schnittstelle
  Die Renderingerweiterung nimmt die Ergebnisse von einer Berichtsdefinition, die mit den tatsächlichen Daten kombiniert wird, und rendert die resultierenden Daten zu einem Format, das verwendbar ist. Die Transformation der kombinierten Daten und der Formatierung wird mit einer Common Language Runtime (CLR)-Klasse ausgeführt, die <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> implementiert. Dies wandelt das Objektmodell in ein Ausgabeformat um, das durch einen Viewer, Drucker oder ein anderes Ausgabeziel konsumierbar ist.  
  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension> verfügt über drei Methoden, die codiert werden müssen.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A> – rendert den Bericht.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A> – rendert einen bestimmten Datenstrom aus dem Bericht.  
  
-   <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>- ruft weitere Informationen ab, z. B. Symbole, die für den Bericht erforderlich sind.  
  
 In den folgenden Abschnitten werden diese Methoden ausführlicher erörtert.  
  
## <a name="render-method"></a>Render-Methode  
 Die <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A>-Methode enthält Argumente, die folgende Objekte darstellen:  
  
-   Den *Bericht*, den Sie rendern möchten. Dieses Objekt enthält Eigenschaften, Daten und Layoutinformationen für den Bericht. Der Bericht ist der Stamm für die Modellstruktur des Berichtsobjekts.  
  
-   Die *ServerParameters*, die das Zeichenfolgen-Wörterbuchobjekt mit den Parametern für den Berichtsserver enthalten, sofern vorhanden.  
  
-   Der *deviceInfo*-Parameter mit den Geräteeinstellungen. Weitere Informationen finden Sie unter [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
-   Der *clientCapabilities*-Parameter, der ein <xref:System.Collections.Specialized.NameValueCollection>-Wörterbuch enthält, das Informationen über den Client umfasst, für den Sie den Rendervorgang durchführen.  
  
-   *RenderProperties* mit Informationen zum Ergebnis des Rendervorgangs.  
  
-   *createAndRegisterStream* ist eine Delegatfunktion, die aufgerufen wird, damit ein Stream hineingerendert wird.  
  
### <a name="deviceinfo-parameter"></a>deviceInfo-Parameter  
 Der *deviceInfo*-Parameter enthält Renderingparameter, nicht Berichtsparameter. Diese Renderingparameter werden an die Renderingerweiterung übergeben. Die *deviceInfo*-Werte werden vom Berichtsserver zu einem <xref:System.Collections.Specialized.NameValueCollection>-Objekt konvertiert. Elemente im *deviceInfo*-Parameter werden als Werte behandelt, bei denen die Groß- und Kleinschreibung nicht beachtet wird. Wenn die Renderinganforderung als Ergebnis des URL-Zugriffs aufgetreten ist, werden die URL-Parameter in Form von `rc:key=value` zu Schlüssel/Wert-Paaren im *deviceInfo*-Wörterbuchobjekt umgewandelt. Der Code für die Browserabfrage enthält folgende Elemente im *clientCapabilities*-Wörterbuch: EcmaScriptVersion, JavaScript, MajorVersion, MinorVersion, Win32, Type und AcceptLanguage. Jedes Name/Wert-Paar im *deviceInfo*-Parameter, das nicht von der Renderingerweiterung erkannt wird, wird ignoriert. Das folgende Codebeispiel zeigt eine <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>-Methode, die Symbole abruft:  
  
```csharp  
public void GetRenderingResource (CreateStream createStreamCallback, NameValueCollection deviceInfo)  
{  
    string[] iconTagValues = deviceInfo.GetValues("Icon");  
    if ((iconTagValues != null) && (iconTagValues.Length > 0) )  
    {  
        // Create a stream to output to.  
        Stream outputStream = createStreamCallback(m_iconResourceName, "gif", null, "image/gif", false);  
        // Get the GIF image for one of the buttons on the toolbar  
        Image requiredImage = (Image) m_resourcemanager.GetObject(m_iconResourceName  
        // Write the image to the output stream  
        requiredImage.Save(outputStream, requiredImage.RawFormat);  
    }  
    return;  
}  
```  
  
## <a name="renderstream-method"></a>RenderStream-Methode  
 Die <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.RenderStream%2A>-Methode rendert einen besonderen Datenstrom aus dem Bericht. Alle Datenströme werden während des ersten <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.Render%2A>-Aufrufs erstellt, aber die Ströme werden anfangs nicht zum Client zurückgegeben. Diese Methode wird für Sekundärströme (wie Bilder in HTML-Rendering) oder zusätzliche Seiten einer mehrseitigen Renderingerweiterung (wie Image/EMF) verwendet.  
  
## <a name="getrenderingresource-method"></a>GetRenderingResource-Methode  
 Die <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>-Methode ruft die Informationen ab, ohne den kompletten Renderingvorgang für den Bericht auszuführen. Manchmal benötigt ein Bericht Informationen, die es nicht erfordern, dass der Bericht selbst gerendert wird. Wenn Sie beispielsweise das zur Renderingerweiterung gehörige Symbol benötigen, verwenden Sie den *deviceInfo*-Parameter, der das Einzeltag **\<Icon>** enthält. In diesen Fällen können Sie die <xref:Microsoft.ReportingServices.OnDemandReportRendering.IRenderingExtension.GetRenderingResource%2A>-Methode verwenden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Rendering Extensions Overview (Übersicht über Renderingerweiterungen)](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
  
  
