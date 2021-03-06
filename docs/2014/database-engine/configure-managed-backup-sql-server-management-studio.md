---
title: Konfigurieren der verwalteten Sicherung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.managedbackup.configure.f1
ms.assetid: 79397cf6-0611-450a-b0d8-e784a76e3091
caps.latest.revision: 9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d09c001bc7c267b2235377a1312609ee8b7b3fa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209830"
---
# <a name="configure-managed-backup-sql-server-management-studio"></a>Konfigurieren der verwalteten Sicherung (SQL Server Management Studio)
  Die **Managed Backup** Dialogfeld können Sie so konfigurieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Standardwerte für die Instanz. In diesem Thema wird beschrieben, wie mit diesem Dialogfeld konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Standardeinstellungen für die Instanz und die Optionen, Sie müssen dabei berücksichtigen. Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] konfiguriert die Einstellungen gelten für die Instanz, auf alle neuen Datenbanken, die anschließend erstellt.  
  
 Wenn Sie konfigurieren möchten [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine bestimmte Datenbank finden Sie unter [aktivieren und Konfigurieren von SQL Server Managed Backup für Windows Azure für eine Datenbank](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
 
> [!NOTE] 
> SQL Server Managed Backup wird nicht von Proxyservern unterstützt. 
  
## <a name="task-list"></a>Aufgabenliste  
  
## <a name="includesssmartbackupincludesss-smartbackup-mdmd-functions-using-managed-backup-interface-in-sql-server-management-studio"></a>[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Funktionen mit Schnittstelle für verwaltete Sicherung in SQL Server Management Studio  
 In dieser Version können Sie nur konfigurieren Standardeinstellungen auf Instanzebene mithilfe der **verwaltete Sicherung** Schnittstelle. Sie können nicht konfiguriert werden [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für eine Datenbank anzuhalten oder fortzusetzen [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Vorgänge oder e-Mail-Benachrichtigungen einrichten. Informationen zum Ausführen von Vorgängen, die derzeit nicht unterstützt wird, über die **Managed Backup** Benutzeroberfläche, siehe [SQL Server Managed Backup für Windows Azure - Beibehaltungs- und Speichereinstellungen](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
## <a name="permissions"></a>Berechtigungen  
 **Ansicht Knotens für verwaltete Sicherung ist SQL Server Management Studio:** anzeigen **Managed Backup** Knoten **Objekt-Explorer**, müssen Sie Systemadministrator sein oder über die folgenden Berechtigungen verfügen. speziell mit Ihrem Benutzerkonto gewährt:  
  
-   `db_backupoperator`  
  
-   `VIEW SERVER STATE`  
  
-   `ALTER ANY CREDENTIAL`  
  
-   `VIEW ANY DEFINITION`  
  
-   `EXECUTE` auf `smart_admin.fn_is_master_switch_on`.  
  
-   `SELECT` auf `smart_admin.fn_backup_instance_config`.  
  
 **Zum Konfigurieren der verwalteten Sicherung:** so konfigurieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] in SQL Server Management Studio müssen Sie Systemadministrator sein oder über die folgenden Berechtigungen verfügen:  
  
 Mitgliedschaft in `db_backupoperator` -Datenbankrolle mit `ALTER ANY CREDENTIAL` Berechtigungen und `EXECUTE` Berechtigungen für `sp_delete_backuphistory` gespeicherte Prozedur.  
  
 `SELECT` Berechtigungen für die `smart_admin.fn_get_current_xevent_settings` Funktion.  
  
 `EXECUTE` Berechtigungen für die `smart_admin.sp_get_backup_diagnostics` gespeicherte Prozedur. Außerdem sind `VIEW SERVER STATE`-Berechtigungen erforderlich, da andere Systemobjekte, die diese Berechtigung erfordern, intern aufgerufen werden.  
  
 `EXECUTE` Berechtigungen für `smart_admin.sp_set_instance_backup`, und `smart_admin.sp_backup_master_switch`.  
  
## <a name="configure-includesssmartbackupincludesss-smartbackup-mdmd-using-sql-server-management-studio"></a>Konfigurieren von [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] mit SQL Server Management Studio  
 Von der **Objekt-Explorer**, erweitern Sie die **Management** Knoten und der rechten Maustaste auf **Managed Backup**. Wählen Sie **Konfigurieren**aus. Das Dialogfeld **Managed Backup** wird geöffnet.  
  
 Überprüfen Sie **Aktivieren der verwalteten Sicherung** aus, und geben Sie die Konfigurationswerte:  
  
 Die **Datei Aufbewahrung** Zeitraum in Tagen angegeben und muss zwischen 1 und 30.  
  
 Die **SQL-Anmeldeinformationen** Sie wählen, sollte mit dem Speicherkonto übereinstimmen. Wenn Sie derzeit keine SQL-Anmeldeinformationen verfügen, die die Authentifizierungsinformationen gespeichert sind, können Sie erstellen, indem Sie auf **erstellen**. Sie können die Anmeldeinformationen auch mit der CREATE CREDENTIAL-Transact-SQL-Anweisung erstellen, und den Speicherkontonamen für die Identität des Speicherkontos und den Zugriffsschlüssel für die geheimen Parameter angeben. Weitere Informationen finden Sie unter [Erstellen von Anmeldeinformationen](../relational-databases/backup-restore/sql-server-backup-to-url.md#credential).  
  
 Geben Sie die **Speicher-URL** für das Windows Azure-Speicherkonto, den SQL-Anmeldeinformationen, die die Authentifizierungsinformationen für das Speicherkonto und die Beibehaltungsdauer für die Sicherungsdateien gespeichert.  
  
 Ist der Speicher-URL-Format: https://\<Speicherkonto >.blob.core.windows.net/  
  
 Überprüfen Sie zum Festlegen der verschlüsselungseinstellungen auf Instanzebene **Sicherung verschlüsseln** aus, und geben Sie den Algorithmus und ein Zertifikat oder asymmetrischen Schlüssel für die Verschlüsselung verwendet.  Dies wird auf Instanzebene festgelegt und für alle neuen nach der Anwendung dieser Konfiguration erstellten Datenbanken verwendet.  
  
> [!WARNING]  
>  Dieses Dialogfeld kann nicht verwendet werden, an die Verschlüsselungsoptionen ohne Konfiguration [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]. Diese Verschlüsselungsoptionen gelten nur für [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Vorgänge. Zum Verwenden der Verschlüsselung für andere Sicherungsverfahren finden Sie unter [Sicherungsverschlüsselung](../relational-databases/backup-restore/backup-encryption.md).  
  
### <a name="considerations"></a>Weitere Überlegungen  
 Wenn Sie konfigurieren [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] auf Instanzebene, gelten die Einstellungen auf alle neuen Datenbanken, die anschließend erstellt.  Diese Einstellungen werden jedoch nicht automatisch von vorhandenen Datenbanken geerbt. So konfigurieren Sie [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] für bereits vorhandene Datenbanken müssen Sie jede Datenbank konfigurieren. Weitere Informationen finden Sie unter [aktivieren und Konfigurieren von SQL Server Managed Backup für Windows Azure für eine Datenbank](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md#DatabaseConfigure).  
  
 Wenn [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] wurde angehalten wurde, mithilfe der `smart_admin.sp_backup_master_switch`, wird Ihnen eine Warnmeldung "verwaltete Sicherung ist deaktiviert und die aktuellen Konfigurationen nicht wirksam werden..." und die aktuellen Konfigurationen werden nicht übernommen.“ Verwenden der `smart_admin.sp_backup_master_switch` gespeichert, und legen Sie die @new_state= 1. Dies wird fortgesetzt, [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] Dienste und die Konfigurationseinstellungen werden wirksam. Weitere Informationen für die gespeicherte Prozedur finden Sie unter [smart_admin.sp_ Backup_master_switch &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/managed-backup-sp-backup-master-switch-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Managed Backup für Microsoft Azure: Interoperabilität und Koexistenz](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
  
