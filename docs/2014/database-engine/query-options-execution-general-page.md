---
title: Abfrageoptionen Ausführung (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
caps.latest.revision: 29
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: a6e8e45ea1ba74aeef1f063ad03154a9574bc9e5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269806"
---
# <a name="query-options-execution-general-page"></a>Abfrageausführung (Seite 'Allgemein')
  Auf dieser Seite können Sie die Optionen zum Ausführen von Abfragen in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] angeben. Um auf dieses Dialogfeld zuzugreifen, klicken Sie mit der rechten Maustaste auf den Hauptteil des Abfrage-Editor-Fensters, und klicken Sie anschließend auf **Abfrageoptionen**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **SET ROWCOUNT**  
 Der Standardwert 0 zeigt an, dass [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] so lange auf die Ergebnisse wartet, bis alle Ergebnisse übermittelt sind. Geben Sie einen Wert größer 0 an, wenn die Abfrage von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nach Übermittlung einer bestimmten Anzahl von Zeilen abgebrochen werden soll. Geben Sie SET ROWCOUNT 0 an, um diese Option zu deaktivieren (sodass alle Zeilen zurückgegeben werden).  
  
 **SET TEXTSIZE**  
 Der Standardwert von 2.147.483.647 Bytes zeigt an, dass [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein vollständiges Datenfeld bereitstellt, das maximal der Größe von `text`-, `ntext`-, `nvarchar(max)`- und `varchar(max)`-Datenfeldern entspricht. Dies hat keine Auswirkungen auf den XML-Datentyp. Geben Sie eine kleinere Zahl an, um Ergebnisse mit großen Werten zu beschränken. Spalten, deren Größe die angegebene Zahl übersteigt, werden abgeschnitten.  
  
 **Ausführungstimeout**  
 Gibt die Wartezeit (in Sekunden) an, nach der die Abfrage abgebrochen wird. Der Wert '0' gibt an, dass der Wartevorgang unbegrenzt ist bzw. kein Timeout erfolgt.  
  
 **Batchtrennzeichen**  
 Geben Sie ein Wort ein, das als Trennzeichen zwischen Transact-SQL-Anweisungen in Batches fungieren soll. Der Standardwert ist GO.  
  
 **Standardmäßig öffnen Sie neue Abfragen im SQLCMD-Modus**  
 Aktivieren Sie dieses Kontrollkästchen, um neue Abfragen im SQLCMD-Modus zu öffnen. Dieses Kontrollkästchen ist nur sichtbar, wenn das Dialogfeld über das Menü **Extras** geöffnet wird.  
  
 Beachten Sie die folgenden Einschränkungen, wenn Sie diese Option auswählen:  
  
-   IntelliSense im [!INCLUDE[ssDE](../includes/ssde-md.md)] -Abfrage-Editor ist deaktiviert.  
  
-   Da der Abfrage-Editor nicht über die Befehlszeile ausgeführt werden kann, ist es nicht möglich, Befehlszeilenparameter, z. B. Variablen, zu übergeben.  
  
-   Da der Abfrage-Editor nicht auf Anforderungen des Betriebssystems reagieren kann, müssen Sie darauf achten, keine interaktiven Anweisungen auszuführen.  
  
 **Auf Standard zurücksetzen**  
 Setzt alle auf dieser Seite verfügbaren Werte auf die ursprünglichen Standardwerte zurück.  
  
  
