---
title: Orígenes de datos de Power BI
description: En este artículo se enumeran los orígenes de datos que admite Power BI, incluida información sobre DirectQuery y la puerta de enlace de datos local.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/07/2020
ms.author: davidi
ms.openlocfilehash: 918b9a98d66a1c739421433d35f593dc74d19773
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/13/2020
ms.locfileid: "91981490"
---
# <a name="power-bi-data-sources"></a>Orígenes de datos de Power BI

En la tabla siguiente se muestran los orígenes de datos que admite Power BI para los conjuntos de datos, incluida información sobre DirectQuery y la puerta de enlace de datos local. Para más información sobre los flujos de datos, consulte [Conectarse a orígenes de datos de flujos de datos de Power BI](../transform-model/service-dataflows-data-sources.md).

| Origen de datos | Conexión desde el Escritorio | Conexión y actualización desde el servicio | DirectQuery/Conexiones dinámicas | Puerta de enlace (compatible) | Puerta de enlace (obligatoria) | Flujos de datos de Power BI |
|---|---|---|---|---|---|---|---|
| Base de datos Access | Sí | Sí | No | Sí <sup>1</sup> | Sí | Sí |
| Active Directory | Sí | Sí | No | Sí | Sí | Sí |
| Adobe Analytics | Sí | Sí | No | No | No | No |
| Amazon Redshift | Sí | Sí | Sí | Sí | No | Sí |
| appFigures | Sí | Sí | No | No | No | No |
| Cubos de AtScale | Sí | Sí | Sí | Sí | No | No |
| Azure Analysis Services | Sí | Sí | Sí | No | No | No |
| Azure Blob Storage | Sí | Sí | No | Sí | No | Sí |
| Azure Cosmos DB | Sí | Sí | No | No | No | No |
| Azure Cost Management | Sí | Sí | No | No | No | No |
| Azure Data Explorer (kusto) | Sí | Sí | Sí | Sí | No | Sí |
| Azure Data Lake Storage Gen1 | Sí | Sí | No | No | No | No |
| Azure Data Lake Storage Gen2 | Sí | Sí | No | Sí | No | Sí |
| Azure DevOps | Sí | Sí | No | No | No | No |
| Azure DevOps Server | Sí | Sí | No | Sí | Sí | No |
| Azure HDInsight (HDFS) | Sí | Sí | No | No | No | No |
| Azure HDInsight Spark | Sí | Sí | Sí | No | No | Sí |
| Azure SQL Database | Sí | Sí | Sí | Sí | No | Sí |
| Azure SQL Data Warehouse | Sí | Sí | Sí | Sí | No | Sí |
| Azure Table Storage | Sí | Sí | No | Sí | No | Sí |
| Conector de BI | Sí | Sí | Sí | Sí | Sí | No |
| BI360: informes presupuestarios y financieros | Sí | Sí | No | No | No | No |
| Common Data Service | Sí | Sí | No | No | No | Sí |
| Data.World - Obtener un conjunto de datos | Sí | Sí | No | No | No | No |
| Denodo | Sí | Sí | Sí | Sí | Sí | No |
| Dremio | Sí | Sí | Sí | Sí | Sí | No |
| Dynamics 365 (en línea) | Sí | Sí | No | No | No | No |
| Dynamics 365 Business Central | Sí | Sí | No | No | No | No |
| Dynamics 365 Business Central (local) | Sí | Sí | No | No | No | No |
| Dynamics 365 Customer Insights | Sí | Sí | No | No | No | No |
| Dynamics NAV | Sí | Sí | No | No | No | No |
| Origen de datos de Emigo | Sí | Sí | No | No | No | No |
| Entersoft Business Suite | Sí | Sí | No | No | No | No |
| Essbase | Sí | Sí | Sí | Sí | Sí | No |
| Exasol | Sí | Sí | Sí | Sí | Sí | No |
| Excel | Sí <sup>3</sup> | Sí <sup>3</sup> | No | Sí <sup>3</sup> | No <sup>4</sup> | Sí |
| Facebook | Sí | Sí | No | No | No | No |
| Archivo | Sí | Sí | No | Sí | Sí | Sí |
| Carpeta | Sí | Sí | No | Sí | Sí | Sí |
| GitHub | Sí | Sí | No | No | No | No |
| Google Analytics | Sí | Sí | No | No | No | No |
| Google BigQuery | Sí | Sí | Sí | No | No | Sí |
| Archivo Hadoop (HDFS) | Sí | No | No | No | No | No |
| HDInsight Interactive Query | Sí | Sí | Sí | No | No | No |
| IBM DB2 | Sí | Sí | Sí | Sí | No | Sí |
| Base de datos Informix de IBM | Sí | Sí | No | Sí | No | No |
| IBM Netezza | Sí | Sí | Sí | Sí | Sí | No |
| Impala | Sí | Sí | Sí | Sí | Sí | Sí |
| Indexima | Sí | Sí | Sí | Sí | Sí | No |
| Industrial App Store | Sí | Sí | No | No | No | No |
| Information Grid | Sí | Sí | No | No | No | No |
| Intersystems IRIS | Sí | Sí | Sí | Sí | Sí | No |
| Almacenamiento de datos de Intune | Sí | Sí | No | No | No | No |
| Jethro ODBC | Sí | Sí | Sí | Sí | Sí | No |
| JSON | Sí | Sí | No | Sí** | No <sup>4</sup> | Sí |
| Kyligence Enterprise | Sí | Sí | Sí | Sí | Sí | No |
| MailChimp | Sí | Sí | No | No | No | No |
| Marketo | Sí | Sí | No | No | No | No |
| MarkLogic ODBC | Sí | Sí | Sí | Sí | Sí | No |
| Microsoft Azure Consumption Insights | Sí | Sí | No | No | No | No |
| Microsoft Exchange | Sí | Sí | No | Sí | No | No |
| Microsoft Exchange Online | Sí | Sí | No | No | No | Sí |
| Microsoft Graph Security | Sí | Sí | No | Sí | No | No |
| Mixpanel | Sí | Sí | No | No | No | No |
| MySQL | Sí | Sí | No | Sí | Sí | Sí |
| OData | Sí | Sí <sup>7</sup> | No | Sí | No | Sí |
| ODBC | Sí | Sí | No | Sí | Sí | Sí |
| OleDb | Sí | Sí | No | Sí | Sí | No |
| Oracle | Sí | Sí | Sí | Sí | Sí | Sí |
| Paxata <sup>8</sup> | Sí | Sí | No | Sí | No | No |
| PDF | Sí | Sí | No | Sí | No <sup>4</sup> | Sí |
| Planview Enterprise One - CTM | Sí | Sí | No | No | No | No |
| Planview Enterprise One - PRM | Sí | Sí | No | No | No | No |
| Planview Projectplace | Sí | Sí | No | No | No | No |
| PostgreSQL | Sí | Sí | Sí | Sí | No | Sí |
| Flujos de datos de Power BI | Sí | Sí | No | No | No | Sí |
| Conjuntos de datos de Power BI | Sí | Sí | Sí | No | No | No |
| Flujos de datos de Power Platform | Sí | Sí | No | No | No | Sí |
| Script de Python | Sí | Sí <sup>5</sup> | No | Sí <sup>5</sup> | Sí | No |
| QubolePresto | Sí | Sí | Sí | Sí | Sí | No |
| Quick Base | Sí | Sí | No | Sí | Sí | No |
| QuickBooks Online | Sí | Sí | No | No | No | No |
| Script de R | Sí | Sí <sup>5</sup> | No | Sí <sup>5</sup> | No | No |
| Roamler | Sí | Sí | No | Sí | No | No |
| Objetos de Salesforce | Sí | Sí | No | No | No | Sí |
| Informes de Salesforce | Sí | Sí | No | No | No | Sí |
| Servidor de mensajería de SAP Business Warehouse | Sí | Sí | Sí | Sí | Sí | Sí |
| Servidor de SAP Business Warehouse | Sí | Sí | Sí | Sí | Sí | Sí |
| SAP HANA | Sí | Sí | Sí | Sí | Sí | Sí |
| Carpeta de SharePoint | Sí | Sí | No | Sí | No <sup>4</sup> | Sí |
| Lista de SharePoint | Sí | Sí | No | Sí | No <sup>4</sup> | Sí |
| Lista de SharePoint Online | Sí | Sí | No | Sí | No | Sí |
| Smartsheet | Sí | Sí | No | No | No | Sí |
| Snowflake | Sí | Sí | Sí | Sí | No | Sí |
| Spark | Sí | Sí | Sí | Sí | No | Sí |
| SparkPost | Sí | Sí | No | No | No | No |
| SQL Server | Sí | Sí | Sí | Sí | Sí | Sí |
| SQL Server Analysis Services | Sí | Sí | Sí | Sí | Sí | No |
| Stripe | Sí | Sí | No | No | No | No |
| SurveyMonkey | Sí | Sí | No | Sí | No | No |
| SweetIQ | Sí | Sí | No | No | No | No |
| Sybase | Sí | Sí | No | Sí | Sí | Sí |
| TeamDesk | Sí | Sí | No | Sí | No | No |
| Tenforce | Sí | Sí | No | No | No | No |
| Teradata | Sí | Sí | Sí | Sí | Sí | Sí |
| Texto o CSV | Sí | Sí | No | Sí | No <sup>4</sup> | Sí |
| Twilio | Sí | Sí | No | No | No | No |
| tyGraph | Sí | Sí | No | No | No | No |
| Vertica | Sí | Sí | Sí | Sí | Sí | Sí |
| Web | Sí | Sí | No | Sí | Sí <sup>6</sup> | Sí |
| Webtrends | Sí | Sí | No | No | No | No |
| Dimensiones de Workforce | Sí | Sí | No | Sí | No | No |
| XML | Sí | Sí | No | Sí | No <sup>4</sup> | Sí |
| Zendesk | Sí | Sí | No | No | No | No |
| | | | | | | | |

<sup>1</sup> Compatible con el [proveedor OLEDB ACE](https://www.microsoft.com/download/details.aspx?id=54920), instalado en el mismo equipo que la puerta de enlace.

<sup>3</sup> Los archivos de Excel 1997-2003 (.xls) requieren el [proveedor OLEDB ACE](https://www.microsoft.com/download/details.aspx?id=54920).

<sup>4</sup> Obligatorio para la versión local de la tecnología.

<sup>5</sup> Solo compatible con la [puerta de enlace personal](service-gateway-personal-mode.md).

<sup>6</sup> Necesario para las bases de datos .html, .xls y de Access.

<sup>7</sup> El servicio Power BI no es compatible con las fuentes de OData que requieren autenticación.

<sup>8</sup> Paxata se admite en la versión de Power BI Desktop optimizada para Power BI Report Server. No se admite en los informes de Power BI publicados en Power BI Report Server. Para ver una lista de los orígenes de datos admitidos, consulte [Orígenes de datos de los informes de Power BI en Power BI Report Server](../report-server/data-sources.md).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

- Muchos conectores de datos para Power BI Desktop requieren Internet Explorer 10 (o una versión posterior) para la autenticación. 
- Algunos orígenes de datos están disponibles en Power BI Desktop optimizados para Power BI Report Server, pero no se admiten cuando se publican en Power BI Report Server. Para ver una lista de los orígenes de datos admitidos, consulte [Orígenes de datos de los informes de Power BI en Power BI Report Server](../report-server/data-sources.md).

## <a name="single-sign-on-sso-for-directquery-sources"></a>Inicio de sesión único (SSO) para orígenes de DirectQuery

Cuando se habilita la opción SSO y los usuarios acceden a informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas al origen de datos subyacente. Esto permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.
La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación. Los orígenes de datos siguientes admiten el inicio de sesión único para las conexiones a través de DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Servidor de mensajes de SAP BW
- Snowflake
- Spark
- SQL Server
- Teradatos

> [!Note]
> No se admite Azure Multi-Factor Authentication (MFA). Los usuarios que quieran usar SSO con DirectQuery se deben excluir de MFA.

## <a name="next-steps"></a>Pasos siguientes

[Conectarse a los datos en Power BI Desktop](desktop-quickstart-connect-to-data.md)  
[Uso de DirectQuery en Power BI](desktop-directquery-about.md)  
[Datos activos de SQL Server Analysis Services en Power BI](sql-server-analysis-services-tabular-data.md)  
[¿Qué es una puerta de enlace de datos local?](service-gateway-onprem.md)  
[Orígenes de datos de los informes de Power BI en Power BI Report Server](../report-server/data-sources.md)
