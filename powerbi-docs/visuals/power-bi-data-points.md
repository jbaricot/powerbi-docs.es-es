---
title: Grandes conjuntos de datos, límites de punto de datos y estrategias de datos
description: Límites de datos para objetos visuales y estrategias de reducción de datos
author: mihart
ms.author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 0feef179fddba93f192559c7ac7bed10c6fa5328
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412538"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>Aplicación de estrategias y límites de punto de datos por tipo de objeto visual

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

Al representar un objeto visual en Power BI, la visualización debe ser rápida y precisa. Para ello se necesitan algoritmos subyacentes configurados para cada tipo de objeto visual. Los objetos visuales en Power BI deben ser lo suficientemente flexibles como para gestionar distintos tamaños de conjuntos de datos. Algunos conjuntos de datos solo tienen un puñado de puntos de datos, mientras que otros disponen de petabytes de puntos de datos. En este artículo se explican las estrategias usadas por Power BI para representar visualizaciones.

## <a name="data-reduction-strategies"></a>Estrategias de reducción de datos
Cada objeto visual emplea una o varias *estrategias de reducción de datos* con el fin de gestionar los volúmenes de datos posiblemente grandes que se van a analizar. Incluso una simple tabla emplea una estrategia para evitar cargar todo el conjunto de datos en el cliente.  La estrategia de reducción usada varía según el tipo de objeto visual. Cada objeto visual se selecciona de las *estrategias de reducción de datos* admitidas como parte de la generación de la solicitud de datos enviada al servidor. 

Cada objeto visual controla los parámetros en esas estrategias para influir en la cantidad total de datos.   

## <a name="strategies"></a>Estrategias
Para cada estrategia, hay valores predeterminados según la forma y el tipo de datos visualizados. Sin embargo, estos valores se pueden invalidar, en el panel de formato de Power BI, para proporcionar la experiencia de usuario adecuada. 

* **Datos basados en ventanas** (segmentación): permita que los usuarios se desplacen por los datos de un objeto visual mediante la carga progresiva de fragmentos del conjunto de datos general.
* **TopN**: solo se muestran los primeros N elementos.
* **Muestra sencilla**: se muestran los elementos primero y último y los N elementos distribuidos entre ellos.
* **BottomN**: se muestran solo los últimos N elementos.  Resulta útil para supervisar los datos actualizados con frecuencia.
* **Muestreo de alta densidad**: algoritmo de muestreo mejorado que respeta mejor los valores atípicos o la forma de una curva.
    * **Muestreo de líneas discretizado**: muestra de puntos de datos según valores atípicos en contenedores a lo largo de un eje.
    * **Muestreo de datos superpuestos**: muestra de puntos de datos según valores superpuestos para preservar los valores atípicos.

## <a name="statistics"></a>Estadísticas
Determinados modelos pueden proporcionar estadísticas sobre el número de valores en determinadas columnas. Cuando existe dicha información, se aprovecha para proporcionar un mejor equilibrio entre varias jerarquías si un objeto visual no reemplaza de forma explícita el recuento de valores para una estrategia.

Para más información, consulte [Novedades de Analysis Services](/sql/analysis-services/what-s-new-in-analysis-services).

## <a name="dynamic-limits"></a>Límites dinámicos
Además de las estrategias anteriores, los objetos visuales con dos jerarquías de agrupamiento de columnas (eje y leyenda, o categoría y serie) usan una estrategia adicional denominada *límites dinámicos*.  Los límites dinámicos están diseñados para equilibrar mejor los puntos de datos. 

Proporcionan una selección mejor de puntos para datos dispersos de lo que harían los límites estáticos. Por ejemplo, se podría configurar un objeto visual para seleccionar 100 categorías y 10 series con un total de 1000 puntos. Pero los datos reales tienen 50 categorías y 20 series.  En tiempo de ejecución de consultas, los límites dinámicos seleccionan las 20 series para llenar los 1000 puntos solicitados.

Los límites dinámicos se aplican automáticamente cuando el servidor es capaz de lo siguiente:

* En Power BI Desktop con SSAS local, versión 2016 o superior, [aprovechar las funcionalidades de SuperDax del servidor](/archive/blogs/analysisservices/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3)

* En el servicio Desktop y Power BI cuando se usa un modelo importado, Direct Query, conectar en directo con el servicio o con PaaS de AS. 

* En el servicio Power BI, al conectar mediante una puerta de enlace local para SSAS local, no se pueden usar límites dinámicos. La puerta de enlace local no es totalmente compatible con la estrategia de límites dinámicos que devuelve una estructura diferente de conjuntos de resultados de la SSAS local.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Estrategias y límites de punto de datos por tipo de objeto visual

### <a name="area-chart"></a>Gráfico de áreas
Consulte [Funcionamiento del muestreo de líneas](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works).

### <a name="barcolumn-chart"></a>Gráfico de columnas o barras
- Cuando está en modo de categorías
    - Categorías: Virtualización mediante ventanas de 500 filas a la vez
    - Series: Primeras 60
    - En el modo escalar (se pueden usar límites dinámicos)
        - Número máximo de puntos: 10 000
        - Categorías: Muestra de 500 valores
        - Series: Primero 20 valores

### <a name="card-multirow"></a>Tarjeta (varias filas) 
- Valores: Virtualización mediante ventanas de 200 filas a la vez

### <a name="combo-chart"></a>Gráfico combinado
 Usa las mismas estrategias que el gráfico de columnas. Tenga en cuenta que la línea del **gráfico combinado** no usa el algoritmo de alta densidad que usa el **gráfico de líneas**.

### <a name="power-bi-visuals"></a>Objetos visuales de Power BI
Es posible obtener hasta 30 000, pero depende de los autores de objetos visuales indicar qué estrategias se van a usar. El límite predeterminado es 1000, pero el creador de objetos visuales puede cambiarlo hasta un máximo de 30 000.

### <a name="doughnut"></a>Anillos
- Número máximo de puntos: 3500
- Agrupar: Primeras 500
- Detalles: Primeras 20

### <a name="filled-map-choropleth"></a>Mapa coroplético 
El mapa coroplético puede usar estadísticas o límites dinámicos. Power BI intenta usar la reducción en el siguiente orden: límites dinámicos, estadísticas y por último configuración. 
- Número máximo de puntos: 10 000
- Categorías: Primeras 500
- Series (si X e Y están presentes): Primeras 20

### <a name="funnel"></a>Embudo
- Número máximo de puntos: 3500
- Categorías: Primeras 3500

### <a name="kpi"></a>KPI
- Eje de tendencia
- Últimas 3500

### <a name="line-chart"></a>Gráfico de líneas
Consulte [Funcionamiento del muestreo de líneas](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works).

### <a name="line-chart-high-density"></a>Gráfico de líneas de alta densidad
Consulte [Muestreo de alta densidad](../create-reports/desktop-high-density-sampling.md).

### <a name="map"></a>Mapa 
- Número máximo de puntos: 3500

Según la configuración, un mapa puede tener:
- Ubicación: Primeras 3500
- Ubicación, tamaño: Primeras 3500
- Agregados de ubicación, latitud y longitud (+/-tamaño): Primeras 3500
- Latitud, longitud: consulte [Gráfico de dispersión de alta densidad](../create-reports/desktop-high-density-scatter-charts.md)
- Latitud, longitud, tamaño: Primeras 3500
- Leyenda, latitud, longitud: consulte [Gráfico de dispersión de alta densidad](../create-reports/desktop-high-density-scatter-charts.md)
- Leyenda, latitud, longitud, tamaño: Primeras 233 leyendas, primeras 15 latitudes y longitudes (se pueden usar límites estadísticos o dinámicos)
- Ubicación, leyenda, latitud y longitud como agregados (+/-tamaño): Primeras 233 ubicaciones, primeras 15 leyendas (se pueden usar límites estadísticos o dinámicos)

### <a name="matrix"></a>Matriz
- Filas: Virtualización mediante ventanas de 500 filas a la vez
- Columnas: Primeras 100 columnas agrupadas 
- Valores: los valores múltiples no se tienen en cuenta para la reducción de datos

### <a name="powerapps-visual"></a>Objeto visual de PowerApps
Es posible obtener hasta 30 000, pero depende de los autores de objetos visuales indicar qué estrategias se van a usar. El límite predeterminado es 1000, pero el creador de objetos visuales puede cambiarlo hasta un máximo de 30 000.

### <a name="radial-gauge"></a>Medidor radial
Sin estrategia de reducción

### <a name="slicer"></a>Segmentación
- Valores: Virtualización mediante ventanas de 200 filas a la vez

### <a name="scatter-chart-high-density"></a>Gráficos de dispersión (alta densidad)
Consulte [Gráficos de dispersión de alta densidad](./desktop-high-density-scatter-charts.md).

### <a name="pie"></a>Gráfico circular
- Número máximo de puntos: 3500
- Agrupar: Primeras 500
- Detalles: Primeras 20

### <a name="r--python-visuals"></a>Objetos visuales de R y Python
Limitado a 150 000 filas. Si se seleccionan más de 150 000 filas, se usan solo las primeras 150 000

### <a name="ribbon-chart"></a>Gráfico de la barra de herramientas
- Cuando está en modo de categorías
    - Categorías: Virtualización (ventana de datos) mediante la ventana de 500 filas a la vez
    - Series: Primeras 60
    - En el modo escalar (se pueden usar límites dinámicos)
        - Número máximo de puntos: 10 000
        - Categorías: Muestra de 500 valores
        - Series: Primero 20 valores

### <a name="shape-map-preview"></a>Mapa de formas (vista previa)
El mapa de formas puede usar estadísticas o límites dinámicos. 
- Número máximo de puntos: 1500
- Categorías: Primeras 500

### <a name="table"></a>Tabla
- Valores: Virtualización (ventana de datos) mediante la ventana de 500 filas a la vez

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Gráfico de rectángulos (se pueden usar estadísticas o límites dinámicos)
- Número máximo de puntos: 3500
- Agrupar: Primeras 500
- Detalles: Primeras 20

### <a name="waterfall-chart"></a>Gráfico de cascada
- Cuando solo hay el depósito de categoría
    - Número máximo de puntos: 3500
    - Solo categoría: primeras 3500
- Cuando están presentes categoría y desglose
    - Categoría: Virtualización (ventana de datos) mediante la ventana de 30 filas a la vez
    - Desglose: primero 200 valores


## <a name="next-steps"></a>Pasos siguientes
[Tipos de visualización](power-bi-report-visualizations.md)
