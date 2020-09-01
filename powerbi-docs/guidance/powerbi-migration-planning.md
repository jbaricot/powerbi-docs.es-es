---
title: Planeamiento de la implementación para migrar a Power BI
description: Guía sobre el planeamiento de la implementación al migrar a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 590e28c727cab88b008d7a05e7df22244e8dabf0
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803369"
---
# <a name="plandeploymenttomigratetopowerbi"></a>Planeamiento de la implementación para migrar a Power BI

En este artículo se explica la **fase 2**, que se refiere a la planeación de la migración de una única solución de Power BI.

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="Imagen que muestra las fases de una migración de Power BI. En este artículo se resalta la fase 2.":::

> [!NOTE]
> Para obtener una explicación completa del gráfico anterior, vea [Información general sobre la migración de Power BI](powerbi-migration-overview.md).

La fase 2 se centra en definir cómo se usan los requisitos establecidos en la fase 1 para migrar una solución a Power BI.

El resultado de la fase 2 incluye tantas decisiones específicas como sea posible para guiar el proceso de implementación.

La toma de decisiones de esta naturaleza es un proceso iterativo y no lineal. En los [pasos previos a la migración](powerbi-migration-pre-migration-steps.md) ya se ha realizado algún planeamiento. Pueden extraerse lecciones de una prueba de concepto (que se describe en la [fase 3](powerbi-migration-proof-of-concept.md)) en paralelo al planeamiento de la implementación. Incluso durante la creación de la solución (que se describe en la [fase 4](powerbi-migration-create-validate-content.md)) puede que surja información adicional que influya en las decisiones de implementación.

> [!IMPORTANT]
> Las fases 1-5 representan actividades relacionadas con una solución concreta. Hay decisiones y actividades en el nivel de organización o inquilino que afectan al proceso en el nivel de solución. Algunas de esas actividades de planeación de nivel superior se tratan en el artículo [Información general sobre la migración de Power BI](powerbi-migration-overview.md). Cuando proceda, dé preferencia a las decisiones de nivel de organización por eficacia y coherencia.

> [!TIP]
> Los temas que se tratan en este artículo también se aplican a un proyecto de implementación estándar de Power BI.

## <a name="choose-power-bi-product"></a>Selección del producto Power BI

Una de las primeras decisiones es elegir el producto Power BI. Se trata de una decisión entre el [servicio Power BI](../fundamentals/power-bi-service-overview.md) o [Power BI Report Server](../report-server/get-started.md). Una vez publicado el contenido, hay muchas opciones adicionales disponibles, como la inserción, la entrega a dispositivos móviles y las suscripciones de correo electrónico.

Para obtener más información sobre las consideraciones de la arquitectura, vea la **sección 3** de las [Notas del producto sobre la implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP).

> [!CAUTION]
> Si le tienta usar archivos de Power BI Desktop almacenados en un sistema de archivos, sea consciente de que no es un enfoque óptimo. El uso del servicio Power BI (o Power BI Report Server) tiene importantes ventajas para la seguridad, la distribución de contenido y la colaboración. El servicio Power BI también permite auditar y supervisar actividades.

## <a name="decide-on-workspace-management-approach"></a>Decisión sobre el enfoque de administración de áreas de trabajo

Las [áreas de trabajo](../collaborate-share/service-new-workspaces.md) son un concepto fundamental del servicio Power BI, con lo que la administración de áreas de trabajo es un importante aspecto de la planeación. Las preguntas que se deben formular incluyen las siguientes:

- ¿Es necesaria una nueva área de trabajo para esta solución nueva?
- ¿Se van a necesitar áreas de trabajo independientes para desarrollo, pruebas y producción?
- ¿Se van a usar áreas de trabajo independientes para los datos y los informes, o basta con una sola área de trabajo? Las áreas de trabajo independientes tienen numerosas ventajas, especialmente para la protección de los conjuntos de datos. En caso necesario se pueden administrar de forma independiente de los usuarios que publican informes.
- ¿Cuáles son los requisitos de seguridad del área de trabajo? Esto influye en la planeación de [roles del área de trabajo](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). Si son consumidores de contenido los que van a usar una aplicación, los [permisos de la aplicación](../collaborate-share/service-create-distribute-apps.md#publish-your-app) se administran de forma independiente del área de trabajo. Los distintos permisos para los visores de la aplicación proporcionan flexibilidad adicional a la hora de cumplir los requisitos de seguridad de los consumidores de solo lectura de informes o paneles.
- ¿Se pueden usar grupos existentes para proteger el nuevo contenido? Se admiten grupos de Azure Active Directory y Microsoft 365. Si está en consonancia con los procesos existentes, el uso de grupos facilita la administración de permisos más que las asignaciones a usuarios individuales.
- ¿Hay alguna consideración de seguridad relacionada con los usuarios invitados externos? Es posible que tenga que trabajar con el administrador de Azure Active Directory y el administrador de Power BI para configurar el [acceso de usuarios invitados](../admin/service-admin-azure-ad-b2b.md).

> [!TIP]
> Le recomendamos que cree un área de trabajo para una actividad o un proyecto de empresarial específicos. Es posible que se sienta tentado a empezar a estructurar áreas de trabajo en función de la estructura de la organización (como un área de trabajo por departamento), pero este enfoque suele acabar siendo demasiado amplio.

## <a name="determine-how-content-will-be-consumed"></a>Determinación de cómo se va a usar el contenido

Resulta útil entender cómo prefieren ver los informes y paneles los consumidores de una solución. Las preguntas que se deben formular incluyen las siguientes:

- ¿Es una [aplicación de Power BI](../consumer/end-user-apps.md) (que incluye informes y paneles de una sola área de trabajo) la mejor manera de entregar contenido a los consumidores o basta el acceso directo a un área de trabajo para los visores de contenido?
- ¿Se van a incrustar determinados informes y paneles en otra ubicación, como [Teams](../collaborate-share/service-embed-report-microsoft-teams.md), [SharePoint Online](../collaborate-share/service-embed-report-spo.md) o un [portal o sitio web seguro](../collaborate-share/service-embed-secure.md)?
- ¿Los consumidores van a acceder al contenido mediante [dispositivos móviles](../consumer/mobile/mobile-apps-for-mobile-devices.md)? Los requisitos para la entrega de informes en dispositivos de pequeño formato influyen en algunas [decisiones de diseño de informes](../create-reports/desktop-create-phone-report.md).

## <a name="decide-if-other-content-may-be-created"></a>Decisión de si se puede crear otro contenido

Hay varias decisiones clave que se deben tomar en relación con la posibilidad de que los consumidores creen contenido nuevo, como:

- ¿Se va a permitir a los consumidores crear informes nuevos a partir del conjunto de datos publicado? Esta capacidad se puede habilitar mediante la asignación del [permiso de compilación](../connect-data/service-datasets-build-permissions.md) para el conjunto de datos a un usuario.
- Si los consumidores quieren personalizar un informe, ¿pueden [guardar una copia](../connect-data/service-datasets-copy-reports.md) y personalizarla de acuerdo a sus necesidades?

> [!CAUTION]
> Aunque la capacidad _Guardar una copia_ es una característica cómoda, se debe usar con precaución si el informe incluye determinados gráficos o mensajes de encabezado y pie de página. Dado que los logotipos, los iconos y los mensajes textuales suelen estar relacionados con los requisitos de personalización de marca o el cumplimiento normativo, es importante controlar cuidadosamente cómo se entregan y distribuyen. Si se usa _Guardar una copia_, pero el nuevo autor no modifica los gráficos ni los mensajes de encabezado y pie de página originales, puede producirse confusión en torno a quién ha elaborado el informe en realidad. También se puede reducir el sentido de la personalización de marca.

## <a name="evaluate-needs-for-premium-capacity"></a>Evaluación de las necesidades de capacidad Premium

Hay capacidades adicionales disponibles cuando se almacena un área de trabajo en una [capacidad Premium](../admin/service-premium-what-is.md). Estas son varias razones por las que las áreas de trabajo de la capacidad Premium pueden ser ventajosas:

- Los consumidores sin una licencia de Power BI Pro pueden acceder al contenido.
- Compatibilidad con conjuntos de datos de gran tamaño.
- Compatibilidad con actualizaciones de datos más frecuentes.
- Compatibilidad con el uso del conjunto completo de características de flujos de datos.
- Características empresariales, lo que incluye canalizaciones de implementación y el punto de conexión XMLA.
- Compatibilidad con informes paginados (cuando la carga de trabajo está habilitada).

## <a name="determine-data-acquisition-method"></a>Determinación del método de adquisición de datos

Los datos que se necesitan en un informe pueden influir en varias decisiones. Las preguntas que se deben formular incluyen las siguientes:

- ¿Se puede usar un [conjunto de datos compartido](../connect-data/service-datasets-share.md) existente de Power BI o es apropiado crear un nuevo conjunto de datos de Power BI para esta solución?
- ¿Es necesario ampliar un conjunto de datos compartido existente con datos o medidas nuevos a fin de satisfacer necesidades adicionales?
- ¿Qué [modo de almacenamiento de datos](../transform-model/desktop-storage-mode.md) es el más adecuado? Las opciones incluyen el modo de importación, DirectQuery, compuesto o de conexión dinámica.
- ¿Deben usarse [agregaciones](../transform-model/desktop-aggregations.md) para mejorar el rendimiento de las consultas?
- ¿Va a resultar útil crear un [flujo de datos](../transform-model/service-dataflows-overview.md) y puede servir como origen de varios conjuntos de datos?
- ¿Se debe registrar un nuevo [origen de datos de puerta de enlace](../connect-data/service-gateway-data-sources.md)?

## <a name="decide-where-original-content-will-be-stored"></a>Decisión de dónde almacenar el contenido original

Además de planear el destino de implementación, también es importante planear dónde se va a almacenar el contenido original (u origen), como:

- Especifique una ubicación aprobada para almacenar los archivos originales de Power BI Desktop (.pbix). Lo ideal es que esta ubicación solo esté disponible para los usuarios que editan el contenido. Debe ser conforme con la configuración de la seguridad en el servicio Power BI.
- Use una ubicación para los archivos originales de Power BI Desktop que incluya historial de versiones o control de código fuente. El control de versiones permite que el autor del contenido revierta a una versión anterior del archivo, si fuera necesario. OneDrive para la Empresa o SharePoint sirven bien a este fin.
- Especifique una ubicación aprobada para almacenar datos de origen no centralizados, como archivos planos o archivos de Excel. Debe ser una ruta de acceso que cualquiera de los autores de conjuntos de datos pueda alcanzar sin errores y de la que se realice una copia de seguridad con regularidad.
- Especifique una ubicación aprobada para el contenido exportado desde el servicio Power BI. El objetivo es garantizar que la seguridad definida en el servicio Power BI no se eluda accidentalmente.

> [!IMPORTANT]
> La especificación de una ubicación protegida para los archivos originales de Power BI Desktop es especialmente importante si contienen datos importados.

## <a name="assess-the-level-of-effort"></a>Evaluación del nivel de esfuerzo

Una vez que hay suficiente información disponible de los requisitos (que se han descrito en la [fase 1](powerbi-migration-requirements.md)) y el proceso de planeación de la implementación de la solución, es posible evaluar el nivel de esfuerzo. Entonces es posible formular un plan de proyecto con tareas, escala de tiempo y responsabilidad.

> [!TIP]
> Los costos de mano de obra (salarios y tarifas) suelen estar entre los mayores gastos de la mayoría de las organizaciones. Aunque puede ser difícil de estimar con precisión, las mejoras de productividad tienen una excelente rentabilidad de la inversión (ROI).

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie de migración de Power BI](powerbi-migration-proof-of-concept.md) se ofrece información sobre la fase 3, que está relacionada con la elaboración de una prueba de concepto para mitigar el riesgo y abordar los factores desconocidos cuanto antes al migrar a Power BI.

Otros recursos útiles incluyen:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
