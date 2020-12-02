---
title: Guía de optimización para Power BI
description: Guía de optimización para Power BI
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/16/2020
ms.openlocfilehash: d55696756f6dca6b70b23b82ccab30c08cc79ec7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392942"
---
# <a name="optimization-guide-for-power-bi"></a>Guía de optimización para Power BI

En este artículo se proporcionan instrucciones que permiten a los desarrolladores y administradores generar y mantener soluciones de Power BI optimizadas. Puede optimizar la solución en diferentes capas arquitectónicas. Las capas incluyen:

- Orígenes de datos
- Modelo de datos
- Visualizaciones, incluidos paneles, informes de Power BI e informes paginados Power BI
- Entorno, incluidas las capacidades, las puertas de enlace de datos y la red

## <a name="optimizing-the-data-model"></a>Optimización del modelo de datos

El modelo de datos es compatible con toda la experiencia de visualización. Los modelos de datos se hospedan externa o internamente y, en Power BI, se hace referencia a ellos como _conjuntos de datos_. Es importante conocer las opciones y elegir el tipo de conjunto de datos apropiado para la solución. Hay tres modos de conjunto de datos: Importación, DirectQuery y Composición. Para más información, vea [Conjuntos de datos en el servicio Power BI](../connect-data/service-datasets-understand.md) y [Modos de conjuntos de datos en el servicio Power BI](../connect-data/service-dataset-modes-understand.md).

Para obtener instrucciones sobre el modo de conjunto de datos específico, vea:

- [Técnicas de reducción de datos para modelos de importación](import-modeling-data-reduction.md)
- [Instrucciones del modelo de DirectQuery en Power BI Desktop](directquery-model-guidance.md)
- [Guía de modelos compuestos de Power BI Desktop](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>Optimización de visualizaciones

Las visualizaciones de Power BI pueden ser paneles, informes de Power BI o informes paginados de Power BI. Cada una tiene distintas arquitecturas, por lo que tienen instrucciones independientes. 

### <a name="dashboards"></a>Paneles

Es importante saber que Power BI mantiene una memoria caché para los iconos del panel, excepto los iconos de los informes dinámicos y los iconos de streaming. Para más información, vea [Actualización de datos en Power BI (Actualización de iconos)](../connect-data/refresh-data.md#tile-refresh). Si el conjunto de datos aplica la [Seguridad de nivel de fila (RLS)](../admin/service-admin-rls.md) dinámica, asegúrese de conocer las implicaciones del rendimiento, ya que los iconos se almacenarán en la caché por cada usuario.

Al anclar iconos de informes dinámicos a un panel, no se sirven desde la memoria caché de consultas. En su lugar, se comportan como los informes y realizan consultas a los núcleos back-end sobre la marcha.

Como sugiere su nombre, recuperar los datos de la memoria caché proporciona un rendimiento mejor y más coherente que confiar en el origen de datos. Una manera de aprovechar las ventajas de esta funcionalidad es hacer que los paneles sean la primera página de inicio de los usuarios. Ancle los objetos visuales más utilizados y muy solicitados en los paneles. De esta manera, los paneles se convierten en una valiosa "primera línea de defensa", que ofrece un rendimiento coherente con menos carga en la capacidad. Los usuarios también pueden hacer clic en un informe para analizar los detalles.

Para DirectQuery y los conjuntos de datos de conexiones dinámicas, la memoria caché se actualiza de forma periódica mediante una consulta al origen de datos. De forma predeterminada, se produce cada hora, aunque puede configurar una frecuencia diferente en la configuración del conjunto de datos. Cada actualización de la memoria caché enviará consultas al origen de datos subyacente para actualizar la memoria caché. El número de consultas que se generan depende del número de objetos visuales anclados en los paneles que dependen de ese origen de datos. Tenga en cuenta que, si está habilitada la seguridad de nivel de fila, se generan consultas para cada contexto de seguridad. Por ejemplo, suponga que hay dos roles diferentes que categorizan a los usuarios y tienen dos vistas diferentes de los datos. Durante la actualización de la memoria caché de consultas, Power BI genera dos conjuntos de consultas.

### <a name="power-bi-reports"></a>Informes de Power BI

Hay varias recomendaciones para optimizar los diseños de los informes de Power BI.

> [!NOTE]
> Cuando los informes se basan en un conjunto de datos de DirectQuery, para optimizaciones de diseño de informes adicionales, vea [Instrucciones del modelo de DirectQuery en Power BI Desktop (Optimización de los diseños de informes)](directquery-model-guidance.md#optimize-report-designs).

#### <a name="apply-the-most-restrictive-filters"></a>Aplicación de los filtros más restrictivos

Cuantos más datos tenga que mostrar un objeto visual, más lenta será su carga. Aunque este principio parece obvio, es muy fácil olvidarlo. Por ejemplo: supongamos que tiene un conjunto de datos grande. Sobre ese conjunto de datos, genera un informe con una tabla. Los usuarios finales utilizan segmentaciones en la página para obtener las filas que desean; normalmente, solo están interesados en algunas docenas de filas.

Un error común es tener la vista predeterminada de la tabla sin filtrar; por ejemplo, más de 100 millones de filas. Los datos de estas filas se cargan en memoria y se descomprimen en cada actualización. Este procesamiento crea enormes demandas de memoria. La solución es usar el filtro "Primeros N" para reducir el número máximo de elementos que se muestran de la tabla. Puede establecer el número máximo de elementos a un número mucho mayor que el que los usuarios necesitarían, por ejemplo, 10 000. El resultado es que la experiencia del usuario final no cambia, pero el uso de memoria se reduce considerablemente. Además, lo más importante es que el rendimiento mejora.

Se recomienda un enfoque de diseño similar al descrito anteriormente para todos los objetos visuales del informe. Hágase la siguiente pregunta: ¿son necesarios todos los datos en este objeto visual? ¿Hay maneras de filtrar la cantidad de datos que se muestran en el objeto visual con un impacto mínimo en la experiencia del usuario final? Tenga en cuenta que las tablas en concreto pueden resultar caras.

#### <a name="limit-visuals-on-report-pages"></a>Limitación de los objetos visuales de las páginas del informe

El principio anterior se aplica por igual al número de objetos visuales agregados a una página del informe. Se recomienda limitar el número de objetos visuales de la página de un informe concreto solo a aquellos que sean necesarios. Las [páginas de obtención de detalles](report-drillthrough.md) y la [información sobre herramientas de páginas de informes](report-page-tooltips.md) son una excelente manera de proporcionar detalles adicionales sin crear una aglomeración de objetos visuales en la página.

#### <a name="evaluate-custom-visual-performance"></a>Evaluación del rendimiento de objetos visuales personalizados

Asegúrese de colocar cada objeto visual personalizado a su ritmo para asegurarse un alto rendimiento. Los objetos visuales de Power BI mal optimizados pueden afectar negativamente al rendimiento de todo el informe.

### <a name="power-bi-paginated-reports"></a>Informes paginados de Power BI

Los diseños de los informes paginados de Power BI se pueden optimizar con la aplicación del diseño de procedimiento recomendado a la recuperación de datos del informe. Para más información, vea [Guía de recuperación de datos de informes paginados](report-paginated-data-retrieval.md).

Además, asegúrese de que la capacidad tiene suficiente memoria asignada para la [carga de trabajo de informes paginados](../admin/service-admin-premium-workloads.md#paginated-reports).

## <a name="optimizing-the-environment"></a>Optimización del entorno

Puede optimizar el entorno de Power BI mediante la configuración de las opciones de capacidad, el ajuste de tamaño de las puertas de enlace de datos y la reducción de la latencia de red.

### <a name="capacity-settings"></a>Configuración de la capacidad

Al usar capacidades, disponibles con Power BI Premium (SKU P) o Power BI Embedded (SKU A y A4-A6), puede administrar la configuración de la capacidad. Para más información, vea [Administración de las capacidades Premium](../admin/service-premium-capacity-manage.md). Para obtener instrucciones sobre cómo optimizar la capacidad, vea [Optimización de las capacidades Premium](../admin/service-premium-capacity-optimize.md).

### <a name="gateway-sizing"></a>Ajuste de tamaño de la puerta de enlace

Una puerta de enlace es necesaria cuando Power BI debe acceder a los datos que no son accesibles directamente a través de Internet. Se puede instalar la [puerta de enlace de datos local](../connect-data/service-gateway-onprem.md) en un servidor local o en una infraestructura como servicio (IaaS) hospedada en la máquina virtual.

Para comprender las cargas de trabajo de puerta de enlace y las recomendaciones de ajuste de tamaño, vea [Ajuste de tamaño de la puerta de enlace de datos local](gateway-onprem-sizing.md).

### <a name="network-latency"></a>Latencia de red

La latencia de red puede afectar al rendimiento de los informes si aumenta el tiempo necesario para que las solicitudes alcancen el servicio Power BI y para la entrega de las respuestas. Los inquilinos de Power BI se asignan a una región específica.

> [!TIP]
> Para determinar dónde se encuentra el inquilino, vea [¿Dónde se encuentra mi inquilino de Power BI?](../admin/service-admin-where-is-my-tenant-located.md).

Cuando los usuarios de un inquilino acceden al servicio Power BI, sus solicitudes siempre se enrutan a esta región. Cuando las solicitudes llegan al servicio Power BI, el servicio puede enviar solicitudes adicionales —por ejemplo, al origen de datos subyacente o a la puerta de enlace— que también están sujetas a la latencia de red.

Las herramientas como [Azure Speed Test](https://azurespeedtest.azurewebsites.net/) proporcionan una indicación de la latencia de red entre el cliente y la región de Azure. En general, para minimizar el impacto de la latencia de red, intente mantener los orígenes de datos, las puertas de enlace y el clúster de Power BI lo más cerca posible. Preferiblemente, residen en la misma región. Si la latencia de red es un problema, intente ubicar las puertas de enlace y los orígenes de datos más cerca del clúster de Power BI situándolos dentro de las máquinas virtuales hospedadas en la nube.

## <a name="monitoring-performance"></a>Supervisión del rendimiento

Puede supervisar el rendimiento para identificar cuellos de botella. Las consultas o los objetos visuales lentos deben ser objeto de optimización continua. La supervisión se puede realizar en tiempo de diseño en Power BI Desktop o en cargas de trabajo de producción en las capacidades de Power BI Premium. Para más información, vea [Supervisión del rendimiento de los informes en Power BI](monitor-report-performance.md).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Guía de Power BI](index.yml)
- [Supervisión del rendimiento de los informes](monitor-report-performance.md)
- Notas del producto: [Planning a Power BI Enterprise Deployment](https://go.microsoft.com/fwlink/?linkid=2057861) (Planeación de una implementación de Power BI Enterprise)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)




