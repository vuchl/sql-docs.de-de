---
title: SQL Server Management Studio – Telemetrie (SSMS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/20/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
caps.latest.revision: 72
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78e74f96f36c5bfb21859bbc1f4ef1916e061b59
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36926881"
---
# <a name="local-audit-for-ssms-usage-feedback-collection"></a>Lokale Überwachung für Feedbackerfassung zur SSMS-Nutzung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
SQL Server Management Studio (SSMS) enthält internetaktivierte Features, die anonyme Featurenutzungsdaten erfassen und an Microsoft senden können. SSMS erfasst möglicherweise Standardinformationen zu Ihrem Computer und Informationen zur Nutzung und Leistung, die möglicherweise an Microsoft übermittelt und analysiert werden, um die Qualität, Sicherheit und Zuverlässigkeit von SSMS zu optimieren. Wir erfassen nicht Ihren Namen, Ihre Adresse oder andere Kontaktinformationen. Weitere Informationen finden Sie in den [Datenschutzbestimmungen von SQL Server](http://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="audit-feature-usage-data"></a>Überwachen von Featurenutzungsdaten

Machen Sie Folgendes, um sich die von SSMS erfassten Featurenutzungsdaten anzeigen zu lassen:
1.  Starten Sie SSMS.
2.  Klicken Sie auf **View** (Ansicht), und klicken Sie anschließend im Hauptmenü auf **Output** (Ausgabe), um das Fenster **Output** (Ausgabe) anzuzeigen. 
3.  Wenn das Fenster **Output** (Ausgabe) angezeigt wird, wählen Sie im Menü **Show output from:** (Ausgabe anzeigen von:) **Telemetry** (Telemetrie) aus.

Während Sie SSMS verwenden, um mit Ihrer Datenbank zu interagieren, zeigt das Fenster **Output** (Ausgabe) die erfassten Daten an.

## <a name="enable-or-disable-usage-feedback-collection-in-ssms"></a>Feedbackerfassung der Nutzung in SSMS aktivieren bzw. deaktivieren

Informationen zum Zustimmen oder Ablehnen der SSMS-Nutzungsdatenerfassung finden Sie unter [How to configure SQL Server 2016 to send feedback to Microsoft (Konfigurieren von SQL Server 2016 zum Senden von Feedback an Microsoft)](http://support.microsoft.com/help/3153756/how-to-configure-sql-server-2016-to-send-feedback-to-microsoft).

## <a name="see-also"></a>Siehe auch

[Lokale Überwachung für Feedbackerfassung zur SQL Server-Nutzung](http://msdn.microsoft.com/library/mt743085.aspx)
