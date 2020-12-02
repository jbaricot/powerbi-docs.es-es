---
title: Generación de conclusiones sobre los datos del conjunto de datos de manera automática
description: Vea cómo obtener información detallada acerca de los conjuntos de datos y los iconos del panel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 09/28/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: 8db804ec3afe4b752ab6f5f8546782cac7135055
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388480"
---
# <a name="generate-data-insights-on-your-dataset-automatically-with-power-bi"></a>Generación de conclusiones sobre los datos del conjunto de datos de manera automática con Power BI
¿Tiene un conjunto de datos nuevo y no está seguro de por dónde empezar?  ¿Necesita crear un panel rápidamente?  ¿Quiere buscar información que puede que le falte?

Extraiga conclusiones rápidas para generar visualizaciones interactivas interesantes basadas en los datos. En este artículo se explica cómo extraer conclusiones rápidas de todo un conjunto de datos. También puede extraer [conclusiones rápidas de un icono específico del panel](../consumer/end-user-insights.md) (conclusiones con ámbito). Puede incluso extraer información detallada a partir de información detallada.

> [!NOTE]
> Información detallada no funciona con DirectQuery, solo con los datos cargados en Power BI.
> 

La característica de conclusiones rápidas se ha creado sobre un creciente [conjunto de algoritmos analíticos avanzados](../consumer/end-user-insight-types.md) desarrollados con Microsoft Research. Estos algoritmos continúan usándose para ayudar a que más personas extraigan conclusiones de sus datos de formas nuevas e intuitivas. También puede interesarle aprender a [optimizar los datos para obtener conclusiones rápidas](service-insights-optimize.md).

## <a name="run-quick-insights-on-a-dataset"></a>Extracción de información rápida de un conjunto de datos
Vea cómo Amanda extrae conclusiones rápidas de un conjunto de datos y abre una de ellas en modo de enfoque. Amanda ancla una de las conclusiones como un icono en el panel y, luego, obtiene conclusiones de un icono del panel.

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


Ahora es su turno. Explore la característica de información detallada mediante el [Ejemplo de análisis de calidad de proveedores](sample-supplier-quality.md).

1. En la pestaña **Conjuntos de datos**, seleccione el botón **Más opciones** (...) y elija **Obtener información rápida**.
   
    ![Pestaña Conjuntos de datos](media/service-insights/power-bi-ellipses.png)
   
    ![Menú de puntos suspensivos](media/service-insights/power-bi-tab.png)
2. Power BI usa [distintos algoritmos](../consumer/end-user-insight-types.md) para buscar tendencias en el conjunto de datos.
   
    ![Cuadro de diálogo Buscando información](media/service-insights/pbi_autoinsightssearching.png)
3. Su información está lista en cuestión de segundos.  Seleccione **Ver información** para mostrar visualizaciones.
   
    ![Mensaje de proceso correcto](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > Algunos conjuntos de datos no pueden generar información porque los datos no son estadísticamente significativos.  Para más información, consulte [Optimización de los datos para información detallada](service-insights-optimize.md).
    > 
    
4. Las visualizaciones se muestran en un lienzo especial de **información rápida** con un máximo 32 tarjetas de información independientes. Cada tarjeta tiene un gráfico o un gráfico con una breve descripción.
   
    ![Lienzo Información rápida](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>Interacción con las tarjetas de información

1. Mantenga el puntero sobre una tarjeta y seleccione el icono de anclaje para agregar la visualización a un panel.

2. Mantenga el puntero sobre una tarjeta, seleccione **Más opciones** (...) y elija **Ver información**. 

    Se abre la pantalla de información en modo de enfoque.
   
    ![Modo de enfoque de información](media/service-insights/power-bi-insight-focus.png)
3. En el Modo enfocado, puede:
   
   * Filtrar las visualizaciones. Si el panel **Filtros** todavía no está abierto, seleccione la flecha situada en el lado derecho de la ventana para expandirlo.

       ![Menú Filtros de Información expandido](media/service-insights/power-bi-insights-filter-new.png)
   * Anclar la tarjeta de conclusiones a un panel mediante la selección **Anclar visualización**.
   * Ejecute información en la propia tarjeta, lo que a menudo se conoce como *información con ámbito*. En la esquina superior derecha, seleccione el icono de bombilla ![icono Obtener información](media/service-insights/power-bi-bulb-icon.png) u **Obtener información**.
     
       ![Icono Obtener información](media/service-insights/pbi-autoinsights-tile.png)
     
     La conclusión se muestra a la izquierda. Las nuevas tarjetas, basadas únicamente en los datos de esa única conclusión, se muestran a la derecha.
     
       ![Información sobre información](media/service-insights/power-bi-insights-on-insights-new.png)
4. Para volver al lienzo original de información, en la esquina superior izquierda, seleccione **Salir del modo de enfoque**.

## <a name="next-steps"></a>Pasos siguientes
- Si es propietario de un conjunto de datos, [optimícelo para Conclusiones rápidas](service-insights-optimize.md).
- Obtenga información sobre los [tipos de Conclusiones rápidas disponibles](../consumer/end-user-insight-types.md).

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/).
