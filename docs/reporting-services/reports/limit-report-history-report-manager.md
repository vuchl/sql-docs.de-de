---
title: Einschränken des Berichtsverlaufs (Berichts-Manager) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 373128872f32b3e8727db8f3059475bcd8dac12a
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43271921"
---
# <a name="limit-report-history-report-manager"></a>Einschränken des Berichtsverlaufs (Berichts-Manager)
  Der Berichtsverlauf stellt eine Auflistung von Berichtsmomentaufnahmen dar, die Sie im Laufe der Zeit erstellen. Sie können den Berichtsverlauf nach Bedarf erstellen oder aber anhand eines Zeitplans festlegen, wie oft eine Momentaufnahme erstellt und dem Berichtsverlauf hinzugefügt wird.  
  
 Der Berichtsverlauf wird in der Berichtsserverdatenbank gespeichert. Wenn Berichtsmomentaufnahmen eine große Datenmenge enthalten, können Sie den Berichtsverlauf einschränken, um die Auswirkungen der Beibehaltung der Momentaufnahmen auf die Datenbankgröße zu minimieren.  
  
### <a name="to-configure-report-history-for-a-report-server"></a>So konfigurieren Sie den Berichtsverlauf für einen Berichtsserver  
  
1.  Klicken Sie im Berichts-Manager auf der globalen Symbolleiste auf **Siteeinstellungen** .  
  
2.  Wählen Sie **Beliebig viele Momentaufnahmen im Berichtsverlauf speichern** aus, wenn Sie alle Berichtsverläufe unbegrenzt lange aufbewahren möchten. Wählen Sie andernfalls **Max. Anzahl von Kopien des Berichtsverlaufs** aus, um die maximale Anzahl von Momentaufnahmen anzugeben, die für einen bestimmten Bericht aufbewahrt werden können.  
  
3.  Klicken Sie auf **Anwenden**.  
  
### <a name="to-configure-report-history-for-a-specific-report"></a>So konfigurieren Sie den Berichtsverlauf für einen bestimmten Bericht  
  
1.  Navigieren Sie im Berichts-Manager zu dem Bericht, dessen Verlauf Sie konfigurieren möchten, und öffnen Sie ihn, indem Sie auf ihn klicken.  
  
2.  Klicken Sie auf die Registerkarte **Eigenschaften** .  
  
3.  Klicken Sie auf die Registerkarte **Verlauf** .  
  
4.  Wählen Sie die Optionen für Ihren Bericht aus, und klicken Sie auf **Anwenden**. Weitere Informationen zu den einzelnen Optionen finden Sie unter [Momentaufnahmeoptionen Eigenschaftenseite (Berichts-Manager)](http://msdn.microsoft.com/library/f6641f59-5267-4f57-8957-63b93d1a9679).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Hinzufügen einer Momentaufnahme zum Berichtsverlauf &#40;Berichts-Manager&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Berichts-Manager (einheitlicher SSRS-Modus)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  
  
  
