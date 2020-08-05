---
title: Paseo por el panel de filtros de informe
description: Procedimiento para agregar un filtro a un informe en el servicio Power BI para consumidores
author: mihart
ms.reviewer: mihart
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 9a6b9dc88c63e430d5f5f24136d34f294d9648b4
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2020
ms.locfileid: "87536501"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Ver el panel Filtros del informe

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

En este artículo se analiza el panel **Filtros** del informe en el servicio Power BI. Use los filtros para descubrir nuevas conclusiones en los datos.

Hay muchas formas diferentes de filtrar los datos en Power BI. Para obtener más información sobre los filtros, vea [Filtros y resaltado en informes de Power BI](../create-reports/power-bi-reports-filters-and-highlighting.md).

![Captura de pantalla de un informe en el explorador con una flecha que apunta a la opción Filtros.](media/end-user-report-filter/power-bi-report.png)

## <a name="working-with-the-report-filters-pane"></a>Trabajar con el panel Filtros de informes

Cuando algún compañero comparta un informe con usted, asegúrese de buscar el panel **Filtros**. A veces se contrae en el borde derecho del informe. Selecciónelo para expandirlo.

![Captura de pantalla del informe con el panel Filtros expandido.](media/end-user-report-filter/power-bi-expand-filter-pane.png)

El panel **Filtros** contiene filtros que el *diseñador* de informes ha agregado al informe. Los *consumidores*, como usted, pueden interactuar con los filtros existentes y guardar los cambios, pero no pueden agregar nuevos filtros al informe. Por ejemplo, en la captura de pantalla anterior el diseñador agregó tres filtros de nivel de página: **Segmento es Todos**, **Año es 2014** y **Región es Central**. Puede cambiar estos filtros e interactuar con ellos, pero no puede agregar un cuarto filtro de nivel de página.

En el servicio Power BI, los informes conservan los cambios que haga en el panel **Filtros**. El servicio lleva esos cambios mediante la versión móvil del informe. 

Para restablecer los valores predeterminados del diseñador en el panel **Filtros**, seleccione **Restablecer valores predeterminados** en la barra de menús superior.

![Captura de pantalla del icono Restablecer valores predeterminados.](media/end-user-report-filter/power-bi-reset-icon.png) 

> [!NOTE]
> Si no ve la opción **Restablecer al valor predeterminado**, es posible que el *diseñador* del informe la haya deshabilitado. El *diseñador* también puede bloquear filtros específicos para que no se puedan cambiar.

## <a name="view-all-the-filters-for-a-report-page"></a>Ver todos los filtros de la página de un informe

En el panel **Filtros** se muestran todos los filtros que ha agregado el diseñador al informe. El panel **Filtros** también es el área donde puede ver información sobre los filtros e interactuar con ellos. Guarde los cambios que haga o use **Restablecer valores predeterminados** para volver a la configuración original de filtro.

Si quiere guardar algún cambio, también puede crear un marcador personal. Para obtener más información, consulte [¿Qué son los marcadores?](end-user-bookmarks.md)

El panel **Filtros** muestra y administra varios tipos de filtros de informe: informe, página del informe y objeto visual.

En este ejemplo, se ha seleccionado un objeto visual que tiene tres filtros. La página del informe también tiene filtros, que aparecen debajo del encabezado **Filtros de esta página**. Además, todo el informe tiene un filtro de **Fecha**.

![Captura de pantalla de un informe con una visualización y sus filtros relacionados destacados.](media/end-user-report-filter/power-bi-filters-pane.png)

Algunos de los filtros tienen **(Todos)** junto a ellos. **(Todos)** implica que se incluyen todos los valores en el filtro. En la captura de pantalla anterior, **Segmento(Todos)** indica que esta página del informe incluye datos sobre todos los segmentos de productos. 

Cualquier persona que vea este informe puede interactuar con estos filtros.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Ver solo esos filtros aplicados a un objeto visual

Para obtener un análisis más detallado de los filtros aplicados a un objeto visual específico, mueva el puntero sobre el objeto visual para mostrar el icono de filtro ![Captura de pantalla del icono de filtro.](media/end-user-report-filter/power-bi-filter-icon.png). Seleccione ese icono de filtro para ver una ventana emergente con todos los filtros, las segmentaciones, etc., que afectan a ese objeto visual. Los filtros de la ventana emergente incluyen los mismos filtros que se muestran en el panel **Filtros**, además de filtrado adicional que afecta al objeto visual seleccionado.

![Captura de pantalla de una lista de filtros con flechas que apuntan a dónde se encuentran esos filtros en el panel Filtros.](media/end-user-report-filter/power-bi-hover-filters.png)

Estos son los tipos de filtros que se pueden mostrar en esta vista:

- Filtros básicos
- Segmentaciones
- Resaltado cruzado
- Filtrado cruzado
- Filtros avanzados
- N filtros principales
- Filtros de fecha relativa
- Segmentaciones de sincronización
- Filtros de inclusión o exclusión
- Filtros que se pasan mediante una dirección URL

En este ejemplo:
1. **Incluido** nos indica que se ha aplicado un filtro cruzado al objeto. Esto significa que los estados de Utah, Colorado y Texas se han seleccionado en uno de los otros objetos visuales de esta página de informe. En este caso, es el mapa. La selección de esos tres estados ha eliminado datos de todos los demás estados en el gráfico de barras seleccionado.  

1. **Fecha** es un filtro que se aplica a todas las páginas de este informe.

1. **Región es Central** y **Año es 2014** son filtros que se aplican a esta página de informe.

4. **Fabricante es VanArsdel, Natura, Aliqui o Pirum** es un filtro que se aplica a este objeto visual.


### <a name="search-in-a-filter"></a>Búsqueda en un filtro

A veces, un filtro puede tener una lista larga de valores. Use el cuadro de búsqueda para buscar y seleccionar el valor que quiera.

![Captura de pantalla del procedimiento para buscar en un filtro.](media/end-user-report-filter/power-bi-search.png)

### <a name="display-filter-details"></a>Mostrar detalles del filtro

Para comprender un filtro, eche un vistazo a los valores y recuentos disponibles.  Para ver los detalles del filtro, mueva el puntero sobre él y seleccione la flecha situada junto al nombre del filtro.
  
![Captura de pantalla de un filtro que muestra la región Oeste seleccionada.](media/end-user-report-filter/power-bi-filter-expand.png)

### <a name="change-filter-selections"></a>Cambiar las selecciones de filtros

Una forma de buscar conclusiones sobre los datos es interactuar con los filtros. Puede cambiar las selecciones de filtros mediante la flecha desplegable situada junto al nombre del campo.  En función del filtro y el tipo de datos que esté filtrando Power BI, sus opciones variarán desde selecciones simples de una lista hasta identificar intervalos de fechas o números. En el filtro avanzado que se muestra a continuación, hemos cambiado el filtro **Total de unidades hasta la fecha** del gráfico de rectángulos para estar entre 2000 y 3000. Fíjese en que este cambio elimina Pirum del gráfico de rectángulos.
  
![Captura de pantalla de un informe y sus filtros que muestra el gráfico de rectángulos seleccionado.](media/end-user-report-filter/power-bi-treemap-filters.png)

> [!TIP]
> Para seleccionar más de un valor de filtro a la vez, mantenga presionada la tecla CTRL. La mayoría de los filtros admiten la selección múltiple.

### <a name="reset-filter-to-default"></a>Restablecer los valores predeterminados del filtro

Si quiere eliminar todos los cambios que ha realizado en los filtros, seleccione **Restablecer valores predeterminados** en la barra de menús superior.  Esta selección devuelve los filtros a su estado original, según lo establecido en el diseñador de informes.

![Captura de pantalla de la opción Restablecer valores predeterminados.](media/end-user-report-filter/power-bi-reset-icon.png)

### <a name="clear-a-filter"></a>Borrado de un filtro

Para restablecer un filtro a (Todos), seleccione el icono de borrador situado junto al nombre del filtro para desactivarlo.

![Captura de pantalla del icono de borrador.](media/end-user-report-filter/power-bi-eraser.png)
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Pasos siguientes

Obtenga información sobre cómo y por qué [los objetos visuales se aplican el filtro cruzado y el resaltado cruzado entre ellos en una página de informe](end-user-interactions.md).
