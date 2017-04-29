---
title: "Auftragsschritt-Eigenschaften – Neuer Auftragsschritt (Seite „Erweitert“) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ea8ecf39a23a0db715c95bb4041c802a382822fa
ms.lasthandoff: 04/11/2017

---
# <a name="job-step-properties---new-job-step-advanced-page"></a>Auftragsschritt-Eigenschaften – Neuer Auftragsschritt (Seite „Erweitert“)
Mithilfe dieser Seite können Sie die Eigenschaften für einen [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]-Agentauftragsschritt anzeigen und ändern.  
  
## <a name="options"></a>enthalten  
**Aktion bei Erfolg**  
Legt fest, welche Aktion der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Agent bei erfolgreicher Auftragsausführung ausführen soll.  
  
**Wiederholungsversuche**  
Legt fest, wie oft vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Agent versucht werden soll, einen fehlgeschlagenen Auftragsschritt erneut auszuführen.  
  
**Wiederholungsintervall (Min)**  
Legt fest, wie lange der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Agent bis zum nächsten Wiederholungsversuch warten soll.  
  
**Aktion bei Fehler**  
Legt fest, welche Aktion der [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Agent bei Fehlschlagen des Auftrags ausführen soll.  
  
## <a name="options-for-transact-sql-job-steps"></a>Optionen für Transact-SQL-Auftragsschritte  
**Ausgabedatei**  
Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll. Diese Option ist nur für Mitglieder der festen Serverrolle **sysadmin** verfügbar.  
  
**...**  
Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
**Sicht**  
In [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
**Ausgabe an vorhandene Datei anfügen**  
Fügt die Ausgabe an den vorhandenen Inhalt der Datei an. Andernfalls wird der vorige Inhalt der Datei bei jeder Ausführung des Auftragsschritts überschrieben.  
  
**In Tabelle protokollieren**  
Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
**Sicht**  
Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
**Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
**Schrittausgabe in Verlauf einschließen**  
Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
**Ausführen als Benutzer**  
Wenn Sie Mitglied der festen Serverrolle **sysadmin** sind, können Sie für die Ausführung dieses Auftragsschritts einen anderen SQL-Anmeldenamen auswählen.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Optionen für Auftragsschritte des Betriebssystems (CmdExec)  
**Ausgabedatei**  
Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll.  
  
**...**  
Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
**Sicht**  
In [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
**Ausgabe an vorhandene Datei anfügen**  
Fügt die Auftragsschrittausgabe bei jeder Ausführung des Schritts an den vorhandenen Inhalt der Datei an.  
  
**In Tabelle protokollieren**  
Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
**Sicht**  
Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
**Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
**Schrittausgabe in Verlauf einschließen**  
Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
## <a name="options-for-powershell-job-steps"></a>Optionen für PowerShell-Auftragsschritte  
**Ausgabedatei**  
Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll.  
  
**...**  
Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
**Sicht**  
In [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
**Ausgabe an vorhandene Datei anfügen**  
Fügt die Auftragsschrittausgabe bei jeder Ausführung des Schritts an den vorhandenen Inhalt der Datei an.  
  
**In Tabelle protokollieren**  
Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
**Sicht**  
Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
**Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
**Schrittausgabe in Verlauf einschließen**  
Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Optionen für Auftragsschritte des Replikation-Warteschlangenlesers  
**Server**  
Legt fest, welcher Server für einen Auftragsschritt des Replikation-Warteschlangenlesers verwendet werden soll.  
  
**Datenbank**  
Legt fest, welche Datenbank für einen Auftragsschritt des Replikation-Warteschlangenlesers verwendet werden soll.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Optionen für Auftragsschritte von SQL Server Analysis Services  
**Ausgabedatei**  
Legt fest, welche Datei für die Ausgabe aus dem Auftragsschritt verwendet werden soll. Diese Option ist nur für Mitglieder der festen Serverrolle **sysadmin** verfügbar.  
  
**...**  
Nach der Datei, die für die Ausgabe aus dem Auftragsschritt verwendet werden soll, können Sie suchen.  
  
**Sicht**  
In [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]ist diese Schaltfläche für die Anzeige von Ausgabedateien deaktiviert. Nutzen Sie stattdessen den Editor für die Anzeige von Auftragsschritt-Ausgabedateien.  
  
**Ausgabe an vorhandene Datei anfügen**  
Fügt die Ausgabe an den vorhandenen Inhalt der Datei an. Andernfalls wird der vorige Inhalt der Datei bei jeder Ausführung des Auftragsschritts überschrieben.  
  
**In Tabelle protokollieren**  
Protokolliert die Ausgabedaten des Auftragsschritts in der **sysjobstepslogs** -Tabelle der **msdb** -Datenbank.  
  
**Sicht**  
Klicken Sie nach Ausführung des Auftragsschritts auf **Anzeigen** , um seine Ausgabe in der Tabelle anzuzeigen.  
  
**Ausgabe an vorhandenen Eintrag in Tabelle anfügen**  
Fügt die Ausgabe an den vorhandenen Inhalt der Tabelle an. Andernfalls wird der vorige Inhalt der Tabelle bei jeder Ausführung des Auftragsschritts überschrieben.  
  
**Schrittausgabe in Verlauf einschließen**  
Wählen Sie diese Option aus, wenn die Ausgabe des Auftragsschritts in den Auftragsverlauf aufgenommen werden soll.  
  
## <a name="see-also"></a>Siehe auch  
[Verwalten von Auftragsschritten](../../ssms/agent/manage-job-steps.md)  
  
