---
title: Vom Client zum Server ausgeführte Konvertierungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], client to server
ms.assetid: 6bb24928-0f3e-4119-beda-cfd04a44a3eb
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33aa66968fe93944172356a9be55d12fa459ddc3
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427899"
---
# <a name="conversions-performed-from-client-to-server"></a>Client-/Server-Konvertierungen
  In diesem Thema wird beschrieben, Datum/Uhrzeit-Konvertierungen zwischen einer Clientanwendung mit geschrieben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher).  
  
## <a name="conversions"></a>Konvertierungen  
 In diesem Thema werden die auf dem Client durchgeführten Konvertierungen beschrieben. Wenn der Client Bruchsekundengenauigkeit für einen Parameter angibt, die von der auf dem Server definierten abweicht, schlägt die Clientkonvertierung in Fällen, in denen der Server eine erfolgreiche Konvertierung zugelassen hätte, möglicherweise fehl. Insbesondere behandelt der Client jedes Abschneiden von Sekundenbruchteilen als Fehler, wohingegen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rundet Zeitwerte auf die nächste ganze Sekunde.  
  
 Wenn ICommandWithParameters:: SetParameterInfo nicht aufgerufen wird, werden DBTYPE_DBTIMESTAMP-Bindungen konvertiert, als wären sie `datetime2`.  
  
|To -><br /><br /> Von|DBDATE (date)|DBTIME (time)|DBTIME2 (time)|DBTIMESTAMP (smalldatetime)|DBTIMESTAMP (datetime)|DBTIMESTAMP (datetime2)|DBTIMESTAMPOFFSET (datetimeoffset)|STR|WSTR|SQLVARIANT<br /><br /> (sql_variant)|  
|----------------------|---------------------|---------------------|----------------------|-----------------------------------|------------------------------|-------------------------------|------------------------------------------|---------|----------|-------------------------------------|  
|DATE|1,2|1,3,4|4,12|1,12|1,12|1,12|1,5, 12|1,12|1,12|1,12<br /><br /> datetime2(0)|  
|DBDATE|1|-|-|1,6|1,6|1,6|1,5, 6|1,10|1,10|1<br /><br /> Datum|  
|DBTIME|-|1|1|1,7|1,7|1,7|1,5, 7|1,10|1,10|1<br /><br /> Time(0)|  
|DBTIME2|-|1,3|1|1,7,10,14|1,7,10,15|1,7,10|1,5,7,10|1,10,11|1,10,11|1<br /><br /> Time(7)|  
|DBTIMESTAMP|1,2|1,3,4|1,4,10|1,10,14|1,10,15|1,10|1,5,10|1,10,11|1,10,11|1,10<br /><br /> datetime2(7)|  
|DBTIMESTAMPOFFSET|1,2,8|1,3,4,8|1,4,8,10|1,8,10,14|1,8,10,15|1,8,10|1,10|1,10,11|1,10,11|1,10<br /><br /> datetimeoffset(7)|  
|FILETIME|1,2|1,3,4|1,4,13|1,13|1,13|1,13|1,5,13|1,13|1,10|1,13<br /><br /> datetime2(3)|  
|BYTES|-|-|-|-|-|-|-|–|–|–|  
|VARIANT|1|1|1|1,10|1,10|1,10|1,10|–|–|1,10|  
|SSVARIANT|1,16|1,16|1,16|1,10,16|1,10,16|1,10,16|1,10,16|–|–|1,16|  
|BSTR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|–|–|–|  
|STR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|–|–|–|  
|WSTR|1,9|1,9|1,9,10|1,9,10|1,9,10|1,9,10|1,9,10|–|–|–|  
  
## <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|-|Es wird keine Konvertierung unterstützt. Wenn die Bindung überprüft wird, wenn IAccessor:: CreateAccessor aufgerufen wird, wird DBBINDSTATUS_UPSUPPORTEDCONVERSION in zurückgegeben *RgStatus*. Bei Verzögerung der Accessorüberprüfung wird DBSTATUS_E_BADACCESSOR festgelegt.|  
|–|Nicht verfügbar.|  
|1|Wenn die bereitgestellten Daten nicht gültig sind, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt. Die Eingabedaten werden überprüft, bevor die Konvertierungen angewendet werden, d.&nbsp;h. auch wenn eine Komponente von einer nachfolgenden Konvertierung ignoriert wird, muss sie gültig sein, damit die Konvertierung ordnungsgemäß durchgeführt werden kann.|  
|2|Zeitfelder werden ignoriert.|  
|3|Sekundenbruchteile müssen 0 sein, oder es wird DBSTATUS_E_DATAOVERFLOW festgelegt.|  
|4|Die Datumskomponente wird ignoriert.|  
|5|Die Zeitzone wird auf die Zeitzone des Clients festgelegt.|  
|6|Die Uhrzeit wird auf 0 (Null) festgelegt.|  
|7|Das Datum wird auf das aktuelle Datum festgelegt.|  
|8|Die Zeit wird zu UTC konvertiert. Wenn während dieser Konvertierung ein Fehler auftritt, wird DBSTATUS_E_CANTCONVERTVALUE festgelegt.|  
|9|Die Zeichenfolge wird als ISO-Literal analysiert und in den Zieltyp konvertiert. Falls dies fehlschlägt, wird die Zeichenfolge als OLE-Datumsliteral analysiert (welches gleichfalls Zeitkomponenten enthält) und vom OLE-Datumstyp (DBTYPE_DATE) in den Zieldatumstyp konvertiert.<br /><br /> Wenn der Zieltyp DBTIMESTAMP, `smalldatetime`, `datetime` oder `datetime2` ist, muss die Zeichenfolge mit der Syntax für Datums-, Uhrzeit- oder `datetime2`-Literalen oder der von OLE erkannten Syntax konform sein. Wenn die Zeichenfolge ein Datumsliteral ist, werden alle Uhrzeitkomponenten auf&nbsp;0 festgelegt. Wenn die Zeichenfolge ein Uhrzeitliteral ist, wird das Datum auf das aktuelle Datum festgelegt.<br /><br /> Für alle anderen Zieltypen muss die Zeichenfolge der Syntax für Literale des Zieltyps entsprechen.|  
|10|Wenn das Abschneiden von Sekundenbruchteilen Datenverlust verursacht, wird DBSTATUS_E_DATAOVERFLOW festgelegt. Für Zeichenfolgenkonvertierungen ist eine Überlaufprüfung nur möglich, wenn die Zeichenfolge der ISO-Syntax entspricht. Wenn es sich bei der Zeichenfolge um ein OLE-Datumsliteral handelt, werden Sekundenbruchteile gerundet.<br /><br /> Für die Konvertierung von DBTIMESTAMP (Datetime) in Smalldatetime [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client wird im Hintergrund den Sekundenwert ab, statt den Fehler dbstatus_e_dataoverflow auszulösen abgeschnitten.|  
|11|Die Anzahl der Dezimalziffern für Sekundenbruchteile (Dezimalstellen) wird anhand der Größe der Zielspalte gemäß der folgenden Tabelle ermittelt. Für Spaltengrößen, die den Bereich in der Tabelle übersteigen, werden 9 Dezimalstellen impliziert. Diese Konvertierung sollte bis zu neun Dezimalstellen für Sekundenbruchteile ermöglichen, das von OLE&nbsp;DB zugelassene Maximum.<br /><br /> Wenn jedoch der Quelltyp DBTIMESTAMP ist, und Sekundenbruchteile auf 0 gesetzt wurden, werden keine Dezimalstellen für Sekundenbruchteile und kein Dezimaltrennzeichen generiert. Dieses Verhalten stellt die Abwärtskompatibilität für Anwendungen sicher, die mit älteren OLE&nbsp;DB-Anbietern entwickelt wurden.<br /><br /> Eine Spaltengröße von ~0 impliziert unbegrenzte Größe in OLE&nbsp;DB (9 Ziffern, sofern nicht die 3-Ziffern-Regel für DBTIMESTAMP gilt).<br /><br /> **DBTIME2** - 8, 10..18 (Länge in Zeichen); 0, 1..9 (skalieren)<br /><br /> **DBTIMESTAMP** - 19, 21..29 (Länge in Zeichen); 0, 1..9 (skalieren)<br /><br /> **DBTIMESTAMPOFFSET** - 26, 28..36 (Länge in Zeichen); 0, 1..9 (skalieren)|  
|12|Gültige Konvertierungssemantik [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] für DBTYPE_DATE wird beibehalten. Die Sekundenbruchteile werden zu&nbsp;0 abgeschnitten.|  
|13|Gültige Konvertierungssemantik [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] für DBTYPE_FILETIME wird beibehalten. Wenn Sie die Windows-FileTimeToSystemTime-API verwenden, ist die Genauigkeit der Sekundenbruchteile auf 1 Millisekunde beschränkt.|  
|14|Gültige Konvertierungssemantik [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] für `smalldatetime` werden beibehalten. Die Sekunden werden auf&nbsp;0 festgelegt.|  
|15|Gültige Konvertierungssemantik [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] für `datetime` werden beibehalten. Sekunden werden zum nächstem 300stel einer Sekunde gerundet.|  
|16|Das Konvertierungsverhalten eines in eine SSVARIANT-Clientstruktur eingebetteten Werts (eines bestimmten Typs) ist mit dem Verhalten desselben Werts und Typs identisch, wenn er nicht eingebettet ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Bindungen und Konvertierungen &#40;OLE-DB&#41;](conversions-ole-db.md)  
  
  
