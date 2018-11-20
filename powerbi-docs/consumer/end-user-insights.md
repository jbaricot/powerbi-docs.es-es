---
title: Generación automática de información sobre los datos con Power BI
description: Vea cómo obtener información detallada acerca de los conjuntos de datos y los iconos del panel.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/10/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: f68e962eacf04005d83ec0def10cf8e0e24f6e10
ms.sourcegitcommit: dc8b8a2cf2dcc96ccb46159802ebd9342a7fa840
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49112047"
---
# <a name="automatically-generate-data-insights-with-power-bi"></a>Generación automática de información sobre los datos con Power BI
Cada icono de visualización del panel es una puerta de entrada a la exploración de datos. Cuando se selecciona un icono, se abre un informe donde puede filtrar y ordenar la información, así como profundizar en el conjunto de datos subyacente al informe. Y al extraer información, Power BI realiza la exploración de datos por usted.

Extraiga información rápida para generar visualizaciones interactivas interesantes basadas en los datos. Se puede extraer información detallada en un icono de un panel específico e incluso en una perspectiva global.

La característica de información detallada se basa en un creciente [conjunto de algoritmos de análisis avanzados](end-user-insight-types.md) desarrollado en combinación con Microsoft Research, que vamos a seguir usando para que más personas encuentren información en sus datos de formas nuevas e intuitivas.

## <a name="run-insights-on-a-dashboard-tile"></a>Información en un icono del panel
Al extraer información en un icono de panel, Power BI busca solo los datos utilizados para crear ese icono de panel único. 

1. [Abra un panel](end-user-dashboards.md).
2. Mantenga el puntero encima de un icono. Seleccione el botón de puntos suspensivos (...) y elija **Ver información**. 

    ![modo del menú de puntos suspensivos](./media/end-user-insights/power-bi-hover.png)


3. El icono se abre en [modo de enfoque](end-user-focus.md) con las tarjetas de información a la derecha.    
   
    ![Modo de enfoque](./media/end-user-insights/pbi-insights-tile.png)    
4. ¿Alguna información capta su interés? Seleccione esa tarjeta de información para profundizar aún más. A la izquierda, se muestra la información seleccionada y, a la derecha, nuevas tarjetas de información, basadas solo en los datos de esa única información.    

 ## <a name="interact-with-the-insight-cards"></a>Interacción con las tarjetas de información
   * Filtrar las visualizaciones.  Para mostrar los filtros, en la esquina superior derecha, seleccione la flecha para expandir el panel Filtros.

     ![Información y menú Filtros expandido](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * Información en la propia tarjeta. A esto se le conoce como **información relacionada**. En la esquina superior derecha, seleccione el icono de bombilla ![icono de Obtener información](./media/end-user-insights/power-bi-bulb-icon.png) u **Obtener información**.
     
     ![Barra de menús con el icono de Obtener información](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     A la izquierda, se muestra la información y, a la derecha, nuevas tarjetas basadas solo en los datos de esa única información.
     
     ![Información sobre información](./media/end-user-insights/power-bi-insights-on-insights-new.png)

Para volver al lienzo original de información, en la esquina superior izquierda, seleccione **Salir del modo de enfoque**.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
- **Ver información** no funciona con DirectQuery, solo con los datos cargados en Power BI.
- **Ver información** no funciona con todos los tipos de iconos del panel. Por ejemplo, no está disponible para los objetos visuales personalizados.<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>Pasos siguientes
Obtenga información acerca de los [tipos de información rápida disponibles](end-user-insight-types.md)
