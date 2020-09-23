---
title: Requisitos de hardware y software para instalar el servidor de informes de Power BI
description: En este artículo se especifican los requisitos mínimos de hardware y software para instalar y ejecutar Power BI Report Server.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 09/17/2020
ms.openlocfilehash: 4579296568524304f416d8e353dcbccac77bfc63
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861760"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Requisitos de hardware y software para instalar el servidor de informes de Power BI

En este artículo se especifican los requisitos mínimos de hardware y software para instalar y ejecutar Power BI Report Server.

## <a name="processor-memory-and-operating-system-requirements"></a>Requisitos de procesador, memoria y sistema operativo

| Componente | Requisito |
| --- | --- |
| .NET Framework |4.7<br><br>.NET Framework se puede instalar manualmente desde [Microsoft .NET Framework 4.7 (Instalador web) para Windows](https://support.microsoft.com/en-us/kb/3186500).<br/><br/> Para más información, recomendaciones e instrucciones sobre .NET Framework 4.7, vea [Guía de implementación de .NET Framework para desarrolladores](/dotnet/framework/deployment/deployment-guide-for-developers).<br/><br/>Windows 8.1 y Windows Server 2012 R2 requieren [KB2919355](https://support.microsoft.com/kb/2919355) antes de instalar .NET Framework 4.7. |
| Disco duro |El servidor de informes de Power BI requiere un mínimo de 1 GB de espacio disponible en disco duro.<br><br>Se requerirá espacio adicional en el servidor de bases de datos en el que se hospeda la base de datos del servidor de informes. |
| Memoria |**Mínimo**: 1 GB<br/><br/> **Recomendado:** 4 GB como mínimo |
| Velocidad del procesador |**Mínimo:** Procesador x64: 1,4 GHz<br/><br/> **Se recomienda que use:** 2.0 GHz o superior |
| Tipo de procesador |Procesador x64: AMD Opteron, AMD Athlon 64, Intel Xeon compatible con Intel EM64T, Intel Pentium IV compatible con EM64T |
| Sistema operativo |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br> |

> [!NOTE]
> La instalación del servidor de informes de Power BI solo es compatible con procesadores x64.


## <a name="database-server-version-requirements"></a>Requisitos de versión del servidor de bases de datos

Se usa SQL Server para hospedar las bases de datos del servidor de informes. La instancia del Motor de base de datos de SQL Server puede ser local o remota. A continuación, se indican las versiones admitidas del Motor de base de datos de SQL Server que pueden usarse para hospedar las bases de datos del servidor de informes:

* Instancia administrada de Azure SQL (Power BI Report Server, versión de enero de 2020 y posteriores)
* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

Al crear la base de datos del servidor de informes en un equipo remoto, se debe configurar la conexión para que use una cuenta de usuario de dominio o una cuenta de servicio que tenga acceso a la red. Si opta por usar una instancia remota de SQL Server, considere detenidamente qué credenciales debe utilizar el servidor de informes para conectarse a la instancia de SQL Server. Para más información, consulte el artículo sobre la [configuración de una conexión de base de datos del servidor de informes](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Consideraciones

El servidor de informes de Power BI instalará los valores predeterminados a fin de establecer la configuración principal necesaria para que un servidor de informes esté operativo. Los requisitos son los siguientes:

* Los idiomas admitidos para Power BI Report Server son: inglés, alemán, español, japonés, italiano, francés, ruso, chino simplificado, chino tradicional, portugués brasileño y coreano
* Debe haber un motor de base de datos de SQL Server disponible después de la instalación y antes de configurar la base de datos del servidor de informes. En la instancia del motor de base de datos se hospeda la base de datos del servidor de informes que el Administrador de configuración de Reporting Services creará. El motor de base de datos no es necesario para la experiencia de instalación real.
* En [Características de Reporting Services compatibles con las ediciones de SQL Server](/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016) se describen las diferencias entre las ediciones de SQL Server.
* La cuenta de usuario que ejecuta el programa de instalación debe ser miembro del grupo local de administradores.
* La cuenta de usuario que ejecuta el Administrador de configuración de Reporting Services debe tener permiso para acceder y crear bases de datos en la instancia del motor de base de datos en el que se hospedan las bases de datos del servidor de informes.
* El programa de instalación debe poder utilizar los valores predeterminados para reservar las direcciones URL que proporcionan acceso al servidor de informes y al portal web. Estos valores son el puerto 80, un carácter comodín seguro y los nombres de directorio virtual con el formato **ReportServer** y **Reports**.

## <a name="read-only-domain-controller-rodc"></a>Controlador de dominio de solo lectura (RODC)

 Puede instalar el servidor de informes en un entorno que tenga un controlador de dominio de solo lectura (RODC). Sin embargo, Reporting Services necesita acceso a un controlador de dominio de lectura y escritura para funcionar correctamente. Si Reporting Services solo tiene acceso a un RODC, podría experimentar errores al intentar administrar el servicio.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Informes de Power BI y conexiones activas de Analysis Services

Puede usar una conexión activa con instancias tabulares o multidimensionales. El servidor de Analysis Services debe tener la versión y edición adecuadas para que funcione correctamente.

| **Versión del servidor** | **SKU necesario** |
| --- | --- |
| 2012 SP1 CU4 o posterior |SKU Business Intelligence y Enterprise |
| 2014 |SKU Business Intelligence y Enterprise |
| 2016 y versiones posteriores |SKU estándar o superior |

## <a name="next-steps"></a>Pasos siguientes

[¿Qué es Power BI Report Server?](get-started.md)  
[Información general de administrador](admin-handbook-overview.md)  
[Instalar un servidor de informes de Power BI](install-report-server.md)  
[Descarga del Generador de informes](https://www.microsoft.com/download/details.aspx?id=53613)  
[Descargar SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)