---
title: Arquitectura de la solución de BI en el centro de excelencia
description: Aprenda lo que debe tener en cuenta al diseñar y desarrollar una plataforma de BI sólida.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: v-pemyer
ms.openlocfilehash: d84f6a4fcf7ff531b76b6e731f165aa6e0df764f
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512134"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>Arquitectura de la solución de BI en el centro de excelencia

Este artículo se dirige a los profesionales y administradores de TI. Conocerá la arquitectura de la solución de BI en el COE y las distintas tecnologías empleadas. Las tecnologías incluyen Azure, Power BI y Excel. Juntas, pueden aprovecharse para ofrecer una plataforma de BI en la nube escalable y controlada por datos.

El diseño de una plataforma de BI sólida es algo parecido a crear un puente; un puente que conecta los datos de origen transformados y enriquecidos con los consumidores de datos. El diseño de esta estructura compleja requiere una mentalidad de ingeniería, aunque puede ser una de las arquitecturas de TI más creativas y gratificantes que pueda diseñar. En una organización de gran tamaño, una arquitectura de la solución de BI puede constar de lo siguiente:

- Orígenes de datos
- Ingesta de datos
- Preparación de datos o macrodatos
- Almacenamiento de datos
- Modelos semánticos de BI
- Informes

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="Diagrama en el que se muestra la arquitectura de plataforma de BI, desde orígenes de datos hasta ingesta de datos, macrodatos, almacén, almacenamiento de datos, modelos semánticos de BI, informes y aprendizaje automático.":::

La plataforma debe admitir demandas específicas. En concreto, se debe escalar y ejecutar para satisfacer las expectativas de los servicios de negocio y los consumidores de datos. Al mismo tiempo, debe ser segura desde el principio. Además, debe ser suficientemente resistente para adaptarse a los cambios, porque existe la certeza de que, con el tiempo, habrá que poner en línea nuevos datos y áreas temáticas.

## <a name="frameworks"></a>Marcos de trabajo

En Microsoft, desde el principio adoptamos un enfoque de tipo sistémico invirtiendo en el desarrollo de un marco. Los marcos de procesos técnicos y empresariales aumentan la reutilización del diseño y la lógica y ofrecen un resultado coherente. También ofrecen flexibilidad en la arquitectura, lo que aprovecha muchas tecnologías, y optimizan y reducen la sobrecarga de ingeniería a través de procesos repetibles.

Aprendimos que los marcos bien diseñados aumentan la visibilidad del linaje de datos, el análisis de impacto, el mantenimiento de la lógica de negocios, la administración de la taxonomía y la optimización de la gobernanza. Además, el desarrollo se hizo más rápido y la colaboración en los equipos de gran tamaño era más eficaz y receptiva.

En este artículo se describen algunos de los marcos de trabajo.

## <a name="data-models"></a>Modelos de datos

Los modelos de datos proporcionan control sobre cómo se estructuran los datos y cómo se accede a ellos. En el caso de servicios de negocio y consumidores de datos, los modelos de datos son la interfaz de la plataforma de BI.

Una plataforma de BI puede ofrecer tres tipos diferentes de modelos:

- Modelos empresariales
- Modelos semánticos de BI
- Modelos de Machine Learning (ML)

### <a name="enterprise-models"></a>Modelos empresariales

Los arquitectos de TI compilan y mantienen los **modelos empresariales**. A veces se les conoce como modelos dimensionales o data marts. Normalmente, los datos se almacenan en formato relacional como tablas de dimensiones y tablas de hechos. Estas tablas almacenan datos limpios y enriquecidos consolidados de muchos sistemas y representan un origen autoritativo para informes y análisis.

Los modelos empresariales proporcionan un origen de datos coherente y único para los informes y BI. Se crean una vez y se comparten como estándar corporativo. Las directivas de gobernanza garantizan la seguridad de los datos, por lo que el acceso a los conjuntos de datos confidenciales (como información de clientes o datos financieros), se restringe en caso necesario. Adoptan convenciones de nomenclatura que garantizan la coherencia, con lo que se afianza la credibilidad de los datos y la calidad.

En una plataforma de BI en la nube, los modelos empresariales se pueden implementar en un [grupo de Synapse SQL en Azure Synapse](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse). A continuación, el grupo de Synapse SQL se convierte en la versión única de la verdad con la que puede contar la organización para obtener conclusiones rápidas y eficaces.

### <a name="bi-semantic-models"></a>Modelos semánticos de BI

Los **modelos semánticos de BI** representan una capa semántica en los modelos empresariales. Los desarrolladores de BI y los usuarios empresariales los compilan y mantienen. Los desarrolladores de BI crean modelos semánticos de BI principales que obtienen datos de los modelos empresariales. Los usuarios empresariales pueden crear modelos independientes de menor escala, o bien pueden ampliar los modelos semánticos de BI principales con orígenes externos o de departamento. Los modelos semánticos de BI normalmente se centran en una sola área temática y a menudo son ampliamente compartidos.

Las capacidades empresariales no solo se habilitan por datos, sino también por modelos semánticos de BI que describen conceptos, relaciones, reglas y estándares. De este modo, representan estructuras intuitivas y fáciles de entender que definen relaciones de datos y encapsulan reglas de negocios como cálculos. También pueden aplicar permisos de datos específicos, que garanticen que las personas adecuadas tengan acceso a los datos correctos. Lo importante es que aceleran el rendimiento de las consultas y proporcionan un análisis interactivo con gran capacidad de respuesta, incluso con varios terabytes de datos. Al igual que los modelos empresariales, los modelos semánticos de BI adoptan convenciones de nomenclatura para garantizar la coherencia.

En una plataforma de BI en la nube, los desarrolladores de BI pueden implementar modelos semánticos de BI en [Azure Analysis Services](/azure/analysis-services/) o [capacidades de Power BI Premium](../admin/service-premium-what-is.md#reserved-capacities). Se recomienda su implementación en Power BI cuando se usa como capa de informes y análisis. Estos productos admiten diferentes modos de almacenamiento, lo que permite que las tablas del modelo de datos almacenen en memoria caché sus datos o utilicen [DirectQuery](directquery-model-guidance.md), que es una tecnología que pasa las consultas a través del origen de datos subyacente. DirectQuery es un modo de almacenamiento ideal cuando las tablas del modelo representan grandes volúmenes de datos o es necesario ofrecer resultados casi en tiempo real. Los dos modos de almacenamiento se pueden combinar: Los [modelos compuestos](composite-model-guidance.md) combinan tablas que usan distintos modos de almacenamiento en un único modelo.

En el caso de modelos con gran cantidad de consultas, puede usarse [Azure Load Balancer](/azure/load-balancer/load-balancer-overview) para distribuir uniformemente la carga de consultas entre réplicas de los modelos. También permite escalar las aplicaciones y crear modelos semánticos de BI de alta disponibilidad.

### <a name="machine-learning-models"></a>Modelos de Machine Learning

Los [**modelos de Machine Learning (ML)**](/windows/ai/windows-ml/what-is-a-machine-learning-model) los compilan y mantienen los científicos de datos. Se desarrollan principalmente a partir de orígenes sin procesar en el lago de datos.

Los modelos de ML entrenados pueden revelar patrones dentro de los datos. En muchas circunstancias, esos patrones pueden usarse para hacer predicciones que pueden emplearse para enriquecer los datos. Por ejemplo, el comportamiento de compra se puede usar para predecir el abandono de clientes o para segmentarlos. Los resultados de la predicción se pueden agregar a los modelos empresariales para permitir el análisis por segmento de clientes.

En una plataforma de BI en la nube, se puede usar [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) para entrenar, implementar, automatizar, administrar y realizar un seguimiento de los modelos de ML.

## <a name="data-warehouse"></a>Almacenamiento de datos

En el centro de una plataforma de BI se encuentra el almacenamiento de datos, que hospeda los modelos empresariales. Se trata de un origen de datos autorizados, como sistema de registro y como centro de conectividad, que presenta modelos empresariales para informes, BI y ciencia de datos.

Muchos servicios de negocio, como las aplicaciones de línea de negocio (LOB), pueden basarse en el almacenamiento de datos como un origen autoritativo y controlado de conocimiento empresarial.

En Microsoft, el almacenamiento de datos se hospeda en [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) y Azure Synapse Analytics.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="Imagen que muestra Azure Synapse Analytics en conexión con Azure Data Lake Storage Gen2.":::

- **ADLS Gen2** convierte a Azure Storage en los cimientos para crear lagos de datos empresariales en Azure. Está diseñado para proporcionar varios petabytes de información, al mismo tiempo que mantiene un rendimiento de cientos de gigabits. También ofrece transacciones y capacidad de almacenamiento de bajo costo. Además, admite el acceso compatible con Hadoop, lo que permite administrar los datos y acceder a ellos del mismo modo que lo haría con un sistema de archivos distribuido de Hadoop (HDFS). De hecho, [Azure HDInsight](/azure/hdinsight/), [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) y Azure Synapse Analytics pueden acceder a los datos almacenados en ADLS Gen2. Por lo tanto, en una plataforma de BI, es una buena opción almacenar datos de origen sin procesar, datos semiprocesados o almacenados provisionalmente y datos listos para producción. La usamos para almacenar todos los datos empresariales.
- **Azure Synapse Analytics** es un servicio de análisis que engloba el almacenamiento de datos empresariales y el análisis de macrodatos. Le ofrece la libertad de consultar los datos como prefiera, ya sea a petición sin servidor o con recursos aprovisionados, a escala. Synapse SQL, un componente de Azure Synapse Analytics, admite análisis completos basados en T‑SQL, por lo que resulta ideal para hospedar modelos empresariales que consten de tablas de dimensiones y de hechos. Las tablas se pueden cargar eficazmente desde ADLS Gen2 mediante consultas sencillas de [T-SQL de Polybase](/sql/relational-databases/polybase/polybase-guide). Entonces tiene la potencia de [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) para ejecutar análisis de alto rendimiento.

### <a name="business-rules-engine-framework"></a>Marco del Motor de reglas de negocio

Hemos desarrollado un marco de **Motor de reglas de negocio** (BRE) para catalogar cualquier lógica de negocios que se pueda implementar en la capa de almacenamiento de datos. Un BRE puede significar muchas cosas, pero en el contexto de un almacenamiento de datos resulta útil para crear columnas calculadas en tablas relacionales. Estas columnas calculadas normalmente se representan como cálculos matemáticos o expresiones que utilizan instrucciones condicionales.

Lo que se pretende es separar la lógica de negocios del código principal de BI. Tradicionalmente, las reglas de negocios están codificadas de forma rígida en procedimientos almacenados de SQL, por lo que a menudo resulta muy difícil mantenerlas cuando las necesidades del negocio cambian. En un BRE, las reglas de negocios se definen una vez y se usan varias veces cuando se aplican a distintas entidades de almacenamiento de datos. Si es necesario cambiar la lógica de cálculo, solo debe actualizarse en un único lugar y no en numerosos procedimientos almacenados. También hay una ventaja añadida: un marco de BRE impulsa la transparencia y visibilidad de la lógica de negocios implementada, que se puede exponer a través de un conjunto de informes que crean documentación de actualización automática.

## <a name="data-sources"></a>Orígenes de datos

Un almacenamiento de datos puede consolidar datos de prácticamente cualquier origen de datos. Se basa principalmente en orígenes de datos de aplicación de línea de negocio, que suelen ser bases de datos relacionales que almacenan datos específicos de cada tema para ventas, marketing, finanzas, etc. Estas bases de datos pueden estar hospedadas en la nube o residir en el entorno local. Otros orígenes de datos pueden estar basados en archivos, especialmente registros web o datos de IOT procedentes de dispositivos. Además, los datos pueden tener su origen en proveedores de software como servicio (SaaS).

En Microsoft, algunos de nuestros sistemas internos envían datos operativos directos a ADLS Gen2 con formatos de archivo sin procesar. Además de nuestro lago de datos, otros sistemas de origen incluyen aplicaciones de línea de negocio relacionales, libros de Excel, otros orígenes basados en archivos y repositorios de datos personalizados y de administración de datos maestros (MDM). Los repositorios de MDM nos permiten administrar los datos maestros para garantizar versiones de datos autoritativas, estandarizadas y validadas.

## <a name="data-ingestion"></a>Ingesta de datos

Periódicamente, y según los ritmos de la empresa, los datos se ingieren desde los sistemas de origen y se cargan en el almacenamiento de datos. Podría ser una vez al día o a intervalos más frecuentes. La ingesta de datos se refiere a la extracción, transformación y carga de datos. O, quizás al revés: extracción, carga y transformación de datos. La diferencia estriba en el lugar donde se produce la transformación. Las transformaciones se aplican para limpiar, ajustar, integrar y estandarizar los datos. Para obtener más información, consulte [Extracción, transformación y carga de datos (ETL)](/azure/architecture/data-guide/relational-data/etl).

En última instancia, el objetivo es cargar los datos correctos en el modelo empresarial con la mayor rapidez y eficacia posibles.

En Microsoft, usamos [Azure Data Factory](/azure/data-factory/introduction) (ADF). Los servicios se usan para programar y orquestar validaciones, transformaciones y cargas masivas de datos de los sistemas de origen externos en nuestro lago de datos. Todo esto se administra mediante marcos personalizados para procesar datos en paralelo y a escala. Además, se lleva a cabo un registro completo para admitir la solución de problemas, la supervisión del rendimiento y el desencadenamiento de notificaciones de alerta cuando se cumplen determinadas condiciones.

Mientras tanto, [Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) (una plataforma de análisis basada en Apache Spark optimizada para la plataforma de servicios en la nube de Azure) realiza transformaciones específicas para la ciencia de datos. También se compilan y ejecutan modelos de ML con cuadernos de Python. Las puntuaciones de estos modelos de ML se cargan en el almacenamiento de datos para integrar las predicciones con los informes y las aplicaciones empresariales. Dado que Azure Databricks accede directamente a los archivos de lago de datos, elimina o minimiza la necesidad de copiar o adquirir datos.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="Imagen que muestra el aprovisionamiento de datos y la orquestación de canalizaciones de datos de Azure Data Factory con Azure Databricks sobre Azure Data Lake Storage Gen2.":::

### <a name="ingestion-framework"></a>Marco de ingesta

Hemos desarrollado un **marco de ingesta** como un conjunto de procedimientos y tablas de configuración. Admite un enfoque controlado por datos para adquirir grandes volúmenes de datos a alta velocidad y con código mínimo. En resumen, este marco simplifica el proceso de adquisición de datos para cargar el almacenamiento de datos.

El marco depende de tablas de configuración que almacenan información relacionada con el origen y el destino de los datos tales como tipo de origen, servidor, base de datos, esquema y detalles relacionados con las tablas. Este enfoque de diseño significa que no es necesario desarrollar canalizaciones específicas de Azure Data Factory ni paquetes de [SQL Server Integration Services (SSIS)](/sql/integration-services/sql-server-integration-services). En su lugar, los procedimientos se escriben en el lenguaje de nuestra elección para crear canalizaciones de Azure Data Factory que se generan dinámicamente y se ejecutan en tiempo de ejecución. Por lo tanto, la adquisición de datos se convierte en un ejercicio de configuración que se pone en práctica fácilmente. Tradicionalmente, se necesitarían amplios recursos de desarrollo extensos para crear paquetes de Azure Data Factory o SSIS codificados de forma rígida.

El marco de ingesta se diseñó para simplificar el proceso de control de los cambios de esquema de origen ascendentes. Resulta fácil actualizar los datos de configuración, manual o automáticamente, cuando se detectan cambios en el esquema para adquirir los atributos recién agregados al sistema de origen.

### <a name="orchestration-framework"></a>Marco de orquestación

Hemos desarrollado un **marco de orquestación** para poner en práctica y orquestar nuestras canalizaciones de datos. Utiliza un diseño controlado por datos que depende de un conjunto de tablas de configuración. Estas tablas almacenan metadatos que describen las dependencias de canalización y cómo asignar los datos de origen a las estructuras de datos de destino. La inversión en el desarrollo de este marco adaptable se ha amortizado desde entonces; ya no es necesario codificar de forma rígida cada movimiento de datos.

## <a name="data-storage"></a>Almacenamiento de datos

Un lago de datos puede almacenar grandes volúmenes de datos sin procesar para su uso posterior junto con transformaciones de datos de almacenamiento provisional.

En Microsoft, usamos ADLS Gen2 como única fuente de confianza. Almacena datos sin procesar junto con datos almacenados provisionalmente y datos listos para producción. Proporciona una solución de lago de datos rentable y altamente escalable para análisis de macrodatos. La combinación del potencial de un sistema de archivos de alto rendimiento con una escala masiva, está optimizada para cargas de trabajo de análisis de datos, lo que acelera la obtención de conclusiones.

ADLS Gen2 proporciona lo mejor de dos mundos: el almacenamiento de blobs y un espacio de nombres de sistema de archivos de alto rendimiento, que se configuran con permisos de acceso específicos.

Los datos refinados se almacenan en una base de datos relacional para ofrecer un almacén de datos de alto rendimiento y altamente escalable para los modelos empresariales, con seguridad, gobernanza y capacidad de administración. Los data marts específicos de cada tema se almacenan en Azure Synapse Analytics, que luego se cargan mediante consultas de T-SQL de Polybase o de Azure Databricks.

## <a name="data-consumption"></a>Consumo de datos

En la capa de informes, los servicios de negocio consumen datos empresariales procedentes del almacenamiento de datos. También tienen acceso a los datos directamente en el lago de datos para realizar tareas de análisis ad hoc o de ciencia de datos.

Los permisos específicos se aplican en todas las capas: en el lago de datos, los modelos empresariales y los modelos semánticos de BI. Los permisos garantizan que los consumidores de datos solo pueden ver los datos para los que tienen derechos de acceso.

En Microsoft, usamos informes y paneles de Power BI e [informes paginados de Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md) Algunos informes y análisis ad hoc se realizan en Excel, especialmente en el caso de los informes financieros.

Publicamos diccionarios de datos, que proporcionan información de referencia sobre nuestros modelos de datos. Se han puesto a disposición de los usuarios a fin de que puedan descubrir información sobre nuestra plataforma de BI. Los diccionarios documentan los diseños de modelos y proporcionan descripciones sobre entidades, formatos, estructura, linaje de datos, relaciones y cálculos. Usamos [Azure Data Catalog](/azure/data-catalog/overview) para que nuestros orígenes de datos sean fáciles de detectar y entender.

Normalmente, los patrones de consumo de datos difieren en función del rol:

- Los **analistas de datos** se conectan directamente a los modelos semánticos de BI principales. Cuando los modelos semánticos de BI principales contienen todos los datos y la lógica que necesitan, usan conexiones dinámicas para crear informes y paneles de Power BI. Cuando tienen que ampliar los modelos con datos departamentales, crean [modelos compuestos](composite-model-guidance.md) de Power BI. Si se necesitan informes de tipo de hoja de cálculo, usan Excel para generar informes basados en modelos semánticos de BI principales o modelos semánticos de BI de departamento.
- Los **desarrolladores de BI** y los autores de informes operativos se relacionan directamente con los modelos empresariales. Usan Power BI Desktop para crear informes de análisis de conexión dinámica. También pueden crear informes de BI de tipo operativo como informes paginados de Power BI si escriben consultas SQL nativas para acceder a los datos de los modelos empresariales de Azure Synapse Analytics mediante T-SQL, o los modelos semánticos de Power BI mediante DAX o MDX.
- Los **científicos de datos** se conectan directamente a los datos del lago de datos. Usan cuadernos de Azure Databricks y Python para desarrollar modelos de ML, que a menudo son experimentales y requieren aptitudes especializadas para su uso en producción.

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="Imagen que muestra el consumo de Azure Synapse Analytics con Power BI, Excel y Azure Machine Learning.":::

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Inteligencia empresarial con Azure Synapse Analytics](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

### <a name="professional-services"></a>Servicios profesionales

Hay partners de Power BI certificados a su disposición para ayudar a su organización a configurar un COE. Pueden ofrecerle un rentable aprendizaje o una auditoría de los datos. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).

También puede ponerse en contacto con partners de consultoría experimentados. Pueden ayudarle a [valorar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evaluar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) o [implementar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
