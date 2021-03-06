---
title: Exportieren eines Berichts über URL-Zugriff | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d44c68f381ee1fd7b6fed31e15bf2639dd57976e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327440"
---
# <a name="export-a-report-using-url-access"></a>Exportieren von Berichten über URL-Zugriff
  Optional können Sie angeben, das Format, in dem zum Rendern eines Berichts mithilfe der *Rs: Format* Parameter. Um beispielsweise von einem im einheitlichen Modus ausgeführten Berichtsserver direkt eine PDF-Kopie eines Berichts abzurufen, geben Sie Folgendes an:  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 Zum Abrufen von einem Berichtsserver im integrierten SharePoint-Modus geben Sie Folgendes an:  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 Gültige Werte für diesen Parameter sind von den Berichtrenderingerweiterungen abhängig, die auf dem Berichtsserver installiert sind, auf den zugegriffen wird. Häufig verwendete Erweiterungen sind HTML4.0, MHTML, IMAGE, EXCEL, WORD, CSV, PDF, XML und NULL. Wenn eine bestimmte Renderingerweiterung nicht auf dem Berichtsserver installiert ist, wird der Bericht nicht gerendert. Es wird ein Fehler generiert und im Browser angezeigt.  
  
 Wenn Sie den *Format* -Parameter nicht als Teil der URL aufnehmen, erkennt der Berichtsserver den Browser und rendert den Bericht im entsprechenden HTML-Format.  
  
## <a name="see-also"></a>Siehe auch  
 [URL-Zugriff &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL Access Parameter Reference (URL-Zugriffsparameterverweis)](url-access-parameter-reference.md)  
  
  
