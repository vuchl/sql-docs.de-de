---
title: LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7c5ce08-8841-49a3-b252-116807ba469a
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df2fe3b4c2b5ef6b70793eadad392536a7f389e5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408619"
---
# <a name="localdberrorinstanceexistswithlowerversion"></a>LOCALDB_ERROR_INSTANCE_EXISTS_WITH_LOWER_VERSION
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|258|  
|Ereignisquelle|Lokale SQL Server-Datenbanklaufzeit 12.0|  
|Komponente|Laufzeit-API der lokalen Datenbank|  
|Meldungstext|Es konnte keine lokale Datenbankinstanz der angegebenen Version erstellt werden. Eine Instanz mit diesem Namen ist zwar bereits vorhanden, aber deren Version ist niedriger als die angegebene Version.|  
  
## <a name="explanation"></a>Erklärung  
 Die angegebene Instanz ist bereits vorhanden, aber ihre Version ist niedriger als angefordert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie die vorhandene Instanz, und wiederholen Sie den Vorgang.  
  
  
