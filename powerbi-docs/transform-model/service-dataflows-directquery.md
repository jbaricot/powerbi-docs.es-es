---
title: Uso de DirectQuery con flujos de datos en Power BI (versión preliminar)
description: Más información sobre el uso de DirectQuery con flujos de datos en Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 669f05c03bd7a42d5b44f6ca2fa1b4d58680f71b
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237739"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Uso de DirectQuery con flujos de datos en Power BI (versión preliminar)

Puede usar DirectQuery para conectarse directamente a flujos de datos y así conectarse directamente a su flujo de datos sin tener que importar los datos. 

El uso de DirectQuery con flujos de datos permite las siguientes mejoras en los procesos de Power BI y flujos de entrada:

* **Evitar programaciones de actualización independientes**: DirectQuery se conecta directamente a un flujo de entrada, lo que elimina la necesidad de crear un conjunto de datos importado. Como tal, el uso de DirectQuery con los flujos de datos significa que ya no necesita programaciones de actualización independientes del flujo de datos y el conjunto de datos para asegurarse de que los datos se sincronizan.

* **Filtrar datos**: DirectQuery resulta útil para trabajar en una vista filtrada de los datos dentro de un flujo de datos. Si desea filtrar los datos y, por tanto, trabajar con un subconjunto más pequeño de los datos del flujo de datos, puede usar DirectQuery (y el motor de proceso) para filtrar los datos de flujo de datos y trabajar con el subconjunto filtrado que necesite.


## <a name="using-directquery-for-dataflows"></a>Uso de DirectQuery en flujos de datos

El uso de DirectQuery con flujos de datos es una característica en versión preliminar disponible a partir de la versión 2020 de mayo de Power BI Desktop. 

También hay requisitos previos para usar DirectQuery con flujos de datos:

* El flujo de datos debe residir en un área de trabajo habilitada para Power BI Premium
* El **motor de proceso** debe estar activado. Para más información sobre el motor de proceso, consulte [Motor de proceso mejorado](service-dataflows-enhanced-compute-engine.md).

## <a name="enable-directquery-for-dataflows"></a>Habilitación de DirectQuery para flujos de datos

Para asegurarse de que el flujo de datos está disponible para el acceso de DirectQuery, el motor de proceso mejorado debe estar en su estado optimizado. Para habilitar DirectQuery para flujos de datos, establezca la nueva opción **Configuración mejorada del motor de proceso** en **Activada**. La siguiente imagen muestra la opción seleccionada correctamente.

![Habilitación del motor de proceso mejorado con flujos de datos](media/service-dataflows-directquery/dataflows-directquery-01.png)

Cuando haya aplicado esa opción, actualice el flujo de datos para que la optimización surta efecto. 


## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Existen algunas limitaciones conocidas de DirectQuery y los flujos de datos, que se explican en la siguiente lista.

* DirectQuery para flujos de datos no funciona con la característica en **versión preliminar de metadatos mejorados** habilitada. Se espera que esta exclusión se quite en una próxima versión mensual de Power BI Desktop.

* Durante el período de versión preliminar de esta característica, algunos clientes pueden experimentar tiempos de espera o problemas de rendimiento al usar DirectQuery con flujos de datos. Estos problemas se solucionan activamente durante este período de versión preliminar.

* Los modelos compuestos o mixtos con orígenes de datos de importación y DirectQuery no se admiten actualmente.

* Durante la visualización, los flujos de datos de gran tamaño pueden presentar problemas relacionados con incidencias de tiempo de expiración. Se espera que esta limitación se elimine cuando la característica pase a la disponibilidad general. Hasta entonces, los flujos de datos de gran tamaño que presenten problemas relacionados con incidencias de tiempo de expiración deberán usar el modo de importación.

* En la configuración del origen de datos, el conector de flujo de datos mostrará las credenciales no válidas si usa DirectQuery. Esto no afecta al comportamiento, de modo que el conjunto de datos funcionará correctamente. Este problema se resolverá a medida que se acerque la disponibilidad general.



## <a name="next-steps"></a>Pasos siguientes

Los siguientes artículos resultan útiles para obtener más información y escenarios al utilizar flujos de datos:

* [Preparación de datos de autoservicio con flujos de datos](service-dataflows-overview.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)
* [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)
* [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md)

Para más información sobre Common Data Service, puede leer su artículo de introducción:
* [Introducción a Common Data Service](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Más información sobre el esquema y las entidades de Common Data Service en GitHub](https://github.com/Microsoft/CDM)

Artículos relacionados de Power BI Desktop:

* [Conexión a conjuntos de datos del servicio Power BI desde Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
* [Información general sobre consultas en Power BI Desktop](desktop-query-overview.md)

Artículos relacionados con el servicio Power BI:
* [Configuración de la actualización programada](../connect-data/refresh-scheduled-refresh.md)
