---
title: Conexión al Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias
description: Procedimientos a fin de obtener e instalar el Panel de ayuda para la toma de decisiones de la COVID-19 para la aplicación de plantilla de emergencias sanitarias y cómo conectarse a los datos
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/13/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 40a585c78de4a95981ff157413e857b48fd35c14
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407580"
---
# <a name="connect-to-the-hospital-emergency-response-decision-support-dashboard"></a>Conexión al Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias
La aplicación de plantilla del Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias es el componente de informes de la [solución de Power Platform para la respuesta ante emergencias sanitarias](https://powerapps.microsoft.com/blog/emergency-response-solution-a-microsoft-power-platform-solution-for-healthcare-emergency-response/). El panel muestra que los administradores de emergencia agregan datos a través de su sistema de mantenimiento para ayudarles a tomar decisiones oportunas y correctas.

![Informe de la aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-report.png)

En este artículo se explica cómo instalar la aplicación y cómo conectarse a los orígenes de datos. Para obtener información sobre cómo usar el informe que verá con esta aplicación, consulte la [documentación del Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard).

Después de instalar la aplicación de plantilla y conectarse a los orígenes de datos, puede personalizar el informe según sus necesidades. Luego puede distribuirlo como una aplicación entre los compañeros de su organización.

## <a name="prerequisites"></a>Requisitos previos

Antes de instalar esta aplicación de plantilla, primero debe instalar y configurar la [solución Respuesta ante emergencias hospitalarias de Power Platform](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure). Al instalar esta solución, se crean las referencias de orígenes de datos necesarias para rellenar la aplicación con datos.

Al instalar la solución de Power Platform Respuesta ante emergencias hospitalarias, tome nota de la [dirección URL de la instancia del entorno Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). La necesitará para conectar la aplicación de plantilla a los datos.

## <a name="install-the-app"></a>Instalación de la aplicación

1. Haga clic en el vínculo siguiente para obtener la aplicación: [Aplicación de plantilla del Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](https://aka.ms/AppSource_Hospital_offer)

1. En la página AppSource de la aplicación, seleccione [**OBTENER AHORA**](https://aka.ms/AppSource_Hospital_offer).

    [![Aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias en AppSource](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-appsource-get-it-now.png)](https://aka.ms/AppSource_Hospital_offer)

1. Lea la información en **Una cosa más** y seleccione **Continuar**.

    ![Aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias, Una cosa más](media/service-connect-to-health-emergency-response/service-health-emergency-response-1-more-thing.png)

1. Haga clic en **Instalar**. 

    ![Instalación de la aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](media/service-connect-to-health-emergency-response/service-health-emergency-response-select-install.png)

    Una vez instalada la aplicación, la verá en la página Aplicaciones.

   ![Aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias en la página de Aplicaciones](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Conexión a orígenes de datos

1. Seleccione el icono de la página Aplicaciones para abrir la aplicación.

1. En la pantalla de presentación, seleccione **Explorar**.

   ![Pantalla de presentación de la aplicación de plantilla](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-splash-screen.png)

   La aplicación se abre y muestra los datos de ejemplo.

1. Seleccione el vínculo **Conectar los datos** en el banner de la parte superior de la página.

   ![Vínculo Conectar los datos de la aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-connect-data.png)

1. En el cuadro de diálogo, haga lo siguiente:
   1. En el campo Nombre de la organización, escriba el nombre de la organización como, por ejemplo, "Contoso Health Systems". Este campo es opcional. Este nombre aparece en la parte superior izquierda del panel.
   1. En el campo CDS_base_solution, escriba la [dirección URL del de la instancia del entorno Common Data Service](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Por ejemplo: https://[myenv].crm.dynamics.com. Cuando termine, haga clic en **Siguiente**.

   ![Cuadro de diálogo de la dirección URL de la aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-url-dialog.png)

1. En el cuadro de diálogo siguiente que aparece, establezca el método de autenticación en **OAuth2**. No tiene que hacer nada en lo que respecta a la configuración de nivel de privacidad.

   Seleccione **Iniciar sesión**.

   ![Cuadro de diálogo de la autenticación de la aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-authentication-dialog.png)

1. En la pantalla de inicio de sesión de Microsoft, inicie sesión en Power BI.

   ![Pantalla de inicio de sesión de Microsoft](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-microsoft-login.png)

   Una vez que haya iniciado sesión, el informe se conectará a los orígenes de datos y se rellenará con datos actualizados. Durante este tiempo se activará el monitor de actividad.

   ![Actualización en curso de la aplicación Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Programación de la actualización del informe

Cuando se haya completado la actualización de los datos, [configure una programación de actualización](../connect-data/refresh-scheduled-refresh.md) para mantener actualizados los datos del informe.

1. En la barra de encabezado superior, seleccione **Power BI**.

   ![Ruta de navegación de Power BI](media/service-connect-to-health-emergency-response/service-health-emergency-response-app-powerbi-breadcrumb.png)

1. En el panel de navegación izquierdo, busque el área de trabajo del Panel de ayuda para la toma de decisiones en respuesta ante emergencias hospitalarias en **Áreas de trabajo** y siga las instrucciones descritas en el artículo [Configuración de la actualización programada](../connect-data/refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Personalizar y compartir

Vea [Personalización y uso compartido de la aplicación](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) para obtener detalles. Asegúrese de revisar las [declinaciones de responsabilidades del informe](../create-reports/sample-covid-19-us.md#disclaimers) antes de publicar o distribuir la aplicación.

## <a name="next-steps"></a>Pasos siguientes
* [Descripción del informe de Respuesta ante emergencias hospitalarias](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#view-the-power-bi-dashboard)
* [Configuración e información sobre la plantilla de ejemplo de Comunicación de crisis en Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
* [¿Qué son las aplicaciones de plantilla de Power BI?](../connect-data/service-template-apps-overview.md)
* [Instalación y distribución de aplicaciones de plantilla en la organización](../connect-data/service-template-apps-install-distribute.md)
