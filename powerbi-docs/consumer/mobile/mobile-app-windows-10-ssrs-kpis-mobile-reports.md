---
title: Visualización de informes y KPI del entorno local en la aplicación Power BI para Windows
description: La aplicación móvil de Power BI para Windows 10 le proporciona acceso móvil directo y táctil a la información local más importante de su empresa.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 05/19/2020
ms.author: painbar
ms.openlocfilehash: 98f528e13bd92692bd76afc42aaac43828f7f586
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90860909"
---
# <a name="view-on-premises-reports-and-kpis-in-the-power-bi-windows-app"></a>Visualización de informes y KPI del entorno local en la aplicación Power BI para Windows
La aplicación móvil Power BI para Windows 10 proporciona acceso móvil táctil en directo a la información local más importante de su empresa en SQL Server 2016 Reporting Services. 

![Informes móviles de Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>Lo primero es lo primero
[Cree informes móviles de Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) con el Publicador de informes móviles de SQL Server 2016 Enterprise Edition y publíquelos en el [portal web de Reporting Services](/sql/reporting-services/web-portal-ssrs-native-mode). Cree KPI justo en el portal web. Organícelos en carpetas y marque sus favoritos, así podrá encontrarlos fácilmente. 

Después, en la aplicación Power BI para Windows 10, podrá ver los KPI, los informes móviles y los informes de Power BI organizados en carpetas o como favoritos. 

> [!NOTE]
> El dispositivo debe ejecutar Windows 10. La aplicación funciona mejor en dispositivos con al menos 1 GB de RAM y 8 GB de almacenamiento interno.

>[!NOTE]
>El soporte técnico de la aplicación móvil de Power BI con **teléfonos con Windows 10 Mobile** finalizará el 16 de marzo de 2021. [Más información](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>Explorar ejemplos sin un servidor SQL Server 2016 Reporting Services
Aunque no tenga acceso a un portal web de Reporting Services, puede explorar las características de los informes móviles de Reporting Services.

1. En el dispositivo Windows 10, abra la aplicación Power BI.
2. Pulse el botón de navegación global ![Botón de navegación global](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) en la esquina superior izquierda.
3. Pulse el icono **Configuración**![icono Configuración](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png), haga clic con el botón derecho o pulse y mantenga pulsado **Conectarse al servidor** y luego **Ver ejemplos**.
   
   ![Ver ejemplos de SSRS](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Abra la carpeta Informes de venta directa o Informes de ventas para explorar los KPI e informes móviles.
   
   ![Informes móviles y KPI de ejemplo](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

Examine los ejemplos para interactuar con informes móviles y KPI.

## <a name="connect-to-a-reporting-services-report-server"></a>Conexión a un servidor de informes de Reporting Services
1. En la parte inferior del panel de navegación, pulse **Configuración** ![Icono Configuración](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Pulse **Conectarse al servidor**.
3. Rellene la dirección del servidor y su nombre de usuario y contraseña. Use este formato para la dirección del servidor:
   
     `https://<servername>/reports` OR   `https://<servername>/reports`
   
   > [!NOTE]
   > Incluya **http** o **https** al principio de la cadena de conexión.
   > 
   > 
   
    Si lo prefiere, pulse **Opción avanzada** para asignar al servidor un nombre.
4. Pulse la marca de verificación para conectarse. 
   
   Ahora verá el servidor en el panel de navegación.
   
   ![Servidor en el panel de navegación](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >Pulse el botón de navegación global ![botón de navegación global](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) en cualquier momento para desplazarse entre los informes móviles de Reporting Services y los paneles del servicio Power BI. 
   > 

   >[!NOTE]
   >No se admiten los servidores de informes configurados con puertos personalizados y no se puede acceder a ellos desde la aplicación de Windows para Power BI. 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Visualización de informes móviles y KPI de Reporting Services en la aplicación de Power BI
Los KPI y los informes móviles de Reporting Services y los informes de Power BI (versión preliminar) se muestran en las mismas carpetas en las que se encuentran en el portal web de Reporting Services.

![Carpetas de informes](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* Puntee un KPI para verlo en el modo de enfoque.
  
    ![KPI en modo de enfoque](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* Puntee un informe móvil para abrirlo e interactuar con él en la aplicación de Power BI.
  
    ![Informes móviles de Reporting Services](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Ver los informes y KPI favoritos
Puede marcar los KPI, informes móviles e informes de Power BI como favoritos en el portal web de Reporting Services y después verlos en una carpeta adecuada en el dispositivo con Windows 10, junto con sus informes y paneles favoritos de Power BI.

* Pulse **Favoritos**.
  
   ![Icono de favoritos](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Todos los favoritos del portal web se encuentran en esta página.
  
Obtenga más información sobre los [favoritos en las aplicaciones móviles Power BI](mobile-apps-favorites.md).

## <a name="remove-a-connection-to-a-report-server"></a>Quitar una conexión a un servidor de informes
Solo puede conectarse a un servidor de informes a la vez desde su aplicación móvil de Power BI. Si quiere conectarse a otro servidor, antes deberá desconectarse del actual.

1. En la parte inferior del panel de navegación, pulse **Configuración** ![Icono Configuración](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png).
2. Mantenga pulsado el nombre del servidor al que no quiere estar conectado.
3. Pulse **Quitar servidor**.
   
    ![Quitar servidor](media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Crear informes móviles y KPI de Reporting Services
Los informes móviles y KPI de Reporting Services no se crean en la aplicación móvil Power BI. Se crean en el Publicador de informes móviles de SQL Server y un portal web de SQL Server 2016 Reporting Services.

* [Cree sus propios informes móviles de Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) y publíquelos en un portal web de Reporting Services.
* Crear [KPI en un portal web de Reporting Services](/sql/reporting-services/working-with-kpis-in-reporting-services)

## <a name="next-steps"></a>Pasos siguientes
* [Introducción a la aplicación móvil de Power BI para Windows 10](mobile-windows-10-phone-app-get-started.md)  
* [¿Qué es Power BI?](../../fundamentals/power-bi-overview.md)  
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)