---
title: Realización de una prueba de concepto para migrar a Power BI
description: Guía sobre la realización de una prueba de concepto al migrar a Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: a51aaee15fc2a5e8d8facc1d34c0724dfa71d663
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086519"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>Realización de una prueba de concepto para migrar a Power BI

En este artículo se explica la **fase 3**, que está relacionada con la elaboración de una prueba de concepto (POC) para mitigar el riesgo y abordar los factores desconocidos cuanto antes al migrar a Power BI.

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="Imagen en la que se muestran las fases de una migración de Power BI. En este artículo se resalta la fase 3.":::

> [!NOTE]
> Para obtener una explicación completa del gráfico anterior, vea [Información general sobre la migración de Power BI](powerbi-migration-overview.md).

La atención de la fase 3 se centra en abordar los factores desconocidos y mitigar los riesgos cuanto antes. Una prueba de concepto técnica resulta útil para validar suposiciones. Se puede realizar de forma iterativa a la vez que el plan de implementación de la solución (explicado en la [fase 2](powerbi-migration-planning.md)).

El resultado de esta fase es una solución de Power BI de ámbito limitado, que aborda las preguntas abiertas iniciales y que está lista para el trabajo adicional de la [fase 4](powerbi-migration-create-validate-content.md), que consiste en prepararla para producción.

> [!IMPORTANT]
> No se pretende que la prueba de concepto sea un trabajo descartable, sino que se espera que sea una iteración temprana de la solución lista para producción. En la organización, puede hacer referencia a esta actividad como un prototipo, un piloto, un boceto, un inicio rápido o un producto mínimamente viable (MVP). No siempre es necesario realizar una prueba de concepto, e incluso se podría hacer de manera informal.

> [!TIP]
> La mayoría de los temas que se tratan en este artículo también se aplican a un proyecto de implementación estándar de Power BI. A medida que la organización gana experiencia con Power BI, se reduce la necesidad de llevar a cabo pruebas de concepto. Pero debido a la rápida cadencia de versiones con Power BI y a la incorporación continua de nuevas características, puede realizar pruebas de concepto periódicas con fines de aprendizaje.

## <a name="set-poc-goals-and-scope"></a>Establecimiento de los objetivos y el ámbito de la prueba de concepto

Al realizar una prueba de concepto, céntrese en los siguientes objetivos:

- Compruebe sus suposiciones sobre el funcionamiento de una característica.
- Infórmese sobre las diferencias de funcionamiento entre Power BI y la plataforma de BI heredada.
- Valide el reconocimiento inicial de determinados requisitos con expertos en la materia.
- Cree un conjunto de datos pequeño con datos reales para comprender y detectar cualquier problema con la estructura de datos, las relaciones, los tipos de datos o los valores de datos.
- Experimente con las expresiones de [sintaxis DAX](/dax/) que usan los cálculos del modelo y valídelas.
- Pruebe la conectividad del origen de datos mediante una puerta de enlace (si va a ser un origen de puerta de enlace).
- Pruebe la actualización de datos mediante una puerta de enlace (si va a ser un origen de puerta de enlace).
- Compruebe las configuraciones de seguridad, incluida la seguridad de nivel de fila, si procede.
- Experimente con las decisiones cosméticas y de diseño.
- Compruebe que toda la funcionalidad del servicio Power BI funciona según lo previsto.

El ámbito de la prueba de concepto depende de cuáles sean los factores desconocidos o de los objetivos que se deban validar con los compañeros. Para reducir la complejidad, mantenga el ámbito de la prueba de concepto lo más restringido posible.

Lo más normal en una migración es que los requisitos sean conocidos porque haya una solución existente desde la que empezar. Pero, en función de la cantidad de mejoras que se vayan a realizar o de las capacidades existentes de Power BI, una prueba de concepto sigue proporcionando un valor considerable. Además, la elaboración de un prototipo con los comentarios de los consumidores puede ser adecuada para aclarar los requisitos rápidamente, especialmente si se realizan mejoras.

> [!IMPORTANT]
> Aunque una prueba de concepto solo incluya un subconjunto de datos, o únicamente objetos visuales limitados, suele ser importante realizarla de principio a fin. Es decir, desde el desarrollo en Power BI Desktop hasta la implementación en un área de trabajo de desarrollo del servicio Power BI. Es la única manera de cumplir los objetivos de la prueba de concepto en su totalidad. Esto se da especialmente si el servicio Power BI debe proporcionar una funcionalidad crítica que no se ha usado antes, como un conjunto de datos de DirectQuery mediante inicio de sesión único. Durante la prueba de concepto, centre los esfuerzos en los aspectos sobre los que no está seguro o que necesita comprobar con otros usuarios.

## <a name="handle-differences-in-power-bi"></a>Control de las diferencias en Power BI

Power BI puede usarse como _herramienta basada en modelos_ o como _herramienta basada en informes_. Una solución basada en modelos conlleva el desarrollo de un modelo de datos, mientras que una solución basada en informes se conecta a un modelo de datos ya implementado.

Debido a su extrema flexibilidad, hay algunos aspectos sobre Power BI que pueden ser sustancialmente diferentes a la plataforma de BI heredada desde la que se está migrando.

### <a name="consider-redesigning-the-data-architecture"></a>Consideración del rediseño de la arquitectura de datos

Si va a migrar desde una plataforma de BI heredada que tiene su propia capa semántica, es probable que la creación de un conjunto de datos de importación sea una buena opción. Power BI funciona mejor con un diseño de tabla de [esquema de estrella](star-schema.md). Por lo tanto, si la capa semántica heredada no es un esquema de estrella, es posible que se requiera cierto rediseño para beneficiarse totalmente de Power BI. El esforzarse en definir una capa semántica que se ajuste a los principios de diseño de los esquemas de estrella (incluidas las relaciones, las medidas usadas habitualmente y la terminología organizativa descriptiva) constituye un excelente punto de partida para los autores de informes autoservicio.

Si va a migrar desde una plataforma de BI heredada donde los informes hacen referencia a orígenes de datos relacionales mediante consultas SQL o procedimientos almacenados, y si tiene previsto usar Power BI en [modo DirectQuery](../connect-data/desktop-use-directquery.md), es posible que pueda lograr prácticamente una migración uno a uno del modelo de datos.

> [!CAUTION]
> Si ve la creación de una gran cantidad de archivos de Power BI Desktop que componen una sola tabla importada, normalmente es un indicador de que el diseño no es óptimo. Si observa esta situación, investigue si el uso de [conjuntos de datos compartidos](../connect-data/service-datasets-across-workspaces.md) creados mediante un diseño de [esquema de estrella](star-schema.md) podría lograr un mejor resultado.

### <a name="decide-how-to-handle-dashboard-conversions"></a>Decisión de cómo controlar conversiones de panel

En el sector de BI, un panel es una colección de objetos visuales que muestra métricas clave en una sola página. Pero en Power BI un panel representa una característica de visualización específica que solo se puede crear en el servicio Power BI. Al migrar un panel desde una plataforma de BI heredada hay dos opciones:

1. El panel heredado se puede volver a crear como _informe_ de Power BI. La mayoría de los informes se crean con Power BI Desktop. Los informes paginados y los informes de Excel también son opciones alternativas.
2. El panel heredado se puede volver a crear como _panel_ de Power BI. Los [paneles](../fundamentals/service-basic-concepts.md#dashboards) son una característica de visualización del servicio Power BI. Los objetos visuales de panel se suelen crear mediante el anclaje de objetos visuales de uno o más informes, Preguntas y respuestas o Conclusiones rápidas.

> [!TIP]
> Dado que los paneles son un tipo de contenido de Power BI, no use la palabra _panel_ en el nombre del informe o panel.

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>Enfoque en la imagen general al volver a crear objetos visuales

Todas las herramientas de BI tienen sus puntos fuertes y sus áreas de enfoque. Por esta razón, es posible que los objetos visuales de informe exactos de los que dependía en una plataforma de BI heredada no tengan un equivalente próximo en Power BI.

Al volver a crear objetos visuales de informe, céntrese más en las preguntas de negocio generales que el informe va a abordar. Eso elimina la presión de replicar el diseño de cada objeto visual exactamente de la misma forma. A pesar de que los consumidores de contenido aprecian la coherencia a la hora de usar informes migrados, es importante no enredarse en interminables debates sobre pequeños detalles.

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie de migración de Power BI](powerbi-migration-create-validate-content.md) se proporciona información sobre la fase 4, que se refiere a la creación y validación de contenido al migrar a Power BI.

Otros recursos útiles incluyen:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
