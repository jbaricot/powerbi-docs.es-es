---
title: 'Introducción al manual del desarrollador: servidor de informes de Power BI'
description: Este es el manual del desarrollador para el servidor de informes de Power BI, una ubicación local para almacenar y administrar informes paginados, móviles o de Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.openlocfilehash: d485c7ab7583d2604cd9da9e4c122c6cceeeb4fe
ms.sourcegitcommit: 8afdd3601209636c9ab92d75f967d4ee0a2cab26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95012010"
---
# <a name="developer-handbook-overview-power-bi-report-server"></a>Introducción al manual del desarrollador: servidor de informes de Power BI

Este es el manual del desarrollador para el servidor de informes de Power BI, una ubicación local para almacenar y administrar informes paginados, móviles o de Power BI.

![Manual del administrador](media/developer-handbook-overview/admin-handbook.png)

En este manual se resaltan las opciones que, como desarrollador, tiene para trabajar con Power BI Report Server.

## <a name="embedding"></a>Inserción

Puede insertar dentro de cualquier informe del servidor de informes de Power BI un iFrame agregando el parámetro querystring `?rs:Embed=true` a la dirección URL. Esta técnica sirve para informes de Power BI, así como para otros tipos de informes.

### <a name="report-viewer-control"></a>Control del visor de informes

Para los informes paginados, puede aprovechar las ventajas del control de visor de informes. Con él, puede colocar el control dentro de una aplicación web o ventanas de .NET. Para más información, consulte [Introducción al control de visor de informes](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started).

## <a name="apis"></a>API

Dispone de varias opciones de API para interactuar con el servidor de informes de Power BI. Esta técnica incluye lo siguiente:

* [API de REST](rest-api.md)
* [Acceso de URL](/sql/reporting-services/url-access-ssrs)
* [Proveedor de WMI](/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

También puede usar las [utilidades de PowerShell de código abierto](https://github.com/Microsoft/ReportingServicesTools) para administrar el servidor de informes.

> [!NOTE]
> Las utilidades de PowerShell admiten archivos de Power BI Desktop (.pbix) a través de los comandos -RsRest*.

Ejecute el comando siguiente para averiguar qué comandos del módulo ReportingServicesTools de PowerShell admiten archivos de Power BI Desktop (.pbix).

```powershell
Get-Command -Module ReportingServicesTools -Noun RsRest*
```

## <a name="custom-extensions"></a>Extensiones personalizadas

La biblioteca de extensiones es un conjunto de clases, interfaces y tipos de valor que se incluyen en el servidor de informes de Power BI. Esta biblioteca proporciona acceso a la funcionalidad del sistema y está diseñada para ser la base en la que se pueden usar aplicaciones de Microsoft .NET Framework para extender los componentes del servidor de informes de Power BI.

Existen varios tipos de extensiones que puede crear.

* Extensiones de procesamiento de datos
* Extensiones de entrega
* Extensiones de representación para informes paginados
* Extensiones de seguridad

Para más información, consulte [Biblioteca de extensiones](/sql/reporting-services/extensions/reporting-services-extension-library).

## <a name="next-steps"></a>Pasos siguientes

[Introducción al control de visor de informes](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)  
[Creación de aplicaciones con el servicio web y .NET Framework](/sql/reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework)  
[Acceso de URL](/sql/reporting-services/url-access-ssrs)  
[Biblioteca de extensiones](/sql/reporting-services/extensions/reporting-services-extension-library)  
[Proveedor WMI](/sql/reporting-services/wmi-provider-library-reference/reporting-services-wmi-provider-library-reference-ssrs)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
