---
title: Preparación para migrar a Power BI
description: Guía sobre los pasos previos a la migración a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: fba37d9f73ea0f61d8a43dc46cd13a5835d4d2a9
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525809"
---
# <a name="prepare-to-migrate-to-power-bi"></a>Preparación para migrar a Power BI

En este artículo se indican las acciones que se pueden considerar antes de migrar a Power BI.

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="Imagen en la que se muestran las fases de una migración de Power BI. En este artículo se enfatizan los pasos previos a la migración.":::

> [!NOTE]
> Para obtener una explicación completa del gráfico anterior, vea [Información general sobre la migración de Power BI](powerbi-migration-overview.md).

En los pasos previos a la migración se hace hincapié en la planeación inicial, que es una preparación importante antes de pasar por las cinco fases de migración. La mayoría de los pasos previos a la migración ocurren una vez, aunque en el caso de las organizaciones de mayor tamaño algunas partes pueden ser iterativas para cada unidad de negocio o departamento.

El resultado de los pasos previos a la migración incluye un modelo de gobernanza inicial, un plan de implementación general inicial, además de un inventario de los informes y los datos que se van a migrar. Se necesita información adicional de las actividades de las fases 1, 2 y 3 para estimar en su totalidad el nivel de esfuerzo necesario para migrar soluciones individuales.

> [!TIP]
> La mayoría de los temas que se tratan en este artículo también se aplican a un proyecto de implementación estándar de Power BI.

## <a name="create-costbenefit-analysis-and-evaluation"></a>Creación de análisis y evaluación de costos y beneficios

Algunas consideraciones fundamentales durante la evaluación inicial incluyen la obtención de lo siguiente:

- Claridad sobre el caso de negocio y la estrategia de BI para alcanzar un estado futuro deseado concreto.
- Claridad sobre qué significa el éxito y sobre cómo medir el progreso y el éxito de la iniciativa de migración.
- Estimaciones de costos y resultados de cálculos de rentabilidad de la inversión (ROI).
- Resultados correctos de varias iniciativas productivas de Power BI de menor ámbito y nivel de complejidad.

## <a name="identify-stakeholders-and-executive-support"></a>Identificación de las partes interesadas y el apoyo directivo

Algunas consideraciones para identificar a las partes interesadas incluyen lo siguiente:

- Garantizar la convergencia con las partes interesadas sobre el caso de negocio y la estrategia de BI.
- Incluir a representantes de todas las unidades de negocio, aunque la migración de su contenido esté prevista para más adelante, a fin de comprender sus motivaciones y preocupaciones.
- Implicar a los expertos de Power BI en una fase temprana.
- Crear, y seguir, un plan de comunicación con las partes interesadas.

> [!TIP]
> Si se teme estar empezando a sobrecargar con información, probablemente esté haciendo lo correcto.

## <a name="generate-initial-governance-model"></a>Creación de un modelo de gobernanza inicial

Algunos puntos clave que se deben abordar al principio de una implementación de Power BI incluyen:

- Objetivos específicos para la adopción de Power BI y dónde encaja en la estrategia general de BI de la organización.
- Cómo se va a controlar el rol Administrador de Power BI, especialmente en organizaciones descentralizadas.
- Directivas relacionadas con la obtención de datos de confianza: uso de orígenes de datos acreditados, solución de problemas de calidad de los datos y uso de definiciones comunes y terminología coherentes.
- Estrategia de seguridad y privacidad de los datos de orígenes de datos, modelos de datos, informes y entrega de contenido a usuarios internos y externos.
- Cómo se van a cumplir los requisitos de cumplimiento, normativos y de auditoría internos y externos.

> [!IMPORTANT]
> El modelo de gobernanza más eficaz intenta equilibrar la capacitación del usuario con el nivel de control necesario. Obtenga más información, lea sobre [Disciplina en el núcleo](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core) y [Flexibilidad en el borde](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge).

## <a name="conduct-initial-deployment-planning"></a>Elaboración de un plan de implementación inicial

El plan de implementación inicial conlleva definir estándares, directivas y preferencias para la implementación de Power BI de la organización.

Observe que la [fase 2](powerbi-migration-planning.md) se refiere al plan de implementación de nivel de solución. Las actividades de la fase 2 deben respetar las decisiones de nivel de organización siempre que sea posible.

Algunos puntos críticos que se deben abordar al principio de una implementación de Power BI incluyen lo siguiente:

- Decisiones de [configuración de inquilinos de Power BI](admin-tenant-settings.md), que se deben documentar.
- Decisiones de [administración de áreas de trabajo](../collaborate-share/service-new-workspaces.md), que se deben documentar.
- Consideraciones y preferencias relacionadas con los datos y los [métodos de distribución de contenido](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md), como aplicaciones, áreas de trabajo, uso compartido, suscripciones e inserción de contenido.
- Preferencias relacionadas con los [modos de conjuntos de datos](../connect-data/service-dataset-modes-understand.md), como el uso del modo de importación, el modo DirectQuery o la combinación de los dos modos en un [modelo compuesto](composite-model-guidance.md).
- [Protección de datos y acceso](../admin/service-admin-power-bi-security.md).
- Trabajo con [conjuntos de datos compartidos](../connect-data/service-datasets-share.md) para la reutilización.
- Aplicación de [certificación de datos](../connect-data/service-datasets-certify.md) para fomentar el uso de datos acreditados y de confianza.
- Uso de diferentes [tipos de informes](../create-reports/index.yml), incluidos informes de Power BI, informes de Excel o informes paginados para diferentes casos de uso o unidades de negocio.
- Enfoques de administración de cambios para administrar artefactos de BI centralizados y artefactos de BI administrados por la empresa.
- Planes de aprendizaje para consumidores, modeladores de datos, autores de informes y administradores.
- Soporte para autores de contenido mediante [plantillas de Power BI Desktop](../create-reports/desktop-templates.md), [objetos visuales personalizados](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/) y estándares de diseño de informes documentados.
- Procedimientos y procesos para administrar los requisitos de los usuarios, como la solicitud de nuevas licencias, la incorporación de nuevos orígenes de datos de puerta de enlace, la obtención de permisos a orígenes de datos de puerta de enlace, la solicitud de nuevas áreas de trabajo, los cambios de permisos de áreas de trabajo y otros requisitos comunes que se pueden detectar de forma periódica.

> [!IMPORTANT]
> El plan de implementación es un proceso iterativo. Las decisiones de implementación se perfeccionan y extienden muchas veces a medida que aumenta la experiencia de la organización con Power BI y que este evoluciona. Las decisiones tomadas a lo largo de este proceso se usan durante el plan de implementación de nivel de solución descrito en la [fase 2](powerbi-migration-planning.md) del proceso de migración.

## <a name="establish-initial-architecture"></a>Establecimiento de la arquitectura inicial

La [arquitectura de la solución de BI](center-of-excellence-business-intelligence-solution-architecture.md) evoluciona y madura con el tiempo. Las tareas de configuración de Power BI que se deben abordar de inmediato incluyen:

- Configuración de inquilinos de Power BI e integración con Azure Active Directory.
- Definición de [administradores de Power BI](../admin/service-admin-role.md).
- Adquisición y asignación de [licencias de usuario](../admin/service-admin-licensing-organization.md) iniciales.
- Configuración y revisión de la [configuración de inquilinos de Power BI](admin-tenant-settings.md).
- Configuración de [roles de áreas de trabajo](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) y asignación de acceso a grupos de seguridad y usuarios de Azure Active Directory.
- Configuración de un clúster de [puerta de enlace de datos](../connect-data/service-gateway-deployment-guidance.md) inicial, con un plan para actualizar con regularidad.
- Adquisición de una [licencia de capacidad Premium](../admin/service-admin-premium-purchase.md) inicial (si procede).
- Configuración de [cargas de trabajo de capacidad Premium](../admin/service-admin-premium-workloads.md), con un plan para administrar de manera continuada.

## <a name="define-success-criteria-for-migration"></a>Definición de criterios de éxito de la migración

La primera tarea es comprender qué se considera éxito de la migración en una solución individual. Estas son algunas de las preguntas que pueden formularse:

- **¿Cuáles son las motivaciones y los objetivos concretos de esta migración?** Para obtener más información, vea [Información general sobre la migración de Power BI (Consideración de los motivos de la migración)](powerbi-migration-overview.md#consider-migration-reasons). En este artículo se indican las razones más habituales para migrar a Power BI. Sin duda, los objetivos deben especificarse en el nivel de organización. Por lo demás, la migración de una solución de BI heredada puede beneficiarse considerablemente de los ahorros de costos, mientras que la migración de otra solución de BI heredada puede centrarse en obtener ventajas de optimización de flujos de trabajo.
- **¿Cuál es la relación costo/beneficio esperada o ROI de esta migración?** El tener un reconocimiento claro de las expectativas relacionadas con el costo, el aumento de capacidades, la menor complejidad o la mayor agilidad resulta útil para medir el éxito. Puede proporcionar principios orientativos para ayudar a tomar decisiones durante el proceso de migración.
- **¿Qué indicadores clave de rendimiento (KPI) se van a usar para medir el éxito?** En la siguiente lista se muestran algunos ejemplos de KPI:
    - Número de informes representados desde la plataforma de BI heredada, que se reduce mes tras mes.
    - Número de informes representados desde Power BI, que aumenta mes tras mes.
    - Número de consumidores de informes de Power BI, que aumenta trimestre tras trimestre.
    - Porcentaje de informes migrados a producción por fecha objetivo.
    - Reducción de costos en el apartado de costos de licencias año tras año.

> [!TIP]
> El [registro de actividad de Power BI](../admin/service-admin-auditing.md) se puede usar como origen para medir el progreso de los KPI.

## <a name="prepare-inventory-of-existing-reports"></a>Preparación del inventario de informes existentes

La preparación de un inventario de los informes existentes en la plataforma de BI heredada es un paso crítico para entender lo que ya existe. El resultado de este paso es un aporte para evaluar el nivel de esfuerzo de migración. Estas son algunas de las actividades relacionadas con la preparación de un inventario:

1. **Inventario de informes:** compile una lista de informes y paneles que sean candidatos para la migración.
2. **Inventario de orígenes de datos:** compile una lista de todos los orígenes de datos a los que acceden los informes existentes. Debe incluir tanto orígenes de datos empresariales como orígenes de datos de departamento y personales. Este proceso puede destapar orígenes de datos desconocidos para el departamento de TI, lo que a menudo se conoce como _TI en la sombra_ .
3. **Registro de auditoría:** obtenga datos del registro de auditoría de la plataforma de BI heredada para comprender los patrones de uso y ayudar a priorizar. La información importante que se debe obtener del registro de auditoría incluye:
    - Número medio de veces que se ha ejecutado cada informe por semana, mes o trimestre.
    - Número medio de consumidores por informe por semana, mes o trimestre.
    - Consumidores de cada informe, especialmente los informes que usan los ejecutivos.
    - Fecha más reciente en que se ha ejecutado cada informe.

> [!NOTE]
> En muchos casos, el contenido no se migra a Power BI tal cual. La migración presenta una oportunidad de rediseñar la arquitectura de datos o de mejorar la entrega de informes. La compilación de un inventario de informes es fundamental para entender lo que existe actualmente a fin de poder empezar a evaluar qué refactorización debe producirse. En el resto de artículos de esta serie se indican las posibles mejoras más detalladamente.

## <a name="explore-automation-options"></a>Estudio de las opciones de automatización

No es posible automatizar completamente un proceso de conversión de Power BI de un extremo a otro.

La compilación del inventario existente de datos e informes es un posible candidato para la automatización si se tiene una herramienta que pueda hacerlo automáticamente. La medida en que se puede usar la automatización en algunas partes del proceso de migración, como la compilación del inventario existente, depende de las herramientas que se tengan.

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie de migración de Power BI](powerbi-migration-requirements.md) se proporciona información sobre la fase 1, que se refiere a la recopilación y la priorización de los requisitos al migrar a Power BI.

Otros recursos útiles incluyen:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
