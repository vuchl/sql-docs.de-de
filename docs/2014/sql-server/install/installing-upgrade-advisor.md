---
title: Installieren des Upgrade Advisors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
caps.latest.revision: 34
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8c15c361f1fc29a805948b3761fd0a04c5c396c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327010"
---
# <a name="installing-upgrade-advisor"></a>Installieren des Upgrade Advisors
  Der Speicherort für das Installieren des Upgrade Advisors für SQL Server 2014 ist abhängig davon, was analysiert werden soll. Der Upgrade Advisor unterstützt die Remoteanalyse aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von Scannen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], Sie können Upgrade Advisor installieren, auf jedem Computer, die eine Verbindung herstellen kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und die erfüllt die [Voraussetzungen für ein Upgrade Advisors](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md). Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Führen Sie die **SQLUA.msi** Datei zum Upgrade Advisor zu installieren. Sie können über die Eingabeaufforderung für unbeaufsichtigte und automatisierte Installationen installieren. Finden Sie unter [Installation von Upgrade Advisor über die Eingabeaufforderung](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) zur Syntax und Beispiele.  
  
 Rufen Sie die SQLUA.msi auf:  
  
-   In der **Redist** Ordner die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Produktmedien.  
  
-   Als Teil der [SQL 2014 Feature Pack-Download](http://www.microsoft.com/download/details.aspx?id=42295).  
  
## <a name="uninstalling-upgrade-advisor"></a>Deinstallieren des Upgrade Advisors  
 Sie können Upgrade Advisor deinstallieren, indem Sie mithilfe von **Software**. Die Syntax der Eingabeaufforderung unterstützt auch das Entfernen/Deinstallieren.  
  
  
