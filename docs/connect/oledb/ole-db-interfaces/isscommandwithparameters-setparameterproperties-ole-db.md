---
title: 'Isscommandwithparameters:: SetParameterProperties (OLE DB) | Microsoft-Dokumentation'
description: "'ISSCommandWithParameters::SetParameterProperties' (OLE DB)"
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters::SetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- SetParameterProperties method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 6d20214d99a9f1b4f9be28be967fb54023057536
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033638"
---
# <a name="isscommandwithparameterssetparameterproperties-ole-db"></a>'ISSCommandWithParameters::SetParameterProperties' (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Legt die Parametereigenschaften für einzelne Parameter nach Ordnungszahl fest oder legt Massenparametereigenschaften durch Angabe eines Arrays von SSPARAMPROPS-Strukturen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
HRESULT SetParameterProperties(  
      DB_UPARAMS cParams,   
      SSPARAMPROPS rgParamProperties[]);  
```  
  
## <a name="arguments"></a>Argumente  
 *cParams*[in]  
 Die Anzahl der SSPARAMPROPS-Strukturen im *rgParamProperties*-Array. Wenn diese Anzahl 0 ist, löscht **ISSCommandWithParameters::SetParameterProperties** alle Eigenschaften, die für Parameter im Befehl möglicherweise festgelegt wurden.  
  
 *rgParamProperties*[in]  
 Ein Array von SSPARAMPROPS-Strukturen, die festgelegt werden sollen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Die **ISSCommandWithParameters::SetParameterProperties**-Methode gibt die gleichen Fehlercodes wie die OLE DB-Kernmethode **ICommandProperties::SetProperties** zurück.  
  
## <a name="remarks"></a>Remarks  
 Das Festlegen von Parametereigenschaften mit dieser Methode ist auf Einzelparameterbasis nach Ordnungszahl oder mit einem einzelnen **ISSCommandWithParameters::SetParameterProperties**-Aufruf zulässig, sobald SSPARAMPROPS aus dem Eigenschaftenarray aufgebaut wurde.  
  
 Die **SetParameterInfo**-Methode muss aufgerufen werden, bevor die **ISSCommandWithParameters::SetParameterProperties**-Methode aufgerufen wird. Durch Aufrufen von `SetParameterProperties(0, NULL)` werden alle angegebenen Parametereigenschaften gelöscht, während der Aufruf von `SetParameterInfo(0,NULL,NULL)` alle Parameterinformationen löscht, einschließlich Eigenschaften, die einem Parameter zugeordnet sind.  
  
 Durch Aufrufen von **ISSCommandWithParameters::SetParameterProperties** zum Festlegen von Eigenschaften für einen Parameter, der nicht dem Typ DBTYPE_XML oder DBTYPE_UDT entspricht, wird DB_E_ERRORSOCCURRED oder DB_S_ERRORSOCCURRED zurückgegeben und das *dwStatus*-Feld aller in SSPARAMPROPS enthaltenen DBPROPs für diesen Parameter mit DBPROPSTATUS_NOTSET markiert. Das DBPROP-Array jedes in SSPARAMPROPS enthaltenen DBPROPs sollte durchsucht werden, um zu ermitteln, auf welchen Parameter DB_E_ERRORSOCCURRED bzw. DB_S_ERRORSOCCURRED verweist.  
  
 Wenn **ISSCommandWithParameters::SetParameterProperties** aufgerufen wird, um die Eigenschaften von Parametern anzugeben, deren Parameterinformationen noch nicht mit **SetParameterInfo** festgelegt wurden, gibt der Anbieter E_UNEXPECTED mit der folgenden Fehlermeldung zurück:  
  
 Die SetParameterProperties-Methode kann für die angegebenen Parameter nicht aufgerufen werden, ohne dass zunächst die SetParameterInfo-Methode aufgerufen wird. Die Parameterinformationen müssen vor dem Festlegen der Parametereigenschaften festgelegt werden.  
  
 Wenn der Aufruf für **ISSCommandWithParameters::SetParameterProperties** einige Parameter enthält, für die die Parameterinformationen festgelegt wurden, und einige Parameter ohne Parameterinformationen, werden die dwStatus-Eigenschaften im DBPROPSET des SSPARAMPROPS-Eigenschaftensatzes mit DBSTATUS_NOTSET zurückgegeben.  
  
 Die SSPARAMPROPS-Struktur ist folgendermaßen definiert:  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
 Verbesserungen in der Datenbank-Engine ab [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] isscommandwithparameters:: SetParameterProperties, genauere Beschreibungen der erwarteten Ergebnisse abrufen können. Diese genaueren Ergebnisse unterscheiden sich möglicherweise aus den Werten von isscommandwithparameters:: SetParameterProperties zurückgegeben wird, in früheren Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../../oledb/features/metadata-discovery.md).  
  
|Member|und Beschreibung|  
|------------|-----------------|  
|*iOrdinal*|Die Ordnungszahl des übergebenen Parameters|  
|*cPropertySets*|Die Anzahl von DBPROPSET-Strukturen in *rgPropertySets*|  
|*rgPropertySets*|Ein Zeiger auf den Speicher, in den ein Array aus DBPROPSET-Strukturen zurückgegeben werden soll|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [ISSCommandWithParameters &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
