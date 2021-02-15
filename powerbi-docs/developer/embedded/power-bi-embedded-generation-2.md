---
title: Explicación de Power BI Embedded Generation 2 como parte de los análisis de Power BI Embedded
description: Obtenga información sobre la oferta de Power BI Embedded Generation 2 en los análisis de Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 02/03/2021
ms.openlocfilehash: fa72ab380cac1a1ac6d12cb431bdacfb5964ee83
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2021
ms.locfileid: "99539651"
---
# <a name="power-bi-embedded-generation-2-preview"></a>Power BI Embedded Generation 2 (versión preliminar)

Power BI Embedded publicó recientemente una nueva versión de Power BI Embedded, **Power BI Embedded Generation 2**, a la que se hace referencia como **Embedded Gen2** por comodidad. Embedded Gen2 se encuentra actualmente en versión preliminar y está disponible para que lo usen los suscriptores de Embedded durante el período de versión preliminar. Todavía puede crear la versión original del recurso de Power BI Embedded, denominada *Embedded Gen 1*, o bien crear un recurso de *Embedded Gen 2*. Durante el período de versión preliminar, puede ejecutar los dos tipos de capacidades de Power BI Embedded en paralelo, y asignar cualquier área de trabajo a una capacidad de Gen1 o Gen2.

Todas las funcionalidades de Power BI Embedded Gen 1, como pausar y reanudar la capacidad, se conservan en Gen 2. Además, el recurso de capacidad de Gen 2 proporciona las siguientes actualizaciones y una experiencia mejorada:

* **Rendimiento mejorado** en cualquier tamaño de capacidad y en todo momento. Las operaciones siempre se ejecutarán a la máxima velocidad y no se ralentizarán cuando la carga de la capacidad se aproxime a los límites de capacidad.

* **Mayor escala**, incluidas las siguientes mejoras:

    * *Ningún límite en la simultaneidad de las actualizaciones*, sin necesidad de realizar un seguimiento de las programaciones de los conjuntos de datos que se actualizan en su capacidad.

    * *Menos restricciones de memoria*

    * *Separación completa entre la interacción con los informes y las actualizaciones programadas*

* **Nivel de entrada inferior para informes paginados y cargas de trabajo de inteligencia artificial**, para empezar con una SKU *A1* y aumentar después según sus necesidades.

* **Escalar un recurso al instante** en Power BI Embedded. Desde el escalado de un recurso de Gen1 en cuestión de minutos, hasta el escalado de un recurso de Gen2 en segundos.

* **Escalado sin tiempo de inactividad** con Embedded Gen2, para poder escalar el recurso de Power BI Embedded sin experimentar ningún tiempo de inactividad.

* **Métricas mejoradas** con datos de uso de capacidad claros y normalizados, que dependen solo de la complejidad de las operaciones de análisis que la capacidad realiza. Las métricas no se ven afectadas por otros factores, como el tamaño de la capacidad y el nivel de carga del sistema, mientras se realiza el análisis. Al usar las métricas mejoradas, la herramienta de generación de informes integrada le permite ver claramente lo siguiente:
    * Análisis de uso
    * Planeamiento del presupuesto
    * Contracargos
    * Necesidad de actualizar la capacidad

    >[!NOTE]
    >Las métricas mejoradas estarán disponibles posteriormente durante el período de versión preliminar. Los clientes pueden acceder a las métricas de uso de los últimos siete días poniéndose en contacto con el soporte técnico.

## <a name="using-embedded-gen2"></a>Uso de Embedded Gen2

Cree un recurso de capacidad de Embedded Gen2 para beneficiarse de sus ventajas. Para crear un recurso de capacidad de Embedded Gen2, siga las instrucciones de [Creación de una capacidad de Power BI Embedded en Azure Portal](azure-pbie-create-capacity.md).

## <a name="known-limitations"></a>Restricciones conocidas

* No se puede realizar el seguimiento de la utilización de la capacidad de Embedded Gen2 en la [aplicación de métricas](../../admin/service-admin-premium-monitor-capacity.md). Para más información, vea [Actualizaciones de supervisión de Prémium Gen2](../../admin/service-premium-what-is.md#updates-for-premium-gen2-preview-2).

* La configuración de la asignación de memoria para cargas de trabajo específicas no se aplica a las capacidades de Embedded Gen2. Para más información, vea [Mejoras de memoria de Embedded Gen 2](embedded-capacity.md#embedded-gen-2-memory-enhancements-preview)

* Si usa XMLA en Embedded Gen2, asegúrese de que usa las últimas versiones de las herramientas de administración y modelado de datos.

* Las características de Analysis Services de Embedded Gen2 solo se admiten en las bibliotecas de cliente más recientes. Las fechas de lanzamiento estimadas para las herramientas dependientes para admitir este requisito se indican en [Limitaciones conocidas de Prémium Gen2](../../admin/service-premium-what-is.md#known-limitations-in-premium-gen2).

* Todas las métricas actuales de Azure y los diagnósticos de registro de Power BI Embedded solo admiten las capacidades de Gen1.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Creación de una capacidad de Power BI Embedded en Azure Portal](azure-pbie-create-capacity.md)

> [!div class="nextstepaction"]
> [Capacidad y SKU de los análisis incrustados de Power BI](embedded-capacity.md)

> [!div class="nextstepaction"]
> [¿Qué es Power BI Premium?](../../admin/service-premium-what-is.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)