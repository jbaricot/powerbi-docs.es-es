---
title: Ejemplos de objetos visuales de Power BI
description: En este artículo se presentan ejemplos de objetos visuales de Power BI, entre ellos, segmentaciones, más de 20 tipos de gráficos, WebGL, además de scripts y objetos visuales de R.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 076ad6549cb68660313dcd8da5ccf8eb1f8f26c7
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049163"
---
# <a name="samples-of-power-bi-visuals"></a>Ejemplos de objetos visuales de Power BI

Puede descargar, usar y modificar estos objetos visuales de Power BI desde GitHub. En estos ejemplos se muestra cómo controlar situaciones comunes al desarrollar con Power BI.

## <a name="slicers"></a>Segmentaciones

Una segmentación limita la parte de los datos que se muestra en otras visualizaciones de un informe. Las segmentaciones son una de las distintas formas de filtrar datos en Power BI.

| <img src="media/samples/chiclet-slicer.png" alt="Screenshot shows Chiclet Slicer." width="200">  | <img src="media/samples/timeline-slicer.png" alt="Screenshot shows Timeline slicer." width="200"> | <img src="media/samples/sample-slicer.png" alt="Screenshot shows Slicer sample." width="200">|
| ------------- | ------------- | -------------|
| [Chiclet Slicer](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>Permite mostrar botones de imagen o texto que actúan como filtro en el lienzo en otros objetos visuales. | [Timeline slicer](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>Selector gráfico de intervalo de fechas que filtra por fecha. | [Ejemplo de segmentación](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>Muestra el uso de la API de filtrado avanzado.

## <a name="charts"></a>Gráficos

Inspírese en nuestra galería, donde encontrará, entre otros, gráficos de barras, gráficos circulares o nube de palabras.

| <img src="media/samples/aster-plot.png" alt="Screenshot shows Aster Plot." width="200">  | <img src="media/samples/bullet-chart.png" alt="Screenshot shows Bullet chart." width="200"> | <img src="media/samples/Chord.png" alt="Screenshot shows Chord." width="200">|
| ------------- | ------------- | -------------|
| [Aster Plot](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>Giro en un gráfico de anillos estándar que usa un segundo valor para dirigir el ángulo de barrido. | [Gráfico de viñetas](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>Un gráfico de barras con elementos visuales adicionales que proporcionan un contexto útil para el seguimiento de los objetivos. | [Chord](https://github.com/Microsoft/powerbi-visuals-chord/) </br>Método gráfico que muestra las relaciones entre los datos de una matriz.
| <img src="media/samples/dot-plot.png" alt="Screenshot shows Dot plot." width="200"> | <img src="media/samples/dual-kpi.png" alt="Screenshot shows Dual K P I." width="200">| <img src="media/samples/enhanced-scatter.png" alt="Screenshot shows Enhanced Scatter." width="200"> 
| [Trazado de puntos](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>Muestra la distribución de frecuencias de una forma atractiva. | [Dual KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>Permite visualizar de forma eficiente dos medidas en un período de tiempo y mostrar su tendencia en una escala de tiempo conjunta | [Enhanced Scatter](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>Mejoras en el gráfico de dispersión existente.
| <img src="media/samples/forcegraph.png" alt="Screenshot shows Force Graph." width="200">| <img src="media/samples/gantt.png" alt="Screenshot shows Gantt." width="200">| <img src="media/samples/table-heatmap.png" alt="Screenshot shows Table Heatmap." width="200">
| [Gráfico de fuerzas](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>Diagrama de diseño de fuerzas con trazado curvo, que resulta útil para mostrar conexiones entre entidades. | [Gantt](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>Gráfico de barras que muestra una escala de tiempo del proyecto o la programación con recursos. | [Table Heatmap](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>Permite comparar datos de forma fácil e intuitiva con colores en una tabla.
| <img src="media/samples/histogram-chart.png" alt="Screenshot shows Histogram chart." width="200"> | <img src="media/samples/linedot-chart.png" alt="Screenshot shows LineDot chart." width="200"> | <img src="media/samples/mekko-chart.png" alt="Screenshot shows Mekko chart." width="200"> 
| [Histograma](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>Visualiza la distribución de datos a lo largo de un intervalo continuo o un período de tiempo determinado. | [LineDot chart](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>Gráfico de líneas animado con puntos animados que mantiene el interés del público en los datos. | [Mekko chart](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>Combinación de un gráfico de columnas apiladas al 100 % y un gráfico de barras apiladas al 100 % en una misma vista
| <img src="media/samples/multikpi.png"alt="En la captura de pantalla se muestra Multi KPI." width="200"> | <img src="media/samples/powerkpi.png"alt="En la captura de pantalla se muestra Power KPI." width="200"> | <img src="media/samples/powerkpi-matrix.png"alt="En la captura de pantalla se muestra KPI Matrix." width="200"> 
| [Multi KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> Eficaz visualización de varios KPI con un KPI clave junto con varios minigráficos de datos auxiliares. | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>Eficaz indicador KPI con gráfico de varias líneas y etiquetas para fecha actual, valor y varianzas. | [Power KPI Matrix](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>Supervisión de cuadros de mandos equilibrados y un número ilimitado de métricas y KPI en una lista compacta y fácil de leer.
| <img src="media/samples/pulse-chart.png" alt="Screenshot shows Pulse chart." width="200">| <img src="media/samples/radar-chart.png" alt="Screenshot shows Radar chart." width="200"> | <img src="media/samples/sankey-chart.png" alt="Screenshot shows Sankey chart." width="200"> 
| [Pulse chart](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>Este gráfico de líneas anotado con eventos clave es idóneo para indicar historias con datos.| [Radar chart](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>Presenta varias medidas trazadas sobre un eje de categorías, lo que resulta útil para comparar atributos. | [Sankey chart](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>Diagrama de flujo en el que el ancho de la serie es proporcional a la cantidad del flujo.
| <img src="media/samples/stream-graph.png" alt="Screenshot shows Stream graph." width="200"> | <img src="media/samples/sunburst.png" alt="Screenshot shows Sunburst chart." width="200">| <img src="media/samples/tornado.png" alt="Screenshot shows Tornado chart." width="200">
| [Stream graph](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>Gráfico de áreas apilado con interpolación suave, que a menudo se usa para mostrar valores a lo largo del tiempo. | [Gráfico de proyección solar](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>Gráfico de anillos multinivel para visualizar datos jerárquicos.| [Gráfico de tornado](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>Compara la importancia relativa de las variables entre dos grupos.
 | <img src="media/samples/word-cloud.png" alt="Screenshot shows Word Cloud." width="200">
 | [Word Cloud](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>Cree un objeto visual divertido a partir de textos frecuentes que salen en sus datos

## <a name="webgl"></a>WebGL

WebGL permite que el contenido web use una API basada en OpenGL ES 2.0 para realizar la representación en 2D y 3D en un lienzo HTML.

| <img src="media/samples/globe-map.png" alt="Screenshot shows Globe Map." width="250">|
| ------------- |
| [Mapa de globo terráqueo](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>Trace ubicaciones en un mapa 3D interactivo

## <a name="r-visuals"></a>Objetos visuales de R

En estos ejemplos se muestra cómo aprovechar la eficacia analítica y visual de los objetos visuales de R y los scripts de R.

| <img src="media/samples/association-rules.png" alt="Screenshot shows Association rules." width="200">| <img src="media/samples/clustering.png" alt="Screenshot shows Clustering." width="200">| <img src="media/samples/clustering-with-outliers.png" alt="Screenshot shows Clustering with outliers." width="200">|
|------------- |------------- |------------- |------------- |
| [Association rules](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>Descubra las relaciones que existen entre datos aparentemente no relacionados mediante el uso de instrucciones if-then. | [Clustering](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>Permite encontrar grupos de similitud en los datos mediante el algoritmo k-means. | [Agrupación con valores atípicos](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>Permite encontrar grupos de similitud y valores atípicos en los datos.
| <img src="media/samples/correlation-plot.png" alt="Screenshot shows Correlation plot." width="200"> | <img src="media/samples/decision-tree-chart.png" alt="Screenshot shows Decision tree chart." width="200"> | <img src="media/samples/forecasting-tbats.png" alt="Screenshot shows Forecasting T B A T S." width="200"> 
| [Correlation plot](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>Resalta las variables mejor correlacionadas en una tabla de datos. | [Gráfico de árbol de decisión](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>Diagrama esquemático en forma de árbol para determinar la probabilidad estadística mediante particionamiento recursivo. | [Forecasting TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>Previsión de serie temporal para series que tienen varias estacionalidades mediante el modelo TBATS.
| <img src="media/samples/forecasting-with-ARIMA.png" alt="Screenshot shows Forecasting with ARIMA." width="200"> | <img src="media/samples/funnel-plot.png" alt="Screenshot shows Funnel plot." width="200"> | <img src="media/samples/outliers-detection.png" alt="Screenshot shows Outliers detection." width="200"> 
| [Forecasting with ARIMA](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>Predice valores futuros basados en datos históricos mediante la media móvil integrada de regresión automática (ARIMA). | [Trazado de embudo](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>Permite encontrar valores atípicos en los datos mediante un trazado de embudo. | [Detección de valores atípicos](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>Permite encontrar valores atípicos en los datos con el método y el trazado más adecuados.
| <img src="media/samples/spline-chart.png" alt="Screenshot shows Spline chart." width="200"> | <img src="media/samples/time-series-decomposition-chart.png" alt="Screenshot shows Time Series decomposition chart." width="200"> | <img src="media/samples/time-series-forecasting-chart.png" alt="Screenshot shows Time series forecasting chart." width="200">
| [Spline chart](https://github.com/Microsoft/powerbi-visuals-spline/) </br>Permite visualizar y comprender los datos ruidosos. | [Time series decomposition chart](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>Permite comprender los componentes de serie temporal mediante la "descomposición por estación y tendencia con LOESS". | [Gráfico de predicción de series temporales](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>Uso del modelo de suavizado exponencial para predecir valores futuros en función de los valores observados anteriormente

## <a name="next-steps"></a>Pasos siguientes

Para probar la creación de objetos visuales en Power BI, vea [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md).
