---
title: Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], adding
- adding tasks
- adding containers
- tasks [Integration Services], adding
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
caps.latest.revision: 44
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1546a8bf4d0da741d63cb8bd8d4b2f849cf921d2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37256936"
---
# <a name="add-or-delete-a-task-or-a-container-in-a-control-flow"></a>Hinzufügen oder Löschen eines Tasks oder Containers in einer Ablaufsteuerung
  Wenn Sie im Ablaufsteuerungs-Designer arbeiten, werden in der Toolbox im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer die Tasks aufgeführt, die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] zum Erstellen einer Ablaufsteuerung in einem Paket bereitstellt. Weitere Informationen über die Toolbox finden Sie unter [SSIS Toolbox](../ssis-toolbox.md).  
  
 Ein Paket kann mehrere Instanzen desselben Tasks einschließen. Jede Instanz eines Tasks wird im Paket eindeutig identifiziert, und Sie können jede Instanz unterschiedlich konfigurieren.  
  
 Wenn Sie einen Task löschen, werden die Rangfolgeneinschränkungen, die den Task mit anderen Tasks und Container in der Ablaufsteuerung verbinden, ebenfalls gelöscht.  
  
 Im Folgenden wird beschrieben, wie ein Task oder Container zur Ablaufsteuerung eines Pakets hinzugefügt oder in dieser gelöscht wird.  
  
### <a name="to-add-a-task-or-a-container-to-a-control-flow"></a>So fügen Sie einer Ablaufsteuerung einen Task oder Container hinzu  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** .  
  
4.  Klicken Sie im Menü **Ansicht**auf **Toolbox** , um **Toolbox** zu öffnen.  
  
5.  Erweitern Sie **Ablaufsteuerungselemente** und **Wartungstasks**.  
  
6.  Ziehen Sie Tasks und Container aus der **Toolbox** auf die Entwurfsoberfläche der Registerkarte **Ablaufsteuerung** .  
  
7.  Verbinden Sie einen Task oder Container innerhalb der Paketablaufsteuerung, indem Sie dessen Konnektor auf eine andere Komponente in der Ablaufsteuerung ziehen.  
  
8.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
### <a name="to-delete-a-task-or-a-container-from-a-control-flow"></a>So löschen Sie einen Task oder Container aus einer Ablaufsteuerung  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen. Führen Sie eines der folgenden Verfahren aus:  
  
    -   Klicken Sie auf die Registerkarte **Ablaufsteuerung** , klicken Sie mit der rechten Maustaste auf den Task oder Container, den Sie entfernen möchten, und klicken Sie anschließend auf **Löschen**.  
  
    -   Öffnen Sie **Paket-Explorer**. Klicken Sie im Ordner **Ausführbare Dateien** mit der rechten Maustaste auf den Task oder Container, den Sie entfernen möchten, und klicken Sie anschließend auf **Löschen**.  
  
3.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Tasks](integration-services-tasks.md)   
 [Integration Services-Container](integration-services-containers.md)   
 [Ablaufsteuerung](control-flow.md)  
  
  
