---
title: Exportieren von Daten (Master Data Services) | Microsoft-Dokumentation
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
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 2d42511c3e7fecfba3f1a8fd92e9f8633564bf17
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332160"
---
# <a name="exporting-data-master-data-services"></a>Exportieren von Daten (Master Data Services)
  Sie können exportieren [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Daten in abonnementsysteme, indem Sie Abonnementsichten erstellen. Die veröffentlichten Daten in der Datenbank [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] können dann von jedem Abonnementsystem angezeigt werden. Weitere Informationen zu Sichten finden Sie unter [Sichten](../relational-databases/views/views.md).  
  
## <a name="subscription-view-formats"></a>Abonnementsichtformate  
 Wenn Sie eine Sicht in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]erstellen, steht Ihnen eine Reihe von Standardsichtformaten in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] zur Auswahl. Mithilfe dieser Formate können Sie Sichten mit folgendem Inhalt erstellen:  
  
-   Alle Blattelemente und deren Attribute  
  
-   Alle konsolidierten Elemente und deren Attribute  
  
-   Alle Auflistungen und deren Attribute  
  
-   Die Elemente, die der Auflistung explizit hinzugefügt wurden  
  
-   Elemente in einer abgeleiteten Hierarchie in einem Format mit über- und untergeordneten Elementen oder Ebenen  
  
-   Elemente in allen expliziten Hierarchien für eine Entität in einem Format mit über- und untergeordneten Elementen oder Ebenen  
  
## <a name="subscription-views-can-become-out-of-date"></a>Abonnementsichten können ihre Aktualität verlieren  
 Nachdem Sie für eine Entität oder eine Hierarchie eine Abonnementsicht erstellt haben, werden Änderungen an den zugeordneten Modellobjekten nicht automatisch in der Sicht widergespiegelt. Sie müssen eine Abonnementsicht in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ggf. erneut generieren, um Änderungen an den Modellobjekten widerzuspiegeln. Die Spalte **Geändert** auf der Seite **Exportieren** wird bei einer Änderung der Modellobjekte in **True** geändert. Der Wert**True** gibt an, dass Sie die Abonnementsicht bearbeiten und speichern sollten, um die Sicht erneut zu generieren.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie eine Abonnementsicht der Masterdaten.|[Erstellen einer Abonnementsicht &#40;Master Data Services&#41;](create-a-subscription-view-to-export-data-master-data-services.md)|  
|Löschen Sie eine vorhandene Abonnementsicht.|[Löschen einer Abonnementsicht &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Abonnementsichtformate &#40;Master Data Services&#41;](../../2014/master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Sichten](../relational-databases/views/views.md)  
  
  
