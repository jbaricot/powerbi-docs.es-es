---
title: Procedimientos para configurar las cargas de trabajo en Power BI Premium
description: Descubra cómo configurar las cargas de trabajo en una capacidad Premium de Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 62579a12588449e0119b96fb3a7c7da2ef7858e5
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2021
ms.locfileid: "99532921"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configuración de cargas de trabajo en una capacidad Premium

En este artículo se describe cómo habilitar y configurar las cargas de trabajo para capacidades Premium de Power BI. De forma predeterminada, las capacidades solo admiten la carga de trabajo asociada con la ejecución de consultas de Power BI. También puede habilitar y configurar cargas de trabajo adicionales para **[AI (Cognitive Services)](../transform-model/dataflows/dataflows-machine-learning-integration.md)** , **[Flujos de datos](../transform-model/dataflows/dataflows-introduction-self-service.md)** e **[Informes paginados](../paginated-reports/paginated-reports-save-to-power-bi-service.md)** .

> [!NOTE]
> Power BI Premium publicó recientemente una nueva versión Premium, denominada **Premium Gen2**, que se encuentra actualmente en versión preliminar. Premium Gen2 simplifica la administración de las funcionalidades Premium y reduce la sobrecarga de administración. Para más información, vea [Power BI Premium Generation 2 (versión preliminar)](service-premium-what-is.md#power-bi-premium-generation-2-preview).
>
>Para consultar las mejoras de Power BI Embedded Gen2, vea [Power BI Embedded Generation 2](../developer/embedded/power-bi-embedded-generation-2.md).

## <a name="default-memory-settings"></a>Configuración de memoria predeterminada

Las cargas de trabajo de consulta están optimizadas y limitadas en función de los recursos determinados por la SKU de la capacidad Premium. Las capacidades Premium también admiten cargas de trabajo adicionales que pueden usar recursos de su capacidad. Los valores de memoria predeterminados para estas cargas de trabajo se basan en los nodos de capacidad disponibles para su SKU. Estos valores de memoria máxima no son acumulativos. 


|                       | EM1/A1                  | EM2/A2                  | EM3/A3                  | P1/A4                  | P2/A5                  | P3/A6                   |
|-----------------------|---------------------------|---------------------------|---------------------------|--------------------------|--------------------------|---------------------------|
| **INTELIGENCIA ARTIFICIAL**                | No compatible               | 40 % predeterminado; 40 % mínimo  | 20 % predeterminado; 20 % mínimo  | 20 % predeterminado; 8 % mínimo  | 20 % predeterminado; 4 % mínimo  | 20 % predeterminado; 2 % mínimo   |
| **Conjuntos de datos**          | 100 % predeterminado; 67 % mínimo | 100 % predeterminado; 40 % mínimo | 100 % predeterminado; 20 % mínimo | 100 % predeterminado; 8 % mínimo | 100 % predeterminado; 4 % mínimo | 100 % predeterminado; 2 % mínimo  |
| **Flujos de datos**         | 40 % predeterminado; 40 % mínimo  | 24 % predeterminado; 24 % mínimo  | 20 % predeterminado; 12 % mínimo  | 20 % predeterminado; 5 % mínimo  | 20 % predeterminado; 3 % mínimo  | 20 % predeterminado; 2 % mínimo   |
| **Informes paginados** | No compatible               | No compatible               | No compatible               | 20 % predeterminado; 10 % mínimo | 20 % predeterminado; 5 % mínimo  | 20 % predeterminado; 2,5 % mínimo |

> [!NOTE]
> **Premium Gen2**, que actualmente se encuentra en versión preliminar, no requiere que se cambie la configuración de la memoria. El sistema subyacente administra automáticamente la memoria de Premium Gen2. 


## <a name="workload-settings"></a>Configuración de la carga de trabajo

En las secciones siguientes se detalla la configuración de la carga de trabajo descrita en la tabla anterior. 

### <a name="ai-preview"></a>IA (Versión preliminar)

La carga de trabajo de IA le permite usar servicios cognitivos y aprendizaje automático automatizado en Power BI. Utilice la siguiente configuración para controlar el comportamiento de la carga de trabajo.

| Nombre de la opción de configuración | Descripción |
|---------------------------------|----------------------------------------|
| **Valor máximo de memoria (%)** | Porcentaje máximo de memoria disponible que los procesos de IA pueden usar en una capacidad. |
| **Permitir el uso de Power BI Desktop** | Este valor se reserva para uso futuro y no aparece en todos los inquilinos. |
| **Permitir crear modelos de Machine Learning** | Especifica si los analistas de negocios pueden entrenar, validar e invocar modelos de aprendizaje automático directamente en Power BI. Para obtener más información, consulte [Aprendizaje automático automatizado en Power BI (versión preliminar)](../transform-model/dataflows/dataflows-machine-learning-integration.md). |
| **Habilitar paralelismo para solicitudes de AI** | Especifica si las solicitudes de IA se pueden ejecutar en paralelo. |
|  |  |

### <a name="datasets"></a>Conjuntos de datos

La carga de trabajo de conjuntos de datos está habilitada de forma predeterminada y no se puede deshabilitar. Utilice la siguiente configuración para controlar el comportamiento de la carga de trabajo. Debajo de la tabla se ofrece información de uso adicional para algunas de las opciones de configuración.

| Nombre de la opción de configuración | Descripción |
|---------------------------------|----------------------------------------|
| **Valor máximo de memoria (%)** | Porcentaje máximo de memoria disponible que los conjuntos de datos pueden usar en una capacidad. |
| **Punto de conexión XMLA** | Especifica que las conexiones de las aplicaciones cliente respetan la pertenencia al grupo de seguridad establecida en los niveles del área de trabajo y la aplicación. Para más información, vea [Conexión a conjuntos de datos con herramientas y aplicaciones cliente](service-premium-connect-tools.md). |
| **Número máximo de conjuntos de filas intermedias** | Número máximo de filas intermedias devueltas por DirectQuery. El valor predeterminado es de 1 000 000, y el intervalo permitido está entre 100 000 y 2 147 483 647. |
| **Tamaño máximo del conjunto de datos sin conexión (GB)** | Tamaño máximo del conjunto de datos sin conexión en memoria. Es el tamaño comprimido en el disco. El valor predeterminado es 0, que es el límite superior que define la SKU. El intervalo permitido está entre 0 y el límite de tamaño de la capacidad. |
| **Número máximo de conjuntos de filas de resultados** | Número máximo de filas devueltas en una consulta DAX. El valor predeterminado es de -1 (sin límite), y el intervalo permitido está entre 100 000 y 2 147 483 647. |
| **Límite de memoria de consulta (%)** | El porcentaje máximo de memoria disponible en la carga de trabajo que se puede usar para ejecutar una consulta MDX o DAX. El valor predeterminado es 0, lo que da como resultado la aplicación del límite de memoria de consulta automática específico de la SKU. |
| **Tiempo de espera de la consulta (en segundos)** | Tiempo de espera máximo de una consulta. El valor predeterminado es de 3600 segundos (1 hora). Un valor de 0 especifica que las consultas no superarán el tiempo de espera. |
| **Actualización automática de páginas** | Botón de alternancia de activación o desactivación para permitir que las áreas de trabajo Premium tengan informes con actualización automática de páginas basada en intervalos fijos. |
| **Intervalo de actualización mínimo** | Si la actualización automática de páginas está activada, es el intervalo mínimo permitido como intervalo de actualización de páginas. El valor predeterminado es cinco minutos y el mínimo permitido es un segundo. |
| **Cambiar medida de detección** | Botón de alternancia de activación o desactivación para permitir que las áreas de trabajo Premium tengan informes con actualización automática de páginas basada en la detección de cambios. |
| **Intervalo de ejecución mínimo** | Si la opción Cambiar medida de detección está activada, es el intervalo de ejecución mínimo permitido para sondear cambios en los datos. El valor predeterminado es cinco segundos y el mínimo permitido es uno. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Número máximo de conjuntos de filas intermedias

Use esta configuración para controlar el impacto de los informes con un uso intensivo de recursos o con un diseño deficiente. Cuando una consulta a un conjunto de datos de DirectQuery genera un resultado muy grande de la base de datos de origen, puede provocar un aumento del uso de memoria y sobrecarga de procesamiento. Esta situación puede hacer que otros usuarios e informes se ejecuten con pocos recursos. Esta configuración permite al administrador de la capacidad ajustar el número de filas que una consulta individual puede capturar del origen de datos.

Como alternativa, si la capacidad puede admitir más que el valor predeterminado de un millón de filas y tiene un conjunto de filas grande, aumente este valor para capturar más filas.

Tenga en cuenta que esta configuración solo afecta a las consultas de DirectQuery, mientras que [Número máximo de conjuntos de filas de resultados](#max-result-row-set-count) afecta a las consultas DAX.

#### <a name="max-offline-dataset-size"></a>Tamaño máximo del conjunto de datos sin conexión

Use esta configuración para impedir que los creadores de informes publiquen un conjunto de datos grande que pueda afectar negativamente a la capacidad. Tenga en cuenta que Power BI no puede determinar el tamaño real en memoria hasta que el conjunto de datos se cargue en la memoria. Es posible que un conjunto de datos con un tamaño sin conexión más pequeño tenga una superficie de memoria mayor que un conjunto de datos de un tamaño sin conexión mayor.

Si tiene un conjunto de datos que es mayor que el tamaño especificado para esta opción, el conjunto de datos no se cargará cuando un usuario intente acceder a él. También se puede producir un error al cargar el conjunto de datos si es mayor que la memoria máxima configurada para su carga de trabajo.

Para proteger el rendimiento del sistema, se aplica un límite máximo de tiempo adicional específico de la SKU para el tamaño máximo de conjunto de datos sin conexión, con independencia del valor configurado. Este límite máximo no se aplica a los conjuntos de datos de Power BI que están optimizados para tamaños de datos grandes. Para obtener más información, vea [Modelos grandes en Power BI Premium](service-premium-large-models.md).

|                                               | EM1/A1 | EM2/A2 | EM3/A3 | P1/A4 | P2/A5 | P3/A6 |
|-----------------------------------------------|----------|----------|----------|---------|---------|---------|
| **Límite máximo para el tamaño máximo del conjunto de datos sin conexión** | 3 GB     | 5 GB     | 6 GB     | 10 GB   | 10 GB   | 10 GB   |

#### <a name="max-result-row-set-count"></a>Número máximo de conjuntos de filas de resultados

Use esta configuración para controlar el impacto de los informes con un uso intensivo de recursos o con un diseño deficiente. Si se alcanza este límite en una consulta DAX, un usuario del informe verá el error siguiente. Debe copiar los detalles del error y ponerse en contacto con un administrador.

![No se pueden cargar datos para este objeto visual](media/service-admin-premium-workloads/could-not-load-data.png)

Tenga en cuenta que esta configuración solo afecta a las consultas DAX, mientras que [Número máximo de conjuntos de filas intermedias](#max-intermediate-row-set-count) afecta a las consultas de DirectQuery.

#### <a name="query-memory-limit"></a>Límite de memoria de consulta

Use esta configuración para controlar el impacto de los informes con un uso intensivo de recursos o con un diseño deficiente. Algunas consultas y cálculos pueden dar lugar a resultados intermedios que usan mucha memoria en la capacidad. Esta situación puede hacer que otras consultas se ejecuten muy lentamente, provoquen la expulsión de otros conjuntos de datos de la capacidad y generen errores de memoria insuficiente para otros usuarios de la capacidad.

Esta configuración se aplica a todas las consultas DAX y MDX que se ejecutan mediante informes de Power BI, informes de Análisis en Excel, así como otras herramientas que pueden conectarse a través del punto de conexión XMLA.

Tenga en cuenta que las operaciones de actualización de datos también pueden ejecutar consultas DAX como parte de la actualización de los iconos del panel y de las cachés de objetos visuales una vez que se han actualizado los datos del conjunto de datos. Es posible que estas consultas también produzcan errores debido a esta configuración, y esto puede provocar que la operación de actualización de datos se muestre con un estado de error aunque los datos del conjunto de datos se hayan actualizado correctamente.

La opción de configuración predeterminada es 0, lo que da como resultado la aplicación del siguiente límite de memoria de consulta automática específico de la SKU.

|                                  | EM1/A1 | EM2/A2 | EM3/A3 | P1/A4 | P2/A5 | P3/A6 |
|----------------------------------|----------|----------|----------|---------|---------|---------|
| **Límite de memoria de consulta automática** | 1 GB     | 2 GB     | 2 GB     | 6 GB    | 6 GB    | 10 GB   |

Para proteger el rendimiento del sistema, se aplica un límite máximo de 10 GB para todas las consultas ejecutadas por informes de Power BI, con independencia del límite de memoria de consulta configurado por el usuario. Este límite máximo no se aplica a las consultas emitidas por herramientas que usan el protocolo Analysis Services (también conocido como XMLA). Los usuarios deben considerar la posibilidad de simplificar la consulta o sus cálculos si la consulta tiene un uso intensivo de memoria.

#### <a name="query-timeout"></a>Tiempo de espera de la consulta

Use esta opción para mantener un mejor control de las consultas de ejecución prolongada, lo que puede hacer que los informes se carguen con lentitud para los usuarios.

Esta configuración se aplica a todas las consultas DAX y MDX que se ejecutan mediante informes de Power BI, informes de Análisis en Excel, así como otras herramientas que pueden conectarse a través del punto de conexión XMLA.

Tenga en cuenta que las operaciones de actualización de datos también pueden ejecutar consultas DAX como parte de la actualización de los iconos del panel y de las cachés de objetos visuales una vez que se han actualizado los datos del conjunto de datos. Es posible que estas consultas también produzcan errores debido a esta configuración, y esto puede provocar que la operación de actualización de datos se muestre con un estado de error aunque los datos del conjunto de datos se hayan actualizado correctamente.

Esta configuración se aplica a una sola consulta y no a la cantidad de tiempo que se tarda en ejecutar todas las consultas asociadas a la actualización de un conjunto de datos o informe. Considere el ejemplo siguiente:

- La opción **Tiempo de espera de la consulta** es 1200 (20 minutos).
- Hay cinco consultas para ejecutar y cada una se ejecuta durante 15 minutos.

El tiempo combinado para todas las consultas es de 75 minutos, pero el límite de la configuración no se alcanza porque todas las consultas individuales se ejecutan durante menos de 20 minutos.

Tenga en cuenta que en los informes de Power BI este valor predeterminado se invalida con un tiempo de espera mucho menor para cada consulta de la capacidad. El tiempo de espera de cada consulta suele ser de aproximadamente tres minutos.

#### <a name="automatic-page-refresh-preview"></a>Actualización automática de páginas (versión preliminar)

Cuando está habilitada, la actualización automática de páginas permite a sus usuarios con capacidad Premium actualizar las páginas de los informes en un intervalo definido, en el caso de los orígenes de DirectQuery. Como administrador de la capacidad, puede hacer lo siguiente:

- Activar y desactivar la actualización automática de páginas
- Definir un intervalo de actualización mínimo

En la siguiente imagen se indica dónde está la opción de intervalo de actualización automática:

![configuración de administrador de intervalo de actualización automática](media/service-admin-premium-workloads/automatic-refresh-interval.png)

Las consultas creadas mediante la actualización automática de páginas van directamente al origen de datos, por lo que es importante tener en cuenta la confiabilidad y la carga de esos orígenes al permitir la actualización automática de páginas en la organización. 

### <a name="dataflows"></a>Flujos de datos

La carga de trabajo del flujos de datos permite usar la preparación de datos de autoservicio del flujo para ingerir, transformar, integrar y enriquecer los datos. Utilice la siguiente configuración para controlar el comportamiento de la carga de trabajo.

| Nombre de la opción de configuración | Descripción |
|---------------------------------|----------------------------------------|
| **Valor máximo de memoria (%)** | Porcentaje máximo de memoria disponible que los flujos de datos pueden usar en una capacidad. |
| **Motor de proceso de flujos de datos mejorado (versión preliminar)** | Habilite esta opción para obtener un cálculo de entidades calculadas hasta 20 veces más rápido al trabajar con volúmenes de datos de gran escala. **Debe reiniciar la capacidad para activar el nuevo motor.** Para obtener más información, vea [Motor de proceso de flujos de datos mejorado](#enhanced-dataflows-compute-engine). |
| **Tamaño del contenedor** | Tamaño máximo del contenedor que los flujos de datos usan para cada entidad en el flujo de datos. El valor predeterminado es 700 MB. Para obtener más información, vea [Tamaño del contenedor](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Motor de proceso de flujos de datos mejorado

Para beneficiarse del nuevo motor de proceso, divida la ingesta de datos en flujos independientes y coloque la lógica de transformación en entidades calculadas en diferentes flujos de datos. Se recomienda este enfoque porque el motor de proceso funciona con flujos de datos que hagan referencia a un flujo existente. No funciona con flujos de trabajo de ingesta. Si sigue este guía, se asegurará de que el nuevo motor de proceso controle los pasos de transformación, como las uniones y combinaciones, para conseguir un rendimiento óptimo.

#### <a name="container-size"></a>Tamaño del contenedor

Al actualizar un flujo de datos, la carga de trabajo de flujos de datos genera un contenedor para cada entidad en el flujo de datos. Cada contenedor puede tomar memoria hasta el volumen especificado en la configuración Tamaño del contenedor. El valor predeterminado para todas las SKU es de 700 MB. Es posible que quiera cambiar este valor si:

- Los flujos de datos tardan demasiado tiempo en actualizarse, o bien se produce un error de actualización del flujo de datos en un tiempo de espera.
- Las entidades de flujo de datos incluyen pasos de cálculo, por ejemplo, una combinación.  

Se recomienda usar la aplicación [Métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md) para analizar el rendimiento de la carga de trabajo Flujo de datos.

En algunos casos, es posible que el aumento del tamaño del contenedor no mejore el rendimiento. Por ejemplo, si el flujo de datos obtiene datos solo de un origen sin realizar cálculos significativos, es probable que cambiar el tamaño del contenedor no sea útil. Es posible que aumentar el tamaño del contenedor sea de ayuda si habilita la carga de trabajo Flujo de datos para asignar más memoria a las operaciones de actualización de entidades. Al tener más memoria asignada, se puede reducir el tiempo que se tarda en actualizar las entidades calculadas de forma intensiva.

El valor Tamaño del contenedor no puede superar la memoria máxima para la carga de trabajo Flujos de datos. Por ejemplo, una capacidad P1 tiene 25 GB de memoria. Si el valor de Memoria máxima (%) de la carga de trabajo Flujo de datos está establecido en 20 %, Tamaño del contenedor (MB) no puede superar 5000. En todos los casos, el valor Tamaño del contenedor no puede superar la memoria máxima, incluso si se establece un valor mayor.

### <a name="paginated-reports"></a>Informes paginados

La carga de trabajo de informes paginados permite ejecutar informes paginados, en función del formato de SQL Server Reporting Services estándar, en el servicio Power BI. Utilice la siguiente configuración para controlar el comportamiento de la carga de trabajo.

| Nombre de la opción de configuración | Descripción |
|---------------------------------|----------------------------------------|
| **Valor máximo de memoria (%)** | Porcentaje máximo de memoria disponible que los informes paginados pueden usar en una capacidad. |
|  |  |

Los informes paginados ofrecen las mismas funciones que las que actualmente proporcionan los informes de SQL Server Reporting Services (SSRS), incluida la capacidad de que los autores de informes agreguen código personalizado.  Esto permite a los autores cambiar los informes de forma dinámica, como modificar los colores del texto en función de expresiones de código.  Para garantizar un aislamiento adecuado, los informes paginados se ejecutan en un espacio aislado protegido por capacidad. Los informes que se ejecutan con la misma capacidad pueden producir efectos secundarios entre ellos. Al igual que restringiría los autores que pueden publicar contenido en una instancia de SSRS, se recomienda seguir un procedimiento similar con los informes paginados. Asegúrese de que los autores que publican contenido en una capacidad sean de confianza para la organización. Puede proteger aún más el entorno mediante el aprovisionamiento de varias capacidades y la asignación de distintos autores a cada una. 

En algunos casos, la carga de trabajo de informes paginados puede dejar de estar disponible. En este caso, la carga de trabajo muestra un estado de error en el portal de administración y los usuarios ven los tiempos de espera para la representación de informes. Para mitigar este problema, deshabilite la carga de trabajo y después vuelva a habilitarla.

## <a name="configure-workloads"></a>Configuración de las cargas de trabajo

Maximice los recursos disponibles de su capacidad habilitando las cargas de trabajo solo si se van a usar. Cambie la memoria y otras opciones solo cuando disponga de una configuración predeterminada específica que no cumpla los requisitos de los recursos de capacidad.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar las cargas de trabajo en el portal de administración de Power BI

1. En **Configuración de la capacidad** > **CAPACIDADES PREMIUM**, seleccione una capacidad.

1. En **MÁS OPCIONES**, expanda **Cargas de trabajo**.

1. Habilite una o varias cargas de trabajo, y establezca un valor para **Memoria máxima** y otras configuraciones.

1. Seleccione **Aplicar**.

### <a name="rest-api"></a>API de REST

Las cargas de trabajo se pueden habilitar y asignar a una capacidad mediante las API de REST [Capacities](/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Supervisión de cargas de trabajo

La aplicación [Métricas de capacidad de Power BI Premium](service-admin-premium-monitor-capacity.md) proporciona métricas de conjuntos de datos, flujos de datos e informes paginados para supervisar las cargas de trabajo habilitadas para sus capacidades. 


> [!IMPORTANT]
> Si la capacidad de Power BI Premium experimenta un uso elevado de los recursos, lo que da lugar a incidencias de rendimiento o fiabilidad, se pueden recibir mensajes de correo electrónico de notificación para identificar y resolver la incidencia en cuestión. Esto puede ser una manera optimizada de solucionar problemas de capacidades sobrecargadas. Para obtener más información, vea las [notificaciones de capacidad y fiabilidad](service-interruption-notifications.md#capacity-and-reliability-notifications).


## <a name="next-steps"></a>Pasos siguientes

[Optimización de las capacidades de Power BI Premium](service-premium-capacity-optimize.md)
[Autoservicio de preparación de los datos en Power BI con flujos de datos](../transform-model/dataflows/dataflows-introduction-self-service.md)
[¿Qué son los informes paginados en Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
[Actualización automática de la página en Power BI Desktop (versión preliminar)](../create-reports/desktop-automatic-page-refresh.md)

¿Tiene más preguntas? [Pregunte a la comunidad de Power BI](https://community.powerbi.com/)

Power BI ha introducido Power BI Premium Gen2 como una oferta en versión preliminar, lo que mejora la experiencia con Power BI Premium mediante mejoras en los siguientes aspectos:
* Rendimiento
* Concesión de licencias por usuario
* Mayor escala
* Métricas mejoradas
* Escalado automático
* Menor sobrecarga de administración

Para más información sobre Power BI Premium Gen2, vea [Power BI Premium Generation 2 (versión preliminar)](service-premium-what-is.md#power-bi-premium-generation-2-preview).