---
title: Configuración de presentación de página en un informe de Power BI
description: Configuración de la presentación de página y configuración de la vista de página de un informe
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/29/2019
LocalizationGroup: Reports
ms.openlocfilehash: 9452a4a6340480bcb6c8b646c16125fe73f68235
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393494"
---
# <a name="apply-page-display-settings-in-a-power-bi-report"></a>Aplicación de la configuración de presentación de página en un informe de Power BI
Sabemos que es crítico lograr un diseño de informe perfecto hasta el último detalle. En ocasiones, esto puede resultar complicado, porque puede que usted y sus compañeros de trabajo vean esos informes en pantallas con relaciones de aspecto y tamaños diferentes. 

La vista de pantalla predeterminada es **Ajustar a la página** y el tamaño de pantalla predeterminado es **16:9**. Si quiere fijar otra relación de aspecto o ajustar el informe de forma diferente, hay dos herramientas que le ayudarán: la configuración de **_Vista de página_* _ y las opciones de _*_Tamaño de página_*_.


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>Dónde encontrar la configuración de la Vista de página en el servicio Power BI y en Power BI Desktop
La configuración de la Vista de página está disponible en el servicio Power BI y en Power BI Desktop, pero la interfaz es ligeramente diferente. Las secciones siguientes explican dónde se pueden buscar las configuraciones de Vista en cada herramienta de Power BI.

### <a name="in-power-bi-desktop"></a>En Power BI Desktop
En la vista de informe, seleccione la pestaña -*Vista** para abrir la configuración de la vista de página, así como la configuración del diseño de teléfono.

  ![Configuración de la vista de página de escritorio](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>En el servicio Power BI (app.powerbi.com)
En el servicio Power BI, abra un informe y seleccione **Vista** en la barra de menús de la parte superior izquierda.

![Configuración de la vista de página de servicio](media/power-bi-report-display-settings/power-bi-change-page-view.png)

La configuración de la Vista de página está disponible en [la Vista de lectura y la Vista de edición](../consumer/end-user-reading-view.md). En la Vista de edición, el propietario de un informe puede asignar una configuración de vista de página a las páginas individuales del informe y esa configuración se guarda con el informe. Cuando los compañeros abren ese informe en la vista de lectura, ven las páginas del informe con la configuración del propietario. En la Vista de lectura, los compañeros pueden cambiar *algunas* opciones de la configuración de la **Vista de página**, pero los cambios no se guardarán cuando cierre el informe.

## <a name="page-view-settings"></a>Configuración de la vista de página
El primer conjunto de opciones de la configuración de la Vista de página controla la presentación de la página del informe en relación con la ventana del explorador. Puede elegir entre:

* **Ajustar a la página** (valor predeterminado): el contenido se escala para ajustarse mejor a la página.
* **Ajustar al ancho**: el contenido se escala para ajustarse al ancho de la página.
* **Tamaño real**: el contenido se muestra en tamaño completo.

El segundo conjunto de opciones de la configuración de la Vista de página controla la posición de los objetos en el lienzo del informe. Puede elegir entre:

* **Mostrar líneas de cuadrícula**: activa las líneas de cuadrícula para ayudarle a colocar los objetos en el lienzo del informe.
* **Ajustar a la cuadrícula**: se usa con **Mostrar líneas de cuadrícula** para colocar y alinear de forma precisa objetos en el lienzo del informe. 
* **Bloquear objetos**: bloquea todos los objetos en el lienzo para que no se puedan mover ni cambiar de tamaño.
* **Panel Selección**: El panel **Selección** enumera todos los objetos en el lienzo. Se puede decidir cuáles mostrar y cuáles ocultar.

    ![panel Selección](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>Configuración de Tamaño de página
![Cambio de configuración de Tamaño de página.](media/power-bi-report-display-settings/power-bi-page-size.png)

La configuración del **Tamaño de página** solo está disponible para los propietarios de los informes. En el servicio Power BI (app.powerbi.com), esto significa que se puede abrir el informe en la [Vista de edición](../consumer/end-user-reading-view.md). La configuración de **Tamaño de página** se encuentra en el panel **Visualizaciones** y controla la relación de aspecto de pantalla y el tamaño real (en píxeles) del lienzo del informe:   

* Relación 4:3
* Relación 16:9 (valor predeterminado)
* Carta
* Personalizado (alto y ancho en píxeles)

## <a name="next-steps"></a>Pasos siguientes
[Vista de informes en Power BI Desktop](desktop-report-view.md)

[Cambio en la configuración de Vista de página y Tamaño de página en sus propios informes de Power BI](../consumer/end-user-report-view.md)

Más información sobre [informes de Power BI](../consumer/end-user-reports.md)

[Conceptos básicos para los diseñadores en el servicio Power BI](../fundamentals/service-basic-concepts.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
