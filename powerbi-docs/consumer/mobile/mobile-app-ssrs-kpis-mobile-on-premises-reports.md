---
title: Ver los informes locales y los KPI en las aplicaciones móviles de Power BI
description: Las aplicaciones móviles de Power BI ofrecen acceso móvil directo y táctil a la información local más importante de su empresa en SQL Server Reporting Services y el servidor de informes de Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/05/2019
ms.author: painbar
ms.openlocfilehash: 2f6d02d6128a2896a19d87f30f46f26f101385f6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861001"
---
# <a name="view-on-premises-report-server-reports-and-kpis-in-the-power-bi-mobile-apps"></a>Visualización de informes y KPI locales del servidor de informes en la aplicaciones móviles de Power BI

Las aplicaciones móviles de Power BI proporcionan acceso móvil directo y táctil a la información local más importante de su empresa en el servidor de informes de Power BI y SQL Server 2016 Reporting Services (SSRS).

Se aplica a:

| ![iPhone](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/iphone-logo-50-px.png) | ![iPad](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/ipad-logo-50-px.png) | ![Teléfono Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-phone-logo-50-px.png) | ![Tableta Android](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/android-tablet-logo-50-px.png) |
|:--- |:--- |:--- |:--- |
| iPhones |iPad |Teléfonos Android |Tabletas Android |


![Página principal del servidor de informes en las aplicaciones móviles](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-pbi-report-server-home.png)

## <a name="first-things-first"></a>Lo primero es lo primero
**Las aplicaciones móviles se encuentran donde visualiza el contenido de Power BI, donde no lo haya creado.**

* Usted y otros creadores de informes de su organización podrán [crear informes de Power BI con Power BI Desktop y publicarlos en el portal web del servidor de informes de Power BI](../../report-server/quickstart-create-powerbi-report.md). 
* Puede crear [KPI desde el mismo portal web](/sql/reporting-services/working-with-kpis-in-reporting-services), organizarlos en carpetas y marcar sus favoritos para encontrarlos fácilmente. 
* [Cree informes móviles de Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher) con el Publicador de informes móviles de SQL Server 2016 Enterprise Edition y publíquelos en el [portal web de Reporting Services](/sql/reporting-services/web-portal-ssrs-native-mode).  

Luego, en las aplicaciones móviles de Power BI, podrá conectarse a cinco servidores de informes como máximo para ver los informes y los KPI de Power BI, organizados en carpetas o recopilados como favoritos. 

## <a name="explore-samples-in-the-mobile-apps-without-a-server-connection"></a>Explorar ejemplos de las aplicaciones móviles sin conexión con el servidor
Aunque no tenga acceso a un portal web de Reporting Services, puede explorar las características de los informes móviles y los KPI de Reporting Services. 

1. Pulse la imagen del perfil en la esquina superior izquierda y, después, pulse **Configuración** en el panel de cuentas que aparece.

2. En la página de configuración que se abre, pulse **Ejemplos de Reporting Services** y examine los ejemplos para interactuar con los informes móviles y los KPI.
   
   ![Ejemplos de Reporting Services](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-ssrs-samples.png)

## <a name="connect-to-an-on-premises-report-server"></a>Conectarse a un servidor de informes local
En las aplicaciones móviles de Power BI podrá ver los informes locales de Power BI, y los informes móviles y los KPI de Reporting Services. 

1. En su dispositivo móvil, abra la aplicación de Power BI.
2. Si todavía no ha iniciado sesión en Power BI, pulse **Servidor de informes**.
   
   ![Iniciar sesión en un servidor de informes](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-connect-to-rs-login.png)
   
   Si ya ha iniciado sesión en la aplicación Power BI, pulse la imagen del perfil en la esquina superior izquierda y, después, pulse **Configuración** en el panel de cuentas que aparece.
3. En la página configuración que se abre, pulse **Conectarse al servidor**.
   
    ![Conectarse al servidor](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-android-server-sign-in.png)

    La aplicación móvil debe tener acceso al servidor de alguna manera. Hay varias maneras de hacerlo:
     * Estar en la misma red o mediante VPN es la manera más fácil.
     * Es posible usar un proxy de aplicación web para conectarse desde fuera de la organización. Consulte [Uso de OAuth para conectarse a Reporting Services](mobile-oauth-ssrs.md) para más información.
     * Abra una conexión (puerto) en el firewall.

4. Rellene la dirección del servidor y asígnele un nombre descriptivo, si quiere. Use este formato para la dirección del servidor:
   
     `https://<servername>/reports`
   
     O
   
     `https://<servername>/reports`
   
   Incluya **http** o **https** delante de la cadena de conexión.
   
    ![Cuadro de diálogo Conectar con el servidor](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-connect-to-server-dialog.png)
5. Una vez que haya escrito la dirección del servidor y un nombre descriptivo opcional, pulse **Conectar** y, después, rellene el nombre de usuario y la contraseña cuando se le solicite.
6. Ahora verá el servidor en el panel Cuentas, en este ejemplo con el nombre "Servidor profesional".
   
   ![Servidor de informes en el panel de navegación](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-left-nav-report-server.png)

## <a name="connect-to-an-on-premises-report-server-in-ios-or-android"></a>Conexión a un servidor de informes local en iOS o Android

Si ve Power BI en la aplicación móvil de iOS o Android, es posible que el administrador de TI haya definido una directiva de configuración de aplicación. Si es así, se habrá simplificado la experiencia de conexión al servidor de informes y no tendrá que proporcionar tanta información cuando se conecte a un servidor de informes. 

1. Verá un mensaje que indica que su aplicación móvil está configurada con un servidor de informes. Pulse en **Iniciar sesión**.

    ![Iniciar sesión en el servidor de informes](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-sign-in.png)

2.  En la página **Conectar al servidor**, los detalles del servidor de informes ya están rellenados. Pulse **Conectar**.

    ![Detalles del servidor de informes rellenados](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ios-remote-configure-connect-server.png)

3. Escriba una contraseña para autenticar y luego pulse en **Iniciar sesión**. 

    ![Detalles del servidor de informes rellenados](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-config-server-address.png)

Ahora puede ver e interactuar con los KPI y los informes de Power BI almacenados en el servidor de informes.

## <a name="view-power-bi-reports-and-kpis-in-the-power-bi-app"></a>Ver los informes y los KPI de Power BI en la aplicación de Power BI
Los informes de Power BI, y los informes móviles y KPI de Reporting Services se muestran en las mismas carpetas en las que están en el portal web de Reporting Services. 

* Pulse un informe de Power BI ![Icono de informe de Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-report-icon.png). Se abre en modo horizontal y puede interactuar con él en la aplicación de Power BI.

    > [!NOTE]
  > El rastreo agrupando y desagrupando datos actualmente no está habilitado en los informes de Power BI de Power BI Report Server.
  
    ![Informe de Power BI](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-iphone-report-server-report.png)
* En Power BI Desktop, los propietarios de informes pueden [optimizar un informe](../../create-reports/desktop-create-phone-report.md) para las aplicaciones móviles de Power BI. En el teléfono móvil, los informes optimizados tienen un icono, ![icono de informe de Power BI optimizado](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-icon.png), y un diseño especiales.
  
    ![Informe de Power BI optimizado para móvil](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-rs-mobile-optimized-report.png)
* Puntee un KPI para verlo en el modo de enfoque.
  
    ![KPI en modo de enfoque](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/pbi_ipad_ssmrp_tile.png)

## <a name="view-your-favorite-kpis-and-reports"></a>Ver los informes y KPI favoritos
Puede marcar KPI e informes como favoritos en el portal web y verlos después en una práctica carpeta en su dispositivo móvil, junto con sus paneles favoritos de Power BI.

* Pulse **Favoritos** en la barra de navegación.
  
   ![Favoritos en el panel de navegación](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-faves-pbi-report-server-update.png)
  
   Los KPI e informes favoritos del portal web se encuentran en esta página, junto con los paneles de Power BI del servicio Power BI:
  
   ![Informes y paneles de Power BI en la página Favoritos](./media/mobile-app-ssrs-kpis-mobile-on-premises-reports/power-bi-ipad-favorites.png)

## <a name="remove-a-connection-to-a-report-server"></a>Quitar una conexión a un servidor de informes
1. Abra el panel Cuentas, pulse **Configuración**.
2. Pulse el nombre del servidor al que no quiera estar conectado.
3. Pulse **Quitar servidor**.

## <a name="next-steps"></a>Pasos siguientes
* [¿Qué es Power BI?](../../fundamentals/power-bi-overview.md)  
* ¿Preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)