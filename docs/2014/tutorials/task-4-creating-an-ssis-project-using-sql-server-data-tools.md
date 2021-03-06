---
title: 'Aufgabe 4: Erstellen eines SSIS-Projekts mit SQL Server Data Tools | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a6fb09370b01a88c23d75b843d588626ed96c9b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208070"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Aufgabe 4: Erstellen eines SSIS-Projekts mit SQL Server Data Tools
  In dieser Aufgabe erstellen Sie ein SSIS-Projekt mit **SQL Server Data Tools** , Bereinigung und Abgleich von Lieferantendaten zu automatisieren.  
  
1.  Starten Sie **SQL Server Data Tools**. Klicken Sie auf Start, zeigen Sie auf **Programme**, erweitern Sie **Microsoft SQL Server 2012**, und klicken Sie auf **SQL Server Data Tools**.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Projekt**.  
  
3.  Erweitern Sie **Business Intelligence** in die **installierte Vorlagen** Bereich, und wählen Sie **Integrationsdienste**.  
  
     ![Visual Studio – neues Projekt (Dialogfeld)](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio – neues Projekt (Dialogfeld)")  
  
4.  Wählen Sie **Integration Services-Projekt** in die **Liste der Projekttypen**.  
  
5.  Typ **CleanseAndCurateSuppliers** für **Namen** , und klicken Sie auf **OK**.  
  
6.  In **Projektmappen-Explorer** Fenster mit der rechten Maustaste **Package.dtsx** , und wählen Sie **umbenennen**. Wenn Sie nicht sehen **Projektmappen-Explorer** Fenster klicken Sie auf **Ansicht** auf der Menüleiste und auf **Projektmappen-Explorer**.  
  
     ![Package.dtsx – umbenennen (Menü)](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx – umbenennen (Menü)")  
  
7.  Typ **CleanseAndCurate.dtsx** , und drücken Sie **EINGABETASTE**. Stellen Sie sicher, dass die **Erweiterung** bleibt **DTSX**.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Hinzufügen eines Datenflusstasks](task-5-adding-data-flow-task.md)  
  
  
