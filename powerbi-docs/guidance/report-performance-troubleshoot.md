---
title: Solución de problemas de rendimiento de los informes en Power BI
description: Guía de solución de problemas para diagnosticar el rendimiento reducido de los informes en Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2020
ms.author: v-pemyer
ms.openlocfilehash: dd3be575946502a886bbf2b89e2a1844f4046ea7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83276959"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>Solución de problemas de rendimiento de los informes en Power BI

En este artículo se proporcionan instrucciones que permiten a los desarrolladores y administradores solucionar problemas de rendimiento reducido de los informes. Se aplica a los informes de Power BI y también a los informes paginados de Power BI.

Los usuarios pueden identificar los informes lentos como aquellos que tardan en cargarse o en actualizarse al interactuar con las segmentaciones de usuarios u otras características. Cuando los informes se hospedan en una capacidad Premium, los informes lentos también se pueden identificar mediante la supervisión de la [aplicación Métricas de Power BI Premium](../admin/service-admin-premium-monitor-capacity.md). Esta aplicación le ayuda a supervisar el estado y la capacidad de su suscripción de Power BI Premium.

## <a name="follow-flowchart-steps"></a>Seguimiento de los pasos del diagrama de flujo

Use el siguiente diagrama de flujo para comprender la causa del rendimiento reducido y determinar la acción que debe llevarse a cabo.

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="Imagen que muestra el diagrama de flujo, que se describe totalmente en el texto del artículo." border="true":::

Hay seis terminadores de diagramas de flujo, cada uno de los cuales describe la acción que se debe realizar:

|Terminador|Acciones|
|---------|---------|
|![Terminador de diagrama de flujo 1.](media/common/icon-01-red-30x30.png)|Administración de capacidad<br />Escalar la capacidad |
|![Terminador de diagrama de flujo 2.](media/common/icon-02-red-30x30.png)|Investigación de la actividad de capacidad durante el uso habitual del informe|
|![Terminador de diagrama de flujo 3.](media/common/icon-03-red-30x30.png)|Cambio de arquitectura<br />Consideración de Azure Analysis Services<br />Comprobación de la puerta de enlace local|
|![Terminador de diagrama de flujo 4.](media/common/icon-04-red-30x30.png)|Consideración de Azure Analysis Services<br />Consideración de Power BI Premium|
|![Terminador de diagrama de flujo 5.](media/common/icon-05-red-30x30.png)|Uso del Analizador del rendimiento de Power BI Desktop<br />Optimización del informe, modelo o DAX|
|![Terminador de diagrama de flujo 6.](media/common/icon-06-red-30x30.png)|Creación de una incidencia de soporte técnico|

## <a name="take-action"></a>Realizar acción

La primera consideración es comprender si el informe lento se hospeda en una capacidad Premium.

### <a name="premium-capacity"></a>Capacidad Premium

Si el informe se hospeda en una capacidad Premium, use la aplicación **Métrica de Power BI Premium** para determinar si la capacidad de hospedaje del informe suele superar los recursos de la capacidad. Es el caso de la CPU cuando con frecuencia supera el 80 %. En el caso de la memoria, es cuando la [métrica de memoria activa](../admin/service-premium-metrics-app.md#the-active-memory-metric) es superior a 50. Si hay presión sobre los recursos, puede que sea necesario [administrar o escalar la capacidad](../admin/service-admin-premium-manage.md) (terminador de diagrama de flujo 1). Si los recursos son adecuados, investigue la actividad de capacidad durante el uso habitual del informe (terminador de diagrama de flujo 2).

### <a name="shared-capacity"></a>Capacidad compartida

Si el informe se hospeda en una capacidad compartida, no es posible supervisar el estado de la capacidad. Deberá tomar un enfoque de investigación diferente.

En primer lugar, determine si se produce un rendimiento reducido a horas específicas del día o del mes. Si es así, y muchos usuarios están abriendo el informe a esas horas, valore dos opciones:

- Aumentar el rendimiento de las consultas mediante la migración del conjunto de datos a [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) o a una capacidad Premium (terminador de diagrama de flujo 4).
- Usar el [Analizador de rendimiento](../create-reports/desktop-performance-analyzer.md) en Power BI Desktop para conocer el comportamiento de cada uno de los elementos de informe, como los objetos visuales y las fórmulas DAX. Es especialmente útil para determinar si la representación de las consultas o de los objetos visuales contribuye a los problemas de rendimiento (terminador de diagrama de flujo 5).

Si determina que no hay ningún patrón horario, considere la posibilidad de que el rendimiento reducido se limite a una zona geográfica o región específica. Si es así, es probable que el origen de datos sea remoto y que haya una comunicación de red lenta. En este caso, valore lo siguiente:

- Cambiar la arquitectura mediante [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) (terminador de diagrama de flujo 3).
- Optimizar el [rendimiento de puerta de enlace de datos local](/data-integration/gateway/service-gateway-performance) (terminador de diagrama de flujo 3).

Por último, si determina que no hay ningún patrón horario _y_ el rendimiento reducido se produce en todas las regiones, investigue si se produce en determinados dispositivos, clientes o exploradores web. Si no es así, use el [Analizador de rendimiento](../create-reports/desktop-performance-analyzer.md) de Power BI Desktop, como se describió anteriormente, para optimizar el informe o modelo (terminador de diagrama de flujo 5).

Al determinar que dispositivos, clientes o exploradores web específicos contribuyen a un rendimiento reducido, se recomienda crear una incidencia a través de la página de soporte técnico de [Power BI](https://powerbi.microsoft.com/support/) (terminador de diagrama de flujo 6).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Guía de Power BI](index.yml)
- [Supervisión del rendimiento de los informes](monitor-report-performance.md)
- [Analizador de rendimiento](../create-reports/desktop-performance-analyzer.md)
- Notas del producto: [Planning a Power BI Enterprise Deployment](https://go.microsoft.com/fwlink/?linkid=2057861) (Planeación de una implementación de Power BI Enterprise)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
