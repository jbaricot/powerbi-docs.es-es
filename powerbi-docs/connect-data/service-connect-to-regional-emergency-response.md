---
title: Conexión con el panel de respuesta ante emergencias regionales
description: Cómo obtener e instalar el panel de ayuda para la toma de decisiones de la COVID-19 para la aplicación de plantilla de respuesta ante emergencias regionales y cómo conectarse a los datos
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82149679"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Conexión con el panel de respuesta ante emergencias regionales
El panel de respuesta ante emergencias regionales es el componente de informes de la [solución de respuesta ante emergencias regionales de Microsoft Power Platform](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Los administradores de la organización regional pueden visualizar el panel en su inquilino de Power BI, lo que les permite ver rápidamente datos y métricas importantes que les ayudarán a tomar decisiones eficaces.

![Informe de la aplicación del panel de respuesta ante emergencias regionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

En este artículo se explica cómo instalar la aplicación de respuesta ante emergencias regionales mediante la aplicación de plantilla del panel de respuesta ante emergencias regionales y cómo conectarse a los orígenes de datos.

Para conocer en detalle lo que se presenta en el panel, vea [Obtener información](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

Después de instalar la aplicación de plantilla y conectarse a los orígenes de datos, puede personalizar el informe según sus necesidades. Luego puede distribuirlo como una aplicación entre los compañeros de su organización.

## <a name="prerequisites"></a>Requisitos previos

Antes de instalar esta aplicación de plantilla, debe instalar y configurar la [solución de respuesta ante emergencias regionales](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy). Al instalar esta solución, se crean las referencias de orígenes de datos necesarias para rellenar la aplicación con datos.

Al instalar la solución de respuesta ante emergencias regionales, tome nota de la [dirección URL de la instancia del entorno Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard). La necesitará para conectar la aplicación de plantilla a los datos.

## <a name="install-the-app"></a>Instalación de la aplicación

1. Haga clic en el vínculo siguiente para obtener la aplicación: [Aplicación de plantilla del panel de respuesta ante emergencias regionales](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. En la página AppSource de la aplicación, seleccione [**OBTENER AHORA**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response).

    [![Aplicación del panel de respuesta ante emergencias regionales en AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Haga clic en **Instalar**. 

    ![Instalación de la aplicación del panel de respuesta ante emergencias regionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    Una vez instalada la aplicación, la verá en la página Aplicaciones.

   ![Aplicación del panel de respuesta ante emergencias regionales en la página de aplicaciones](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Conexión a orígenes de datos

1. Seleccione el icono de la página Aplicaciones para abrir la aplicación.

1. En la pantalla de presentación, seleccione **Explorar**.

   ![Pantalla de presentación de la aplicación de plantilla](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   La aplicación se abre y muestra los datos de ejemplo.

1. Seleccione el vínculo **Conectar los datos** en el banner de la parte superior de la página.

   ![Vínculo Conectar los datos de la aplicación del panel de respuesta ante emergencias regionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. En el campo cuadro de diálogo que aparece, escriba la [dirección URL de la instancia del entorno Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Por ejemplo: https://[myenv].crm.dynamics.com. Cuando termine, haga clic en **Siguiente**.

   ![Cuadro de diálogo de la dirección URL de la aplicación del panel de respuesta ante emergencias regionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. En el cuadro de diálogo siguiente que aparece, establezca el método de autenticación en **OAuth2**. No tiene que hacer nada en lo que respecta a la configuración de nivel de privacidad.

   Seleccione **Iniciar sesión**.

   ![Cuadro de diálogo de autenticación de la aplicación del panel de respuesta ante emergencias regionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. En la pantalla de inicio de sesión de Microsoft, inicie sesión en Power BI.

   ![Pantalla de inicio de sesión de Microsoft](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   Una vez que haya iniciado sesión, el informe se conectará a los orígenes de datos y se rellenará con datos actualizados. Durante este tiempo se activará el monitor de actividad.

   ![Actualización en curso de la aplicación del panel de respuesta ante emergencias regionales](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Programación de la actualización del informe

Cuando se haya completado la actualización de los datos, [configure una programación de actualización](../refresh-scheduled-refresh.md) para mantener actualizados los datos del informe.

1. En la barra de encabezado superior, seleccione **Power BI**.

   ![Ruta de navegación de Power BI](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. En el panel de navegación izquierdo, busque el área de trabajo del panel de respuesta ante emergencias regionales en **Áreas de trabajo** y siga las instrucciones descritas en el artículo [Configuración de la actualización programada](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizar y compartir

Vea [Personalización y uso compartido de la aplicación](../service-template-apps-install-distribute.md#customize-and-share-the-app) para obtener detalles. Asegúrese de revisar las [declinaciones de responsabilidades del informe](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) antes de publicar o distribuir la aplicación.

## <a name="next-steps"></a>Pasos siguientes
* [Descripción del panel de respuesta ante emergencias regionales](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Configuración e información sobre la plantilla de ejemplo de Comunicación de crisis en Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
* [¿Qué son las aplicaciones de plantilla de Power BI?](../service-template-apps-overview.md)
* [Instalación y distribución de aplicaciones de plantilla en la organización](../service-template-apps-install-distribute.md)
