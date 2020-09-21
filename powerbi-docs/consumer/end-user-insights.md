---
title: Ejecución y visualización de conclusiones en los iconos del panel
description: Como usuario final de Power BI, aprenda cómo obtener conclusiones sobre los iconos del panel.
author: mihart
ms.reviewer: mihart
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 09/09/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 21bccbd11f8d2060b648e22c8ed8aa9471c820f0
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642553"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Visualización de conclusiones de datos en los iconos del panel con Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Cada [icono](end-user-tiles.md) de objeto visual del panel es una puerta de entrada a la exploración de datos. Cuando se selecciona un icono, se abre un informe o las [Preguntas y respuestas](end-user-q-and-a.md), donde puede filtrar y ordenar, así como profundizar en el conjunto de datos subyacente al informe. Y al extraer información, Power BI realiza la exploración de datos por usted.

![Modo de menú de puntos suspensivos que muestra Ver información como una opción](./media/end-user-insights/power-bi-insight.png)

Extraiga información para generar objetos visuales interactivos interesantes basados en los datos. Se puede extraer información en un icono de un panel específico e incluso conclusiones a partir de información detallada.

La característica de información se basa en un creciente [conjunto de algoritmos de análisis avanzados](end-user-insight-types.md) desarrollado junto con Microsoft Research, que vamos a seguir usando para que más personas encuentren información en sus datos de formas nuevas e intuitivas.

## <a name="run-insights-on-a-dashboard-tile"></a>Información en un icono del panel
Al extraer información en un icono de panel, Power BI busca solo los datos utilizados para crear ese icono de panel único. 

1. [Abra un panel](end-user-dashboards.md).
2. Mantenga el puntero encima de un icono. Seleccione **Más opciones** (...) y elija **Ver información**. 

    ![Captura de pantalla en la que se muestra que, al seleccionar los puntos suspensivos, se abre el menú desplegable](./media/end-user-insights/power-bi-hover.png)


3. El icono se abre en [modo de enfoque](end-user-focus.md) con las tarjetas de información a la derecha.    
   
    ![Modo de enfoque](./media/end-user-insights/power-bi-insights-tiles.png)    
4. ¿Alguna información capta su interés? Seleccione esa tarjeta de información para profundizar aún más. A la izquierda, se muestra la información seleccionada y, a la derecha, nuevas tarjetas de información, basadas solo en los datos de esa única información.    

 ## <a name="interact-with-the-insight-cards"></a>Interacción con las tarjetas de información
Una vez que tenga abierta una conclusión, siga explorando.

   * Filtre el objeto visual en el lienzo.  Para mostrar los filtros, en la esquina superior derecha, seleccione la flecha para expandir el panel Filtros.

      ![Tarjeta de información con el menú Filtros expandido](./media/end-user-insights/power-bi-filter.png)
   
   * Información en la propia tarjeta. A esto se le conoce como **información relacionada**. Seleccione una tarjeta de información para activarla. Se moverá a la izquierda del lienzo del informe y, a la derecha, se mostrarán nuevas tarjetas basadas solamente en los datos de esa única tarjeta.
   
      ![Información relacionada y menú Filtros expandido](./media/end-user-insights/power-bi-insights-card.png)
   
     
Para volver al informe, en la esquina superior izquierda, seleccione **Salir del modo de enfoque**.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- **Ver información** no funciona con todos los tipos de iconos del panel. Por ejemplo, no está disponible para los objetos visuales personalizados de Power BI.<!--[Power BI visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Pasos siguientes

Ejecutar información detallada en los objetos visuales de informe [mediante la característica de análisis](end-user-analyze-visuals.md)    
Obtenga información acerca de los [tipos de información detallada disponibles](end-user-insight-types.md)

