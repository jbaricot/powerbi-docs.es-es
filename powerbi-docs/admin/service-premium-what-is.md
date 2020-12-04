---
title: ¿Qué es Microsoft Power BI Premium?
description: Power BI Premium proporciona capacidades para la organización, lo que ofrece un rendimiento más confiable y mayores volúmenes de datos, sin tener que comprar licencias por usuario.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: licensing support
LocalizationGroup: Premium
ms.openlocfilehash: 6fcbdeef8c7c02656e5637f6103fda76faeb26c9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412285"
---
# <a name="what-is-power-bi-premium"></a>¿Qué es Power BI Premium?

Puede usar Power BI Premium para acceder a características y funcionalidades que solo están disponibles en Premium, a fin de ofrecer mayor escalabilidad y rendimiento para el contenido de Power BI de su organización. Power BI Premium permite a más usuarios de su organización sacar el máximo partido de Power BI con mayor rendimiento y capacidad de respuesta. Por ejemplo, con Power BI Premium, usted y los usuarios de la organización obtienen las funciones siguientes:

> [!div class="checklist"]
> * Mayor escalabilidad y rendimiento de los informes de Power BI
> * Flexibilidad de otorgar licencias por capacidad
> * Las mejores características de su categoría para la visualización de datos y la extracción de información, como los análisis basados en IA, los flujos de datos reutilizables y que admiten composición, y los informes paginados
> * Unificación de autoservicio y BI empresarial con una variedad de funcionalidades exclusivas de Premium que admiten cargas de trabajo más pesadas y requieren escalabilidad empresarial
> * Licencia integrada para ampliar BI local con Power BI Report Server
> * Compatibilidad con la residencia de datos por región (Multi-Geo) y las claves de cifrado administradas por el cliente para los datos en reposo (BYOK)
> * Capacidad de compartir contenido de Power BI con cualquier persona (incluso fuera de la organización) sin adquirir una licencia por usuario


![Captura de pantalla que muestra el portal de administración de Power B I.](media/service-premium-what-is/premium-admin-portal.png) 

En este artículo se presentan las características principales de Power BI Premium. Si es necesario, se proporcionan vínculos a otros artículos con información más detallada. Para más información sobre Power BI Pro y Power BI Premium, consulte la sección de _comparación de las características de Power BI_ de [Precios de Power BI](https://powerbi.microsoft.com/pricing/).

## <a name="power-bi-premium-generation-2-preview"></a>Power BI Premium Generation 2 (versión preliminar)

Power BI Premium publicó recientemente una nueva versión de Power BI Premium, **Power BI Premium Generation 2**, a la que se hace referencia como **Premium Gen2** por comodidad. Premium Gen2 se encuentra actualmente en versión preliminar y está disponible para que lo usen los suscriptores Premium durante el período de versión preliminar. Puede seleccionar la versión original de Premium o cambiar a Premium Gen2. Basta con que use una versión u otra para su capacidad Premium. 

Premium Gen2 proporciona las siguientes características o experiencias mejoradas:

* Posibilidad para otorgar licencias **Premium por usuario**, además de en función de la capacidad.

* **Rendimiento** mejorado en cualquier tamaño de capacidad y en todo momento: Las operaciones de análisis se ejecutan hasta 16 veces más rápido en Premium Gen2. Las operaciones siempre se ejecutarán a la máxima velocidad y no se ralentizarán cuando la carga de la capacidad se aproxime a los límites de capacidad.

* **Mayor escala**:
    * *Ningún límite* en la simultaneidad de las actualizaciones, sin necesidad de realizar un seguimiento de las programaciones de los conjuntos de datos que se actualizan en su capacidad
    * Menos restricciones de memoria
    * Separación completa entre la interacción con los informes y las actualizaciones programadas

* Las **métricas mejoradas** con datos de uso de capacidad claros y normalizados, que dependen solo de la complejidad de las operaciones de análisis que la capacidad realiza, y no de su tamaño, el nivel de carga del sistema mientras realizan el análisis u otros factores. Con las métricas mejoradas, el análisis de uso, la planificación del presupuesto, los contracargos y la necesidad de actualizar son claramente visibles con los informes integrados. Las métricas mejoradas estarán disponibles y se optimizarán durante el período de versión preliminar.

* La **escalabilidad automática** permite *agregar automáticamente* un núcleo virtual cada vez durante los períodos de 24 horas en los que la carga de la capacidad supera sus límites, lo que evita la ralentización causada por la sobrecarga. Los núcleos virtuales se quitan automáticamente cuando se detecta el tiempo de inactividad. Los núcleos virtuales se cargan en la suscripción de Azure según la modalidad de pago por uso. La escalabilidad automática estará disponible durante el período de la versión preliminar. 

* **Sobrecarga de administración reducida** con notificaciones de administrador proactivas y configurables sobre el nivel de uso de la capacidad y el aumento de la carga.


### <a name="using-premium-gen2"></a>Uso de Premium Gen2

Habilite Premium Gen2 para beneficiarse de sus actualizaciones. Para habilitar Premium Gen2, siga estos pasos:

1. En el portal de administración, vaya a **Configuración de la capacidad**.
2. Seleccione **Power BI Premium**.
3. Aparece una sección titulada **Premium Generation 2 (versión preliminar)** , en la que hay un control deslizante para habilitar Premium Generation 2 (versión preliminar). 
4. Mueva el control deslizante a **Habilitado**.

En la imagen siguiente se muestra cómo habilitar Premium Gen2. 

![Habilitar Premium Generation 2](media/service-premium-what-is/enable-premium-gen2.gif#lightbox) 

### <a name="known-limitations-in-premium-gen2"></a>Limitaciones conocidas de Premium Gen2

Las siguientes limitaciones conocidas se aplican actualmente a Premium Gen2:

1.  No se puede realizar el seguimiento de la utilización de la capacidad Premium Gen2 en la aplicación de métricas.

2.  La configuración de la capacidad Premium Gen2 para cargas de trabajo específicas todavía no es visible en la página de configuración de la capacidad Premium Gen2 en el portal de administración. Para cambiar la configuración, haga una transición de la capacidad a la versión original de Premium, cambie la configuración y, a continuación, vuelva a establecer la capacidad para usar Premium Gen2. La configuración de asignación de memoria no es aplicable a las capacidades Premium Gen2.

3.  Si usa XMLA en Premium Gen2, asegúrese de que usa las últimas versiones de las [herramientas de administración y modelado de datos](service-premium-connect-tools.md#data-modeling-and-management-tools). 

4.  Las características de Analysis Services de Premium Gen2 solo se admiten en las bibliotecas de cliente más recientes. Las fechas de lanzamiento estimadas para las herramientas dependientes para admitir este requisito son las siguientes:

    |Herramienta|Versión mínima necesaria|Fecha de lanzamiento estimada|
    |---|---|---|
    |SQL Server Management Studio (SSMS)|18,8|8 de diciembre de 2020|
    |SQL Server Data Tools (SSDT)|2.9.15|Disponibilidad general, 30 de noviembre de 2020|
    | AS PowerShell| Mayor que 21.1.18229|26 de noviembre de 2020|

## <a name="subscriptions-and-licensing"></a>Suscripciones y licencias

Power BI Premium es una suscripción de Microsoft 365 de nivel de inquilino disponible en dos familias de SKU (referencia de almacén):

- SKU **P** (P1-P5) para la inserción y las funciones empresariales, que requieren un compromiso mensual o anual, se facturan mensualmente e incluyen una licencia para instalar Power BI Report Server en el entorno local.

- SKU **EM** (EM1-EM3) para la inserción de la _organización_, que requieren un compromiso anual que se factura mensualmente. Las SKU EM1 y EM2 solo están disponibles a través de planes de licencias por volumen. No se pueden comprar directamente.

### <a name="updates-for-premium-gen2-preview"></a>Actualizaciones de Premium Gen2 (versión preliminar)
En la actualidad Premium Gen2 está disponible como una característica en versión preliminar totalmente compatible solo con las SKU **P** y **EM**. La capacidad de las SKU **A** todavía no ofrece todas las ventajas adicionales introducidas en la actualización de la versión preliminar de Premium Gen2.


### <a name="purchasing"></a>Compra

Los administradores compran las suscripciones de Power BI Premium en el Centro de administración de Microsoft 365. En concreto, solo los administradores globales o los administradores de facturación pueden comprar las SKU. Una vez compradas, el inquilino recibe un número correspondiente de núcleos virtuales para asignar a las capacidades, lo que se conoce como *agrupación de núcleos virtuales*. Por ejemplo, la compra de una SKU P3 proporciona al inquilino 32 núcleos virtuales. Para más información, vea [Adquisición de Power BI Premium](service-admin-premium-purchase.md).

#### <a name="power-bi-premium-per-user-preview"></a>Power BI Premium por usuario (versión preliminar)

Power BI **Premium por usuario** permite a las organizaciones conceder licencias para características Premium por usuario. Premium por usuario (PPU) incluye todas las funcionalidades de licencia de Power BI Pro y agrega características como informes paginados, IA y otras funcionalidades que solo están disponibles para los suscriptores de Premium. Premium por usuario se encuentra actualmente en versión preliminar. Para obtener más información sobre Premium por usuario, incluida una comparación de características y otra información sobre su versión preliminar, vea el artículo [Preguntas más frecuentes sobre Power BI Premium por usuario (versión preliminar)](service-premium-per-user-faq.md). 


## <a name="reserved-capacities"></a>Capacidades reservadas

Con Power BI Premium, se obtienen *capacidades reservadas*. A diferencia de una capacidad compartida donde el procesamiento de análisis de las cargas de trabajo se ejecuta en recursos informáticos compartidos con otros clientes, una capacidad reservada es para uso exclusivo de una organización. Se aísla con recursos informáticos reservados que proporcionan un rendimiento confiable y coherente para el contenido hospedado. Tenga en cuenta que el procesamiento de los siguientes tipos de contenido de Power BI se almacena en una capacidad compartida en lugar de la capacidad reservada:

* Libros de Excel (a menos que los datos se importen primero en Power BI Desktop)
* [Conjuntos de datos de inserción](/rest/api/power-bi/pushdatasets)
* [Conjuntos de datos de streaming](../connect-data/service-real-time-streaming.md#set-up-your-real-time-streaming-dataset-in-power-bi)
* [Preguntas y respuestas](../create-reports/power-bi-tutorial-q-and-a.md)

Las áreas de trabajo residen dentro de las capacidades. Cada usuario de Power BI tiene un área de trabajo personal que se conoce como **Mi área de trabajo**. Pueden crearse áreas de trabajo adicionales, llamadas **áreas de trabajo** para posibilitar la colaboración. Las áreas de trabajo, incluidas las personales, se crean de forma predeterminada en la capacidad compartida. Cuando tiene capacidades Premium, Mis áreas de trabajo y las áreas de trabajo se pueden asignar a las capacidades Premium.

Los administradores de capacidad tienen la sección Mis áreas de trabajo asignada automáticamente a las capacidades Premium.

### <a name="updates-for-premium-gen2-preview"></a>Actualizaciones de Premium Gen2 (versión preliminar)

Los nodos de Premium Gen2 ya no usan la infraestructura reservada. En su lugar, el servicio garantiza que haya suficiente capacidad de proceso para cada carga de trabajo en ejecución mediante la asignación de suficientes recursos de un grupo compartido de nodos informáticos con alta capacidad.


### <a name="capacity-nodes"></a>Nodos de capacidad

Como se describe en la sección [Suscripciones y licencias](#subscriptions-and-licensing), hay dos familias de SKU de Power BI Premium: **EM** y **P**. Todas las SKU de Power BI Premium están disponibles como *nodos* de capacidad, que representan una cierta cantidad de recursos que consta de procesador, memoria y almacenamiento. Además de los recursos, cada SKU tiene límites operativos en cuanto al número de conexiones de DirectQuery y dinámicas por segundo, y el número de actualizaciones del modelo paralelas.

El procesamiento se consigue mediante un número determinado de núcleos virtuales, que se divide por igual entre el back-end y el front-end.

Los **núcleos virtuales de back-end** son responsables de funciones básicas de Power BI, como el procesamiento de consultas, la administración de caché, la ejecución de servicios R, la actualización del modelo y la representación de informes e imágenes en el lado servidor. A los núcleos virtuales de back-end se les asigna una cantidad fija de memoria que se usa principalmente para hospedar modelos, también conocidos como "conjuntos de datos activos".

Los **núcleos virtuales de front-end** son responsables de la administración de documentos de informes, paneles y servicios web, la administración de derechos de acceso, la programación, las API, las cargas y descargas, y en general de todo lo relacionado con las experiencias del usuario.

El almacenamiento se establece en **100 TB por nodo de capacidad**.

Los recursos y los límites de cada SKU Premium (y la SKU A de tamaño equivalente) se describen en la tabla siguiente:

| Nodos de capacidad | Total de núcleos virtuales | Núcleos virtuales de back-end | RAM (GB) | Núcleos virtuales de front-end | Límites de conexiones dinámicas/DirectQuery (por segundo) | Paralelismo de actualización de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 3 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 <sup>[1](#limit)</sup>| 64 | 32 | 200 | 32 | 240 | 48 |
| P5 <sup>[1](#limit)</sup>| 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

<a name="limit">1</a>: solo por solicitud especial. Para modelos muy grandes de más de 100 GB.

>[!NOTE]
>El uso de una sola SKU mayor (por ejemplo, una SKU P2) puede ser preferible a la combinación de SKU más pequeñas (por ejemplo, dos SKU P1). Por ejemplo, puede usar modelos más grandes y lograr un mayor paralelismo con la SKU P2.

#### <a name="updates-for-premium-gen2-preview"></a>Actualizaciones de Premium Gen2 (versión preliminar)

Con **Premium Gen2**, la cantidad de memoria disponible en cada tamaño de nodo se establece en el límite de la superficie de memoria de un solo artefacto y no en el consumo acumulativo de memoria. Por ejemplo, en Premium Gen2, solo un único tamaño de conjunto de datos se limita a 25 GB, en comparación con la versión Premium original, donde la superficie de memoria total de los conjuntos de datos administrados al mismo tiempo estaba limitada a 25 GB.


### <a name="capacity-workloads"></a>Cargas de trabajo de capacidad

Las cargas de trabajo de capacidad son servicios disponibles para los usuarios. De forma predeterminada, las capacidades Premium y de Azure solo admiten una carga de trabajo de conjunto de datos asociada con la ejecución de consultas de Power BI. La carga de trabajo de conjunto de datos no se puede deshabilitar. Se pueden habilitar cargas de trabajo adicionales para [IA (Cognitive Services)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [Flujos de datos](../transform-model/dataflows/dataflows-introduction-self-service.md) e [Informes paginados](../paginated-reports/paginated-reports-save-to-power-bi-service.md). Estas cargas de trabajo solo se admiten en las suscripciones Premium. 

Cada carga de trabajo adicional permite configurar la memoria máxima (como un porcentaje de la memoria total de la capacidad) que puede usar la carga de trabajo. Los valores predeterminados para la memoria máxima se determinan por SKU. Puede maximizar los recursos disponibles de la capacidad si habilita solo las cargas de trabajo adicionales cuando se usan. Y puede cambiar la configuración de memoria solo cuando disponga de una configuración predeterminada específica que no cumpla los requisitos de recursos de la capacidad. Los administradores de la capacidad pueden habilitar y configurar cargas de trabajo para una capacidad mediante la **configuración de la capacidad** en el [Portal de administración](service-admin-portal.md), o bien con las [API REST de las capacidades](/rest/api/power-bi/capacities).  

![Habilitación de las cargas de trabajo](media/service-admin-premium-workloads/admin-portal-workloads.png)

Para más información, vea [Configuración de cargas de trabajo en una capacidad Premium](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Cómo funcionan las capacidades

En todo momento, el servicio Power BI realiza un uso óptimo de los recursos de capacidad, aunque sin superar los límites impuestos en la capacidad.

Las operaciones de capacidad se clasifican como *interactivas* o *en segundo plano*. Las operaciones interactivas incluyen la representación de solicitudes y la respuesta a interacciones del usuario (filtrado, preguntas y respuestas, etc.). Las operaciones en segundo plano incluyen las actualizaciones de flujos de datos y del modelo de importación, y el almacenamiento en caché de consultas de panel.

Es importante comprender que las operaciones interactivas siempre tienen prioridad sobre las operaciones en segundo plano para garantizar la mejor experiencia del usuario posible. Si no hay recursos suficientes, las operaciones en segundo plano se agregan a una cola en espera hasta que se liberen los recursos. El servicio Power BI puede interrumpir a mitad del proceso las operaciones en segundo plano, como las actualizaciones del conjunto de datos, agregarlas a una cola y reintentarlas después.

Los modelos de importación se deben cargar en memoria en su totalidad para que se puedan consultar o actualizar. El servicio Power BI usa algoritmos sofisticados para administrar el uso de memoria de manera equitativa, pero en raras ocasiones, la capacidad se puede sobrecargar si no hay suficientes recursos para satisfacer las demandas en tiempo real de los clientes. Aunque es posible que una capacidad almacene muchos modelos de importación en almacenamiento persistente (hasta 100 TB por capacidad Premium), no todos los modelos residen necesariamente en la memoria al mismo tiempo; de lo contrario, el tamaño del conjunto de datos en memoria puede superar fácilmente el límite de memoria de la capacidad. Además de la memoria necesaria para cargar los conjuntos de datos, se necesita memoria adicional para la ejecución de las consultas y las operaciones de actualización.

Por tanto, los modelos de importación se cargan en la memoria y se quitan de ella en función del uso. Un modelo de importación se carga cuando se consulta (operación interactiva), o bien cuando se va a actualizar (operación en segundo plano).

La eliminación de un modelo de la memoria se denomina *expulsión*. Es una operación que Power BI puede realizar rápidamente según el tamaño de los modelos. Si la capacidad no experimenta ninguna presión de memoria y el modelo no está inactivo (es decir, se uso de forma activa), el modelo puede residir en la memoria sin ser expulsado. Cuando Power BI determina que no hay memoria suficiente para cargar un modelo, el servicio Power BI intentará liberar memoria mediante la expulsión de los modelos inactivos, que normalmente se definen como modelos cargados para las operaciones interactivas que no se han usado en los últimos tres minutos \[[1](#endnote-1)\]. Si no hay ningún modelo inactivo para expulsar, el servicio Power BI intenta expulsar los que se han cargado para las operaciones en segundo plano. Como último recurso, después de 30 segundos de intentos fallidos \[[1](#endnote-1)\], se produce un error en la operación interactiva. En este caso, se notifica el error al usuario del informe con una sugerencia de que vuelva a intentarlo en breve. En algunos casos, es posible que los modelos se descarguen de la memoria debido a operaciones de servicio.

Es importante resaltar que la expulsión del conjunto de datos es un comportamiento normal en la capacidad. La capacidad se esfuerza por equilibrar el uso de memoria mediante la administración del ciclo de vida en memoria de los modelos de forma transparente para los usuarios. Una tasa de expulsión alta no significa necesariamente que la capacidad no tenga los recursos suficientes. Pero puede ser un problema si el rendimiento de las consultas o actualizaciones se degrada debido a la sobrecarga de cargar y expulsar modelos repetidamente en un breve intervalo de tiempo.

En las actualizaciones de modelos de importación siempre se usa mucha memoria, ya que los modelos se deben cargar en la memoria. También se necesita memoria intermedia adicional para el procesamiento. Una actualización completa puede usar aproximadamente el doble de la cantidad de memoria que necesita el modelo porque Power BI mantiene una instantánea existente del modelo en memoria hasta que se completa la operación de procesamiento. Esto permite consultar el modelo incluso cuando se está procesando. Las consultas se pueden enviar a la instantánea existente del modelo hasta que la actualización se haya completado y los nuevos datos del modelo estén disponibles.

La actualización incremental realiza la actualización de la partición en lugar de todo el modelo, normalmente será más rápida y necesitará menos memoria, y puede reducir considerablemente el uso de recursos de la capacidad. Las actualizaciones también pueden hacer un uso intensivo de la CPU para los modelos, especialmente aquellos con transformaciones de Power Query, o bien tablas o columnas calculadas que son complejas o se basan en un gran volumen de datos.

Las actualizaciones, como las consultas, requieren que el modelo se cargue en memoria. Si no hay suficiente memoria, el servicio Power BI intentará expulsar los modelos inactivos, y si esto no es posible (porque todos los modelos estén activos), el trabajo de actualización se pone en cola. Las actualizaciones normalmente consumen mucha CPU, incluso mucho más que las consultas. Por esta razón, se impone un límite en el número de actualizaciones simultáneas, calculado como el límite superior de 1,5 veces el número de núcleos virtuales de back-end. Si hay demasiadas actualizaciones simultáneas, la actualización programada se pone en cola hasta que haya una ranura de actualización disponible, lo que hace que la operación tarde más tiempo en completarse. Las actualizaciones a petición, como las que desencadena una solicitud de usuario o una llamada de API, se volverán a intentar tres veces \[[1](#endnote-1)\]. Si sigue sin haber recursos suficientes, se producirá un error en la actualización.

#### <a name="updates-for-premium-gen2-preview"></a>Actualizaciones de Premium Gen2 (versión preliminar)

En Premium Gen2 no se necesitan límites de memoria acumulados y, por tanto, las actualizaciones simultáneas del conjunto de datos no contribuyen a las restricciones de recursos. No hay ningún límite en cuanto al número de actualizaciones en ejecución por núcleo virtual. Pero la actualización de conjuntos de datos individuales todavía se controla mediante los límites de CPU y memoria de la capacidad existente. Puede programar y ejecutar tantas actualizaciones como sea necesario en un momento dado, y el servicio Power BI las ejecutará en el momento programado pertinente.

Notas de la sección:   
<a name="endnote-1"></a>\[1\] Sujeto a cambios.

### <a name="regional-support"></a>Compatibilidad con regiones

Al crear una capacidad, los administradores globales y los administradores del servicio Power BI pueden especificar una región donde residirán las áreas de trabajo asignadas a la capacidad. Esto se conoce como **Multi-Geo**. Con Multi-Geo, las organizaciones pueden cumplir los requisitos de residencia de datos mediante la implementación de contenido en centros de datos de una región específica, incluso si es distinta de la región en la que reside la suscripción a Microsoft 365. Para más información, vea [Compatibilidad de Multi-Geo con Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Administración de capacidades

La administración de las capacidades Premium implica las tareas de crear o eliminar capacidades, asignar administradores y áreas de trabajo, configurar cargas de trabajo, supervisar y realizar ajustes para optimizar el rendimiento de la capacidad. 

Los administradores globales y los administradores del servicio Power BI pueden crear capacidades Premium a partir de los núcleos virtuales disponibles, o bien modificar capacidades Premium existentes. Cuando se crea una capacidad, se especifican el tamaño de la capacidad y la región geográfica, y se asigna al menos un administrador. 

Cuando se crean capacidades, la mayoría de las tareas administrativas se realizan en el [Portal de administración](service-admin-portal.md).

![Captura de pantalla que muestra el portal de administración de Power B I con Mi área de trabajo seleccionada.](media/service-premium-what-is/premium-admin-portal.png)

Los administradores de capacidad pueden asignar áreas de trabajo a la capacidad, administrar permisos de usuario y asignar otros administradores. Los administradores de capacidad también pueden configurar cargas de trabajo, ajustar las asignaciones de memoria y, si es necesario, reiniciar una capacidad, para restablecer las operaciones en caso de una sobrecarga de la capacidad.

![Captura de pantalla que muestra la administración de capacidades en el portal de administración de Power BI.](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Los administradores de capacidad también pueden asegurarse de que una capacidad se ejecuta sin problemas. Pueden supervisar el estado de la capacidad directamente en el Portal de administración o mediante la aplicación Métricas de capacidad de Premium.

Para más información sobre la creación de capacidades y la asignación de administradores y áreas de trabajo, vea [Administración de las capacidades Premium](service-premium-capacity-manage.md). Para más información sobre los roles, vea [Roles de administrador relacionados con Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Supervisión

La supervisión de las capacidades Premium proporciona a los administradores una descripción del funcionamiento de las capacidades. Las capacidades se pueden supervisar mediante el Portal de administración o con la aplicación [Power BI Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

La supervisión en el portal proporciona una vista rápida con métricas generales en las que se indica el promedio de cargas colocadas y recursos usados por la capacidad en los últimos siete días. 

![Captura de pantalla que muestra el estado de capacidad en el portal de administración de Power B I.](media/service-premium-what-is/premium-admin-portal-health.png)

> [!NOTE]
> **Actualizaciones de Premium Gen2 (versión preliminar)** : Premium Gen2 solo requiere supervisar un único aspecto, es decir, la cantidad de tiempo de CPU que la capacidad necesita para satisfacer la carga en cualquier momento. Si ha superado el tiempo de CPU según el tamaño de la SKU que ha comprado, la capacidad se escala automáticamente para adaptarse a las necesidades, o bien limita las operaciones interactivas en función de los valores de configuración.


La aplicación **Power BI Premium Capacity Metrics** proporciona la información más detallada sobre el rendimiento de las capacidades. La aplicación proporciona un panel general e informes más detallados.

![Panel de métricas de la aplicación](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Desde el panel de la aplicación puede hacer clic en una celda de la métrica para abrir un informe detallado. Los informes proporcionan métricas detalladas y capacidad de filtrado para explorar en profundidad la información más importante necesaria para que las capacidades sigan funcionando sin problemas.

![Los recuentos de picos periódicos de tiempo de espera de consultas indican la posible saturación de la CPU.](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Para más información sobre la supervisión de capacidades, vea [Supervisión de capacidades en el portal de administración](service-admin-premium-monitor-portal.md) y [Supervisión de capacidades Premium con la aplicación](service-admin-premium-monitor-capacity.md).

#### <a name="updates-for-premium-gen2-preview"></a>Actualizaciones de Premium Gen2 (versión preliminar)
Las capacidades **Premium Gen2** no usan la aplicación Métricas, sino la aplicación Utilización de la capacidad, que estará disponible durante la versión preliminar. La aplicación Utilización de la capacidad se puede iniciar desde la página de administración de capacidad en el **portal de administración** para cada capacidad.


### <a name="optimizing-capacities"></a>Optimización de las capacidades

El uso óptimo de las capacidades es fundamental para garantizar que los usuarios obtienen el rendimiento y que se obtiene el máximo partido de la inversión en Premium. Mediante la supervisión de métricas clave, los administradores pueden determinar la mejor forma de solucionar los cuellos de botella y tomar las medidas necesarias. Para más información, vea [Optimización de las capacidades Premium](service-premium-capacity-optimize.md) y [Escenarios de las capacidades Premium](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>API REST de las capacidades

Las API REST de Power BI incluyen una colección de [API de capacidades](/rest/api/power-bi/capacities). Con las API, los administradores pueden administrar mediante programación muchos aspectos de las capacidades Premium, incluidas la habilitación y deshabilitación de cargas de trabajo, la asignación de áreas de trabajo a una capacidad y mucho más.

## <a name="large-datasets"></a>Conjuntos de datos de gran tamaño

En función de la SKU, Power BI Premium permite cargar archivos de modelo de Power BI Desktop (.pbix) con un tamaño máximo de **10 GB**. Después de cargarlo, el modelo se puede publicar en un área de trabajo asignada a una capacidad Premium. Después, el conjunto de datos se puede actualizar hasta un tamaño de **12 GB**.

### <a name="size-considerations"></a>Consideraciones de tamaño

Los grandes conjuntos de datos pueden consumir muchos recursos. Debe tener al menos una SKU P1 o A4 para cualquier conjunto de datos superior a 1 GB. Aunque la publicación de conjuntos de datos grandes en áreas de trabajo respaldadas por SKU A hasta A3 podría funcionar, no sucede lo mismo con su actualización.

En la tabla siguiente se muestran las SKU recomendadas para cargar el archivo. pbix o publicarlo en el servicio Power BI:

   |SKU  |Tamaño de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | hasta 10 GB   |

La SKU A4 de Power BI Embedded es igual a SKU P1, A5 = P2 y A6 = P3.

Si habilita [modelos grandes](service-premium-large-models.md) en un conjunto de datos, las limitaciones de tamaño del archivo .pbix se siguen aplicando a la carga o publicación de archivos. Sin embargo, con la actualización incremental y los modelos grandes combinados, los conjuntos de datos pueden alcanzar un tamaño mucho mayor que estos límites. Con los modelos de gran tamaño, el tamaño del conjunto de datos solo está limitado por el tamaño de la capacidad Power BI Premium.

Los archivos .pbix representan datos en un *estado muy comprimido*. Los datos probablemente se expandirán al cargarse en memoria y, a partir de ahí, podrían expandirse varias veces más durante la actualización de datos.

La actualización programada de conjuntos de datos grandes puede tardar mucho tiempo y hacer un uso intensivo de los recursos. Es importante no programar demasiadas actualizaciones superpuestas. Se recomienda configurar la [actualización incremental](service-premium-incremental-refresh.md), ya que es más rápida y fiable, y consume menos recursos.

La carga inicial de informes de grandes conjuntos de datos puede tardar mucho si ha pasado un tiempo desde la última vez que se ha usado el conjunto de datos. Una barra de carga para los informes de carga larga muestra el progreso de carga.

Aunque las restricciones de memoria y tiempo por consulta son mucho mayores en la capacidad Premium, se recomienda usar filtros y segmentaciones para que los objetos visuales muestren únicamente lo necesario.

## <a name="incremental-refresh"></a>Actualización incremental

La actualización incremental proporciona una parte integral de la presencia y el mantenimiento de grandes conjuntos de datos en Power BI Premium y Power BI Pro. La actualización incremental tiene muchas ventajas, por ejemplo, las actualizaciones son más rápidas porque solo hay que actualizar los datos que hayan cambiado. Las actualizaciones son más confiables, ya que no es necesario mantener conexiones de larga duración a orígenes de datos volátiles. Se reduce el consumo de recursos porque, al haber menos datos que actualizar, se reduce el consumo total de memoria y de otros recursos. Las directivas de actualización incremental se definen en **Power BI Desktop** y se aplican cuando se publican en un área de trabajo de una capacidad Premium. 

![Detalles de la actualización](media/service-premium-incremental-refresh/refresh-details.png)

Para más información, vea [Actualizaciones incrementales en Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Informes paginados

Los informes paginados, compatibles con las SKU P1-P3 y A4-A6, se basan en la tecnología de lenguaje RDL (Report Definition Language) de SQL Server Reporting Services. Aunque se basen en la tecnología RDL, no es lo mismo que Power BI Report Server, que es una plataforma de informes descargable que se puede instalar en el entorno local, y que también se incluye con Power BI Premium. Los informes paginados se formatean para ajustarse a una página que se puede imprimir o compartir. Los datos se muestran en una tabla, incluso si esta abarca varias páginas. Mediante el uso de la aplicación de escritorio de Windows gratuita [**Generador de informes de Microsoft Power BI**](https://aka.ms/pbireportbuilder), los usuarios pueden crear informes paginados y publicarlos en el servicio.

En Power BI Premium, los informes paginados son una carga de trabajo que se debe habilitar para una capacidad mediante el portal de administración. Los administradores de capacidad pueden habilitar y después especificar la cantidad de memoria como un porcentaje del total de recursos de memoria de la capacidad. A diferencia de otros tipos de carga de trabajo, Premium ejecuta los informes paginados en un espacio contenido dentro de la capacidad. Se usa la memoria máxima especificada para este espacio, con independencia de si la carga de trabajo está o no activa. El valor predeterminado es 20 %. 

> [!NOTE]
> En **Premium Gen2 (versión preliminar)** , no se realiza ninguna administración de la memoria para los informes paginados. Con Premium Gen2, los informes paginados se admiten en las SKU EM1-EM3.

### <a name="paginated-reports-and-premium-gen2"></a>Informes paginados y Premium Gen2

Cuando se usa Premium Gen2, los informes paginados de Power BI se benefician de las mejoras arquitectónicas y de ingeniería reflejadas en Premium Gen2. En las secciones siguientes se describen las ventajas de Premium Gen2 para los informes paginados.

**Mayor disponibilidad de las SKU**: los informes paginados que se ejecutan en Premium Gen2 pueden ejecutar informes en todas las SKU Premium y Embedded disponibles. La facturación se calcula por hora de CPU, en un período de 24 horas. Esto amplía considerablemente las SKU que admiten informes paginados.

**Escalado dinámico**: con Premium Gen2, los desafíos asociados a los picos de actividad o la necesidad de recursos se pueden controlar dinámicamente según sea necesario. 

**Almacenamiento en caché mejorado**: antes de Premium Gen2, los informes paginados eran necesarios para realizar muchas operaciones en el contexto de la memoria asignada a la capacidad de la carga de trabajo. Ahora, con Premium Gen2, las reducciones de la memoria necesaria para muchas operaciones mejoran la capacidad de los clientes para realizar operaciones de ejecución prolongada sin afectar a las sesiones de otros usuarios. 

**Aislamiento de código y seguridad mejorados**: con Premium Gen2, el aislamiento de código puede producirse a nivel de usuario y no en función de la capacidad, como era el caso de la oferta Premium original. 

Para más información, vea [¿Qué son los informes paginados en Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md) Para más información sobre cómo habilitar la carga de trabajo de informes paginados, vea [Configuración de cargas de trabajo en una capacidad Premium](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Power BI Report Server
 
Power BI Report Server, que se incluye con Power BI Premium, es un servidor de informes *local* con un portal web. Puede crear el entorno de BI en almacenamiento local y distribuir los informes detrás del firewall de la organización. Report Server proporciona a los usuarios acceso a informes enriquecidos e interactivos, así como a funciones de creación de informes empresariales de SQL Server Reporting Services. Los usuarios pueden explorar datos visuales y descubrir rápidamente patrones para tomar mejores decisiones con más rapidez. Report Server proporciona gobernanza bajo sus propias condiciones. Cuando llegue el momento, Power BI Report Server facilita la migración a la nube, donde la organización puede aprovechar al máximo toda la funcionalidad de Power BI Premium.

Para más información, vea [Power BI Report Server](../report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Uso compartido de contenido ilimitado

Con Premium, todos los usuarios dentro o fuera de la organización pueden ver el contenido de Power BI, incluidos los informes paginados e interactivos, sin necesidad de comprar licencias individuales. 

![Uso compartido de contenido](media/service-premium-what-is/premium-sharing.png)

Premium permite una amplia distribución de contenido por parte de los usuarios de Pro sin solicitar licencias Pro a los destinatarios que ven el contenido. Las licencias Pro son necesarias para los creadores de contenido. Los creadores se conectan a orígenes de datos, modelan los datos y crean paneles e informes que se empaquetan como aplicaciones del área de trabajo. Los usuarios sin licencia Pro todavía pueden acceder a un área de trabajo que se encuentre en una capacidad Power BI Premium, siempre y cuando tengan un rol de espectador. 

Para más información, vea [Licencias de Power BI](service-admin-licensing-organization.md).

## <a name="analysis-services-in-power-bi-premium"></a>Analysis Services en Power BI Premium

De forma interna, el **motor Vertipaq de Analysis Services** probado por Microsoft impulsa los conjuntos de datos y áreas de trabajo de Power BI Premium. Analysis Services proporciona la capacidad de programación y compatibilidad con herramientas y aplicaciones cliente a través de las bibliotecas de cliente y las API que admiten el protocolo XMLA de estándar abierto. De manera predeterminada, las cargas de trabajo del conjunto de datos de la capacidad Premium de Power BI admiten conexiones *de solo lectura* desde herramientas y aplicaciones cliente de Microsoft y de terceros a través de un **punto de conexión de XMLA**. Los administradores de capacidad también pueden optar por deshabilitar o permitir las operaciones de *lectura/escritura* a través del punto de conexión.

Con el acceso de solo lectura, herramientas de Microsoft como SQL Server Management Studio (SSMS) y SQL Server Profiler, y aplicaciones de terceros como DAX Studio y aplicaciones de visualización de datos, se pueden conectar a conjuntos de datos Premium y consultarlos mediante XMLA, MDX, DAX, DMV y eventos de seguimiento. Con el acceso de lectura y escritura, herramientas de modelado de datos empresariales como Visual Studio con la extensión de proyectos de Analysis Services o Tabular Editor de código abierto pueden implementar modelos tabulares como un conjunto de datos en un área de trabajo Premium. Y con herramientas como SSMS, los administradores pueden usar el lenguaje de scripting de modelos tabulares (TMSL) para generar scripts de cambios de metadatos y escenarios de actualización de datos avanzados. 

Para obtener más información, consulte [Conectividad del conjunto de datos con el punto de conexión de XMLA](service-premium-connect-tools.md).

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)


## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Administración de las capacidades Premium](service-premium-capacity-manage.md)
> [Documentación sobre Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
