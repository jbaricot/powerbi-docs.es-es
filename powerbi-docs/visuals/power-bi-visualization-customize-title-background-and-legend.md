---
title: Introducción al formato de las visualizaciones de Power BI
description: Personalización de los títulos, los fondos, las etiquetas y las leyendas de las visualizaciones
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: removed
ms.custom: video-OgjX-pFGgfM, video-RE4IY3L
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 1/13/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 8cfba48839f4055c7d48bf01a475cf2804053239
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/02/2021
ms.locfileid: "99422338"
---
# <a name="customize-visualization-titles-backgrounds-labels-and-legends"></a>Personalización de los títulos, los fondos, las etiquetas y las leyendas de las visualizaciones

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

En este tutorial obtendrá información sobre diferentes formas de personalizar las visualizaciones. Hay numerosas opciones para personalizar las visualizaciones. La mejor manera para obtener información de todas ellas es explorando el panel **Formato** (seleccione el icono de rodillo de pintura). Para ayudarle a comenzar, en este artículo se muestra cómo personalizar un título, una leyenda, un fondo, una etiqueta o una capa de una visualización y cómo agregar un tema.

No se pueden personalizar todas las visualizaciones. Consulte la [lista completa](#visualization-types-that-you-can-customize) de visualizaciones para obtener más información.

## <a name="prerequisites"></a>Requisitos previos

- Servicio Power BI o Power BI Desktop

- Informe del ejemplo de análisis de minoristas

> [!NOTE]
> Para compartir el informe con un compañero en Power BI es necesario que los dos tengan licencias de Power BI Pro individuales o que el informe esté guardado en la capacidad Premium. Consulte [Filtrado y uso compartido de un informe de Power BI](../collaborate-share/service-share-reports.md).

## <a name="customize-visualization-titles-in-reports"></a>Personalización de los títulos de las visualizaciones en los informes

Para continuar, inicie sesión en Power BI Desktop y abra el informe [Ejemplo de análisis de minoristas](../create-reports/sample-datasets.md).

> [!NOTE]
> Al anclar una visualización a un panel, se convierte en un icono de panel. Los iconos también se pueden personalizar con [nuevos títulos y subtítulos, hipervínculos y cambios de tamaño](../create-reports/service-dashboard-edit-tile.md).

1. Vaya a la página **Nuevas tiendas** del informe **Ejemplo de análisis de minoristas**.

1. Seleccione el gráfico de columnas agrupadas **Recuento de tiendas abiertas por mes abierto y cadena** gráfico de columnas agrupadas.

1. En el panel **Visualizaciones**, seleccione el icono de rodillo para mostrar las opciones de formato.

1. Seleccione **Título** para expandir esa sección.

   ![Captura de pantalla del panel Formato con el icono de rodillo resaltado y una flecha al menú desplegable Título.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-format-menu.png)

1. Mueva el control deslizante de **Título** a **Activar**.

1. Para cambiar el texto del título, escriba *Recuento de tiendas por mes de apertura* en el campo **Texto del título**.

    ![Captura de pantalla del panel Formato con el texto Título escrito.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-title.png)

1. Cambie el **color de fuente** a blanco y el **color de fondo** a azul.

    a. Seleccione la lista desplegable y elija un color en **Colores del tema**, **Colores recientes** o **Color personalizado**.

    ![Captura de pantalla de las opciones de color de fuente y color de fondo.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-color.png)

    b. Seleccione el menú desplegable para cerrar la ventana de colores.

1. Aumente el tamaño del texto a **16 puntos**.

1. La última personalización que haremos en el título del gráfico es alinearlo en el centro de la visualización.

    ![Captura de pantalla de los controles de alineación con la opción Centrar seleccionada.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-align.png)

    En este punto del tutorial, el título del gráfico de columnas agrupadas tendrá un aspecto similar al siguiente:

    ![Captura de pantalla del gráfico de columnas agrupadas recién configurado.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-table.png)

Guarde los cambios realizados y pase a la sección siguiente.

Si necesita revertir todos los cambios, seleccione **Volver al valor predeterminado** en la parte inferior del panel de personalización **Título**.

![Captura de pantalla de la opción Volver al valor predeterminado.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-revert.png)

## <a name="customize-visualization-backgrounds"></a>Personalización del fondo de la visualización

Con el mismo gráfico de columnas agrupadas seleccionado, expanda las opciones de **Fondo**.

1. Mueva el control deslizante de **Fondo** a **Activar**.

1. Seleccione el menú desplegable y elija un color gris.

1. Cambie la **transparencia** al **74 %** .

En este punto del tutorial, el fondo del gráfico de columnas agrupadas tendrá un aspecto similar al siguiente:

![Captura de pantalla del gráfico de columnas agrupadas con color de fondo actualizado.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-background.png)

Guarde los cambios realizados y pase a la sección siguiente.

Si necesita revertir todos los cambios, seleccione **Volver al valor predeterminado** en la parte inferior del panel de personalización **Fondo**.

## <a name="customize-visualization-legends"></a>Personalización de las leyendas de la visualización

1. Abra la página de informe **Introducción** y seleccione el gráfico **Varianza total de ventas por mes fiscal y administrador del distrito**.

1. Seleccione el icono del rodillo de pintura para abrir el panel Formato en la pestaña **Visualización**.

1. Expanda las opciones de **Leyenda**:

    ![Captura de pantalla de la tarjeta Leyenda.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-legends.png)

1. Mueva el control deslizante de **Leyenda** a **Activar**.

1. Mueva la leyenda a la izquierda de la visualización.

1. Agregue un título a la leyenda cambiando **Título** a **Activar**.

1. Escriba *Administrador* en el campo **Nombre de leyenda**.

1. Cambie el **color** a negro.

Guarde los cambios realizados y pase a la sección siguiente.

Si necesita revertir todos los cambios, seleccione **Volver al valor predeterminado** en la parte inferior del panel de personalización **Leyenda**.

## <a name="customize-total-labels-for-stacked-visuals"></a>Personalización de las etiquetas totales para objetos visuales apilados

Los objetos visuales apilados pueden mostrar las etiquetas de datos y las etiquetas totales. En un gráfico de columnas apiladas, las etiquetas de datos identifican el valor de cada parte de una columna. Las etiquetas totales muestran el valor total de toda la columna agregada. 

Vea como Rien agrega las etiquetas locales a un gráfico apilado y, luego, siga los pasos siguientes para intentarlo usted mismo.

> [!VIDEO https://www.youtube.com/embed/OgjX-pFGgfM]

1. Abra la página del informe **Información general** y seleccione el gráfico de barras **Promedio de tamaño de área de ventas por cadena y tipo de tienda**.

1. En la pestaña **Visualización**, seleccione el ![icono del gráfico de barras apiladas](media/power-bi-visualization-customize-title-background-and-legend/power-bi-stacked-bar.png) para convertir este gráfico de barras en un gráfico de barras apiladas. Observe que el objeto visual conserva sus etiquetas de datos.

    ![Captura de pantalla del gráfico de barras apiladas nuevo.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-stacked-chart.png)

1. Seleccione el icono del rodillo de pintura para abrir el panel Formato en la pestaña **Visualización**.

1. Mueva el control deslizante **Etiquetas totales** a **Activado**. 

    ![Captura de pantalla que muestra el control deslizante de etiquetas totales establecido en Activado.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-totals.png)

1. También puede dar formato a las etiquetas totales. En este ejemplo, el color se cambió a blanco, se aumentó el tamaño de la fuente y se optó por mostrar los valores como **Miles**.

    ![Captura de pantalla del gráfico de barras apiladas nuevo con las etiquetas totales.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-bar-totals.png)

## <a name="customize-layer-order"></a>Personalización del orden de las capas

Cambie el orden de las capas de los objetos visuales y las formas de los informes. El orden de las capas determina qué objetos aparecen delante cuando se seleccionan. Siempre que se selecciona un objeto en el lienzo del informe, se activa y se desplaza a la capa superior. En el caso de los objetos visuales, esto facilita la interacción con el objeto visual seleccionado. Pero en el caso de las formas y los fondos, se recomienda protegerlos en el nivel inferior, de modo que no se puedan seleccionar accidentalmente y cubran u oculten los objetos visuales del informe. 

Los controles de las capas están disponibles en el servicio Power BI, Power BI Desktop, Mobile y Report Server. En este artículo se muestra cómo cambiar el comportamiento del orden de las capas en el servicio Power BI.

Vea cómo Rien cambia el orden de las capas y luego siga los pasos para intentarlo por sí mismo.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4IY3L]

1. Agregue una nueva página de informe al seleccionar el signo más amarillo.

1. Agregue una forma al lienzo. Aquí se ha agregado un rectángulo azul.

    ![Captura de pantalla de la nueva página de informe con un rectángulo azul.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-shape.png)

1. Copie y pegue un objeto visual de otra página del informe.

    ![Captura de pantalla de la nueva página de informe con un rectángulo azul y un gráfico circular.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-layer.png)

    Ahora que hay 2 capas, intente seleccionar el gráfico circular y luego el fondo. Al seleccionar el gráfico circular, Power BI activa ese objeto y muestra su menú de encabezado. Al seleccionar el rectángulo, Power BI activa ese objeto y lo coloca en la parte delantera, donde oculta el gráfico circular. Puede cambiar este comportamiento predeterminado.

1. Seleccione el rectángulo y abra el panel Formato. Expanda **General** y busque el botón de alternancia **Mantener orden de las capas**. Guarde los cambios del informe y cambie a la vista de lectura.

    ![Captura de pantalla de la nueva página de informe y Mantener orden de las capas establecido en Activado.](media/power-bi-visualization-customize-title-background-and-legend/power-bi-maintain-layer.png)

1. En la vista de lectura, al seleccionar el rectángulo azul, se mantiene en la capa de detrás.

## <a name="customize-colors-using-a-theme"></a>Personalizar los colores con un tema

Con los temas para informes puede aplicar cambios de diseño a todo el informe; por ejemplo, usar colores corporativos, cambiar conjuntos de iconos o aplicar nuevos formatos visuales predeterminados. Al aplicar un tema para informe, todos los objetos visuales del informe usan los colores y el formato del tema seleccionado.

Para aplicar un tema a un informe, seleccione **Cambiar tema** en la barra de menús. Elija un tema.  El siguiente informe usa el tema **Solar**.

![Informe con el tema Solar de amarillos, naranjas y rojos](media/power-bi-visualization-customize-title-background-and-legend/power-bi-theme.png)

## <a name="visualization-types-that-you-can-customize"></a>Tipos de visualización que se pueden personalizar

A continuación, encontrará una lista de las visualizaciones y opciones de personalización que están disponibles para cada tipo:

| Visualización | Título | Fondo | Leyenda | Etiquetas totales
|:--- |:--- |:--- |:--- |:--- |
| Área | sí | sí |sí | sí  |
| Barra | sí | sí |sí | sí |
| Tarjeta | sí | sí |N/D | N/D |
| Tarjeta de varias filas | sí | sí | N/D | n/d |
| Columna | sí | sí | sí |  sí |
| Combinado | sí | sí | sí | sí |
| Anillo | sí | sí | sí | N/D |
| Mapa coroplético | sí | sí | sí |n/d |
| Embudo | sí | sí | N/D |N/D |
| Medidor | sí | sí | N/D |N/D |
| Influenciador clave | sí | sí | N/D |N/D |
| KPI | sí | sí | N/D |N/D |
| Línea | sí | sí | sí |n/d |
| Mapa | sí | sí | sí |n/d |
| Matriz | sí | sí | N/D |sí |
| Gráfico circular | sí | sí | sí |N/D |
| Preguntas y respuestas | sí | sí | N/D |N/D |
| Dispersión | sí | sí | sí |n/d |
| Forma | sí | sí | sí |n/d |
| Segmentación | sí | sí | N/D |N/D |
| Tabla | sí | sí | N/D |sí |
| Cuadro de texto | no | sí | N/D |N/D |
| Gráfico de rectángulos | sí | sí | sí |n/d |
| Cascada | sí | sí | sí |n/a |

## <a name="next-steps"></a>Pasos siguientes

- [Personalización de las propiedades de los ejes X e Y](power-bi-visualization-customize-x-axis-and-y-axis.md)

- [Introducción a las propiedades de eje y formato de color](service-getting-started-with-color-formatting-and-axis-properties.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
