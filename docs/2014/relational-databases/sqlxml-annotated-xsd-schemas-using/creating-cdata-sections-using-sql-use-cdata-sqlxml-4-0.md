---
title: 'Erstellen von CDATA-Abschnitten mithilfe von SQL: use-Cdata (SQLXML 4.0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb7e3e0acc985dce3d3783de63bea95f9de6877f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175424"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>Erstellen von CDATA-Abschnitten mit sql:use-cdata (SQLXML 4.0)
  In XML werden Textblöcke, die Zeichen enthalten, die andernfalls als Markup erkannt würden, mit CDATA-Abschnitten in Escapezeichen umgewandelt.  
  
 In einer Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann manchmal Zeichen enthalten, die von der XML-Parser als Markupzeichen behandelt werden, zum Beispiel werden spitze Klammern (\< und >), das kleiner-als-oder-gleich-Symbol (< =), und das kaufmännische und-Zeichen (&) sind als Markupzeichen behandelt. Sie können diese Sonderzeichen in einem CDATA-Abschnitt jedoch umschließen, um zu verhindern, dass sie als Markupzeichen behandelt werden. Der Text innerhalb des CDATA-Abschnitts wird vom XML-Parser als Nur-Text behandelt.  
  
 Mit der `sql:use-cdata`-Anmerkung wird angegeben, dass die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegebenen Daten in einem CDATA-Abschnitt umschlossen werden (d. h., sie gibt an, ob der Wert aus einer Spalte, die von `sql:field` angegeben wird, in einem CDATA-Abschnitt eingeschlossen werden soll). Die `sql:use-cdata`-Anmerkung kann nur für Elemente angegeben werden, die einer Datenbankspalte zugeordnet werden.  
  
 Die `sql:use-cdata`-Anmerkung akzeptiert einen booleschen Wert (0 = false und 1 = true). Zulässig sind die Werte 0, 1, true und false.  
  
 Diese Anmerkung kann nicht mit `sql:url-encode` oder für die Attributtypen ID, IDREF, IDREFS, NMTOKEN und NMTOKENS verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>A. Angeben von sql:use-cdata für ein Element  
 Im folgenden Schema `sql:use-cdata` auf 1 (True) festgelegt ist, die für die  **\<AddressLine1 >** innerhalb der  **\<Adresse >** Element. Daraufhin werden die Daten in einem CDATA-Abschnitt zurückgegeben.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine Beispiel-XPath-Abfrage anhand des Schemas  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UseCData.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen UseCDataT.xml im gleichen Verzeichnis, in dem Sie UseCData.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungschema (UseCData.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
