---
title: 'Tutorial: Vorbereiten des Servers für die Replikation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7d6d757969acb1509641a74cc1c528bc717e01bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323940"
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Lernprogramm: Vorbereiten des Servers für die Replikation
  Es ist wichtig, einen Sicherheitsplan zu erstellen, bevor Sie die Replikationstopologie konfigurieren. In diesem Lernprogramm erfahren Sie, wie Sie eine Replikationstopologie besser sichern und die Verteilung konfigurieren können. Dieser Vorgang stellt den ersten Schritt für die Replikation von Daten dar. Es ist erforderlich, dieses Lernprogramm vor allen anderen Lernprogrammen abzuschließen.  
  
> [!NOTE]  
>  Für das sichere Replizieren von Daten zwischen Servern empfiehlt es sich, alle Empfehlungen unter [Bewährte Methoden für die Replikationssicherheit](security/replication-security-best-practices.md)zu implementieren.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 In diesem Lernprogramm erfahren Sie, wie Sie einen Server vorbereiten, sodass die Replikation sicher und mit den geringsten Privilegien ausgeführt werden kann. In der ersten Lektion wird veranschaulicht, wie Sie die Windows-Dienstkonten erstellen können, die zur Ausführung von Replikations-Agents verwendet werden. In der zweiten Lektion erfahren Sie, wie der Ordner konfiguriert wird, in dem Momentaufnahmeveröffentlichungen generiert und gespeichert werden. In der dritten Lektion wird das Konfigurieren der Verteilung und das Festlegen der Berechtigungen erläutert.  
  
## <a name="requirements"></a>Anforderungen  
 Dieses Lernprogramm ist für Benutzer vorgesehen, die mit grundlegenden Datenbankvorgängen vertraut sind, aber nur über begrenzte Erfahrungen in Bezug auf die Replikation verfügen.  
  
 Ihr System muss die folgenden installierten Komponenten aufweisen, damit dieses Lernprogramm verwendet werden kann:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] mit der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank. Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert.  
  
 **Geschätzte Zeit zum Bearbeiten dieses Lernprogramms: 30 Minuten**  
  
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm  
  
-   [Lektion 1: Erstellen von Windows-Konten für die Replikation](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Lektion 2: Vorbereiten des Momentaufnahmeordners](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Lektion 3: Konfigurieren der Verteilung](lesson-3-configuring-distribution.md)  
  
 [Lernprogramm starten](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Verteilung konfigurieren](configure-distribution.md)   
 [Sicherheit und Schutz &#40;Replikation&#41;](security/security-and-protection-replication.md)  
  
  
