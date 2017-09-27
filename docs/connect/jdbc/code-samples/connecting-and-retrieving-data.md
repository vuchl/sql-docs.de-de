---
title: Herstellen einer Verbindung und zum Abrufen von Daten | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff00f7cfde3f75a653be5d89064d9b3d56268295
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-and-retrieving-data"></a>Verbinden und Abrufen von Daten
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Bei der Arbeit mit der [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], es gibt zwei primäre Methoden zum Herstellen einer Verbindungs mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Datenbank. Eine Verbindungseigenschaften in der Verbindungs-URL festzulegen, und rufen Sie anschließend die GetConnection-Methode der zurückzugebenden DriverManager-Klasse ist eine [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) Objekt.  
  
> [!NOTE]  
>  Eine Liste der vom JDBC-Treiber unterstützten Verbindungseigenschaften finden Sie [Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Die zweite Methode werden die Verbindungseigenschaften mit den festlegungsmethoden des der [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) -Klasse, und dem anschließenden Aufrufen der [GetConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md) Methode, um ein SQLServerConnection zurückzugeben. -Objekt.  
  
 Die Themen in diesem Abschnitt beschreiben die verschiedenen Möglichkeiten, in dem Sie können eine Verbindung mit, einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Datenbank, und sie zeigen auch verschiedene Techniken zum Abrufen von Daten.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Verbindungs-URL – Beispiel](../../../connect/jdbc/connection-url-sample.md)|Beschreibt, wie eine Verbindungs-URL für die Verbindung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] und verwenden Sie eine SQL-Anweisung zum Abrufen von Daten.|  
|[Beispiel für Datenquellen](../../../connect/jdbc/data-source-sample.md)|Beschreibt die Verwendung einer Datenquelle, um eine Verbindung zu SQL Server herzustellen und Daten anschließend mit einer gespeicherten Prozedur abzurufen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiele für JDBC-Treiberanwendungen](../../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  