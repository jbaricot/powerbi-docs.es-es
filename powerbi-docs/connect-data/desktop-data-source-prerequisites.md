---
title: Requisitos previos de los orígenes de datos de Power BI
description: Requisitos previos de los orígenes de datos de Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 01/29/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 55e219ff5da73774adaec768b48a0aedd90c1748
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405385"
---
# <a name="power-bi-data-source-prerequisites"></a>Requisitos previos de los orígenes de datos de Power BI
Para cada proveedor de datos, Power BI admite una versión de proveedor específica en los objetos. Para obtener más información sobre los orígenes de datos disponibles para Power BI, vea [Orígenes de datos](desktop-data-sources.md). La tabla siguiente describe estos requisitos.

| Origen de datos | Proveedor | Versión mínima de proveedor | Versión mínima de origen de datos | Objetos admitidos de origen de datos | Vínculo de descarga |
| --- | --- | --- | --- | --- | --- |
| SQL Server |ADO.net (integrado en .Net Framework) |.NET Framework 3.5 (únicamente) |SQL Server 2005 o superior |Tablas/vistas, funciones escalares, funciones de tabla |Se incluye en .NET Framework 3.5 o superior |
| Acceso |Motor de base de datos de Microsoft Access (ACE) |ACE 2010 SP1 |Sin restricción |Tablas/vistas |[Vínculo de descarga](./desktop-access-database-errors.md) |
| Excel (únicamente archivos .xls) (ver nota 1) |Motor de base de datos de Microsoft Access (ACE) |ACE 2010 SP1 |Sin restricción |Tablas, hojas |[Vínculo de descarga](./desktop-access-database-errors.md) |
| Oracle (ver nota 2) |ODP.NET |ODAC 11.2 versión 5 (11.2.0.3.20) |9.x o superior |Tablas/vistas |[Vínculo de descarga](./desktop-connect-oracle-database.md) |
| | System.Data.OracleClient (integrado en .NET Framework) |.NET Framework 3.5 |9.x o superior |Tablas/vistas |Se incluye en .NET Framework 3.5 o superior |
| IBM DB2 |Cliente ADO.Net de IBM (parte del paquete de controladores del servidor de datos IBM) |10.1 |9.1 o superior |Tablas/vistas |[Vínculo de descarga](https://go.microsoft.com/fwlink/?linkid=274911&clcid=0x409) |
| MySQL |Connector/Net |6.6.5 |5.1 |Tablas/vistas, funciones escalares |[Vínculo de descarga](https://go.microsoft.com/fwlink/?linkid=278885&clcid=0x409) |
| PostgreSQL |Proveedor NPGSQL de ADO.NET (incluido con Power BI Desktop) |4.0.10 |9,4 |Tablas/vistas |[Vínculo de descarga](https://go.microsoft.com/fwlink/?linkid=282716&clcid=0x409) |
| Teradata |Proveedor de datos .NET para Teradata |14+ |12+ |Tablas/vistas |[Vínculo de descarga](https://go.microsoft.com/fwlink/?linkid=278886&clcid=0x409) |
| SAP Sybase SQL Anywhere |iAnywhere.Data.SQLAnywhere para .NET 3.5 |16+ |16+ |Tablas/vistas |[Vínculo de descarga](https://go.microsoft.com/fwlink/?linkid=324846) |

>[!NOTE]
>Los archivos de Excel que tienen una extensión .xlsx no requieren una instalación de proveedor independiente.

>[!NOTE]
>Los proveedores de Oracle también necesitan software cliente de Oracle (versión 8.1.7 o superior).
> 
>