---
title: Massenladen von Daten mithilfe des SQL Server-Ziels | Microsoft-Dokumentation
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
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b607ee9d90822c6e7e39d3d8b89822bcc05201c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260964"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a>Massenladen von Daten mithilfe des SQL Server-Ziels
  Das Paket muss bereits mindestens einen Datenflusstask und eine Datenquelle enthalten, damit Sie ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ziel hinzufügen und konfigurieren können.  
  
### <a name="to-load-data-using-a-sql-server-destination"></a>So laden Sie Daten mithilfe eines SQL Server-Ziels  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ziel auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie das Ziel mit einer Quelle oder einer vorherigen Transformation im Datenfluss, indem Sie einen Konnektor auf das Ziel ziehen.  
  
5.  Doppelklicken Sie auf das Ziel.  
  
6.  Wählen Sie im Dialogfeld **Ziel-Editor für SQL**auf der Seite **Verbindungs-Manager** einen vorhandenen OLE SQL-Verbindungs-Manager aus, oder klicken Sie auf **Neu** , um einen neuen Verbindungs-Manager zu erstellen. Weitere Informationen finden Sie unter [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
7.  Führen Sie eine der folgenden Aktionen aus, um die Tabelle oder die Sicht anzugeben, in die die Daten geladen werden sollen:  
  
    -   Wählen Sie eine vorhandene Tabelle oder Sicht aus.  
  
    -   Klicken Sie auf **Neu**, und schreiben Sie im Dialogfeld **Tabelle erstellen** eine SQL-Anweisung, mit der eine Tabelle oder Sicht erstellt wird.  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] generiert eine Standard-CREATE TABLE-Anweisung auf Grundlage der verbundenen Datenquelle. Diese Standard-CREATE TABLE-Anweisung enthält nicht das FILESTREAM-Attribut, selbst wenn die Quelltabelle eine Spalte mit der Erklärung des FILESTREAM-Attributs enthält. Um eine [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Komponente mit dem FILESTREAM-Attribut auszuführen, implementieren Sie zunächst die FILESTREAM-Speicherung in der Zieldatenbank. Fügen Sie dann das FILESTREAM-Attribut der CREATE TABLE-Anweisung im Dialogfeld **Tabelle erstellen** hinzu. Weitere Informationen finden Sie unter [Blob-Daten &#40;Binary Large Object, SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
8.  Klicken Sie auf **Zuordnungen** , und ordnen Sie Spalten aus der Liste **Verfügbare Eingabespalten** Spalten in der Liste **Verfügbare Zielspalten** zu, indem Sie Spalten von einer Liste in eine andere Liste ziehen.  
  
    > [!NOTE]  
    >  Vom Ziel werden automatisch gleichnamige Spalten zugeordnet.  
  
9. Klicken Sie auf **Erweitert** , und legen Sie die Optionen für das Massenladen fest: **Identität beibehalten**, **NULL-Werte beibehalten**, **Tabellensperre**, **Einschränkungen überprüfen**und **Trigger auslösen**.  
  
     Optional können Sie die erste und letzte einzufügende Eingabezeile, die maximal zulässige Anzahl von Fehlern, nach der der Einfügevorgang beendet wird, sowie die Spalten, nach der der Einfügevorgang sortiert wird, angeben.  
  
    > [!NOTE]  
    >  Die Sortierreihenfolge wird durch die Reihenfolge bestimmt, in der die Spalten aufgelistet sind.  
  
10. Klicken Sie auf **OK**.  
  
11. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Ziels](sql-server-destination.md)   
 [Integration Services-Transformationen](transformations/integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](integration-services-paths.md)   
 [Datenflusstask](../control-flow/data-flow-task.md)  
  
  
