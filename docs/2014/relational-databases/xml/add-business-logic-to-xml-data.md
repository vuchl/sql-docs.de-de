---
title: Hinzufügen von Geschäftslogik zu XML-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8e2346587c198789f81663af9d98e5310b78de03
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890116"
---
# <a name="add-business-logic-to-xml-data"></a>Hinzufügen von Geschäftslogik zu XML-Daten
  Ihre Geschäftslogik kann auf verschiedene Art und Weise den XML-Daten hinzugefügt werden:  
  
-   Sie können Zeilen- oder Spalteneinschränkungen schreiben, um beim Einfügen und Bearbeiten von XML-Daten domänenspezifische Einschränkungen zu erzwingen.  
  
-   Sie können einen Trigger für die XML-Spalte schreiben, der ausgelöst wird, wenn Sie Werte in die Spalte einfügen oder aktualisieren. Der Trigger kann domänenspezifische Überprüfungsregeln enthalten oder Eigenschaftentabellen auffüllen.  
  
-   Die Datenbank-Engine ist in der Lage, verwalteten Code auszuführen. Sie können diese CLR-Integration (Common Language Runtime) nutzen, um verwalteten Code zu schreiben, an den Sie XML-Werte übergeben, und die vom System.Xml-Namespace bereitgestellten Möglichkeiten zur XML-Verarbeitung verwenden. Ein Beispiel hierfür ist die Anwendung der XSL-Transformation auf XML-Daten. Alternativ können Sie den XML-Code in eine oder mehrere verwaltete Klassen deserialisieren und diese mithilfe von verwaltetem Code verarbeiten.  
  
-   Sie können gespeicherte Transact-SQL-Prozeduren und -Funktionen schreiben, mit denen das Verarbeiten der XML-Spalte für Ihre Unternehmensanforderungen gestartet wird.  
  
## <a name="example-applying-xsl-transformation"></a>Beispiel: Anwenden der XSL-Transformation  
 Angenommen, eine CLR-Funktion **TransformXml()** , akzeptiert eine `xml` Daten-Datentypinstanz und eine XSL-Transformation, die in einer Datei gespeichert, wendet die Transformation auf die XML-Daten und gibt dann den transformierten XML-Code im Ergebnis zurück. Es folgt eine Skeleton-Funktion, die in C# geschrieben ist:  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 Nachdem die Assembly registriert und eine benutzerdefinierte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktion erstellt wurde ( **SqlXslTransform()** entsprechend **TransformXml()**), kann die Funktion von Transact-SQL aus aufgerufen werden, wie in der folgenden Abfrage gezeigt:  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 Das Abfrageergebnis enthält ein Rowset der transformierten XML-Daten.  
  
 Die CLR-Integration in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erweitert die Möglichkeiten zum Zerlegen der XML-Daten in Tabellen oder zum Höherstufen von Eigenschaften sowie die Möglichkeiten zum Abfragen von XML-Daten durch Verwenden von verwalteten Klassen im System.Xml-Namespace. Weitere Informationen finden Sie unter [XML-Daten &#40;SQL Server&#41;](xml-data-sql-server.md).  
  
  
