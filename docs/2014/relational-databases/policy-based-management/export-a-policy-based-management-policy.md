---
title: Exportieren einer Richtlinie der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b740a5934caedabf72d7aede9aa240849ace45f4
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820936"
---
# <a name="export-a-policy-based-management-policy"></a>Exportieren einer Richtlinie der richtlinienbasierten Verwaltung
  In diesem Thema wird beschrieben, wie Sie eine Richtlinie der richtlinienbasierten Verwaltung mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]exportieren.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Exportieren einer Richtlinie mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der PolicyAdministratorRole-Rolle in der msdb-Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-export-a-policy"></a>So exportieren Sie eine Richtlinie  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um den Server zu erweitern, in dem die zu exportierende Richtlinie der richtlinienbasierten Verwaltung enthalten ist.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie auf das Pluszeichen, um **Richtlinienverwaltung**zu erweitern.  
  
4.  Klicken Sie auf das Pluszeichen, um den Ordner **Richtlinien** zu erweitern.  
  
5.  Klicken Sie mit der rechten Maustaste auf die zu exportierende Richtlinie, und wählen Sie **Richtlinie exportieren**aus.  
  
6.  Geben Sie im Dialogfeld **Richtlinie exportieren** den Pfad und den Namen der Datei in der Adressleiste ein. Suchen Sie alternativ im Navigationsbereich des Dialogfelds einen geeigneten Speicherort für die Datei, und geben Sie den Namen der XML-Datei in das Feld **Dateiname** ein.  
  
7.  Wenn Sie fertig sind, klicken Sie auf **Speichern**.  
  
  
