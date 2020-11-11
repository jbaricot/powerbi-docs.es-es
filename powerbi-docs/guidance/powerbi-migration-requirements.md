---
title: Recopilación de requisitos para migrar a Power BI
description: Guía sobre la recopilación y priorización de requisitos al migrar a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 21d619c42648f90746af9961475bb531dc24d5ab
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396665"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>Recopilación de requisitos para migrar a Power BI

En este artículo se explica la **fase 1** , que se refiere a la recopilación y priorización de requisitos al migrar a Power BI.

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="Imagen en la que se muestran las fases de una migración de Power BI. En este artículo se resalta la fase 1.":::

> [!NOTE]
> Para obtener una explicación completa del gráfico anterior, vea [Información general sobre la migración de Power BI](powerbi-migration-overview.md).

El énfasis de la fase 1 se pone en la recopilación de información y la planeación de una solución individual que se va a migrar a Power BI.

El resultado de la fase 1 incluye los requisitos detallados a los que se ha dado prioridad. Pero es necesario finalizar por completo las actividades adicionales de las fases 2 y 3 para estimar totalmente el nivel de esfuerzo.

> [!IMPORTANT]
> Las fases 1-5 representan actividades relacionadas con una solución concreta. Hay decisiones y actividades en el nivel de organización o inquilino que afectan al proceso en el nivel de solución. Algunas de esas actividades de planeación de nivel superior se tratan en el artículo [Información general sobre la migración de Power BI](powerbi-migration-overview.md). Cuando proceda, dé preferencia a las decisiones de nivel de organización por eficacia y coherencia.

> [!TIP]
> La mayoría de los temas que se tratan en este artículo también se aplican a un proyecto de implementación estándar de Power BI.

## <a name="compile-requirements"></a>Compilación de requisitos

El inventario de los artefactos de BI existentes, compilado en los [pasos previos a la migración](powerbi-migration-pre-migration-steps.md), se convierte en la entrada de los requisitos de la nueva solución que se va a crear en Power BI. La recopilación de requisitos consiste en comprender el estado actual, así como los elementos que los usuarios quieren cambiar o refactorizar al rediseñar informes en Power BI. Los requisitos detallados resultan útiles para el plan de implementación de la solución de la [fase 2](powerbi-migration-planning.md), durante la creación de una prueba de concepto en la [fase 3](powerbi-migration-proof-of-concept.md) y al crear la solución lista para producción en la [fase 4](powerbi-migration-create-validate-content.md).

### <a name="gather-report-requirements"></a>Recopilación de requisitos de informe

Compile información detallada y fácil de referenciar sobre los informes, como:

- **Propósito, público y acción esperada:** identifique el propósito y el proceso empresarial aplicable a cada informe, así como el público, el flujo de trabajo analítico y la acción esperada que deben realizar los consumidores del informe.
- **Empleo del informe por parte de los consumidores:** le recomendamos que se reúna con los consumidores del informe existente para comprender exactamente lo que hacen con él. Puede observar que ciertos elementos del informe se pueden eliminar o mejorar en la nueva versión de Power BI. Este proceso conlleva una inversión de tiempo adicional, pero es valioso para informes críticos o que se usan con frecuencia.
- **Propietario y experto en la materia:** identifique al propietario del informe y a los expertos en la materia asociados al informe o al dominio de datos. Pueden convertirse en los propietarios del nuevo informe de Power BI en el futuro. Incluya cualquier requisito específico de administración de cambios (los requisitos suelen diferir entre las soluciones administradas por TI y las administradas por el negocio), así como las aprobaciones, que se van a necesitar cuando se realicen cambios en adelante.
- **Método de entrega de contenido:** aclare las expectativas de los consumidores del informe en cuanto a la entrega de contenido. Puede ser una ejecución interactiva a petición, insertada dentro de una aplicación personalizada, o una entrega según una programación mediante una suscripción de correo electrónico. También puede haber requisitos para desencadenar notificaciones de alerta.
- **Necesidades de interactividad:** determine qué requisitos de interactividad _debe tener_ y cuáles sería _agradable tener_ , como filtros, exploración en profundidad u obtención de detalles.
- **Orígenes de datos:** asegúrese de que se detectan todos los orígenes de datos necesarios para el informe y de que se entienden las necesidades de latencia de datos (actualización de datos). Identifique los requisitos de datos históricos, tendencias e instantáneas de datos de cada informe, de modo que se puedan alinear con los requisitos de datos. La documentación del origen de datos también puede ser útil más adelante cuando se realice la validación de datos de un nuevo informe con sus datos de origen.
- **Requisitos de seguridad:** aclare los requisitos de seguridad (como los visores permitidos, los editores permitidos y cualquier necesidad de seguridad de nivel de fila), incluidas las excepciones a la seguridad normal de la organización. Documente cualquier nivel de confidencialidad de datos, privacidad de datos o necesidades regulatorias o de cumplimiento.
- **Cálculos, KPI y reglas de negocio:** identifique y documente todos los cálculos, KPI y reglas de negocio que estén definidos actualmente en el informe existente para que se puedan alinear con los requisitos de datos.
- **Requisitos de uso, diseño y cosméticos:** identifique las necesidades específicas de uso, diseño y cosméticas relacionadas con las visualizaciones de datos, los requisitos de agrupación y ordenación y la visibilidad condicional. Incluya cualquier consideración específica relacionada con la entrega a dispositivos móviles.
- **Necesidades de impresión y exportación:** determine si hay algún requisito específico para imprimir, exportar o disponer de un diseño perfecto. Estas necesidades influyen en qué tipo de informe va a ser más adecuado (como un informe de Power BI, Excel o paginado). Tenga en cuenta que los consumidores de los informes suelen dar mucha importancia al modo en que siempre han hecho las cosas, así que no tenga miedo de cuestionar su forma de pensar. Asegúrese de hablar de _mejoras_ en lugar de _cambios_.
- **Riesgos o preocupaciones:** determine si hay otros requisitos técnicos o funcionales para los informes, así como cualquier riesgo o preocupación con respecto a la información que se presenta en ellos.
- **Incidencias abiertas y elementos de trabajo pendiente:** identifique el mantenimiento futuro, los problemas conocidos o las solicitudes aplazadas para agregarlos al trabajo pendiente en este momento.

> [!TIP]
> Considere la posibilidad de clasificar los requisitos como requisitos que _debe tener_ o que sería _agradable tener_. A menudo los consumidores solicitan todo lo que pueden necesitar por adelantado porque creen que puede ser su única oportunidad de realizar solicitudes. Además, al abordar prioridades en varias iteraciones, ponga el trabajo pendiente a disposición de las partes interesadas. Eso ayuda a la comunicación, la toma de decisiones y el seguimiento de los compromisos pendientes.

### <a name="gather-data-requirements"></a>Recopilación de requisitos de datos

Compile información detallada relativa a los datos, como:

- **Consultas existentes:** identifique si existen consultas de informe o procedimientos almacenados existentes que pueda usar un [modelo DirectQuery](../connect-data/desktop-use-directquery.md) o un [modelo compuesto](../transform-model/desktop-composite-models.md), o que se puedan convertir en un modelo de importación.
- **Tipos de orígenes de datos:** compile los tipos de orígenes de datos que sean necesarios, incluidos orígenes de datos centralizados (por ejemplo, un almacenamiento de datos de negocio) y orígenes de datos no estándar (como archivos planos o archivos de Excel que aumenten los orígenes de datos de negocio con fines informativos). También es importante saber dónde se encuentran los orígenes de datos a efectos de conectividad de la [puerta de enlace de datos](../connect-data/service-gateway-onprem.md).
- **Necesidades de estructura de datos y limpieza:** determine la estructura de datos de cada origen de datos necesario y en qué medida se necesitan actividades de [limpieza de datos](../transform-model/desktop-query-overview.md).
- **Integración de datos:** evalúe cómo se va a controlar la integración de datos cuando haya varios orígenes de datos y cómo se pueden definir [relaciones](../transform-model/desktop-create-and-manage-relationships.md) entre cada tabla del modelo. Identifique elementos de datos específicos necesarios para simplificar el modelo y [reducir su tamaño](import-modeling-data-reduction.md).
- **Latencia de datos aceptable:** determine las necesidades de latencia de datos de cada origen de datos. Estas van a influir en las decisiones sobre qué [modo de almacenamiento de datos](../transform-model/desktop-storage-mode.md) usar. También es importante conocer la frecuencia de actualización de datos de las tablas del modelo de importación.
- **Volumen de datos y escalabilidad:** evalúe las expectativas de volumen de datos, que van a influir en las decisiones sobre la [compatibilidad con modelos grandes](../admin/service-premium-large-models.md) y el diseño de modelos DirectQuery o [modelos compuestos](../transform-model/desktop-composite-models.md). También es fundamental conocer las consideraciones relacionadas con las necesidades de datos históricos. En el caso de los conjuntos de datos de mayor tamaño, también es necesario determinar las reglas de [actualización incremental de datos](../admin/service-premium-incremental-refresh.md).
- **Medidas, KPI y reglas de negocio:** evalúe las necesidades de medidas, KPI y reglas de negocio. Van a afectar a las decisiones sobre dónde aplicar la lógica: en el conjunto de datos o en el proceso de integración de datos.
- **Datos maestros y catálogo de datos:** considere si hay problemas en los datos maestros que requieran atención. Determine si la integración con un catálogo de datos empresariales es adecuada para mejorar la detectabilidad, el acceso a las definiciones o la generación de una terminología coherente aceptada por la organización.
- **Seguridad y privacidad de los datos:** determine si hay alguna consideración de seguridad o de privacidad de datos específica para los conjuntos de datos, incluidos requisitos de [seguridad de nivel de fila](../admin/service-admin-rls.md).
- **Incidencias abiertas y elementos de trabajo pendiente:** agregue cualquier problema conocido, defectos sabidos de calidad de los datos, mantenimiento futuro o solicitudes aplazadas al trabajo pendiente en este momento.

> [!IMPORTANT]
> La reutilización de datos se puede lograr con [conjuntos de datos compartidos](../connect-data/service-datasets-share.md), que opcionalmente se pueden [certificar](../collaborate-share/service-endorse-content.md) para indicar confiabilidad y mejorar la capacidad de detección. La reutilización de la preparación de datos se puede lograr con [flujos de datos](../transform-model/dataflows/dataflows-introduction-self-service.md) para reducir la lógica repetitiva en varios conjuntos de datos. Los flujos de datos también pueden reducir de forma considerable la carga sobre los sistemas de origen, ya que los datos se recuperan con menos frecuencia: varios conjuntos de datos pueden importar datos del flujo de datos.

## <a name="identify-improvement-opportunities"></a>Identificación de oportunidades de mejora

En la mayoría de las situaciones, se producen algunas modificaciones y mejoras. Es raro que se produzca una migración directa uno a uno sin ninguna refactorización ni mejora. Los tres tipos de mejoras que puede considerar incluyen:

- **Consolidación de informes:** los informes similares se pueden consolidar mediante técnicas como filtros, marcadores o personalización. Si tiene menos informes, cada uno con mayor flexibilidad, esto puede mejorar considerablemente la experiencia de los consumidores de los informes. Le recomendamos que optimice los conjuntos de datos de [Preguntas y respuestas (consultas en lenguaje natural)](../natural-language/q-and-a-best-practices.md) para ofrecer una flexibilidad aún mayor a los consumidores de informes, permitiéndoles crear sus propias visualizaciones.
- **Mejoras de eficacia:** durante la recopilación de requisitos, a menudo se pueden identificar mejoras. Por ejemplo, si los analistas compilan números manualmente o si se puede simplificar un flujo de trabajo. [Power Query](../transform-model/desktop-query-overview.md) puede desempeñar un importante papel en el reemplazo de actividades manuales que se realizan actualmente. Si los analistas de negocios se encuentran realizando las mismas actividades para limpiar y preparar los datos de forma habitual, los pasos de preparación de datos repetibles de Power Query pueden traducirse en un ahorro de tiempo considerable y una reducción de errores.
- **Centralización del modelo de datos:** un conjunto de datos certificado y acreditado actúa como espina dorsal de un programa de BI autoservicio administrado. En este caso, los datos se administran una vez y los analistas tienen flexibilidad para usar y aumentar esos datos a fin de satisfacer sus necesidades de elaboración de informes y análisis.

> [!NOTE]
> Para obtener más información sobre la centralización de modelos de datos, lea sobre [Disciplina en el núcleo](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) y [Flexibilidad en el borde](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="prioritize-and-assess-complexity"></a>Priorización y evaluación de la complejidad

En este punto, el inventario inicial está disponible y puede incluir requisitos específicos. Al priorizar el conjunto inicial de artefactos de BI listos para la migración, los informes y los datos se deben considerar colectivamente, así como de forma independiente entre sí.

Identifique los informes de alta prioridad, que pueden incluir informes que:

- Aporten un valor considerable a la empresa.
- Se ejecuten con frecuencia.
- Sean necesarios para la alta dirección o los ejecutivos.
- Impliquen un nivel de complejidad razonable (para mejorar las posibilidades de éxito durante las iteraciones de migración iniciales).

Identifique los datos de alta prioridad, que pueden incluir datos que:

- Contengan elementos de datos críticos.
- Sean datos comunes de la organización que sirvan para muchos casos de uso.
- Se puedan usar para crear un conjunto de datos compartido que los informes y muchos autores de informes puedan reutilizar.
- Impliquen un nivel de complejidad razonable (para mejorar las posibilidades de éxito durante las iteraciones de migración iniciales).

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie de migración de Power BI](powerbi-migration-planning.md) se proporciona información sobre la fase 2, que se refiere a la planeación de la migración de una única solución de Power BI.

Otros recursos útiles incluyen:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).