---
title: 'Gewusst wie: Klonen einer vorhandenen Datenbank | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aad3594a-11cf-4e68-a622-071a93d43875
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1037250907c897ce08f85da5af1c739849091338
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085922"
---
# <a name="how-to-clone-an-existing-database"></a>Vorgehensweise: Klonen einer vorhandenen Datenbank
In dieser Aufgabe werden einige der in den vorherigen Prozeduren eingeführten Schritte verwendet, um eine neue Datenbank zu erstellen und vorhandene Daten in diese zu portieren. Darüber hinaus werden die Schritte durchgeführt, die unter [Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md) beschrieben werden, um das Schema einer Quell- und das einer Projektdatenbank zu synchronisieren.  
  
Mit diesen Schritten können Sie auf einfache Weise eine Entwicklungs- oder Testdatenbank aus einer Produktionsdatenbank mit identischem Schema und identischen Daten erstellen. Anschließend können Sie mit der Entwicklung der Testdatenbank in einem verbundenen Modus fortfahren oder ein Datenbankprojekt für Offlineentwicklung und -tests erstellen. Hierbei muss der Betrieb der Produktionsdatenbank nicht unterbrochen werden.  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden die Entitäten verwendet, die in vorherigen Vorgehensweisen im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) erstellt wurden.  
  
### <a name="to-create-a-development-database"></a>So erstellen Sie eine Entwicklungsdatenbank  
  
1.  Erweitern Sie im **SQL Server-Objekt-Explorer** unter dem Knoten **SQL Server** die verbundene Serverinstanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken**, und wählen Sie **Neue Datenbank hinzufügen** aus.  
  
3.  Benennen Sie die neue Datenbank in **TradeDev** um.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Datenbank **Trade** im **SQL Server-Objekt-Explorer**, und klicken Sie auf **Schemavergleich**. Führen Sie die Schritte im Thema [Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md) durch, und wählen Sie dabei die ursprüngliche Datenbank **Trade** als Quelle und die neue Datenbank **TradeDev** als Ziel aus. Dadurch wird **TradeDev** mit dem Schema aus **Trade** aktualisiert.  
  
### <a name="to-replicate-data"></a>So replizieren Sie Daten  
  
1.  Im vorherigen Schritt wurde nur das Schema der Produktionsdatenbank in der Entwicklungsdatenbank dupliziert. In dieser Prozedur duplizieren Sie Produktionsdaten in der Entwicklungsdatenbank.  
  
    Klicken Sie in der Datenbank **Trade** mit der rechten Maustaste auf die Tabelle **Suppliers**, und wählen Sie **Daten anzeigen** aus. Der Daten-Editor wird geöffnet.  
  
2.  Klicken Sie auf der Symbolleiste neben **Max. Zeilen** auf die Schaltfläche **Skript**.  
  
3.  Wenn das Skriptfenster geöffnet wird, stellen Sie sicher, dass in der Statusleiste unter dem Transact\-SQL-Skriptbereich „Verbunden“ angezeigt wird. Wenn „Getrennt“ angezeigt wird, klicken Sie auf die Schaltfläche **Verbinden** (die Schaltfläche außen links auf der Symbolleiste), und geben Sie Ihre Server- und Anmeldeinformationen ein.  
  
4.  Wählen Sie im Dropdownmenü **Datenbank** neben den Schaltflächen **Verbinden**/**Trennen** den Eintrag **TradeDev** aus. Dies ist mit der Transact\-SQL`USE`-Anweisung vergleichbar. Dadurch wird sichergestellt, dass das Skript im Code-Editor für die Datenbank **TradeDev** ausgeführt wird.  
  
5.  Klicken Sie auf die Schaltfläche **Abfrage ausführen**, um die `INSERT`-Anweisungen auszuführen. Dadurch werden alle Zeilen aus der Tabelle `Suppliers` der Datenbank `Trade` in der Tabelle `Suppliers` der Datenbank `TradeDev` eingefügt.  
  
6.  Wiederholen Sie die obigen Schritte für alle Tabellen in der Datenbank `Trade`, damit sie mit der Datenbank `TradeDev` repliziert werden.  
  
7.  Überprüfen Sie mithilfe des Daten-Editors, ob alle Tabellen in der neuen Datenbank `TradeDev` aufgefüllt wurden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
