---
title: Anwendungstypen | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26835fa277391f359d628ec25c03d38364e398e7
ms.contentlocale: de-de
ms.lasthandoff: 09/09/2017

---
# <a name="types-of-applications"></a>Anwendungstypen
ODBC-Anwendungen können wie folgt klassifiziert werden:  
  
-   **Reine ODBC 2.**  
     ***X* Anwendung** eine 32-Bit-Anwendung, die:  
  
    -   Ruft nur ODBC 2. *x* Funktionen (einschließlich der ODBC-1.0-Funktion **SQLSetParam**). Dazu gehören die ODBC-1. *x* Anwendungen, die auf 32 Bits portiert haben.  
  
    -   Erwartet, dass ODBC 2. *x* Verhalten für Funktionen, die Änderungen am Systemverhalten hatten. (Siehe [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) für Weitere Informationen.)  
  
    -   Nicht mit ODBC 3.5-Headern neu kompiliert wurde.  
  
-   **Reine ODBC 2.**  
     ***X* Anwendung neu kompiliert** eine reine ODBC 2..* X* Anwendung, die neu kompiliert wurde mithilfe der ODBC 3.5-Header-Dateien durch Festlegen von ODBCVER = 0x0250.  
  
-   **Reine ODBC 2.**  
     ***X* Unicode-Anwendung** eine reine ODBC 2..* X* erneut kompiliert, Anwendung, die Unicode-kompatibel ist und verwendet den SQL_WCHAR-Datentyp.  
  
-   **Reine Open Group und ISO**–**kompatibler ODBC-Anwendung** eine 32-Bit-Anwendung, die:  
  
    -   Ruft die Funktionen, die in den Open Group oder ISO-CLI-Standards definiert. (Diese Funktionen möglicherweise veraltete 3.0-Funktionen enthalten.)  
  
    -   Verwendet nicht die Unicode-Datentypen.  
  
    -   Erwartet, dass ODBC 3.0-Verhalten für Funktionen, die Änderungen am Systemverhalten hatten.  
  
-   **Reine ODBC 3.0-Anwendung** eine 32-Bit-Anwendung, die:  
  
    -   Mit 3.0 Headern kompiliert wird.  
  
    -   Ruft alle ODBC 3.0-Funktion, ggf. einschließlich derer, die als veraltet markiert werden.  
  
    -   Erwartet, dass ODBC 3.0-Verhalten für Funktionen, die Änderungen am Systemverhalten hatten.  
  
-   **Reine ODBC 3.5-Anwendung** A 32 oder 64-Bit-Anwendung, die:  
  
    -   Sie können Unicode-Datentypen.  
  
    -   Ruft alle ODBC 3.5-Funktion, ggf. einschließlich derer, die als veraltet markiert werden.  
  
    -   Erwartet, dass ODBC 3.5-Verhalten für Funktionen, die Änderungen am Systemverhalten hatten.  
  
-   **Reine ODBC 3.8 (oder höher)-Anwendung** eine 32-Bit oder 64-Bit-Anwendung, die:  
  
    -   Sie können Unicode-Datentypen.  
  
    -   Ruft alle ODBC 3.8-Funktion, ggf. einschließlich derer, die als veraltet markiert werden.  
  
    -   Erwartet, dass ODBC 3.8-Verhalten für Funktionen, die Änderungen am Systemverhalten hatten.  
  
-   **Anwendung ersetzt** A 32 oder 64-Bit-Anwendung, die:  
  
    -   Implementiert neues Verhalten für die duplizierte Funktionalität.  
  
    -   Verwendet keine neuen Funktionen in zukünftigen Versionen von ODBC nur innerhalb der bedingten Code.  
  
    -   Bedingten Code zur Behandlung von Änderungen am Systemverhalten verfügt über eingeschränkten oder hat sich selbst um eine frühere Version von ODBC-Anwendung werden registriert.