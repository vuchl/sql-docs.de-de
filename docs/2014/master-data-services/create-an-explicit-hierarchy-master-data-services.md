---
title: Erstellen einer expliziten Hierarchie (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
caps.latest.revision: 7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d75b956b6d9be23bd17e3df705724d3876d583
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219490"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a>Erstellen einer expliziten Hierarchie (Master Data Services)
  Erstellen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eine explizite Hierarchie, wenn Sie eine unregelmäßige Hierarchie benötigen, in der Elemente auf jeder Ebene vorhanden sein können. Explizite Hierarchien enthalten Elemente aus einer einzelnen Entität.  
  
 Wenn Sie eine explizite Hierarchie erstellt haben, können Sie dieser im Funktionsbereich **Explorer** Elemente hinzufügen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Die Entität muss für explizite Hierarchien und Auflistungen aktiviert werden. Weitere Informationen finden Sie unter [Aktivieren einer Entität für explizite Hierarchien und Auflistungen &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).  
  
### <a name="to-create-an-explicit-hierarchy"></a>So erstellen Sie eine explizite Hierarchie  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modellansicht** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie die Zeile für die Entität aus, für die Sie eine explizite Hierarchie erstellen möchten.  
  
5.  Klicken Sie auf **Ausgewählte Entität bearbeiten**.  
  
6.  Auf der **Entität bearbeiten** auf der Seite die **explizite Hierarchien** Bereich, klicken Sie auf **explizite Hierarchie hinzufügen**.  
  
7.  Auf der **explizite Hierarchie hinzufügen** auf der Seite die **Name der expliziten Hierarchie** Feld Geben Sie einen Namen für die Hierarchie.  
  
8.  Optional können Sie das Kontrollkästchen für **Obligatorische Hierarchie** deaktivieren, um die Hierarchie als nicht obligatorische Hierarchie zu erstellen. Weitere Informationen zu Hierarchietypen finden Sie unter [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).  
  
9. Klicken Sie auf **Hierarchie speichern**.  
  
10. Auf der **Entität bearbeiten** auf **Entität speichern**.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Erstellen eines konsolidierten Elements &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [Verschieben von Elementen innerhalb einer Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Explizite Hierarchien &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Abgeleitete Hierarchien mit expliziten Abschlüssen &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Ändern des Namens einer expliziten Hierarchie &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
