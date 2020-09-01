---
title: Información general sobre la migración a Power BI
description: Aprenda a planear y llevar a cabo una migración desde otra herramienta de BI de terceros a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: aa17e6293a4bd946b1d6b7acad45623fa2393c57
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803515"
---
# <a name="power-bi-migration-overview"></a>Información general sobre la migración a Power BI

Los clientes adoptan cada vez más medidas para estandarizar Power BI con el fin de impulsar una cultura de datos, lo que implica habilitar inteligencia empresarial con características de autoservicio (SSBI) administrada, racionalizar la entrega de BI empresarial y resolver presiones económicas. La finalidad de esta serie de artículos sobre la migración a Power BI es proporcionarle instrucciones sobre cómo planear y llevar a cabo una migración desde una herramienta de BI de terceros a Power BI.

Los artículos de la serie sobre la migración a Power BI incluyen los siguientes:

1. Información general sobre la migración a Power BI (este artículo)
1. [Preparación para realizar la migración a Power BI](powerbi-migration-pre-migration-steps.md)
1. [Recopilación de requisitos para la migración a Power BI (fase 1)](powerbi-migration-requirements.md)
1. [Planeamiento de la implementación para la migración a Power BI (fase 2)](powerbi-migration-planning.md)
1. [Realización de una prueba de concepto para la migración a Power BI (fase 3)](powerbi-migration-proof-of-concept.md)
1. [Creación de contenido para la migración a Power BI (fase 4)](powerbi-migration-create-validate-content.md)
1. [Implementación en Power BI (fase 5)](powerbi-migration-deploy-support-monitor.md)
1. [Más información sobre las migraciones de los clientes a Power BI](powerbi-migration-learn-from-customers.md)

Hay dos supuestos: su organización tiene actualmente una plataforma de BI heredada y se ha tomado la decisión de migrar formalmente el contenido y los usuarios a Power BI. La migración al servicio Power BI es el objetivo principal de esta serie. Es posible que se apliquen consideraciones adicionales en el caso de los clientes de nubes nacionales, además de lo que se describe en esta serie de artículos.

En el diagrama siguiente se muestran cuatro fases generales para implementar Power BI en su organización.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="Imagen que muestra las cuatro fases generales, que se describen en la tabla siguiente.":::

|Fase|Descripción|
|--------|-----------|
|![Fase 1.](media/common/icon-01-red-30x30.png)|**Configuración y evaluación de Power BI**. La primera fase implica el establecimiento de la arquitectura inicial de Power BI. En este momento, se controlan la implementación preliminar y el planeamiento de la gobernanza, así como evaluaciones de Power BI, como el análisis de costos y beneficios, o la rentabilidad de la inversión.|
|![Fase 2.](media/common/icon-02-red-30x30.png)|**Creación rápida de soluciones en Power BI**. En la segunda fase, los autores de BI con características de autoservicio pueden empezar a usar y evaluar Power BI en función de sus necesidades, y se puede obtener valor de Power BI rápidamente. Las actividades de la fase 2 conceden importancia a la agilidad y al valor empresarial rápido, que son fundamentales para lograr la aceptación de la selección de una nueva herramienta de BI como Power BI. Por esta razón, el diagrama muestra las actividades de la fase 2 en paralelo con las actividades de migración de la fase 3.|
|![Fase 3.](media/common/icon-03-red-30x30.png)|**Migración de recursos de BI de la plataforma heredada a Power BI**. La tercera fase aborda la migración a Power BI. Se trata del objetivo de esta serie de artículos sobre la migración a Power BI. En la sección siguiente se describen cinco fases de migración específicas.|
|![Fase 4.](media/common/icon-04-red-30x30.png)|**Adopción, control y supervisión de Power BI**. La fase final consta de actividades continuas tales como el fomento de una cultura de datos, la comunicación y el aprendizaje. Estas actividades tienen gran repercusión en una implementación eficaz de Power BI. Es importante contar con directivas y procesos de gobernanza y seguridad adecuados para su organización, además de auditorías y supervisiones que le permitan escalar, crecer y mejorar continuamente.|

> [!IMPORTANT]
> Una migración formal a Power BI casi siempre se produce en paralelo con el desarrollo de una nueva solución de Power BI. _Solución de Power BI_ es un término genérico que engloba el uso de datos e informes. Un solo archivo de Power BI Desktop (.pbix) puede contener un modelo de datos, un informe o ambos. Se recomienda [separar el modelo de datos de los informes](../guidance/report-separate-from-model.md) con fines de reutilización de datos, pero no es necesario.
>
> El uso de Power BI para crear requisitos, mientras planea y lleva a cabo la migración formal, le ayudará a ganar aceptación. Las fases simultáneas ofrecen a los autores de contenido una experiencia práctica y real con Power BI.

## <a name="five-stages-of-a-power-bi-migration"></a>Cinco fases de una migración a Power BI

La fase 3 del diagrama aborda la migración a Power BI. Durante esta fase, hay cinco fases comunes.

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="Imagen que muestra las fases de una migración a Power BI, que se describen a continuación.":::

Las fases que se muestran en el diagrama anterior son las siguientes:

- [Pasos previos a la migración](#pre-migration-steps)
- [Fase 1: recopilación y priorización de requisitos](#stage-1-gather-requirements-and-prioritize)
- [Fase 2: planeamiento de la implementación](#stage-2-plan-for-deployment)
- [Fase 3: realización de una prueba de concepto](#stage-3-conduct-proof-of-concept)
- [Fase 4: creación y validación de contenido](#stage-4-create-and-validate-content)
- [Fase 5: implementación, soporte técnico y supervisión](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>Pasos previos a la migración

Los pasos previos a la migración incluyen acciones que puede plantearse antes de comenzar un proyecto para migrar contenido de una plataforma de BI heredada a Power BI. Normalmente se incluye el planeamiento inicial de la implementación de nivel de inquilino. Para más información sobre estas actividades, consulte [Preparación para realizar la migración a Power BI](powerbi-migration-pre-migration-steps.md).

### <a name="stage-1-gather-requirements-and-prioritize"></a>Fase 1: recopilación y priorización de requisitos

El énfasis de la fase 1 radica en recopilar información y planear la migración de una sola solución. Este proceso debe ser iterativo y tener como ámbito un esfuerzo de tamaño razonable. La salida de la fase 1 incluye un inventario por orden de prioridad de los informes y datos que se van a migrar. Se necesitan actividades adicionales en las fases 2 y 3 para calcular por completo el nivel de esfuerzo. Para más información sobre las actividades de la fase 1, consulte [Recopilación de requisitos para la migración a Power BI](powerbi-migration-requirements.md).

### <a name="stage-2-plan-for-deployment"></a>Fase 2: planeamiento de la implementación

La fase 2 se centra en cómo se pueden cumplir los requisitos definidos en la fase 1 para cada solución específica. La salida de la fase 2 incluye tantos detalles como sea posible para guiar el proceso, aunque se trata de un proceso iterativo y no lineal. La creación de una prueba de concepto (fase 3) puede producirse en paralelo con esta fase. Incluso durante la creación de la solución (fase 4), puede que haya información adicional que influya en las decisiones de planeamiento de la implementación. Este tipo de planeamiento de implementación de la fase 2 se centra en el nivel de la solución, a la vez que respeta las decisiones ya realizadas en el nivel de la organización. Para más información sobre las actividades de la fase 2, consulte [Planeamiento de la implementación para la migración a Power BI](powerbi-migration-planning.md).

### <a name="stage-3-conduct-proof-of-concept"></a>Fase 3: realización de una prueba de concepto

El énfasis de la fase 3 se pone en abordar los factores desconocidos y mitigar los riesgos cuanto antes. Una prueba de concepto (POC) técnica resulta útil para validar supuestos y se puede realizar de forma iterativa junto con el planeamiento de la implementación (fase 2). La salida de esta fase es una solución de Power BI de ámbito reducido. Tenga en cuenta que no se pretende que la POC sea un trabajo descartable. Aunque es probable que haya que realizar trabajo adicional en la fase 4 para que esté lista para producción. En este sentido, en su organización, puede hacer referencia a esta actividad como un prototipo, un piloto, un boceto, un inicio rápido o un producto mínimamente viable (MVP). No siempre es necesario realizar una POC y se puede realizar de manera informal. Para más información sobre las actividades de la fase 3, consulte [Realización de una prueba de concepto para la migración a Power BI](powerbi-migration-proof-of-concept.md).

### <a name="stage-4-create-and-validate-content"></a>Fase 4: creación y validación de contenido

En la fase 4 es donde se realiza el trabajo real para convertir la POC en una solución lista para producción. La salida de esta fase es una solución de Power BI completa que se ha validado en un entorno de desarrollo. Debe estar lista para implementación en la fase 5. Para más información sobre las actividades de la fase 4, consulte [Creación de contenido para la migración a Power BI](powerbi-migration-create-validate-content.md).

### <a name="stage-5-deploy-support-and-monitor"></a>Fase 5: implementación, soporte técnico y supervisión

El objetivo principal de la fase 5 es implementar la nueva solución de Power BI en producción. La salida de esta fase es una solución de producción que los usuarios empresariales utilizan de forma activa. Cuando se usa una metodología ágil, conviene tener algunas mejoras planeadas, que se entregarán en una futura iteración. Según su nivel de comodidad con Power BI, como el uso de minimización de riesgos e interrupción del usuario, puede optar por realizar una implementación por fases. También puede implementar inicialmente en un grupo más pequeño de usuarios piloto. El soporte técnico y la supervisión también son importantes en esta fase y de forma continua. Para más información sobre las actividades de la fase 5, consulte [Migración a Power BI](powerbi-migration-deploy-support-monitor.md).

> [!TIP]
> La mayoría de los conceptos descritos en esta serie de artículos sobre la migración a Power BI se aplican también a un proyecto de implementación estándar de Power BI.

## <a name="consider-migration-reasons"></a>Consideración de los motivos de la migración

La habilitación de una cultura de datos productiva y de calidad es un objetivo principal de muchas organizaciones. Power BI es una herramienta excelente para facilitar este objetivo. Tres razones comunes por las que podría considerarse una migración a Power BI se pueden resumir en lo siguiente:

- **Habilitar BI con características de autoservicio administradas**, presentando nuevas funcionalidades que potencien la comunidad de usuarios de BI de autoservicio. Power BI hace que el acceso a la información y la toma de decisiones estén disponibles más ampliamente, mientras que se depende menos de aptitudes especializadas que pueden ser difíciles de encontrar.
- **Racionalizar la entrega de BI empresarial** para cumplir requisitos que no se abordan con las herramientas de BI existentes, al tiempo que se disminuye el nivel de complejidad, se reduce el costo de propiedad y es posible su estandarización a partir de varias herramientas de BI actualmente en uso.
- **Resolver presiones económicas** para aumentar la productividad con menos recursos, tiempo y personal.

## <a name="achieve-power-bi-migration-success"></a>Logro del éxito en la migración a Power BI

Cada migración es ligeramente diferente. Puede depender de la estructura organizativa, las estrategias de datos, la madurez de la administración de datos y los objetivos de la organización. Sin embargo, hay algunas prácticas que vemos constantemente cuando nuestros clientes logran el éxito en la migración a Power BI.

- **Patrocinio ejecutivo**: identifique un patrocinador ejecutivo al principio del proceso. Esta persona debe ser alguien que impulse BI de forma activa en la organización y que se dedique personalmente a lograr un resultado positivo de la migración. Lo ideal es que el patrocinador ejecutivo tenga la autoridad y responsabilidad finales en los resultados relacionados con Power BI.
- **Aprendizaje, soporte técnico y comunicación**: reconozca que es algo más que una iniciativa tecnológica. Cualquier proyecto de inteligencia empresarial o de análisis es también una iniciativa que involucra al personal, por lo que es conveniente invertir desde el principio en el aprendizaje y el soporte técnico del usuario. Además, cree un plan de comunicación que explique con transparencia a todas las partes interesadas lo que sucede y el porqué, y que establezca expectativas realistas. Asegúrese de incluir un bucle de comentarios en el plan de comunicación para recoger las aportaciones de las partes interesadas.
- **Logros rápidos**: inicialmente, dé prioridad a los elementos más importantes que tengan un valor empresarial tangible y sean apremiantes. En lugar de tratar estrictamente de migrar siempre los informes exactamente como aparecen en la plataforma de BI heredada, céntrese en la pregunta empresarial que el informe trata de responder (incluida la acción que se va a realizar) al abordar el informe rediseñado.
- **Modernización y mejoras**: esté dispuesto a replantearse cómo se han hecho siempre las cosas. Una migración puede brindar una oportunidad de lograr mejoras. Por ejemplo, podría eliminar la preparación manual de los datos o reubicar reglas de negocio que se limitaban a un único informe. Valore la posibilidad de refactorizar, modernizar y consolidar las soluciones existentes cuando el esfuerzo pueda justificarse. Esto puede incluir la consolidación de varios informes en uno o la eliminación de artefactos heredados que no se han usado durante un tiempo.
- **Aprendizaje continuo**: esté preparado para usar un enfoque por fases mientras aprende y se adapta continuamente. Trabaje en ciclos cortos e iterativos que aporten valor rápidamente. Haga una práctica frecuente de completar pequeñas POC para minimizar el riesgo de factores desconocidos, validar supuestos e informarse sobre las nuevas características. Como Power BI es un servicio en la nube que se actualiza mensualmente, es importante mantenerse al tanto de los desarrollos y ajustar el rumbo cuando sea necesario.
- **Resistencia al cambio**: entienda que tal vez haya distintos niveles de resistencia al cambio; algunos usuarios se resistirán al aprendizaje de una nueva herramienta. Además, algunos profesionales que han dedicado mucho tiempo y esfuerzo para obtener experiencia con una herramienta de BI distinta pueden sentirse amenazados por ser desplazados. Esté preparado, ya que pueden originarse controversias internas, especialmente en organizaciones altamente descentralizadas.
- **Restricciones**: sea realista con los planes de migración, lo que incluye la financiación, las estimaciones de tiempo, así como los roles y las responsabilidades de todos los usuarios implicados.

## <a name="acknowledgments"></a>Agradecimientos

Melissa Coates, Microsoft MVP de la plataforma de datos y propietaria de [Coates Data Strategies](https://www.coatesdatastrategies.com/), es quien ha redactado esta serie de artículos. Entre los colaboradores y revisores se incluyen Marc Reguera, Venkatesh Titte, Patrick Baumgartner, Tamer Farag, Richard Tkachuk, Matthew Roche, Adam Saxton, Chris Webb, Mark Vaillancourt, Daniel Rubiolo, David Iseminger y Peter Myers.

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie sobre la migración a Power BI](powerbi-migration-pre-migration-steps.md), conocerá los pasos previos a la migración a Power BI.

Otros recursos útiles incluyen los siguientes:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Migración de informes de SSRS a Power BI](migrate-ssrs-reports-to-power-bi.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
