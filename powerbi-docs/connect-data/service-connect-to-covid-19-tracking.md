---
title: Conexión al informe de seguimiento de la COVID-19 en EE. UU.
description: Cómo obtener e instalar la aplicación de plantilla Casos de la COVID-19 en EE. UU. y cómo conectarse a los datos.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/05/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: fc421f7635a3d6e3b2336d5bce081d7914c0fad5
ms.sourcegitcommit: 8250187368d3de48663eb516a816ff701119b579
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96998873"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>Conexión al informe de seguimiento de la COVID-19 en EE. UU.
En este artículo se explica cómo instalar la aplicación de plantilla para el informe de seguimiento de la COVID-19 y cómo conectarse a los orígenes de datos.

![Informe de seguimiento de la COVID-19 en EE. UU.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

Para obtener información detallada sobre el propio informe, incluidas las declinaciones de responsabilidad e información sobre los datos, vea [Ejemplo de seguimiento de la COVID-19 para los gobiernos estatales y locales de EE. UU.](../create-reports/sample-covid-19-us.md).

Después de instalar la aplicación de plantilla y conectarse a los orígenes de datos, puede personalizar el informe según sus necesidades. Luego puede distribuirlo como una aplicación entre los compañeros de su organización.

## <a name="install-the-app"></a>Instalación de la aplicación

1. Haga clic en el vínculo siguiente para obtener la aplicación: [Aplicación de plantilla del Informe de seguimiento de la COVID-19 en EE. UU.](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. Una vez que esté en la página de AppSource de la aplicación, haga clic en [**OBTENER AHORA**](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms).

    [![Informe de seguimiento de la COVID-19 en EE. UU. en AppSource](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. Cuando se le solicite, haga clic en **Instalar**. Una vez instalada la aplicación, la verá en la página Aplicaciones.

   ![Informe de seguimiento de la COVID-19 en EE. UU. en la página Aplicaciones](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Conexión a orígenes de datos

1. Haga clic en el icono de la página Aplicaciones para abrir la aplicación. La aplicación se abre y muestra los datos de ejemplo.

1. Seleccione el vínculo **Conectar los datos** en el banner de la parte superior de la página.

   ![Vínculo de conexión de datos de la aplicación de GitHub](media/service-connect-to-covid-19-tracking/power-bi-covid-19-connect-data.png)

1. Aparecerá el cuadro de diálogo Parámetros. No hay parámetros obligatorios. Haga clic en **Next**.

   ![Captura de pantalla del cuadro de diálogo de parámetros del informe de seguimiento de la COVID-19 en EE. UU.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-parameters-dialog.png)

1. Aparecerá el cuadro de diálogo Método de autenticación. Los valores recomendados están rellenados previamente. No los cambie a menos que tenga un conocimiento específico de los distintos valores que se pueden seleccionar.

    Haga clic en **Next**.

   ![Captura de pantalla del cuadro de diálogo Autenticación del Informe de seguimiento de la COVID-19 en EE. UU.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-authentication-dialog.png)

1. Haga clic en **Iniciar sesión**.

   ![Captura de pantalla del cuadro de diálogo Inicio de sesión del Informe de seguimiento de la COVID-19 en EE. UU.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)
 
   El informe se conectará a los orígenes de datos y se rellenará con datos actualizados. Durante este tiempo, verá datos de ejemplo y que la actualización está en curso.

   ![Actualización en curso del Informe de seguimiento de la COVID-19 en EE. UU.](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Programación de la actualización del informe

Cuando se haya completado la actualización de datos, estará en el área de trabajo asociada a la aplicación. [Configure una programación de actualización](../connect-data/refresh-scheduled-refresh.md) para mantener actualizados los datos del informe.

## <a name="customize-and-share"></a>Personalizar y compartir

Vea [Personalización y uso compartido de la aplicación](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app) para obtener detalles. Asegúrese de revisar las [declinaciones de responsabilidades del informe](../create-reports/sample-covid-19-us.md#disclaimers) antes de publicar o distribuir la aplicación.

## <a name="next-steps"></a>Pasos siguientes
* [Ejemplo de seguimiento de la COVID-19 para gobiernos locales y estatales de EE. UU.](../create-reports/sample-covid-19-us.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
* [¿Qué son las aplicaciones de plantilla de Power BI?](../connect-data/service-template-apps-overview.md)
* [Instalación y distribución de aplicaciones de plantilla en la organización](../connect-data/service-template-apps-install-distribute.md)
