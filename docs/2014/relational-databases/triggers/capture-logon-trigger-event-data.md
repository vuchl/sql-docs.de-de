---
title: Erfassen von Ereignisdaten für Logon-Trigger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b8af11178bf4f2d56d3b1d8df515c12298b81d5b
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422995"
---
# <a name="capture-logon-trigger-event-data"></a>Erfassen von Ereignisdaten für Logon-Trigger
  Wenn Sie XML-Daten zu LOGON-Ereignissen für die Verwendung in Logon-Triggern erfassen möchten, verwenden Sie die [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) -Funktion. Mit dem LOGON-Ereignis wird das folgende Ereignisdatenschema zurückgegeben:  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 Enthält `LOGON`.  
  
 `<PostTime>`  
 Enthält die Uhrzeit, zu der eine Anforderung zum Erstellen einer Sitzung ausgegeben wird.  
  
 `<SID>`  
 Enthält den base64-verschlüsselten binären Datenstrom der Sicherheits-ID (SID) für den angegebenen Anmeldenamen.  
  
 `<ClientHost>`  
 Enthält den Hostnamen des Clients, von dem aus die Verbindung hergestellt wird. Der Wert lautet '`<local_machine>`', wenn der Name des Clients und des Servers identisch sind. Andernfalls entspricht der Wert der IP-Adresse des Clients.  
  
 `<IsPooled>`  
 Lautet `1` , wenn die Verbindung durch Verbindungspooling wiederverwendet wird. Andernfalls lautet der Wert `0`.  
  
  
