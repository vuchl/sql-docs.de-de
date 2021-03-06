---
title: SQLServerPreparedStatement-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f0189a7a3a12f41c6e07414a1f548eab15404ed
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786305"
---
# <a name="sqlserverpreparedstatement-class"></a>SQLServerPreparedStatement-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt die grundlegende Implementierung der JDBC-Funktion für vorbereitete Anweisungen dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** SQLServerStatement  
  
 **Implementiert** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerPreparedStatement stellt Methoden bereit, mit denen Sie Parameter in Form beliebiger nativer Java-Typen und verschiedener Java-Objekttypen angeben können. SQLServerPreparedStatement bereitet anhand der gespeicherten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozedur **sp_prepare** Anweisungen vor und verwendet das zurückgegebene Anweisungshandle erneut für jede darauffolgende Ausführung einer Anweisung, wobei normalerweise verschiedene vom Benutzer bereitgestellte Parameter verwendet werden.  
  
 SQLServerPreparedStatement unterstützt Batchverarbeitung, wobei eine Reihe von vorbereiteten Anweisungen in einem einzelnen Datenbankroundtrip ausgeführt wird, um die Laufzeitleistung zu verbessern.  
  
 Diese Klasse unterstützt das Entpacken in die SQLServerPreparedStatement-Klasse, ISQLServerPreparedStatement-Schnittstelle, java.sql.PreparedStatement-Schnittstelle, und die Klassen und Schnittstellen, die von SQLServerStatement, die für das Entpacken unterstützt werden. Weitere Informationen finden Sie unter [Wrapper und Schnittstellen](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
