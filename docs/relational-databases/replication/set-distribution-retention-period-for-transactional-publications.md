---
title: Festlegen der Beibehaltungsdauer für die Verteilung von Transaktionsveröffentlichungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26fd699262d30d4565448aae544c0193b8d90fb4
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37354988"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Festlegen der Beibehaltungsdauer für die Verteilung von Transaktionsveröffentlichungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Geben Sie die Mindestbeibehaltungsdauer und die maximale Beibehaltungsdauer der Verteilung im Dialogfeld **Eigenschaften der Verteilungsdatenbank - \<Verteilungsdatenbank>** an. Dieses Dialogfeld ist über die Seite **Allgemein** des Dialogfelds **Verteilereigenschaften - \<Distributor>** verfügbar. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>So geben Sie die Beibehaltungsdauer für die Verteilung an  
  
1.  Klicken Sie auf der Seite **Allgemein** des Dialogfelds **Verteilereigenschaften - \<Distributor>** auf die Schaltfläche mit den drei Punkten (**…**) für die Verteilungsdatenbank.  
  
2.  Zum Angeben der Mindestbeibehaltungsdauer geben Sie einen Wert in das Feld **Mindestens** ein; zum Angeben der maximalen Beibehaltungsdauer geben Sie einen Wert in das Feld **Aber nicht länger als** ein.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)   
 [Abonnementablauf und -deaktivierung](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
