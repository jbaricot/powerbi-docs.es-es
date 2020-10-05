---
title: Conexión a Power BI Premium Capacity Metrics
description: Cómo obtener e instalar la aplicación de plantilla Power BI Premium Capacity Metrics y cómo conectarse a los datos.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/18/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 42526dbae857c6488fe129cc7781672691782de1
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375244"
---
# <a name="connect-to-power-bi-premium-capacity-metrics"></a>Conexión a Power BI Premium Capacity Metrics

La supervisión de las capacidades es esencial para tomar decisiones fundamentadas sobre el uso óptimo de los recursos de capacidad Premium. La aplicación Power BI Premium Capacity Metrics proporciona la información más detallada sobre el rendimiento de las capacidades.

![Informe de la aplicación Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-report.png)

En este artículo se describe cómo instalar la aplicación y conectarse a los orígenes de datos. Para obtener información sobre el contenido del informe y cómo usarlo, consulte [Supervisión de capacidades Premium con la aplicación](../admin/service-admin-premium-monitor-capacity.md) y [Entrada de blog de la aplicación Premium Capacity Metrics](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/).

Después de instalar la aplicación y conectarse a los orígenes de datos, puede personalizar el informe según sus necesidades. Luego puede distribuirlo entre los compañeros de su organización.

> [!NOTE]
> La instalación de aplicaciones de plantilla requiere [permisos](./service-template-apps-install-distribute.md#prerequisites). Si no tiene permisos suficientes, póngase en contacto con el administrador de Power BI.

## <a name="install-the-app"></a>Instalación de la aplicación

1. Haga clic en el vínculo siguiente para obtener la aplicación: [Aplicación de plantilla Power BI Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. En la página AppSource de la aplicación, seleccione [**OBTENER AHORA**](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt).

    [![Aplicación Power BI Premium Capacity Metrics en AppSource](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-appsource-get-it-now.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_pcmm.capacity-metrics-dxt)

1. Seleccione **Instalar**. 

    ![Instalación de la aplicación Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metric-select-install.png)

    > [!NOTE]
    > Si ha instalado la aplicación previamente, se le preguntará si desea [sobrescribir esa instalación](./service-template-apps-install-distribute.md#update-a-template-app) o instalarla en una nueva área de trabajo.

    Una vez instalada la aplicación, la verá en la página Aplicaciones.

   ![Aplicación Power BI Premium Capacity Metrics en la página de la aplicación](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Conectarse a orígenes de datos

1. Seleccione el icono de la página Aplicaciones para abrir la aplicación.

1. En la pantalla de presentación, seleccione **Explorar**.

   ![Pantalla de presentación de la aplicación de plantilla](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-splash-screen.png)

   La aplicación se abre y muestra los datos de ejemplo.

1. Seleccione el vínculo **Conectar los datos** en el banner de la parte superior de la página.

   ![Vínculo de conexión de datos de la aplicación Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-connect-data.png)

1. En el cuadro de diálogo que se abre, establezca la diferencia horaria con UTC, es decir, la diferencia en horas entre la hora universal coordinada y la hora de la ubicación. A continuación, haga clic en **Siguiente**.
  
   ![Cuadro de diálogo de establecimiento de UTC de la aplicación Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-setutc-dialog.png)
   **Nota: El formato de media hora debe ser decimal (por ejemplo: 5,5, 2,5, etc.).**

1. En el siguiente cuadro de diálogo que aparece, no tiene que hacer nada. Tan solo seleccione **Iniciar sesión**.

   ![Cuadro de diálogo de autenticación de la aplicación Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-authentication-dialog.png)

1. En la pantalla de inicio de sesión de Microsoft, inicie sesión en Power BI.

   ![Pantalla de inicio de sesión de Microsoft](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-microsoft-login.png)

   Una vez que haya iniciado sesión, el informe se conectará a los orígenes de datos y se rellenará con datos actualizados. Durante este tiempo se activará el monitor de actividad.

   ![Actualización en curso de la aplicación Power BI Premium Capacity Metrics](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-refresh-monitor.png)

   Los datos del informe se actualizarán automáticamente una vez al día, a menos que haya deshabilitado esta opción durante el proceso de inicio de sesión. También puede [configurar su propia programación de actualización](./refresh-scheduled-refresh.md) para mantener actualizados los datos del informe si así lo quiere.

## <a name="customize-and-share"></a>Personalizar y compartir

Para iniciar la personalización de la aplicación, haga clic en el icono de lápiz en la esquina superior derecha.

 ![Icono Editar](media/service-connect-to-pbi-premium-capacity-metrics/service-pbi-premium-capacity-metrics-app-customize.png)

Vea [Personalización y uso compartido de la aplicación](./service-template-apps-install-distribute.md#customize-and-share-the-app) para obtener detalles.

## <a name="next-steps"></a>Pasos siguientes
* [Supervisión de capacidades Premium con la aplicación](../admin/service-admin-premium-monitor-capacity.md)
* [Entrada de blog de la aplicación Premium Capacity Metrics](https://powerbi.microsoft.com/blog/premium-capacity-metrics-app-new-health-center-with-kpis-to-explore-relevant-metrics-and-steps-to-mitigate-issues/)
* [¿Qué son las aplicaciones de plantilla de Power BI?](./service-template-apps-overview.md)
* [Instalación y distribución de aplicaciones de plantilla en la organización](./service-template-apps-install-distribute.md)
* ¿Tiene preguntas? [Pruebe a plantearlas en la Comunidad de Power BI](https://community.powerbi.com/)