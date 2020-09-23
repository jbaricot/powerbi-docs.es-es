---
title: Orígenes de datos de informes paginados en Power BI Report Server
description: Obtenga información acerca de los orígenes de datos a los que pueden conectarse los informes paginados (.rdl) en Power BI Report Server.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: maggies
ms.openlocfilehash: fcf0a286487922fcfc217b4d293aa731ad1564a6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861231"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Orígenes de datos de informes paginados en Power BI Report Server
Los informes paginados de Reporting Services en Power BI Report Server admiten los mismos orígenes de datos que se admiten en SQL Server Reporting Services. Vea la lista de [orígenes de datos compatibles con Reporting Services](/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Conexión a orígenes de datos de Oracle con UseInstalledUICulture

Para conectarse a orígenes de datos de Oracle, Power BI Report Server utiliza el proveedor de datos de Oracle para .NET (ODP.NET), que es independiente de NLS.

De forma predeterminada, el servidor de informes usa la referencia cultural de la interfaz de usuario del primer cliente para cargar ODP.NET.  Como resultado, todas las conexiones posteriores a Oracle desde el servidor de informes estarán en esa referencia cultural inicial de la interfaz de usuario hasta que se reinicie el servicio.  Este enfoque puede provocar problemas al representar un informe debido a discrepancias en el formato de la referencia cultural de la interfaz de usuario.

Para ofrecer una mejor experiencia en Power BI Report Server, se ha introducido un valor de configuración denominado UseInstalledUICulture. Cuando UseInstalledUICulture se establece en true, el servidor de informes siempre carga ODP.NET en la referencia cultural de la interfaz de usuario del servidor en lugar de la referencia cultural del primer cliente.
Esta opción está disponible en Power BI Report Server a partir de la versión del servicio de marzo de 2020.

Para habilitar la característica, modifique el archivo rsreportserver.config de la entrada de extensión de ORACLE como se indica a continuación.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Pasos siguientes
Ahora que se ha conectado al origen de datos, [cree un informe paginado](quickstart-create-paginated-report.md).  


¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)