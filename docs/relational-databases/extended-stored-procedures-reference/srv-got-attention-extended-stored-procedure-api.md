---
title: "„srv_got_attention“ (API für die erweiterte gespeicherte Prozedur) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_got_attention
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 429c804e3d7b836e21a6c49868f5043e7cb9345e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>'srv_got_attention' (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Überprüft, ob die aktuelle Verbindung oder der aktuelle Task abgebrochen werden muss, und gibt TRUE zurück, wenn die Verbindung beendet oder der Batch abgebrochen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *srvproc*   
 Zeiger, der eine Datenbankverbindung identifiziert  
  
## <a name="return-value"></a>Rückgabewert  
 TRUE, wenn die Verbindung beendet oder der Batch abgebrochen wird. FALSE, wenn die Verbindung bzw. der Batch aktiv ist.  
  
## <a name="remarks"></a>Hinweise  
 Eine erweiterte gespeicherte Prozedur mit langer Ausführungszeit sollte die Servertätigkeit in regelmäßigen Abständen mit **srv_got_attention** prüfen, damit die Prozedur sich selbst beenden kann, falls die Verbindung beendet oder der Batch abgebrochen wurde.  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  