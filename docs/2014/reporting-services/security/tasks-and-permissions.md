---
title: Aufgaben und Berechtigungen | Microsoft-Dokumentation
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
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
caps.latest.revision: 39
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 38e0063f336ef7c2cb7a7bcfc33c0026259b4c83
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177197"
---
# <a name="tasks-and-permissions"></a>Aufgaben und Berechtigungen
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]stellen *Aufgaben* Aktionen dar, die ein Benutzer oder Administrator ausführen kann. Aufgaben sind vordefiniert. Es ist nicht möglich, benutzerdefinierte Aufgaben zu erstellen oder die vom Programm oder über ein Tool bereitgestellten Aufgaben zu ändern. Es gibt insgesamt fünfundzwanzig Aufgaben. Diese Aufgaben enthalten alle Vorgänge, die für die rollenbasierte Sicherheit zur Verfügung stehen. Beispiele für Aufgaben sind "Berichte anzeigen", "Berichte verwalten" oder "Berichtsservereigenschaften verwalten".  
  
 Jede Aufgabe besteht aus Berechtigungen, die ebenfalls vordefiniert sind. Beispielsweise enthält die Aufgabe "Ordner verwalten" Berechtigungen zum Erstellen und Löschen von Ordnern sowie zum Anzeigen und Aktualisieren der Ordnereigenschaften. Die Berechtigungen für die einzelnen Aufgaben sind dokumentiert, um eine genauere Beschreibung der einzelnen Aufgaben bereitzustellen. Die direkte Interaktion mit Berechtigungen und das Angeben von Berechtigungen in Rollenzuweisungen sind nicht möglich. Vielmehr werden Benutzern Berechtigungen indirekt über die Aufgaben erteilt, die zu Rollendefinitionen gehören.  
  
 Aufgaben können nur ausgeführt werden, wenn sie Teil einer Rolle sind und diese Rolle in einer Rollenzuweisung enthalten ist. Wenn z. B. die Aufgabe Modelle anzeigen nicht in einer Rolle enthalten ist oder diese Rolle nicht Teil einer Rollenzuweisung ist, können Benutzer keine Berichtsmodelle anzeigen. Das folgende Diagramm veranschaulicht, wie Berechtigungen in Aufgaben kombiniert und wie Aufgaben in Rollen kombiniert werden, die für spezielle Rollenzuweisungen verwendet werden können.  
  
 ![Diagramm für Berechtigungen und Aufgaben](../media/report-securityobjects.gif "Permissions and task diagram")  
Diagramm für Berechtigungen und Aufgaben  
  
## <a name="system-and-item-level-tasks"></a>Aufgaben auf System- und Elementebene  
 Aufgaben können zwei Kategorien zugeordnet werden: Aufgaben auf Systemebene und auf Elementebene. In einer Rolle können nur Aufgaben aus einer einzigen Kategorie vorhanden sein. In der folgenden Tabelle sind die verschiedenen Aufgabenkategorien beschrieben.  
  
|Kategorie|Description|  
|--------------|-----------------|  
|[Aufgaben auf Elementebene](tasks-and-permissions-item-level-tasks.md)|Aktionen, die für Elemente ausgeführt werden, die von einem Berichtsserver verwaltet werden, wie z. B. Ordner, Berichte, Berichtsmodelle und Ressourcen.<br /><br /> Als Bereich für Aufgaben auf Elementebene gilt der Ordnernamespace des Berichtsservers. Alle Elemente, auf die über die Ordner auf einem Berichtsserver oder über eine URL zugegriffen wird, sind durch Rollenzuweisungen gesichert, die Aufgaben auf Elementebene enthalten.|  
|[Aufgaben auf Systemebene](tasks-and-permissions-system-level-tasks.md)|Aktionen, die auf Systemebene ausgeführt werden, wie z. B. die Verwaltung von Aufträgen oder freigegebenen Zeitplänen, die für viele Elemente verwendet werden können. Der Bereich für Aufgaben auf Systemebene liegt außerhalb des Ordnernamespaces des Berichtsservers.|  
  
## <a name="see-also"></a>Siehe auch  
 [Rollendefinitionen](role-definitions.md)   
 [Vordefinierte Rollen](role-definitions-predefined-roles.md)   
 [Granting Permissions on a Native Mode Report Server (Erteilen von Berechtigungen für einen Berichtsserver im einheitlichen Modus)](granting-permissions-on-a-native-mode-report-server.md)  
  
  
