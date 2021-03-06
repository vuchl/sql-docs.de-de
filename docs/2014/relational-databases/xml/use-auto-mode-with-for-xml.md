---
title: Verwenden des AUTO-Modus mit FOR XML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, AUTO mode
- ELEMENTS option
- FOR XML AUTO mode
- AUTO FOR XML mode
ms.assetid: 7140d656-1d42-4f01-a533-5251429f4450
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3ed5e1d620a5a56848a57f67b92345fc535db3cf
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888496"
---
# <a name="use-auto-mode-with-for-xml"></a>Verwenden des AUTO-Modus mit FOR XML
  Wie in [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)beschrieben, gibt der AUTO-Modus Abfrageergebnisse als geschachtelte XML-Elemente zurück. Damit ist jedoch keine genaue Steuerungsmöglichkeit über die Form des XML-Codes gegeben, der aus einem Abfrageergebnis generiert wird. Die AUTO-Modusabfragen sind nützlich, wenn Sie einfache Hierarchien generieren möchten. Allerdings können Sie durch [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md) und [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md) bessere Steuerungsmöglichkeiten und eine höhere Flexibilität in Bezug auf die Form des aus einem Abfrageergebnis generierten XML-Codes erzielen.  
  
 Jede Tabelle in der FROM-Klausel, aus der mindestens eine Spalte in der SELECT-Klausel aufgeführt ist, wird als ein XML-Element dargestellt. Die in der SELECT-Klausel aufgelisteten Spalten werden den entsprechenden Attributen oder Unterelementen zugeordnet, wenn die wahlweise Option ELEMENTS in der FOR XML-Klausel angegeben wurde.  
  
 Die XML-Hierarchie, also die Schachtelung der Elemente, im resultierenden XML-Code basiert auf der Tabellenreihenfolge, die durch die Spalten identifiziert wird, die in der SELECT-Klausel angegeben sind. Deshalb ist die Reihenfolge, in der die Spaltennamen in der SELECT-Klausel angegeben werden, von großer Bedeutung. Die erste identifizierte Tabelle von links bildet das oberste Element in dem resultierenden XML-Dokument. Die zweite Tabelle von links (identifiziert durch die Spalten in der SELECT-Anweisung) bildet ein Unterelement im obersten Element usw.  
  
 Falls ein in der SELECT-Klausel aufgeführter Spaltenname aus einer Tabelle stammt, die bereits durch eine zuvor angegebene Spalte in der SELECT-Klausel identifiziert wird, wird die Spalte als Attribut zu dem bereits erstellten Element hinzugefügt. Es wird also keine neue Ebene der Hierarchie geöffnet. Wenn die Option ELEMENTS angegeben ist, wird die Spalte als Attribut hinzugefügt.  
  
 Führen Sie z. B. die folgende Abfrage aus:  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO  
```  
  
 Dies ist das Teilergebnis:  
  
```  
<Cust CustomerID="1" CustomerType="S">  
  <OrderHeader CustomerID="1" SalesOrderID="43860" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="44501" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="45283" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="46042" Status="5" />  
</Cust>  
...  
```  
  
 Beachten Sie in der SELECT-Klausel Folgendes:  
  
-   Die CustomerID verweist auf die Cust-Tabelle. Deshalb wird ein <`Cust`>-Element erstellt, dem CustomerID als Attribut hinzugefügt wird.  
  
-   Als Nächstes verweisen die drei Spalten OrderHeader.CustomerID, OrderHeader.SaleOrderID und OrderHeader.Status auf die OrderHeader-Tabelle. Deshalb wird ein <`OrderHeader`>-Element als Unterelement des <`Cust`>-Elements hinzugefügt, und die drei Spalten werden als Attribute von <`OrderHeader`> hinzugefügt.  
  
-   Als Nächstes verweist die Cust.CustomerType-Spalte erneut auf die Cust-Tabelle, die bereits durch die Cust.CustomerID-Spalte identifiziert wurde. Aus diesem Grund wird kein neues Element erstellt. Stattdessen wird das CustomerType-Attribut zum zuvor erstellten <`Cust`>-Element hinzugefügt.  
  
-   Die Abfrage gibt Aliasnamen für die Tabellennamen an. Diese Aliasnamen erscheinen als die entsprechenden Elementnamen.  
  
-   ORDER BY ist erforderlich, um alle untergeordneten Elemente unter einem übergeordneten Element zu gruppieren.  
  
 Diese Abfrage gleicht der vorherigen Abfrage, außer dass in der SELECT-Klausel die Spalten in der OrderHeader-Tabelle vor den Spalten in der Cust-Tabelle angegeben werden. Deshalb wird zuerst das <`OrderHeader`>-Element erstellt und erst danach wird diesem Element das untergeordnete <`Cust`>-Element hinzugefügt.  
  
```  
select OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerID,   
       Cust.CustomerType  
from Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
where Cust.CustomerID = OrderHeader.CustomerID  
for xml auto  
```  
  
 Dies ist das Teilergebnis:  
  
```  
<OrderHeader CustomerID="1" SalesOrderID="43860" Status="5">  
  <Cust CustomerID="1" CustomerType="S" />  
</OrderHeader>  
...  
```  
  
 Wenn die Option ELEMENTS der FOR XML-Klausel hinzugefügt wird, wird elementzentriertes XML zurückgegeben.  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO, ELEMENTS  
```  
  
 Dies ist das Teilergebnis:  
  
```  
<Cust>  
  <CustomerID>1</CustomerID>  
  <CustomerType>S</CustomerType>  
  <OrderHeader>  
    <CustomerID>1</CustomerID>  
    <SalesOrderID>43860</SalesOrderID>  
    <Status>5</Status>  
  </OrderHeader>  
   ...  
</Cust>  
...  
```  
  
 In dieser Abfrage werden die CustomerID-Werte aus einer Zeile mit denen in der nächsten verglichen, wenn die \<Cust>-Elemente erstellt werden, weil CustomerID der Primärschlüssel der Tabelle ist. Wenn CustomerID nicht als Primärschlüssel für die Tabelle identifiziert wurde, werden alle Spaltenwerte (in dieser Abfrage CustomerID und CustomerType) aus einer Zeile mit denen in der nächsten Zeile verglichen. Wenn die Werte voneinander abweichen, wird dem XML-Code ein neues \<Cust>-Element hinzugefügt.  
  
 Wenn beim Vergleichen dieser Spaltenwerte eine der miteinander zu vergleichenden Spalten den Datentyp **text**, **ntext**, **image**oder **xml**aufweist, nimmt FOR XML an, dass die Werte sich unterscheiden und nicht miteinander verglichen werden, obwohl sie sich gleichen können. Das liegt daran, dass das Vergleichen von großen Objekten nicht unterstützt wird. Für jede ausgewählte Zeile werden die Elemente dem Ergebnis hinzugefügt. Beachten Sie, dass die Spalten des Datentyps **(n)varchar(max)** und **varbinary(max)** verglichen werden.  
  
 Wenn eine Spalte in der SELECT-Klausel nicht einer der in der FROM-Klausel identifizierten Tabellen zugeordnet werden kann (z. B. bei Aggregatspalten oder berechneten Spalten), wird die Spalte dem XML-Dokument in der tiefsten Schachtelungsebene hinzugefügt, wenn sie in der Liste entdeckt wird. Wird eine solche Spalte als erste Spalte in der SELECT-Klausel aufgeführt, wird sie dem obersten Element hinzugefügt.  
  
 Wenn das Platzhalterzeichen (*) in der SELECT-Klausel angegeben wurde, wird die Schachtelung auf die gleiche Art wie oben beschrieben bestimmt (d. h. auf der Grundlage der Reihenfolge, in der die Zeilen von der Abfrage-Engine zurückgegeben werden).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 Die folgenden Themen enthalten weitere Informationen zum AUTO-Modus:  
  
-   [Verwenden der Option BINARY BASE64](use-the-binary-base64-option.md)  
  
-   [AUTO-Modus-Heuristik beim Ermitteln der Form des zurückgegebenen XML-Codes](auto-mode-heuristics-in-shaping-returned-xml.md)  
  
-   [Beispiele: Verwenden des AUTO-Modus](examples-using-auto-mode.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)  
  
  
