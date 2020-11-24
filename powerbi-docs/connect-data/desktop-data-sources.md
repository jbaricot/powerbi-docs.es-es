---
title: Orígenes de datos en Power BI Desktop
description: Orígenes de datos en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 11/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 143d4a51a403563b337c753055fa56e9c25edc26
ms.sourcegitcommit: 029aacd09061a8aa45b57f05d0dc95c93dd16a74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2020
ms.locfileid: "94560043"
---
# <a name="data-sources-in-power-bi-desktop"></a>Orígenes de datos en Power BI Desktop

Power BI Desktop permite conectarse a datos de muchos orígenes diferentes. Para obtener una lista completa de los orígenes de datos disponibles, vea [Orígenes de datos de Power BI](power-bi-data-sources.md).

Use la cinta de opciones **Inicio** para conectarse a los datos. Para mostrar el menú de los tipos de datos **Más comunes**, seleccione la etiqueta del botón **Obtener datos** o la flecha abajo.

![Menú de los tipos de datos Más comunes, Obtener datos en Power BI Desktop](media/desktop-data-sources/data-sources-01.png)

Para ir al cuadro de diálogo **Obtener datos**, muestre el menú de los tipos de datos **Más comunes** y seleccione **Más**. Puede abrir el cuadro de diálogo **Obtener datos** (y omitir el menú **Más comunes**) si selecciona directamente el icono **Obtener datos**.

![Botón Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> El equipo de Power BI está ampliando continuamente los orígenes de datos disponibles en Power BI Desktop y en el servicio Power BI. Por lo tanto, a menudo verá las versiones anteriores de orígenes de datos en proceso de desarrollo marcados como **Beta** o **Versión preliminar**. Cualquier origen de datos marcada como **Beta** o **Versión preliminar** tiene una compatibilidad y funcionalidades limitadas y no se debe usar en entornos de producción. Además, es posible que los orígenes de datos marcados como **Beta** o **Versión preliminar** para Power BI Desktop no estén disponibles para su uso en el servicio Power BI u otros servicios de Microsoft hasta que el origen de datos esté disponible con carácter general (GA).

> [!NOTE]
> Hay muchos conectores de datos para Power BI Desktop que requieren Internet Explorer 10 (o posterior) para la autenticación. 


## <a name="data-sources"></a>Orígenes de datos

En el cuadro de diálogo **Obtener datos** se organizan los tipos de datos en las categorías siguientes:

* Todo
* Archivo
* Base de datos
* Power Platform
* Azure
* Servicios en línea
* Otros

La categoría **Todos** incluye todos los tipos de conexión de datos de todas las categorías.

### <a name="file-data-sources"></a>Orígenes de datos de archivo

La categoría **Archivo** proporciona las siguientes conexiones de datos:

* Excel
* Texto o CSV
* XML
* JSON
* Carpeta
* PDF
* Carpeta de SharePoint

La siguiente imagen muestra la ventana **Obtener datos** para **Archivo**.

![Orígenes de datos de archivo, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>Orígenes de datos de base de datos

La categoría **Base de datos** proporciona las siguientes conexiones de datos:

* Base de datos SQL Server
* Base de datos Access
* Base de datos SQL Server Analysis Services
* Base de datos Oracle
* Base de datos IBM Db2
* Base de datos Informix de IBM (beta)
* IBM Netezza
* Base de datos MySQL
* Base de datos PostgreSQL
* Base de datos Sybase
* Base de datos Teradata
* Base de datos SAP HANA
* Servidor de aplicaciones de SAP Business Warehouse
* Servidor de mensajería de SAP Business Warehouse
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* Cubos de AtScale
* Data Virtuality LDW (beta)
* Denodo
* Dremio
* Exasol
* Indexima
* InterSystems IRIS (Beta)
* Jethro (beta)
* Kyligence
* Linkar PICK Style / MultiValue Databases (Beta)
* MariaDB (Beta)
* MarkLogic
* Conector de BI
* Actian (beta)

> [!NOTE]
> Para habilitar algunos conectores de bases de datos, debe seleccionar primero **Archivo > Opciones y configuración > Opciones** y, después, **Características en vista previa**. Si no ve algunos de los conectores mencionados anteriormente y quiere usarlos, compruebe la configuración de **Características en vista previa**. Tenga también en cuenta que cualquier origen de datos marcada como *Beta* o *Versión preliminar* tiene una compatibilidad y funcionalidades limitadas, y no debe usarse en entornos de producción.

La siguiente imagen muestra la ventana **Obtener datos** para **Base de datos**.

![Orígenes de datos de base de datos, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Orígenes de datos de Power Platform

La categoría **Power Platform** proporciona las conexiones de datos siguientes:

* Conjuntos de datos de Power BI
* Flujos de datos de Power BI
* Common Data Service
* Flujos de entrada de Power Platform (Beta)

En la imagen siguiente se muestra la ventana **Obtener datos** para **Power Platform**.

![Orígenes de datos de Power Platform, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Orígenes de datos de Azure

La categoría **Azure** proporciona las siguientes conexiones de datos:

* Azure SQL Database
* Azure Synapse Analytics (SQL DW)
* Base de datos de Azure Analysis Services
* Azure Database for PostgreSQL
* Azure Blob Storage
* Azure Table Storage
* Azure Cosmos DB
* Azure Data Explorer (Kusto)
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight Interactive Query
* Azure Cost Management
* Azure Databricks
* Azure Time Series Insights (Beta)


La siguiente imagen muestra la ventana **Obtener datos** para **Azure**.

![Orígenes de datos de Azure, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>Orígenes de datos de Online Services

La categoría **Online Services** proporciona las siguientes conexiones de datos:

* Lista de SharePoint Online
* Microsoft Exchange Online
* Dynamics 365 (en línea)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (local)
* Microsoft Azure Consumption Insights (Beta)
* Azure DevOps (solo Boards)
* Azure DevOps Server (solo Boards)
* Objetos de Salesforce
* Informes de Salesforce
* Google Analytics
* Adobe Analytics
* appFigures (Beta)
* Data.World - Obtener un conjunto de datos (Beta)
* GitHub (Beta)
* LinkedIn Sales Navigator (Beta)
* Marketo (Beta)
* Mixpanel (Beta)
* Planview Enterprise One - PRM (Beta)
* QuickBooks Online (Beta)
* Smartsheet
* SparkPost (Beta)
* SweetIQ (Beta)
* Planview Enterprise One - CTM (Beta)
* Twilio (Beta)
* Zendesk (Beta)
* Asana (beta)
* Dynamics 365 Customer Insights (Beta)
* Origen de datos de Emigo
* Entersoft Business Suite (Beta)
* FactSet Analytics
* Palantir Foundry
* Industrial App Store
* Intune Data Warehouse (Beta)
* Microsoft Graph Security (Beta)
* Projectplace para Power BI
* Product Insights (Beta)
* Quick Base
* Spigit (Beta)
* TeamDesk (Beta)
* Webtrends Analytics (Beta)
* Witivio (Beta)
* Workplace Analytics (Beta)
* Creador de Zoho (Beta)
* eWay-CRM (Beta)
* API inteligente PPM de hexágono


La imagen siguiente muestra la ventana **Obtener datos** para **Online Services**

![Orígenes de datos de Online Services, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>Otros orígenes de datos

La categoría **Otros** proporciona las siguientes conexiones de datos:

* Web
* Lista de SharePoint
* Fuente de OData
* Active Directory
* Microsoft Exchange
* Archivo Hadoop (HDFS)
* Spark
* Hive LLAP
* Script de R
* Script de Python
* ODBC
* OLE DB
* Acterys: Planeamiento y automatización de modelos (Beta)
* Automation Anywhere (Beta)
* Solver
* Cherwell (Beta)
* Cognite Data Fusion (Beta)
* FHIR
* Information Grid (Beta)
* Jamf Pro (Beta)
* MicroStrategy for Power BI
* Paxata
* QubolePresto (Beta)
* Roamler (Beta)
* Shortcuts Business Insights (Beta)
* Siteimprove
* SurveyMonkey (Beta)
* Tenforce (Smart)List
* TIBCO(R) Data Virtualization (beta)
* Vena (Beta)
* Vessel Insight (Beta)
* Zucchetti HR Infinity (Beta)
* Anaplan Connector v1.0 (beta)
* Starburst Enterprise Presto (beta)
* Consulta en blanco



La siguiente imagen muestra la ventana **Obtener datos** para **Otros**.

![Otros orígenes de datos en Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> En este momento, no es posible conectarse a orígenes de datos personalizados que se protegen mediante Azure Active Directory.

### <a name="template-apps"></a>Aplicaciones plantilla

Puede buscar aplicaciones de plantilla para su organización seleccionando el vínculo **Aplicaciones de plantilla** cerca de la parte inferior de la ventana **Obtener datos**. 

![Cuadro de diálogo Obtener datos para Otros orígenes de datos en Power BI Desktop](media/desktop-data-sources/data-sources-12.png)

Las aplicaciones de plantilla disponibles pueden variar en función de su organización.

## <a name="connecting-to-a-data-source"></a>Conectarse a un origen de datos

Para conectarse a un origen de datos, seleccione el origen de datos en la ventana **Obtener datos** y seleccione **Conectar**. En la siguiente imagen, la opción **Web** está seleccionada en la categoría de conexión de datos **Otros** .

![Conectar a la Web, cuadro de diálogo Obtener datos, Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

Se muestra una ventana de conexión, específica al tipo de conexión de datos. Si se necesitan credenciales, se le pedirá que las proporcione. La siguiente imagen muestra una dirección URL que se escribió para conectarse a un origen de datos web.

![Dirección URL de entrada, cuadro de diálogo Desde la Web, Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

Escriba la dirección URL o la información de conexión de recurso y, luego, seleccione **Aceptar**. Power BI Desktop realiza la conexión al origen de datos y presenta los orígenes de datos disponibles en el **Navegador**.

![Cuadro de diálogo Navegador, Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

Para cargar los datos, seleccione el botón **Cargar** en la parte inferior del panel **Navegador**. Para transformar o editar la consulta en el Editor de Power Query antes de cargar los datos, seleccione el botón **Transformar datos**.

Eso es todo lo que se necesita para conectarse a orígenes de datos en Power BI Desktop. Intente conectarse a datos de nuestra lista de orígenes de datos en crecimiento y vuelva a consultarla con frecuencia, debido a que siempre agregamos elementos a esta lista.

## <a name="using-pbids-files-to-get-data"></a>Usar archivos PBIDS para obtener datos

Los archivos PBIDS son archivos de Power BI Desktop con una estructura específica y tienen la extensión .PBIDS para identificarlos como archivo de origen de datos de Power BI.

Un archivo .PBIDS se puede crear para optimizar la experiencia **Obtener datos** de los creadores de informes nuevos o principiantes de la organización. Si crea el archivo .PBIDS a partir de informes existentes, es más fácil que los autores de informes principiantes creen nuevos informes a partir de los mismos datos.

Cuando un autor abre un archivo .PBIDS, Power BI Desktop se abre y pide al usuario las credenciales para autenticarse y conectarse al origen de datos especificado en el archivo. El cuadro de diálogo **Navegación** se abre y el usuario debe seleccionar las tablas del origen de datos que quiera cargar en el modelo. Puede que también deba seleccionar las bases de datos y el modo de conexión si no se especifican en el archivo .PBIDS.

A partir de ese momento, el usuario puede empezar a crear visualizaciones o seleccionar **Orígenes recientes** para cargar un conjunto de tablas nuevo en el modelo.

Actualmente, los archivos .PBIDS solo admiten un único origen de datos en un archivo. Si se especifica más de un origen de datos, se producirá un error.


### <a name="how-to-create-a-pbids-connection-file"></a>Creación de un archivo de conexión .PBIDS

Si tiene un archivo de Power BI Desktop existente (.PBIX) que ya está conectado a los datos que le interesan, puede simplemente exportar estos archivos de conexión desde Power BI Desktop. Este es el método recomendado, ya que el archivo .PBIDS se puede generar automáticamente desde Desktop. Además, todavía puede editar o crear manualmente el archivo en un editor de texto. 

Para crear el archivo .PBIDS, seleccione **Archivo > Opciones y configuración > Configuración del origen de datos**:

![Opción del menú Configuración de origen de datos](media/desktop-data-sources/data-sources-09.png)

En el cuadro de diálogo que aparece, seleccione el origen de datos que quiere exportar como .PBIDS y, a continuación, seleccione **Export PBIDS** (Exportar .PBIDS).

![Cuadro de diálogo Configuración del origen de datos](media/desktop-data-sources/data-sources-10.png)

Al seleccionar el botón **Export PBIDS** (Exportar .PBIDS), Power BI Desktop genera el archivo .PBIDS, cuyo nombre puede cambiar y que puede guardar en el directorio y compartir con otros usuarios. También puede abrir el archivo en un editor de texto y seguir modificando el archivo, incluida la especificación del modo de conexión en el propio archivo, tal como se muestra en la siguiente imagen. 

![Uso de un editor de texto para modificar el archivo .PBIDS](media/desktop-data-sources/data-sources-11.png)

Si prefiere crear manualmente los archivos .PBIDS en un editor de texto, debe especificar las entradas necesarias para una única conexión y guardar el archivo con la extensión .PBIDS. Opcionalmente, puede especificar el modo de conexión como DirectQuery o Importar. Si el **modo** no existe o es nulo en el archivo, se pedirá al usuario que abre el archivo en Power BI Desktop que seleccione **DirectQuery** o **Importar**.


### <a name="pbids-file-examples"></a>Ejemplos de archivos PBIDS

En esta sección se proporcionan algunos ejemplos de orígenes de datos de uso frecuente. El tipo de archivo .PBIDS solo admite las conexiones de datos que también se admiten en Power BI Desktop, salvo las siguientes excepciones: Direcciones URL de wiki, Live Connect y Consulta en blanco.

El archivo .PBIDS *no* incluye información de autenticación ni de tablas y esquemas.  

En los fragmentos de código siguientes se muestran varios ejemplos comunes de archivos PBIDS, pero no son completos. En el caso de otros orígenes de datos, puede consultar el [Formato de referencia de origen de datos (DSR)](/azure/data-catalog/data-catalog-dsr#data-source-reference-specification) para obtener información sobre protocolos y direcciones.

Si está editando o creando manualmente los archivos de conexión, le presentamos estos ejemplos por su carácter práctico, pero no están diseñados para ser exhaustivos ni incluyen todos los conectores admitidos en formato DSR.

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>Carpeta

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP HANA

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>Lista de SharePoint

La dirección URL debe llevar al sitio de SharePoint en sí y no a una lista dentro del sitio. Los usuarios obtienen un navegador que les permite seleccionar una o más listas de ese sitio, cada una de las cuales se convierte en una tabla del modelo.

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>Archivo de texto

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>Flujo de datos

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>Pasos siguientes

Puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](../transform-model/desktop-common-query-tasks.md)