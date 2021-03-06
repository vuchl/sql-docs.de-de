---
title: Bereitstellen eines SSIS-Pakets mit Transact-SQL (VS Code) | Microsoft-Dokumentation
ms.date: 05/21/2018
ms.topic: quickstart
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 44d41b54ff2b422b66e0be2bfe42497fa1ff458e
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35329254"
---
# <a name="deploy-an-ssis-project-from-visual-studio-code-with-transact-sql"></a>Bereitstellen eines SSIS-Pakets aus Visual Studio Code mit Transact-SQL
In diesem Schnellstart wird erläutert, wie Sie mit Visual Studio Code eine Verbindung mit der SSIS-Katalogdatenbank herstellen und anschließend mithilfe von Transact-SQL-Anweisungen ein im SSIS-Katalog gespeichertes SSIS-Projekt bereitstellen.

Visual Studio Code ist ein Code-Editor für Windows, macOS und Linux, der Erweiterungen unterstützt. Dazu gehört auch die `mssql`-Erweiterung zum Herstellen einer Verbindung mit Microsoft SQL Server, Azure SQL-Datenbank und Azure SQL Data Warehouse. Weitere Informationen zu VS Code finden Sie unter [Visual Studio Code](https://code.visualstudio.com/).

## <a name="prerequisites"></a>Voraussetzungen

Prüfen Sie, bevor Sie beginnen, ob Sie die neueste Version von Visual Studio Code installiert haben und die `mssql`-Erweiterung geladen ist. Informationen zum Herunterladen dieser Tools finden Sie auf den folgenden Seiten:
-   [Herunterladen von Visual Studio Code](https://code.visualstudio.com/Download)
-   [mssql extension (mssql-Erweiterung)](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)

## <a name="supported-platforms"></a>Unterstützte Plattformen

Mithilfe der Informationen in diesem Schnellstart können Sie auf den folgenden Plattformen SSIS-Projekte bereitstellen:

-   SQL Server unter Windows

Mithilfe der Informationen in diesem Schnellstart können Sie keine SSIS-Pakete in Azure SQL-Datenbank bereitstellen. Die gespeicherte Prozedur `catalog.deploy_project` erwartet den Pfad zur Datei `.ispac` im lokalen Dateisystem. Weitere Informationen zum Bereitstellen und Ausführen von Paketen in Azure finden Sie unter [Migration von SQL Server Integration Services-Workloads in die Cloud per Lift & Shift](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Dieser Schnellstart enthält keine Anleitung zum Bereitstellen von SSIS-Paketen in SQL Server unter Linux. Weitere Informationen zum Ausführen von Paketen finden Sie unter [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](../linux/sql-server-linux-migrate-ssis.md).

## <a name="set-language-mode-to-sql-in-vs-code"></a>Festlegen des Sprachmodus auf SQL in VS Code

Legen Sie den Sprachmodus auf `mssql`SQL**in Visual Studio Code fest, um**-Befehle und T-SQL IntelliSense zu aktivieren.

1. Öffnen Sie zuerst Visual Studio Code und dann ein neues Fenster. 

2. Klicken Sie auf **Nur-Text** in der unteren rechten Ecke der Statusleiste.
 
3. Klicken Sie im sich öffnenden Dropdownmenü **Sprachmodus auswählen** auf **SQL**, oder geben Sie es ein, und drücken Sie dann die **EINGABETASTE**, um den Sprachmodus auf „SQL“ festzulegen. 

## <a name="connect-to-the-ssis-catalog-database"></a>Herstellen einer Verbindung mit der SSIS-Katalogdatenbank

Verwenden Sie Visual Studio Code, um eine Verbindung mit dem SSIS-Katalog herzustellen.

1. Drücken Sie in VS Code **STRG+UMSCHALT+P** (oder **F1**), um die Befehlspalette zu öffnen.

2. Geben Sie **sqlcon** ein, und drücken Sie die **EINGABETASTE**.

3. Drücken Sie die **EINGABETASTE**, um **Create Connection Profile** (Verbindungsprofil erstellen) auszuwählen. Mithilfe dieses Schritts wird ein Verbindungsprofil für Ihre SQL Server-Instanz erstellt.

4. Befolgen Sie die Anweisungen, um die Verbindungseigenschaften für das neue Verbindungsprofil anzugeben. Nachdem Sie sämtliche Werte angegeben haben, drücken Sie die **EINGABETASTE**, um fortzufahren. 

   | Einstellung       | Vorgeschlagener Wert | Weitere Informationen |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Servername** | Der vollqualifizierte Servername |  |
   | **Datenbankname** | **SSISDB** | Dies ist der Name der Datenbank, mit der eine Verbindung hergestellt werden soll. |
   | **Authentifizierung** | SQL-Anmeldung | |
   | **User name** | Das Konto des Serveradministrators | Dabei handelt es sich um das Konto, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort (SQL-Anmeldung)** | Das Kennwort für das Konto des Serveradministrators | Dabei handelt es sich um das Kennwort, das Sie beim Erstellen des Servers angegeben haben. |
   | **Kennwort speichern** | Ja oder Nein | Wenn Sie nicht bei jedem Neustart Ihr Kennwort eingeben möchten, wählen Sie „Ja“ aus. |
   | **Namen für dieses Profil eingeben** | Ein Profilname wie **mySSISServer** | Wenn Sie den Profilnamen speichern, wird bei späteren Anmeldungen schneller eine Verbindung hergestellt. | 

5. Drücken Sie die **ESC**-Taste, um die Meldung zu schließen, in der Sie darüber informiert werden, dass das Profil erstellt und eine Verbindung hergestellt wurde.

6. Überprüfen Sie Ihre Verbindung in der Statusleiste.

## <a name="run-the-t-sql-code"></a>Ausführen des T-SQL-Codes
Führen Sie den folgenden Transact-SQL-Code aus, um ein SSIS-Projekt bereitzustellen.

1. Geben Sie im Fenster **Editor** die folgende Abfrage in ein leeres Abfragefenster ein.

2. Aktualisieren Sie die Parameterwerte in der für das System gespeicherten `catalog.deploy_project`-Prozedur.

3. Drücken Sie **STRG+UMSCHALT+E**, um den Code und das Projekt bereitzustellen.

```sql
DECLARE @ProjectBinary AS varbinary(max)
DECLARE @operation_id AS bigint
SET @ProjectBinary = (SELECT * FROM OPENROWSET(BULK '<project_file_path>.ispac', SINGLE_BLOB) AS BinaryData)

EXEC catalog.deploy_project @folder_name = '<target_folder>',
    @project_name = '<project_name',
    @Project_Stream = @ProjectBinary,
    @operation_id = @operation_id out
```

## <a name="next-steps"></a>Nächste Schritte
- Erfahren Sie mehr über weitere Möglichkeiten, ein Paket bereitzustellen.
    - [Deploy an SSIS package with SSMS (Bereitstellen eines SSIS-Pakets mit SSMS)](./ssis-quickstart-deploy-ssms.md)
    - [Deploy an SSIS package with Transact-SQL (SSMS) (Bereitstellen eines SSIS-Pakets mit Transact-SQL [SSMS])](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Deploy an SSIS package from the command prompt (Bereitstellen eines SSIS-Projekts von der Befehlszeile aus)](./ssis-quickstart-deploy-cmdline.md)
    - [Deploy an SSIS package with PowerShell (Bereitstellen eines SSIS-Pakets mit PowerShell)](ssis-quickstart-deploy-powershell.md)
    - [Deploy an SSIS package with C# (Bereitstellen eines SSIS-Pakets mit C#)](./ssis-quickstart-deploy-dotnet.md) 
- Führen Sie ein bereitgestelltes Paket aus. Für die Ausführung eines Pakets können Sie aus mehreren Tools und Sprachen auswählen. Weitere Informationen finden Sie in den folgenden Artikeln:
    - [Run an SSIS package with SSMS](./ssis-quickstart-run-ssms.md) (Ausführen eines SSIS-Pakets mit SSMS)
    - [Run an SSIS package with Transact-SQL (SSMS) (Ausführen eines SSIS-Pakets mit Transact-SQL [SSMS])](./ssis-quickstart-run-tsql-ssms.md)
    - [Run an SSIS package with Transact-SQL (VS Code)](ssis-quickstart-run-tsql-vscode.md) (Ausführen eines SSIS-Pakets mit Transact-SQL [VS Code])
    - [Run an SSIS package from the command prompt](./ssis-quickstart-run-cmdline.md) (Ausführen eines SSIS-Pakets über die Eingabeaufforderung)
    - [Run an SSIS package with PowerShell](ssis-quickstart-run-powershell.md) (Ausführen eines SSIS-Pakets mit PowerShell)
    - [Run an SSIS package with C#](./ssis-quickstart-run-dotnet.md) (Ausführen eines SSIS-Pakets mit C#) 
