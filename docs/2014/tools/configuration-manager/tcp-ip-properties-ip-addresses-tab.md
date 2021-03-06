---
title: TCP / IP-Eigenschaften (Registerkarte "IP-Adressen") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], listening on
- listening [SQL Server], on ports
ms.assetid: 4c17ed45-9da7-4bec-bce6-970109fe7365
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cb09573cd77f74044647925bd43310223c4ce67e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187590"
---
# <a name="tcp-ip-properties-ip-addresses-tab"></a>TCP / IP-Eigenschaften (Registerkarte "IP-Adressen")
  Verwenden Sie das Dialogfeld **TCP/IP-Eigenschaften** (Registerkarte IP-Adressen), um die TCP/IP-Protokolloptionen für eine spezielle IP-Adresse zu konfigurieren. Nur die Optionen **Dynamische TCP-Ports** und **TCP-Port** können durch Auswahl von **IPAll** für alle Adressen sofort konfiguriert werden.  
  
 Änderungen werden erst dann wirksam, wenn [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu gestartet wurde. Informationen über das Starten und Beenden des SQL Server-Browser-Dienstes finden Sie unter "Vorgehensweise: Starten und Beenden des SQL Server-Browser-Dienstes" in der Onlinedokumentation.  
  
## <a name="static-vs-dynamic-ports"></a>Statische und Dynamische Ports  
 Die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauscht für eingehende Verbindungen an Port 1433. Der Port kann aus Sicherheitsgründen oder wegen Anforderungen von Clientanwendungen geändert werden. Standardmäßig werden benannte Instanzen (einschließlich SQL Server Express) zur Überwachung von dynamischen Ports konfiguriert. Lassen Sie das Feld **Dynamische TCP-Ports** leer, und geben Sie eine verfügbare Portnummer in das Feld **TCP-Port** ein, um einen statischen Port zu konfigurieren. Weitere Informationen zum Öffnen von Ports in der Firewall finden Sie unter "Konfigurieren der Windows-Firewall für den SQL Server-Zugriff" in der Onlinedokumentation.  
  
## <a name="dynamic-ports"></a>Dynamische Ports  
 Wenn eine Instanz beim Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur Überwachung von dynamischen Ports konfiguriert ist, wird das Betriebssystem auf einen verfügbaren Port überprüft und ein Endpunkt für diesen Port geöffnet. Eingehende Verbindungen müssen diese Portnummer zum Verbinden angeben. Da sich die Portnummer bei jedem Start von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändern kann, stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser-Dienst bereit, um an den Ports zu lauschen und eingehende Verbindungen an den aktuellen Port für diese Instanz zu leiten. Das Verwenden von dynamischen Ports macht das Verbinden auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durch eine Firewall schwierig, da die Portnummer sich bei einem Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändern kann. Dies erfordert Änderungen an den Firewalleinstellungen. Konfigurieren Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Verwenden eines statischen Ports, um Verbindungsprobleme durch eine Firewall zu vermeiden.  
  
## <a name="options"></a>Tastatur  
 **Active**  
 Gibt an, dass die IP-Adresse auf dem Computer aktiviert ist. Nicht verfügbar für **IPAll**.  
  
 **Enabled**  
 Wenn die Eigenschaft **Auf Alle lauschen** unter **TCP/IP-Eigenschaften** (Registerkarte Protokoll) auf **Nein**festgelegt ist, gibt diese Eigenschaft an, ob SQL Server auf die IP-Adresse lauscht. Wenn die Eigenschaft **Auf Alle Lauschen** unter **TCP/IP-Eigenschaften** (Registerkarte Protokoll) auf **Ja**festgelegt ist, wird die Eigenschaft ignoriert. Nicht verfügbar für **IPAll**.  
  
 **IP-Adresse**  
 Zeigt die von dieser Verbindung verwendete IP-Adresse an oder ändert diese. Führt die von diesem Computer verwendete IP-Adresse sowie die IP-Loopbackadresse 127.0.0.1 auf. Nicht verfügbar für **IPAll**. Die IP-Adresse kann sowohl im IPv4- oder IPv6-Format vorliegen.  
  
 **Dynamische TCP-Ports**  
 Leer, wenn dynamische Ports nicht aktiviert sind. Legen Sie den Wert 0 fest, um dynamische Ports zu verwenden.  
  
 Für **IPAll**wird die Portnummer des verwendeten dynamischen Ports angezeigt.  
  
 **TCP-Port**  
 Zeigt den Port an, an dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lauscht, oder ändert diesen. Die Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] lauscht an Port 1433.  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] kann an mehreren Ports auf derselben IP-Adresse lauschen. Ports werden (durch Trennzeichen getrennt) im Format 1433,1500,1501 aufgelistet. Dieses Feld ist auf 2047 Zeichen begrenzt.  
  
 Zum Konfigurieren einer einzelnen IP-Adresse zum Lauschen an mehreren Ports muss der Parameter **Auf Alle Lauschen** auch auf **Nein** festgelegt sein. Diesen finden Sie im Dialogfeld **TCP/IP-Eigenschaften** auf der Registerkarte **Protokolle**. Weitere Informationen finden Sie unter "Vorgehensweise: Konfigurieren der Datenbank-Engine zum Lauschen an mehreren TCP-Ports" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="adding-or-removing-ip-addresses"></a>Hinzufügen und Entfernen von IP-Adressen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurations-Manager zeigt die IP-Adressen, die zum Zeitpunkt verfügbar waren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wurde. Die verfügbaren IP-Adressen können sich ändern, wenn Netzwerkkarten hinzugefügt oder entfernt werden, wenn dynamisch zugewiesene IP-Adressen ablaufen, wenn die Netzwerkstruktur neu konfiguriert wird oder wenn der physische Standort des Computers geändert wird, z. B. bei einem Laptop, über das von einem anderen Gebäude aus eine Verbindung mit dem Netzwerk hergestellt wird. Zum Ändern der IP-Adresse bearbeiten Sie das Feld **IP-Adresse**, und starten Sie anschließend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [SQL Server-Browserdienst](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
