---
title: Rollen und Berechtigungen (Reporting Services) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: security
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1e26c8b95824ab9bc67b5425145322dfbdb59bca
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43272421"
---
# <a name="roles-and-permissions-reporting-services"></a>Rollen und Berechtigungen (Reporting Services)
  Reporting Services stellt ein Authentifizierungssubsystem und ein rollenbasiertes Autorisierungsmodell bereit. Authentifizierungs- und Autorisierungsmodelle sind je nachdem, ob der Berichtsserver im einheitlichen Modus oder im integrierten SharePoint-Modus ausgeführt wird, unterschiedlich. Ist der Berichtsserver Bestandteil einer umfangreicheren SharePoint-Bereitstellung, wird mit SharePoint-Berechtigungen festgelegt, wer Zugriff auf den Berichtsserver hat.  
  
## <a name="identity-and-access-control-for-native-mode"></a>Identität und Zugriffssteuerung für den systemeigenen Modus  
 Die Standardauthentifizierung basiert auf der Windows-Authentifizierung und der integrierten Sicherheit. Sie können die Authentifizierungseinstellungen so ändern, dass der Berichtsserver auf andere Authentifizierungsanforderungen reagieren kann. Alternativ können Sie sogar die Standardsicherheitsfunktionen durch eine von Ihnen bereitgestellte benutzerdefinierte Authentifizierungserweiterung ersetzen.  
  
 Die Autorisierung basiert auf Rollen, die Sie einem Prinzipal zuweisen. Jede Rolle besteht aus einer Reihe von zusammenhängenden Aufgaben, die wiederum aus zusammenhängenden Vorgängen bestehen. So erteilt z. B. die Aufgabe **Berichte verwalten** Zugriff auf folgende Berichtsservervorgänge: Anzeigen, Hinzufügen, Aktualisieren, Löschen und Planen von Berichten sowie Aktualisieren von Berichtseigenschaften.  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a>Identität und Zugriffssteuerung für den SharePoint-Modus  
 Im integrierten SharePoint-Modus werden die Authentifizierung und die Autorisierung auf der SharePoint-Website verarbeitet, bevor Anforderungen den Berichtsserver erreichen. Abhängig von der Konfiguration der Authentifizierung enthalten Anforderungen von einer SharePoint-Website ein Sicherheitstoken oder einen vertrauenswürdigen Benutzernamen. Durch die für SharePoint-Benutzer und -Gruppen festgelegten Berechtigungen wird der Zugriff auf in SharePoint-Bibliotheken gespeicherte Berichtsserverelemente autorisiert.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
 Beschreibt das rollenbasierte Autorisierungsmodell, das Zugriff auf Inhalt und Vorgänge bereitstellt.  
  
 [Erteilen von Berechtigungen für Berichtsserverelemente auf einer SharePoint-Website](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 Erläutert, wie mit SharePoint-Gruppen, Berechtigungsebenen und Berechtigungen der Zugriff auf einen Berichtsserver gesteuert werden kann.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Authentifizierung mit dem Berichtsserver](../../reporting-services/security/authentication-with-the-report-server.md)   
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
