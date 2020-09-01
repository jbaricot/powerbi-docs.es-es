---
title: Creación de contenido para la migración a Power BI
description: Instrucciones para crear y validar contenido al realizar la migración a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a12a320b061967e9201e3513e504277a9df586b4
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803510"
---
# <a name="createcontenttomigratetopowerbi"></a>Creación de contenido para la migración a Power BI

En este artículo se describe la **fase 4**, que se refiere a la creación y validación de contenido al realizar la migración a Power BI.

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="Imagen que muestra las fases de una migración a Power BI. En este artículo se resalta la fase 4.":::

> [!NOTE]
> Para obtener una explicación completa del gráfico anterior, consulte el artículo de [información general sobre la migración a Power BI](powerbi-migration-overview.md).

La fase 4 se centra en realizar el trabajo real para convertir la prueba de concepto (POC) en una solución lista para producción.

La salida de esta fase es una solución de Power BI que se ha validado en un área de trabajo de desarrollo y está lista para su implementación en producción.

> [!TIP]
> La mayoría de los temas que se tratan en este artículo también se aplican a un proyecto de implementación estándar de Power BI.

## <a name="create-the-production-solution"></a>Creación de la solución de producción

En este momento, la misma persona que realizó la POC puede llevar a cabo la generación de la solución de Power BI lista para producción. También es posible que otro usuario esté implicado. Si las escalas de tiempo no se ven comprometidas, es genial que los usuarios que se vayan a encargar del desarrollo de Power BI en el futuro estén involucrados. De este modo, pueden aprender activamente.

> [!IMPORTANT]
> Reutilice la mayor parte del trabajo de la POC que sea posible.

### <a name="develop-new-import-dataset"></a>Desarrollo de un nuevo conjunto de datos de importación

Puede optar por crear un nuevo conjunto de datos de importación cuando ya no haya uno de Power BI existente que satisfaga sus necesidades, o si este no puede mejorarse para ajustarse a estas necesidades.

Idealmente, desde el principio, considere la posibilidad de desacoplar el trabajo de desarrollo para los datos y los informes. [Desacoplar los datos y los informes](report-separate-from-model.md) facilitará la separación del trabajo y los permisos cuando los responsables del modelado de datos y los informes sean personas distintas. Permite un enfoque más escalable y fomenta la reusabilidad de los datos.

Las actividades esenciales relacionadas con el desarrollo de un conjunto de datos de importación incluyen lo siguiente:

- [Adquirir datos](../connect-data/desktop-quickstart-connect-to-data.md) de uno o más orígenes de datos (que pueden ser un flujo de datos de Power BI).
- [Dar forma a los datos, así como combinarlos y prepararlos](../connect-data/desktop-shape-and-combine-data.md).
- Crear el [modelo de conjunto de datos](../transform-model/desktop-modeling-view.md), incluidas las [tablas de fechas](../transform-model/desktop-date-tables.md).
- Crear y comprobar [relaciones de modelo](../transform-model/desktop-create-and-manage-relationships.md).
- [Definir medidas](../transform-model/desktop-measures.md).
- Configurar [seguridad de nivel de fila](../admin/service-admin-rls.md), en caso necesario.
- Configurar sinónimos y [optimizar las Preguntas y respuestas](../natural-language/q-and-a-best-practices.md).
- Planear la escalabilidad, el rendimiento y la simultaneidad, lo que puede influir en sus decisiones sobre los modos de almacenamiento de datos, como el uso de una [modelo compuesto](../transform-model/desktop-composite-models.md) o [agregaciones](../transform-model/desktop-aggregations.md).

> [!TIP]
> Si dispone de varios entornos de desarrollo, pruebas y producción, considere la posibilidad de [parametrizar](/power-query/power-query-query-parameters) orígenes de datos. Esto hará que la implementación, que se describe en la [fase 5](powerbi-migration-deploy-support-monitor.md), sea mucho más fácil.

### <a name="develop-new-reports-and-dashboards"></a>Desarrollo de informes y paneles nuevos

Las actividades esenciales relacionadas con el desarrollo de un informe o panel de Power BI incluyen lo siguiente:

- Decidir el uso de una conexión dinámica a un modelo de datos existente o crear un modelo de datos nuevo.
- Al crear un modelo de datos nuevo, decida el [modo de almacenamiento de datos](../transform-model/desktop-storage-mode.md) para las tablas del modelo (Importación, DirectQuery o Compuesto).
- Decidir cuál es la mejor herramienta de visualización de datos para cumplir los requisitos: Power BI Desktop, el generador de informes paginados o Excel.
- Decidir los [mejores objetos visuales](../consumer/end-user-visual-type.md) para indicarle al informe la historia que debe contar y resolver las preguntas que el informe debe responder.
- Garantizar que todos los objetos visuales presenten una terminología clara, concisa y empresarial.
- Abordar los requisitos de interactividad.
- Al usar la conexión dinámica, agregar [medidas de nivel de informe](../transform-model/desktop-tutorial-create-measures.md).
- Crear un [panel](../create-reports/service-dashboards.md) en el servicio Power BI, especialmente cuando los consumidores quieran una forma sencilla de supervisar las métricas clave.

> [!NOTE]
> Muchas de estas decisiones se habrán realizado en fases anteriores de planeación o en el POC técnico.

## <a name="validate-the-solution"></a>Validación de la solución

Hay cuatro aspectos principales en la validación de una solución de Power BI:

1. Precisión de los datos
2. Seguridad
3. Funcionalidad
4. Rendimiento

### <a name="validate-data-accuracy"></a>Validación de la precisión de los datos

Como esfuerzo único durante la migración, deberá asegurarse de que los datos del informe nuevo coinciden con los que se muestran en el informe heredado. O bien, si hay diferencias, ser capaz de explicar el por qué. Encontrar un error en la solución heredada que queda resuelto en la solución nueva es más común de lo que podría pensar.

Como parte de los esfuerzos continuos de validación de datos, el informe nuevo normalmente tendrá que comprobarse de forma cruzada con el sistema de origen inicial. Idealmente, esta validación se produce de forma reiterativa cada vez que se publica un cambio en un informe.

### <a name="validate-security"></a>Validación de seguridad

Al validar la seguridad, hay dos aspectos principales que hay que tener en cuenta:

- Permisos de datos
- Acceso a conjuntos de datos, informes y paneles

En un conjunto de datos de importación, los permisos de datos se aplican mediante la definición de [seguridad de nivel de fila](../admin/service-admin-rls.md) (RLS). También es posible que el sistema de origen aplique permisos de datos al usar el modo de almacenamiento DirectQuery (posiblemente con [inicio de sesión único](../connect-data/service-gateway-sso-overview.md)).

Las principales formas de conceder acceso al contenido de Power BI son las siguientes:

- [Roles de área de trabajo](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (para editores y visores de contenido).
- [Permisos de aplicación](../collaborate-share/service-create-distribute-apps.md#publish-your-app) aplicados a un conjunto empaquetado de contenido del área de trabajo (para visores).
- [Compartir](../collaborate-share/service-share-dashboards.md) un informe o panel individual (para visores).

> [!TIP]
> Se recomienda entrenar a los autores de contenido en cómo administrar la seguridad de forma eficaz. También es importante tener una prueba, auditoría y supervisión sólidas.

### <a name="validate-functionality"></a>Validación de la funcionalidad

Es el momento de comprobar de nuevo los detalles del conjunto de datos, como los nombres de campo, el formato, la ordenación y el comportamiento de resumen predeterminado. Las características interactivas de los informes, como los [segmentaciones](../visuals/power-bi-visualization-slicers.md), la [exploración en profundidad](../consumer/end-user-drill.md), la [obtención de detalles](../create-reports/desktop-drillthrough.md), las [expresiones](../create-reports/desktop-conditional-format-visual-titles.md), los [botones](../create-reports/desktop-buttons.md) o los [marcadores](../create-reports/desktop-bookmarks.md), también se deben comprobar.

Durante el proceso de desarrollo, la solución de Power BI debe publicarse en un área de trabajo de desarrollo en el servicio Power BI de forma periódica. Compruebe que toda la funcionalidad actúa según lo previsto en el servicio, como la representación de objetos visuales personalizados. También es un buen momento para realizar más pruebas. Pruebe la [actualización programada](../connect-data/refresh-scheduled-refresh.md), [Preguntas y respuestas](../consumer/end-user-q-and-a.md) y cómo los informes y paneles se ven en un [dispositivo móvil](../consumer/mobile/mobile-apps-for-mobile-devices.md).

### <a name="validate-performance"></a>Validación del rendimiento

El rendimiento de la solución Power BI es un elemento importante para la experiencia del consumidor. La mayoría de los informes deben presentar objetos visuales en menos de diez segundos. Si tiene informes que tardan más tiempo en cargarse, páuselos y reconsidere qué puede estar contribuyendo a estos retrasos. El rendimiento de los informes debe evaluarse con regularidad en el servicio Power BI, además de en Power BI Desktop.

Muchos de los problemas de rendimiento surgen del subestándar [DAX (expresiones de análisis de datos)](../transform-model/desktop-quickstart-learn-dax-basics.md), de un diseño deficiente del conjunto de datos o de un diseño de informe poco óptimo (por ejemplo, intentar representar demasiados objetos visuales en una sola página). Las incidencias del entorno técnico, como la red, una puerta de enlace de datos sobrecargada o la forma de configurar una capacidad Premium, también pueden contribuir a generar incidencias de rendimiento. Para obtener más información, vea la [Guía de optimización para Power BI](power-bi-optimization.md) y [Solución de problemas de rendimiento de los informes en Power BI](report-performance-troubleshoot.md).

## <a name="document-the-solution"></a>Documentación de la solución

Hay dos tipos principales de documentación que son útiles para una solución Power BI:

- Documentación del conjunto de datos
- Documentación del informe

La documentación se puede almacenar en cualquier lugar donde el público de destino tenga un acceso más sencillo. Entre las opciones comunes se incluyen las siguientes:

- **En un sitio de SharePoint**: puede existir un sitio de SharePoint para el Centro de excelencia o un sitio de la comunidad interna de Power BI.
- **En una aplicación**: las direcciones URL se pueden configurar al publicar una aplicación de Power BI para dirigir al consumidor a más información.
- **En archivos individuales de Power BI Desktop**: los elementos del modelo, como las tablas y las columnas, pueden definir una descripción. Estas descripciones aparecen como información sobre herramientas en el panel **Campos** al crear informes.

> [!TIP]
> Si crea un sitio con el fin de que sirva como centro para la documentación relacionada con Power BI, valore la posibilidad de [personalizar el menú Obtener ayuda](../admin/service-admin-portal.md#publish-get-help-information) con la ubicación de su URL.

### <a name="create-dataset-documentation"></a>Creación de la documentación del conjunto de datos

La documentación del conjunto de datos está dirigida a los usuarios que van a administrar este conjunto de datos en el futuro. Es útil incluir lo siguiente:

- Decisiones de diseño adoptadas y los motivos.
- Quién posee, mantiene y certifica los conjuntos de datos.
- Requisitos de actualización de datos.
- Reglas de negocios personalizadas definidas en los conjuntos de datos.
- Seguridad específica del conjunto de datos o requisitos de privacidad de los datos.
- Necesidades de mantenimiento futuras.
- Incidencias abiertas conocidas o elementos de trabajo pendiente diferidos.

También puede optar por crear un registro de cambios que resuma los cambios más importantes que se hayan producido en el conjunto de datos a lo largo del tiempo.

### <a name="create-report-documentation"></a>Creación de la documentación del informe

La documentación del informe, que se estructura normalmente como un tutorial dirigido a los consumidores del informe, puede ayudar a los consumidores a obtener más valor de los informes y paneles. A menudo un tutorial de vídeo breve sirve para este propósito.

También puede optar por incluir documentación adicional del informe en una página oculta del mismo. Podría incluir decisiones de diseño y un registro de cambios.

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie de migración de Power BI](powerbi-migration-deploy-support-monitor.md) se proporciona información sobre la fase 5, que se refiere a la implementación, admisión y supervisión de contenido al realizar la migración a Power BI.

Otros recursos útiles incluyen los siguientes:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
