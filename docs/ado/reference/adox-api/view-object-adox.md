---
title: View-Objekt (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2980c92b7980fe2fa6ec16f82bc4d8f7d3aff585
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287439"
---
# <a name="view-object-adox"></a>View-Objekt (ADOX)
Stellt einen gefilterten Satz von Datensätzen oder eine virtuelle Tabelle dar. Bei der Verwendung in Verbindung mit dem ADO [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das **Ansicht** Objekt kann zum Hinzufügen, löschen oder Ändern von Sichten verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Eine Sicht ist eine virtuelle Tabelle, die aus anderen Datenbanktabellen oder-Ansichten erstellt wurde. Die **Ansicht** Objekts können Sie eine Ansicht erstellen, ohne zu wissen, oder verwenden Sie den Anbieter "CREATE VIEW"-Syntax.  
  
 Mit den Eigenschaften des eine **Ansicht** -Objekt können Sie:  
  
-   Wählen Sie die Ansicht mit der [Namen](../../../ado/reference/adox-api/name-property-adox.md) Eigenschaft.  
  
-   Geben Sie die ADO **Befehl** -Objekt, das verwendet werden kann, hinzufügen, löschen oder Ändern von Sichten mit der [Befehl](../../../ado/reference/adox-api/command-property-adox.md) Eigenschaft.  
  
-   Rückgabeinformationen Datum mit dem [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md) und [DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md) Eigenschaften.  
  
 Dieser Abschnitt enthält das folgende Thema.  
  
-   [View-Objekt – Eigenschaften, Methoden und Ereignisse](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Ansichten und Felder Beispiel für Auflistungen (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Ansichten Append-Methode (Beispiel) (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views-Auflistung, CommandText-Eigenschaft (VB)-Beispiel](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Ansichten löschen Methodenbeispiel (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views-Auflistung (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
