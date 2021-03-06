---
title: Wichtige Änderungen in SQL Server Reporting Services in SQL Server 2016 | Microsoft-Dokumentation
ms.date: 07/02/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bb8bd3ab583e4bd0c23d0c879a5a3ee09359adfe
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43269766"
---
# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>Aktuelle Änderungen in SQL Server Reporting Services in SQL Server 2016

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

In diesem Thema werden wichtige Änderungen in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]beschrieben. Diese Änderungen können u. U. zur Funktionsunfähigkeit von Anwendungen, Skripts oder Funktionen führen, die auf früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]basieren. Diese Probleme können nach einem Upgrade oder in benutzerdefinierten Skripts oder Berichten auftreten.

## <a name="security-extensions"></a>Sicherheitserweiterungen

Benutzerdefinierte Sicherheitserweiterungen erfordern einige Änderungen, damit sie mit dem neuen [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]funktionieren. Sicherheitserweiterungen müssen die IAuthenticationExtension2-Schnittstelle verwenden.

## <a name="wmi-provider"></a>WMI-Anbieter

Der Name der [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] -Anwendung ändert sich von „ReportManager“ in „ReportServerWebApp“.

## <a name="next-steps"></a>Nächste Schritte

[Behavior changes to SQL Server Reporting Services in SQL Server 2016 (Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2016)](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Neues bei Reporting Services (SSRS)](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[Deprecated features in SQL Server Reporting Services in SQL Server 2016 (Als veraltet markierte Funktionen in SQL Server Reporting Services in SQL Server 2016)](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[Discontinued functionality to SQL Server Reporting Services in SQL Server 2016 (Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQL Server 2016)](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](http://go.microsoft.com/fwlink/?LinkId=620231)
