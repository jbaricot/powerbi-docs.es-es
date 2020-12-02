---
title: Conectarse a los datos mediante las interfaces genéricas de Power BI Desktop
description: Información sobre cómo conectarse a distintos orígenes de datos con las interfaces genéricas de Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: b7e0ec270ad70be91d5aea598148e69e88df09f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405569"
---
# <a name="connect-to-data-by-using-power-bi-desktop-generic-interfaces"></a>Conexión a datos mediante las interfaces genéricas de Power BI Desktop 

**Power BI Desktop** permite conectarse a un gran número de orígenes de datos distintos gracias a los conectores de datos que lleva integrados, como por ejemplo las **bases de datos de Access** y los recursos de **Zendesk**, tal como se puede ver en la ventana **Obtener datos**. También es posible conectarse a muchos *otros* tipos de orígenes de datos a través de las interfaces genéricas (como **ODBC** o **API de REST**) integradas en **Power BI Desktop**, con lo que se amplían aún más las opciones de conectividad.

![Captura de pantalla del cuadro de diálogo Obtener datos en el que se muestra la selección de ODBC.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_1.png)

## <a name="power-bi-desktop-data-interfaces"></a>Interfaces de datos de Power BI Desktop
**Power BI Desktop** incluye una colección cada vez mayor de conectores de datos cuya finalidad es establecer conexión con un origen de datos específico. Por ejemplo, durante la secuencia de conexión, el conector de datos **Lista de SharePoint** proporciona campos específicos e información complementaria que están diseñados para **Listas de SharePoint**, que es lo que ocurre con otros orígenes de datos que se muestran en la ventana que aparece al seleccionar **Obtener datos > Más...** , como figura en la imagen anterior.

Además, **Power BI Desktop** permite usar una de las interfaces de datos genéricas enumeradas a continuación para conectarse a orígenes de datos que no aparecen en las listas de la ventana **Obtener datos**:

* **ODBC**
* **OLE DB**
* **OData**
* **API de REST**
* **Script de R**

Si se proporcionan los parámetros adecuados en las ventanas de conexión facilitadas por estas interfaces genéricas, el mundo de los orígenes de datos a los que se puede obtener acceso y que se pueden usar en **Power BI Desktop** se amplía de manera significativa.

En las secciones siguientes encontrará listas de orígenes de datos a los que se puede acceder con estas interfaces genéricas.

Si no encuentra el origen de datos que desea usar con **Power BI Desktop**, envíe su idea a la [lista de ideas y solicitudes](https://ideas.powerbi.com/) del equipo de Power BI.

## <a name="data-sources-accessible-through-odbc"></a>Orígenes de datos accesibles a través de ODBC
El conector **ODBC** en **Power BI Desktop** permite importar datos desde cualquier controlador ODBC de terceros con simplemente especificar un **Nombre de origen de datos (DSN)** o una *cadena de conexión*. También hay la opción de especificar una instrucción SQL para que se ejecute en el controlador ODBC.

![Captura de pantalla del cuadro de diálogo del conector ODBC, en el que se muestran las opciones DNS y Avanzado.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_2.png)

En la lista siguiente se detallan algunos ejemplos de orígenes de datos a los que **Power BI Desktop** se puede conectar mediante la interfaz genérica **ODBC**.

| Conector genérico de Power BI Desktop | Origen de datos externo | Vínculo para más información |
| --- | --- | --- |
| ODBC |Cassandra |[Controlador ODBC de Cassandra](https://www.simba.com/drivers/cassandra-odbc-jdbc/) |
| ODBC |Couchbase DB |[Couchbase y Power BI](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |
| ODBC |DynamoDB |[Controlador ODBC de DynamoDB](https://www.simba.com/drivers/dynamodb-odbc-jdbc/) |
| ODBC |Google BigQuery |[Controlador ODBC de BigQuery](https://www.simba.com/drivers/bigquery-odbc-jdbc/) |
| ODBC |HBase |[Controlador ODBC de HBase](https://www.simba.com/drivers/hbase-odbc-jdbc/) |
| ODBC |Hive |[Controlador ODBC de Hive](https://www.simba.com/drivers/hive-odbc-jdbc/) |
| ODBC |IBM Netezza |[Información de IBM Netezza](https://www.ibm.com/support/knowledgecenter/SSULQD_7.2.1/com.ibm.nz.datacon.doc/c_datacon_plg_overview.html) |
| ODBC |Presto |[Controlador ODBC de Presto](https://www.simba.com/drivers/presto-odbc-jdbc/) |
| ODBC |Project Online |[Artículo sobre Project Online](desktop-project-online-connect-to-data.md) |
| ODBC |Progress OpenEdge |[Entrada de blog sobre el controlador ODBC Progress OpenEdge](https://www.progress.com/blogs/connect-microsoft-power-bi-to-openedge-via-odbc-driver) |

## <a name="data-sources-accessible-through-ole-db"></a>Orígenes de datos accesibles a través de OLE DB
El conector **OLE DB** en **Power BI Desktop** permite importar datos desde cualquier controlador OLE DB de terceros con simplemente especificar una *cadena de conexión*. También hay la opción de especificar una instrucción SQL para que se ejecute en el controlador OLE DB.

![Captura de pantalla del cuadro de diálogo del conector OLE DB, en el que se muestran la cadena de conexión y las opciones avanzadas.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_3.png)

En la lista siguiente se detallan algunos ejemplos de orígenes de datos a los que **Power BI Desktop** se puede conectar mediante la interfaz genérica **OLE DB**.

| Conector genérico de Power BI Desktop | Origen de datos externo | Vínculo para más información |
| --- | --- | --- |
| OLE DB |SAS OLE DB |[Proveedor SAS para OLE DB](https://support.sas.com/downloads/package.htm?pid=648) |
| OLE DB |Sybase OLE DB |[Proveedor Sybase para OLE DB](http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.infocenter.dc35888.1550/doc/html/jon1256941734395.html) |

## <a name="data-sources-accessible-through-odata"></a>Orígenes de datos accesibles a través de OData
El conector **OData** en **Power BI Desktop** permite importar datos desde cualquier dirección URL de **OData** con simplemente escribir o pegar la URL de **OData**. Es posible agregar varias partes de la dirección URL. Para ello, basta con escribir o pegar esos vínculos en los cuadros de texto de la ventana **Fuente OData**.

![Captura de pantalla del cuadro de diálogo Fuente OData, en el que se muestran los campos Partes de la URL y Vista previa de la URL.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_4.png)

En la lista siguiente se detallan algunos ejemplos de orígenes de datos a los que **Power BI Desktop** se puede conectar mediante la interfaz genérica **OData**.

| Conector genérico de Power BI Desktop | Origen de datos externo | Vínculo para más información |
| --- | --- | --- |
| OData |Próximamente |Comprobar próximamente orígenes de datos OData |

## <a name="data-sources-accessible-through-rest-apis"></a>Orígenes de datos accesibles a través de las API de REST
La conexión a orígenes de datos mediante las **API de REST** permite usar la información de todo tipo de orígenes de datos que admiten **REST**.

![Captura de pantalla del cuadro de diálogo Consulta en el que se muestran los orígenes de datos.](media/desktop-connect-using-generic-interfaces/generic-data-interfaces_5.png)

En la lista siguiente se detallan algunos ejemplos de orígenes de datos a los que **Power BI Desktop** se puede conectar mediante la interfaz genérica **API de REST**.

| Conector genérico de Power BI Desktop | Origen de datos externo | Vínculo para más información |
| --- | --- | --- |
| API de REST |Couchbase DB |[Información sobre la API de REST de Couchbase](https://powerbi.microsoft.com/blog/visualizing-data-from-couchbase-server-v4-using-power-bi/) |

## <a name="data-sources-accessible-through-r-script"></a>Orígenes de datos accesibles a través de scripts de R
Los **scripts de R** se pueden usar para tener acceso a orígenes de datos y utilizar esos datos en **Power BI Desktop**.

![Captura de pantalla del cuadro de diálogo Script de R, donde se muestra el script de ejecución.](media/desktop-connect-using-generic-interfaces/r-scripts-2.png)

En la lista siguiente se detallan algunos ejemplos de orígenes de datos a los que **Power BI Desktop** se puede conectar mediante la interfaz genérica **Scripts de R**.

| Conector genérico de Power BI Desktop | Origen de datos externo | Vínculo para más información |
| --- | --- | --- |
| Script R |Archivos SAS |[Instrucciones de script de R de CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| Script R |Archivos SPSS |[Instrucciones de script de R de CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |
| Script R |Archivos estadísticos de R |[Instrucciones de script de R de CRAN](https://cran.r-project.org/doc/manuals/R-data.html) |

## <a name="next-steps"></a>Pasos siguientes
Con **Power BI Desktop** puede conectarse a todo tipo de orígenes de datos. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
