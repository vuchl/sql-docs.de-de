---
title: Arbeiten mit Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 306b227a4b193811c7207f111fc35a48148e4bbf
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37228920"
---
# <a name="working-with-data-types"></a>Arbeiten mit Datentypen
  Daten sind in vielen Typen und Größen verfügbar, beispielsweise als Zeichenfolge mit einer definierten Länge, als Zahl mit einer bestimmten Genauigkeit oder als benutzerdefinierter Datentyp, bei dem es sich um ein anderes Objekt mit einem eigenen Satz an Regeln handelt. Die <xref:Microsoft.SqlServer.Management.Smo.DataType> -Objekt klassifiziert den Typ der Daten, damit sie ordnungsgemäß von verarbeitet werden kann [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Das <xref:Microsoft.SqlServer.Management.Smo.DataType>-Objekt ist Objekten zugeordnet, die Daten akzeptieren. Die folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)-Objekte akzeptieren Daten, die von definiert werden, müssen ein <xref:Microsoft.SqlServer.Management.Smo.DataType> -Objekteigenschaft:  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 Die `DataType`-Eigenschaft für Objekte, die Daten akzeptieren, kann auf unterschiedliche Weise festgelegt werden.  
  
-   Verwenden Sie den Standardkonstruktor und geben <xref:Microsoft.SqlServer.Management.Smo.DataType> -Objekteigenschaften explizit  
  
-   Verwenden Sie einen überladenen Konstruktor, und geben Sie die <xref:Microsoft.SqlServer.Management.Smo.DataType> -Eigenschaften als Parameter.  
  
-   Geben Sie die <xref:Microsoft.SqlServer.Management.Smo.DataType> Inline im Objektkonstruktor.  
  
-   Verwenden Sie eines der statischen Elemente der <xref:Microsoft.SqlServer.Management.Smo.DataType>-Klasse, zum Beispiel `Int`. In diesem Fall wird eine Instanz eines <xref:Microsoft.SqlServer.Management.Smo.DataType>-Objekts zurückgegeben.  
  
 Das <xref:Microsoft.SqlServer.Management.Smo.DataType>-Objekt verfügt über einige Eigenschaften, die den Datentyp definieren. Beispielsweise gibt die <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>-Eigenschaft den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp an. Die Konstanten Werte, die darstellen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen finden Sie in der <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> Enumeration. Dies gilt für Datentypen wie `varchar`, `nchar`, `currency`, `integer`, `float` und `datetime`.  
  
 Nachdem der Datentyp definiert wurde, müssen bestimmte Eigenschaften für die Daten festgelegt werden. Beispielsweise muss bei einem `nchar`-Typ die Länge der Zeichenfolgenddaten mit der `Length`-Eigenschaft angegeben werden. Das Gleiche gilt für numerische Werte, für die Genauigkeit und Dezimalstellenanzahl angegeben werden muss.  
  
 Der <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>-Datentyp und der <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>-Datentyp beziehen sich auf Objekte, die die Definition des vom Benutzer definierten Datentyps enthalten. <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> basiert auf den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen aus der <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>-Enumeration. Die <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> basiert auf [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET-Datentypen. In der Regel würden diese Daten eines bestimmten Typs darstellen, der wegen der von der Organisation definierten Geschäftsregeln in der Datenbank häufig verwendet wird. Beispielsweise wäre ein Datentyp, mit dem ein Währungsbetrag und ein Währungsbezeichner gespeichert wird, für eine Firma hilfreich, die mit mehreren Währungen arbeitet.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> -Enumeration enthält eine Liste aller der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-unterstützten Datentypen.  
  
## <a name="examples"></a>Beispiele  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Konstruktion eines DataType-Objekts mit der Spezifikation im Konstruktor in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie den Konstruktor zu verwenden, um Instanzen von Datentypen zu erstellen, die auf anderen basieren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> und die XML-Typen erfordern einen Namenswert zur Identifizierung des Objekts.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes1](SMO How to#SMO_VBDataTypes1)]  -->  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Konstruktion eines DataType-Objekts mit der Spezifikation im Konstruktor in Visual C#  
 Dieses Codebeispiel zeigt, wie Sie den Konstruktor zu verwenden, um Instanzen von Datentypen zu erstellen, die auf anderen basieren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen.  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> und die XML-Typen erfordern einen Namenswert zur Identifizierung des Objekts.  
  
```  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguements specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Konstruktion eines DataType-Objekts mithilfe des Standardkonstruktors in Visual Basic  
 Dieses Codebeispiel zeigt, wie Sie den Standardkonstruktor verwenden, um Instanzen von Datentypen zu erstellen, die auf anderen basieren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen. Mithilfe der Eigenschaften wird der Datentyp dann angegeben.  
  
 **Beachten Sie** der <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, und die XML-Typen erfordern einen Namenswert zur Identifizierung des Objekts.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDataTypes2](SMO How to#SMO_VBDataTypes2)]  -->  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Konstruktion eines DataType-Objekts mithilfe des Standardkonstruktors in Visual C#  
 Dieses Codebeispiel zeigt, wie Sie den Standardkonstruktor verwenden, um Instanzen von Datentypen zu erstellen, die auf anderen basieren [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentypen. Mithilfe der Eigenschaften wird der Datentyp dann angegeben.  
  
 **Beachten Sie** der <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, und die XML-Typen erfordern einen Namenswert zur Identifizierung des Objekts.  
  
```  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
