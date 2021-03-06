---
title: Erstellen, Aufbauen und Abfragen von geography-Instanzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server]
- geodetic data type [SQL Server]
- geography data type [SQL Server], about geography data type
ms.assetid: b585851e-d15b-411f-adeb-aeabeb777c0b
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea4dc0a27743e62f0a13f866895cd7fe0ed0ae79
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37284716"
---
# <a name="create-construct-and-query-geography-instances"></a>Erstellen, Aufbauen und Abfragen von geography-Instanzen
  Der räumliche `geography`-Datentyp stellt Daten in einem Erdkugel-Koordinatensystem dar. Dieser Datentyp wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]als .NET CLR-Datentyp (Common Language Runtime) implementiert. Der `geography`-Datentyp in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert ellipsenähnliche (Erdkugel-)Daten, wie z. B. GPS-Breiten- und Längenkoordinaten.  
  
 Die `geography` -Typ ist vordefiniert und in jeder Datenbank verfügbar. Sie können Tabellenspalten des `geography`-Typs in der gleichen Weise erstellen und `geography`-Daten in der gleichen Weise verwenden wie andere vom System bereitgestellte Typen.  
  
##  <a name="creating"></a> Erstellen einer neuen geography-Instanz  
  
###  <a name="existing"></a> Erstellen einer neuen geography-Instanz anhand einer vorhandenen Instanz  
 Die `geography` -Datentyp stellt zahlreiche integrierte Methoden zum Erstellen von neuen können `geography` Instanzen auf Grundlage vorhandener Instanzen.  
  
 **So erstellen Sie einen Puffer um eine geography**  
 [STBuffer &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stbuffer-geography-data-type)  
  
 **So erstellen Sie einen Puffer um eine Geografie mit einer Toleranz**  
 [BufferWithTolerance &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/bufferwithtolerance-geography-data-type)  
  
 **So erstellen Sie eine geography-Instanz aus der Schnittmenge von zwei geography-Instanzen**  
 [STIntersection &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **So erstellen Sie eine geography-Instanz aus der Vereinigung von zwei geography-Instanzen**  
 [STUnion &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stunion-geography-data-type)  
  
 **So erstellen Sie eine Geografie aus Punkten ohne überlappende Geografien**  
 [STDifference &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
###  <a name="wkt"></a> Erstellen einer geography-Instanz anhand einer WKT-Eingabe (Well-Known Text)  
 Die `geography` -Datentyp bietet mehrere integrierte Methoden, die eine geography-Instanz aus der Open Geospatial Consortium (OGC) WKT-Darstellung zu generieren. Der WKT-Standard ist eine Textzeichenfolge, die den Austausch von Geografiedaten in Textform ermöglicht.  
  
 **So erstellen Sie einen beliebigen geography-Instanztyp anhand einer WKT-Eingabe**  
 [STGeomFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomfromtext-geography-data-type)  
  
 [Parse &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/parse-geography-data-type)  
  
 **So erstellen Sie eine Point-geography-Instanz anhand einer WKT-Eingabe**  
 [STPointFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpointfromtext-geography-data-type)  
  
 **So erstellen Sie eine MultiPoint-geography-Instanz anhand einer WKT-Eingabe**  
 [STMPointFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpointfromtext-geography-data-type)  
  
 **So erstellen Sie eine LineString-geography-Instanz anhand einer WKT-Eingabe**  
 STLineFromText (geography-Datentyp)  
  
 **So erstellen Sie eine MultiLineString-geography-Instanz anhand einer WKT-Eingabe**  
 [STMLineFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmlinefromtext-geography-data-type)  
  
 **So erstellen Sie eine Polygon-geography-Instanz anhand einer WKT-Eingabe**  
 [STPolyFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpolyfromtext-geography-data-type)  
  
 **So erstellen Sie eine MultiPolygon-geography-Instanz anhand einer WKT-Eingabe**  
 [STMPolyFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpolyfromtext-geography-data-type)  
  
 **So erstellen Sie eine GeometryCollection-geography-Instanz anhand einer WKT-Eingabe**  
 [STGeomCollFromText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomcollfromtext-geography-data-type)  
  
###  <a name="wkb"></a> Erstellen einer geography-Instanz aus einer WKB-Eingabe (Well-Known Binary)  
 WKB ist ein Binärformat, das vom OGC, die erlaubt `Geography` Daten zwischen einer Clientanwendung und einer SQL-Datenbank ausgetauscht werden. Die folgenden Funktionen akzeptieren die WKB-Eingabe zum Zweck der Erstellung von geography-Instanzen:  
  
 **So erstellen Sie einen beliebigen geography-Instanztyp anhand einer WKB-Eingabe**  
 [STGeomFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomfromwkb-geography-data-type)  
  
 **So erstellen Sie eine Point-geography-Instanz anhand einer WKB-Eingabe**  
 [STPointFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpointfromwkb-geography-data-type)  
  
 **So erstellen Sie eine MultiPoint-geography-Instanz anhand einer WKB-Eingabe**  
 [STMPointFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpointfromwkb-geography-data-type)  
  
 **So erstellen Sie eine LineString-geography-Instanz anhand einer WKB-Eingabe**  
 [STLineFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stlinefromwkb-geography-data-type)  
  
 **So erstellen Sie eine MultiLineString-geography-Instanz anhand einer WKB-Eingabe**  
 [STMLineFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmlinefromwkb-geography-data-type)  
  
 **So erstellen Sie eine Polygon-geography-Instanz anhand einer WKB-Eingabe**  
 [STPolyFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stpolyfromwkb-geography-data-type)  
  
 **So erstellen Sie eine MultiPolygon-geography-Instanz anhand einer WKB-Eingabe**  
 [STMPolyFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stmpolyfromwkb-geography-data-type)  
  
 **So erstellen Sie eine GeometryCollection-geography-Instanz anhand einer WKB-Eingabe**  
 [STGeomCollFromWKB &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeomcollfromwkb-geography-data-type)STGeomCollFromWKB (geography-Datentyp)  
  
###  <a name="gml"></a> Erstellen einer geography-Instanz anhand einer GML-Texteingabe  
 Die `geography` -Datentyp stellt eine Methode eine `geography` -Instanz aus GML bereit, eine XML-Darstellung einer `geography` Instanz. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt eine Teilmenge von GML.  
  
 Weitere Informationen über Geography Markup Language finden Sie in der OGC-Spezifikation: [OGC Specifications, Geography Markup Language.](http://go.microsoft.com/fwlink/?LinkId=93629)  
  
 **So erstellen Sie einen beliebigen geography-Instanztyp anhand einer GML-Eingabe**  
 [GeomFromGML &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/geomfromgml-geography-data-type)  
  
##  <a name="returning"></a> Zurückgeben von WKT (Well-Known Text) oder WKB (Well-Known Binary) von einer geography-Instanz  
 Sie können die folgenden Methoden verwenden, entweder das WKT- oder WKB-Format der zurückzugebenden eine `geography` Instanz:  
  
 **So geben Sie die WKT-Darstellung einer geography-Instanz zurück**  
 [STAsText &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stastext-geography-data-type)  
  
 [ToString &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/tostring-geography-data-type)  
  
 **So geben Sie eine WKT-Darstellung einer geography-Instanz einschließlich Z- und M-Werten zurück**  
 [AsTextZM &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/astextzm-geography-data-type)  
  
 **So geben Sie die WKB-Darstellung einer geography-Instanz zurück**  
 [STAsBinary &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stasbinary-geography-data-type)  
  
 **So geben Sie eine GML-Darstellung einer geography-Instanz zurück**  
 [AsGml &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/asgml-geography-data-type)  
  
##  <a name="query"></a> Abfragen von Eigenschaften und Verhalten von geography-Instanzen  
 Alle `geography` Instanzen haben eine Reihe von Eigenschaften, die über Methoden abgerufen werden können, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält. In den folgenden Themen werden die Eigenschaften und Verhalten von geography-Typen und die Methoden zum Abrufen der einzelnen Eigenschaften und Verhalten beschrieben.  
  
###  <a name="valid"></a> Gültigkeit, Instanztyp und GeometryCollection-Informationen  
 Nach einer `geography` -Instanz erstellt wurde, können Sie die folgenden Methoden den Instanztyp zurückgeben oder ist eine `GeometryCollection` Instanz, die einen bestimmten zurückgeben `geography` Instanz.  
  
 **So geben Sie den Instanztyp einer Geografie zurück**  
 [STGeometryType &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeometrytype-geography-data-type)  
  
 **So bestimmen Sie, ob eine Geografie einen gegebenen Instanztyp aufweist**  
 [InstanceOf &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/instanceof-geography-data-type)  
  
 **So bestimmen Sie, ob eine geography-Instanz für ihren Instanztyp wohlgeformt ist**  
 [STNumGeometries &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stnumgeometries-geography-data-type)  
  
 **So geben Sie eine bestimmte Geografie in einer GeometryCollection-Instanz zurück**  
 [STGeometryN &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stgeometryn-geography-data-type)STGeometryN (geography-Datentyp)  
  
###  <a name="number"></a> Anzahl von Punkten  
 Alle nicht leeren `geography` -Instanzen bestehen *Punkte*. Diese Punkte stellen den Längengrad und den Breitengrad der Erde dar, auf die die `geography`-Instanzen gezeichnet werden. Der Datentyp `geography` stellt zahlreiche integrierte Methoden bereit zum Abfragen der Punkte einer Instanz.  
  
 **So geben Sie die Anzahl von Punkten zurück, aus denen eine Instanz besteht**  
 [STNumPoints &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stnumpoints-geography-data-type)  
  
 **So geben Sie einen bestimmten Punkt einer Instanz zurück**  
 [STPointN &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)  
  
 **So geben Sie den Ausgangspunkt einer Instanz zurück**  
 [STStartPoint &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/ststartpoint-geography-data-type)  
  
 **So geben Sie den Endpunkt einer Instanz zurück**  
 [STEndpoint &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stendpoint-geography-data-type)  
  
###  <a name="dimension"></a> Dimension  
 Einen nicht leeren `geography` Instanz möglich 0-1-, oder 2-dimensionalen. Nulldimensionale `geography` Instanzen, z. B. `Point` und `MultiPoint`, haben weder Länge noch Fläche. Eindimensionale Objekte (z. B. `LineString, CircularString`, `CompoundCurve` und `MultiLineString`) weisen eine Länge auf. Zweidimensionale Instanzen, z. B. `Polygon, CurvePolygon`, und `MultiPolygon`, haben Fläche und Länge. Für leere Instanzen wird als Dimension -1 ausgegeben, und für eine `GeometryCollection`-Auflistung wird die maximale Dimension der darin enthaltenen Elemente zurückgegeben.  
  
 **So geben Sie die Dimension einer Instanz zurück**  
 [STDimension &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stdimension-geography-data-type)  
  
 **So geben Sie die Länge einer Instanz zurück**  
 [STLength &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stlength-geography-data-type)  
  
 **So geben Sie die Fläche einer Instanz zurück**  
 [STArea &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/starea-geography-data-type)  
  
###  <a name="empty"></a> Empty  
 Ein *leere* `geography` -Instanz besitzt keine Punkte. Die Länge von leeren `LineString, CircularString`-, `CompoundCurve`- und `MultiLineString`-Instanzen ist 0 (null). Die Fläche von leeren `Polygon, CurvePolygon` und `MultiPolygon` -Instanzen ist 0.  
  
 **So bestimmen Sie, ob eine Instanz leer ist**  
 [STIsEmpty &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stisempty-geography-data-type)  
  
###  <a name="closure"></a> Abgeschlossenheit  
 Ein *geschlossen* `geography` -Instanz ist eine Abbildung, deren Ausgangs- und Endpunkte identisch. `Polygon` -Instanzen gelten als geschlossen. Alle `Point`-Instanzen gelten als nicht geschlossen.  
  
 Ein Ring ist eine einfache, geschlossen `LineString` Instanz.  
  
 **So bestimmen Sie, ob eine Instanz abgeschlossen ist**  
 [STIsClosed &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stisclosed-geography-data-type)  
  
 **So geben Sie die Anzahl von Ringen in einer Polygoninstanz zurück**  
 [NumRings &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/numrings-geography-data-type)  
  
 **So geben Sie einen gegebenen Ring einer geography-Instanz zurück**  
 [RingN &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/ringn-geography-data-type)  
  
###  <a name="srid"></a> SRID (Spatial Reference ID)  
 Spatial Reference ID (SRID) ist ein Bezeichner, der ellipsenförmige Koordinatensystem angibt, die `geography` -Instanz dargestellt wird. Zwei `geography`-Instanzen mit unterschiedlichen SRIDs können nicht verglichen werden.  
  
 **So können Sie die SRID einer Instanz festlegen oder zurückgeben**  
 [STSrid &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stsrid-geography-data-type)  
  
 Diese Eigenschaft kann geändert werden.  
  
##  <a name="rel"></a> Bestimmen von Beziehungen zwischen geography-Instanzen  
 Die `geography` -Datentyp stellt viele integrierte Methoden Sie bestimmen von Beziehungen zwischen zwei können `geography` Instanzen.  
  
 **So bestimmen Sie, ob zwei Instanzen die gleiche Punktmenge umfassen**  
 [STEquals &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stequals-geometry-data-type)  
  
 **So bestimmen Sie, ob zwei Instanzen disjunkt sind**  
 [STDisjoint &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stdisjoint-geometry-data-type)  
  
 **So bestimmen Sie, ob sich zwei Instanzen überschneiden**  
 [STIntersects &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stintersects-geometry-data-type)  
  
 **So bestimmen Sie den Punkt bzw. die Punkte, an dem bzw. denen sich zwei Instanzen überschneiden**  
 [STIntersection &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stintersection-geography-data-type)  
  
 **So bestimmen Sie die kürzeste Entfernung zwischen Punkten in zwei geography-Instanzen**  
 [STDistance &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stdistance-geometry-data-type)  
  
 **So bestimmen Sie zwischen zwei geography-Instanzen bestehende die Differenz in Punkten**  
 [STDifference &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stdifference-geography-data-type)  
  
 **So leiten Sie die symmetrische Differenz oder eindeutigen Punkte einer geography-Instanz ab, die mit einer anderen Instanz verglichen wird**  
 [STSymDifference &#40;geography-Datentyp&#41;](/sql/t-sql/spatial-geography/stsymdifference-geography-data-type)  
  
##  <a name="supportedsrid"></a> geography-Instanzen müssen unterstützte SRIDs verwenden  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt SRIDs auf der Grundlage der EPSG-Standards. Wenn Berechnungen mit geografischen räumlichen Daten ausgeführt werden oder Methoden mit geografischen räumlichen Daten verwendet werden, müssen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützte SRIDs für `geography`-Instanzen verwendet werden. Die SRID muss mit einer der SRIDs übereinstimmen, die in der **sys.spatial_reference_systems** -Katalogsicht angezeigt werden. Wie bereits erwähnt, wenn Sie Berechnungen mit räumlichen Daten unter Verwendung der `geography` -Datentyp, die Ergebnisse hängt von der Ellipsenform, bei der Erstellung Ihrer Daten verwendet wurde, da jeder Ellipsenform ein bestimmter Bezeichner (zugeordnet ist SRID).  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird beim Einsatz von Methoden für `geography`-Instanzen standardmäßig der SRID 4326 verwendet, der dem räumlichen Referenzsystem WGS 84 zugeordnet ist. Wenn Sie Daten aus einem anderen räumlichen Referenzsystem als WGS 84 (bzw. SRID 4326) verwenden, müssen Sie die SRID dieser geografischen räumlichen Daten bestimmen.  
  
##  <a name="examples"></a> Beispiele  
 Die folgenden Beispiele zeigen, wie Geografiedaten hinzugefügt und abgefragt werden.  
  
-   Im ersten Beispiel wird eine Tabelle mit einer Identitätsspalte und der `geography` -Spalte `GeogCol1`erstellt. Eine dritte Spalte rendert die `geography` -Spalte als Darstellung im Open Geospatial Consortium (OGC) WKT-Format und verwendet die `STAsText()` -Methode. Dann werden zwei Zeilen eingefügt: Eine Zeile enthält eine `LineString` -Instanz des Typs `geography`und die andere eine `Polygon` -Instanz.  
  
    ```  
    IF OBJECT_ID ( 'dbo.SpatialTable', 'U' ) IS NOT NULL   
        DROP TABLE dbo.SpatialTable;  
    GO  
  
    CREATE TABLE SpatialTable   
        ( id int IDENTITY (1,1),  
        GeogCol1 geography,   
        GeogCol2 AS GeogCol1.STAsText() );  
    GO  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326));  
  
    INSERT INTO SpatialTable (GeogCol1)  
    VALUES (geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326));  
    GO  
    ```  
  
-   Im zweiten Beispiel werden mithilfe der `STIntersection()` -Methode die Punkte zurückgegeben, an denen die beiden zuvor eingegebenen `geography` -Instanzen sich schneiden.  
  
    ```  
    DECLARE @geog1 geography;  
    DECLARE @geog2 geography;  
    DECLARE @result geography;  
  
    SELECT @geog1 = GeogCol1 FROM SpatialTable WHERE id = 1;  
    SELECT @geog2 = GeogCol1 FROM SpatialTable WHERE id = 2;  
    SELECT @result = @geog1.STIntersection(@geog2);  
    SELECT @result.STAsText();  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Räumliche Daten &#40;SQL Server&#41;](spatial-data-sql-server.md)  
  
  
