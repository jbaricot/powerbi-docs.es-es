---
title: Procedimientos recomendados para flujos de datos
description: Una colección de vínculos de procedimientos recomendados e instrucciones para flujos de datos
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Data from files
ms.openlocfilehash: fb688b20fd8b5ee1288f670fba9f7f45fc058680
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565363"
---
# <a name="dataflows-best-practices"></a>Procedimientos recomendados para flujos de datos

Los **flujos de datos** de Power BI son una solución de preparación de datos centrada en la empresa, que habilita un ecosistema de datos que está listo para su uso, reutilización e integración. En este artículo se proporciona una lista de procedimientos recomendados, con vínculos a artículos y otra información que le ayudará a comprender y usar los flujos de datos a su capacidad máxima.

## <a name="dataflows-across-the-power-platform"></a>Flujos de datos en Power Platform

Los flujos de datos se pueden usar en distintas tecnologías de Power Platform, como Power Query, Microsoft Dynamics 365 y otras ofertas de Microsoft. Consulte [¿Qué son los flujos de entrada?](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) para obtener más información sobre el funcionamiento de los flujos de datos en Power Platform.


## <a name="dataflows-best-practices-table-and-links"></a>Vínculos y tablas de procedimientos recomendados de flujos de datos

En la tabla siguiente se proporciona una colección de vínculos a artículos en los que se describen los procedimientos recomendados para crear flujos de trabajo o trabajar con ellos. Los vínculos incluyen información sobre el desarrollo de la lógica de negocios, el desarrollo de flujos de datos complejos, la reutilización de flujos de datos y cómo lograr la escalabilidad empresarial con los flujos de datos.


|**Tema.**  |**Sección de instrucciones**  |**Vínculo a un artículo o contenido**  |
|---------|---------|---------|
|Power Query     | Sugerencias y trucos para sacar el máximo partido a su experiencia de limpieza y transformación de datos        |[Procedimientos recomendados de Power Query](/power-query/best-practices)        |
|Uso de entidades calculadas     |Existen ventajas de rendimiento para el uso de entidades calculadas en un flujo de datos         |[Escenarios de entidades calculadas](/power-query/dataflows/computed-entities-scenarios)         |
|Desarrollo de flujos de datos complejos     |Patrones para desarrollar flujo de datos de alto rendimiento y a gran escala         |[Flujos de datos complejos](/power-query/dataflows/best-practices-developing-complex-dataflows)         |
|Reutilización de flujos de datos     |Patrones, instrucciones y casos de uso         |[Reutilización de flujos de datos](/power-query/dataflows/best-practices-reusing-dataflows)         |
|Implementaciones a gran escala     |Instrucciones y uso a gran escala para complementar la arquitectura empresarial         |[Almacenamiento de datos mediante flujos de datos](/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows)         |
|Uso de proceso mejorado     |Mejora potencial del rendimiento de los flujos de datos hasta 25 veces más         |[Motor de proceso mejorado](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|Optimización de la configuración de la carga de trabajo     |Saque el máximo partido de su infraestructura de flujos de datos mediante la comprensión de los mecanismos que puede extraer para maximizar el rendimiento         |[Configuración de la carga de trabajo de flujos de datos](dataflows-premium-workload-configuration.md)         |
|Combinación y expansión de tablas     |Creación de combinaciones de alto rendimiento         |[Optimización de las operaciones de expansión de tablas](/power-query/optimize-expanding-table-columns)         |
|Orientación sobre el plegado de consultas     |Aceleración de transformaciones mediante el sistema de origen         |[Plegado de consultas](/power-query/power-query-folding)         |
|Uso de la generación de perfiles de datos     |Descripción de la calidad, la distribución y el perfil de las columnas         |[Herramientas de generación de perfiles de datos](/power-query/data-profiling-tools)         |
|Implementación del control de errores     |Desarrollo de flujos de datos sólidos resistentes a errores de actualización, con sugerencias         |[Patrones de errores comunes](/power-query/dealing-with-errors)  </br> [Control de errores complejos](/power-query/error-handling)      |
|Uso de la vista de esquema      |Mejora de la experiencia de creación al trabajar con una tabla ancha y realizar operaciones de nivel de esquema         |[Vista de esquema](/power-query/schema-view)         |
|Entidades vinculadas      |Reutilización y referencias de transformaciones         |[Entidades vinculadas](/power-query/dataflows/linked-entities)         |
|Actualización incremental      |Comparación entre la carga de datos recientes o modificados, y la recarga completa         |[Actualización incremental](/power-query/dataflows/incremental-refresh)         |
|||


        
## <a name="next-steps"></a>Pasos siguientes

En los artículos siguientes encontrará más información sobre los flujos de datos y Power BI:

* [Introducción a los flujos de datos y la preparación de datos de autoservicio](dataflows-introduction-self-service.md)
* [Creación de un flujo de datos](dataflows-create.md)
* [Configurar y consumir un flujo de datos](dataflows-configure-consume.md)
* [Características prémium de flujos de datos](dataflows-premium-features.md)
* [Configuración del almacenamiento de flujo de datos para usar Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [IA con flujos de datos](dataflows-machine-learning-integration.md)
* [Limitaciones y consideraciones de flujos de datos](dataflows-features-limitations.md)