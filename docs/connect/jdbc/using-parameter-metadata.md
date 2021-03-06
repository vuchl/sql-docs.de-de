---
title: Verwenden von Parametermetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 825494c70ea9ed5d36cbf1c16ed4cdedfbfbd87d
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661732"
---
# <a name="using-parameter-metadata"></a>Verwenden von Parametermetadaten

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Für die Abfrage der enthaltenen Parameter bei [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)- oder [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)-Objekten implementiert [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] die [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md)-Klasse. Diese Klasse enthält eine Vielzahl von Feldern und Methoden, die Informationen in der Form eines einzelnen Werts zurückgeben.

Um ein SQLServerParameterMetaData-Objekt zu erstellen, können Sie die [GetParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) der die Sqlserverpreparedstatement- und SQLServerCallableStatement-Klasse.

Im folgenden Beispiel eine offene Verbindung mit der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] -Beispieldatenbank an die Funktion übergeben, die GetParameterMetaData-Methode der SQLServerCallableStatement-Klasse wird verwendet, um ein SQLServerParameterMetaData-Objekt, und klicken Sie dann verschiedene zurückgeben Methoden von der SQLServerParameterMetaData-Objekt werden zum Anzeigen von Informationen zu Typ und Modus der Parameter, die in der gespeicherten Prozedur HumanResources.uspUpdateEmployeeHireInfo enthalten sind.

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> Es gibt einige Einschränkungen auf, wenn die SQLServerParameterMetaData-Klasse mit vorbereiteten Anweisungen verwendet.
>
> **Mit Microsoft JDBC-Treiber 6.0 (oder höher) für SQL Server:** Bei SQL Server 2008 oder 2008 R2 unterstützt der JDBC-Treiber SELECT-, DELETE-, INSERT- und UPDATE-Anweisungen. Diese Anweisungen dürfen jedoch keine Unterabfragen und/oder Joins enthalten.

Auch MERGE-Abfragen werden bei SQL Server 2008 oder 2008 R2 nicht für die SQLServerParameterMetaData-Klasse unterstützt. Bei SQL Server 2012 und höheren werden Parametermetadaten in komplexen Abfragen unterstützt.

Abrufen von Parametermetadaten für verschlüsselte Spalten werden nicht unterstützt. **Mit Microsoft-JDBC-Treiber 4.1 oder 4.2 für SQL Server:** Der JDBC-Treiber unterstützt SELECT-, DELETE-, INSERT- und UPDATE-Anweisungen. Diese Anweisungen dürfen jedoch keine Unterabfragen und/oder Joins enthalten. Abfragen ZUSAMMENFÜHREN, werden auch nicht für die SQLServerParameterMetaData-Klasse unterstützt.
