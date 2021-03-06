---
title: Drucken von Berichten aus anderen Anwendungen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 380bebaa85da73108af8611ac537565dc5d91d00
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278856"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a>Drucken von Berichten aus anderen Anwendungen (Berichts-Generator und SSRS)
  Berichts-Generator stellt eine Exportoption bereit, mit der Sie einen Bericht in anderen Anwendungen einfach anzeigen können. Die `Export` Befehl steht auf der Symbolleiste des Berichts, der am oberen Rand eines Berichts angezeigt wird, wenn Sie es in einem Browser oder einer webbasierten Anwendung öffnen. Nach dem Export eines Berichts wird dieser in einer anderen Anwendung angezeigt (durch Exportieren eines Berichts nach Excel wird der Bericht z. B. in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]geöffnet). Das Exportieren des Berichts zum Drucken wird nur dann empfohlen, wenn die Anwendung über spezifische Druckfunktionen verfügt, die Sie verwenden möchten.  
  
 Wenn Sie einen Bericht in eine andere Anwendung exportieren möchten, muss diese Anwendung installiert sein. Adobe Acrobat Reader muss z. B. auf dem Computer installiert sein, damit der Export in das Acrobat-Format (PDF) möglich ist. Wenn Sie einen Bericht in das TIFF-Format exportieren möchten, platziert der Berichtsserver den Bericht in eine Anwendung zum Anzeigen des TIFF-Dateityps. Die verwendete Anwendung hängt zwar von der Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] ab, aber in der Regel handelt es sich dabei um die Windows Bild- und Faxanzeige. Die Standardauflösung entspricht einer Bildschirmauflösung von 96 dpi (Dots per Inch, Punkte pro Zoll). Die Auflösung in der Windows Bild- und Faxanzeige kann entsprechend der Leistung Ihres Druckers auf 300 dpi oder 600 dpi erhöht werden. Weitere Informationen zum Anpassen der Auflösung finden Sie in der Windows-Produktdokumentation.  
  
 Falls Sie Webarchiv (auch MHTML genannt) auswählen, wird der Bericht in den Standardbrowser exportiert. Beim Drucken über den Browser können Informationen zum Berichtspfad unten auf jeder Seite hinzugefügt werden. Mithilfe von Browseroptionen können Sie in den meisten Fällen die Pfadinformationen auf gedruckten Seiten ausblenden. Weitere Informationen finden Sie in der Produktdokumentation des verwendeten Browsers.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Drucken eines Berichts &#40;Berichts-Generator und SSRS&#41;](print-a-report-report-builder-and-ssrs.md)   
 [Drucken von Berichten in einem Browser mit dem Drucksteuerelement (Berichts-Generator und SSRS)](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [Exportieren eines Berichts in ein anderes Dateiformat (Berichts-Generator und SSRS)](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS )](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
