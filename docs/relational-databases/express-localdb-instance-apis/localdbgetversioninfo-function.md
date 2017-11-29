---
title: LocalDBGetVersionInfo-Funktion | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: LocalDBGetVersionInfo
apilocation: sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c9bcc5ae184ac67e4443df4023cb2be8e4b8faa4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="localdbgetversioninfo-function"></a>LocalDBGetVersionInfo-Funktion
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Gibt Informationen für die angegebene SQL Server Express LocalDB-Version, z. B., ob es vorhanden ist und die vollständige LocalDB-Versionsnummer (inklusive Build- und Releasenummer) zurück.  
  
 Die Informationen werden zurückgegeben, in Form von einer **Struktur** mit dem Namen **LocalDBVersionInfo**, die weist folgende Definition.  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **Headerdatei:** sqlncli.h  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Parameter  
 *wszVersionName*  
 [Eingabe] Der Name der LocalDB-Version.  
  
 *pVersionInfo*  
 [Ausgabe] Der Puffer zum Speichern der Informationen zur LocalDB-Version.  
  
 *dwVersionInfoSize*  
 [Eingabe] Nimmt die Größe der *VersionInfo* Puffer.  
  
## <a name="returns"></a>Rückgabewert  
 S_OK  
 Die Funktion wurde erfolgreich ausgeführt.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB ist nicht auf dem Computer installiert.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Mindestens ein angegebener Eingabeparameter ist ungültig.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 Die angegebene LocalDB-Version ist nicht vorhanden.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Ein unerwarteter Fehler ist aufgetreten. Weitere Informationen finden Sie im Ereignisprotokoll.  
  
## <a name="details"></a>Details  
 Der Grund für die Einführung der **Struktur** -größenargument (*LpVersionInfoSize*) besteht darin, aktivieren die API zurückzugebenden verschiedene Versionen von der **LocalDBVersionInfostruct**effektiv Aufwärts-und Abwärtskompatibilität aktivieren.  
  
 Wenn die **Struktur** -größenargument (*LpVersionInfoSize*) entspricht der Größe einer bekannten Version von der **LocalDBVersionInfostruct**, diese Version von den  **Struktur** zurückgegeben wird. Andernfalls wird LOCALDB_ERROR_INVALID_PARAMETER zurückgegeben.  
  
 Ein typisches Beispiel **LocalDBGetVersionInfo** zur Verwendung der API sieht wie folgt aus:  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L”11.0”, &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Codebeispiel, in dem die LocalDB-API verwendet wird, finden Sie unter [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Express LocalDB-Header und -Versionsinformationen](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  