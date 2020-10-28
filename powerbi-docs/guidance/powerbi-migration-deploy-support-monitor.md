---
title: Implementación en Power BI
description: Instrucciones para implementar, admitir y supervisar el contenido al realizar la migración a Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: f9268409977b3aa78e1ebda6f1f6b2e732451455
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681031"
---
# <a name="deploy-to-power-bi"></a>Implementación en Power BI

En este artículo se describe la **fase 5** , que se refiere a la implementación, admisión y supervisión de contenido al realizar la migración a Power BI.

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="Imagen que muestra las fases de una migración a Power BI. En este artículo se resalta la fase 5.":::

> [!NOTE]
> Para obtener una explicación completa del gráfico anterior, consulte el artículo de [información general sobre la migración a Power BI](powerbi-migration-overview.md).

El objetivo principal de la fase 5 es implementar la nueva solución de Power BI en producción.

La salida de esta fase es una solución de producción lista para su uso en la empresa. Cuando se trabaja con un método ágil, conviene tener algunas mejoras planeadas, que se entregarán en una futura iteración. El soporte técnico y la supervisión también son importantes en esta fase y de forma continua.

> [!TIP]
> A excepción de la ejecución en paralelo y la retirada de los informes heredados, que se describen a continuación, los temas que se tratan en este artículo se aplican también a un proyecto de implementación estándar de Power BI.

## <a name="deploy-to-test-environment"></a>Implementación en un entorno de prueba

En el caso de las soluciones administradas por TI o las que son críticas para la productividad empresarial, generalmente hay un entorno de prueba. Un entorno de prueba se encuentra entre el desarrollo y la producción, y no es necesario para todas las soluciones Power BI. Un área de trabajo de prueba puede servir como ubicación estable, separada del desarrollo, para que las pruebas de aceptación de usuario (UAT) se efectúen antes de la versión para producción.

Si el contenido se ha publicado en un área de trabajo de capacidad Premium, las [canalizaciones de implementación](../create-reports/deployment-pipelines-overview.md) pueden simplificar el proceso de implementación en áreas de trabajo de desarrollo, prueba y producción. Como alternativa, la publicación puede realizarse manualmente o con [scripts de PowerShell](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/).

### <a name="deploy-to-test-workspace"></a>Implementación en el área de trabajo de prueba

Las actividades clave durante una implementación en el área de trabajo de prueba suelen incluir lo siguiente:

- **Cadenas de conexión y parámetros** : ajuste las cadenas de conexión del conjunto de datos si el origen de datos difiere entre el entorno de desarrollo y de prueba. Se puede utilizar la [parametrización](../connect-data/service-parameters.md) para administrar de forma eficaz las cadenas de conexión.
- **Contenido del área de trabajo** : publique conjuntos de datos e informes en el área de trabajo de prueba, y cree paneles.
- **Aplicación** : publique una [aplicación](../consumer/end-user-apps.md) mediante el contenido del área de trabajo de prueba, si forma parte del proceso de UAT. Normalmente, los permisos de aplicación se restringen a un número pequeño de personas implicadas en el proceso de UAT.
- **Actualización de datos** : [programe la actualización de los conjuntos de datos](../connect-data/refresh-scheduled-refresh.md) de importación durante el período en el que el proceso de UAT se lleva a cabo de forma activa.
- **Seguridad** : actualice o compruebe los [roles del área de trabajo](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces). El acceso a las áreas de trabajo de prueba incluye un número reducido de personas que participan en las pruebas de aceptación de usuario.

> [!NOTE]
> Para más información sobre las opciones de implementación en desarrollo, prueba y producción, consulte la sección 9 del documento [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP).

### <a name="conduct-user-acceptance-testing"></a>Realización de pruebas de aceptación de usuario

Por lo general, el proceso de UAT implica a usuarios empresariales expertos en la materia. Una vez comprobado, dan su aprobación con respecto a que el nuevo contenido es preciso, cumple los requisitos y es posible su implementación para un consumo más amplio por parte de otros usuarios.

El grado de formalidad de este proceso de UAT, incluidas las aprobaciones por escrito, dependerá de sus prácticas de administración de cambios.

## <a name="deploy-to-production-environment"></a>Implementación en el entorno de producción

Hay varias consideraciones sobre su implementación en el entorno de producción que hay que tener en cuenta.

### <a name="conduct-a-staged-deployment"></a>Realización de una implementación por fases

Si está tratando de minimizar el riesgo y la interrupción del usuario, o si hay otros problemas, puede optar por realizar una implementación por fases. Es posible que la primera implementación en producción implique un grupo más pequeño de usuarios piloto. Con una prueba piloto, se pueden solicitar comentarios a los usuarios piloto de forma activa.

Expanda los permisos en el área de trabajo de producción, o la aplicación, gradualmente hasta que todos los usuarios de destino tengan permiso para la nueva solución de Power BI.

> [!TIP]
> Use el [registro de actividad de Power BI](../admin/service-admin-auditing.md) para comprender cómo los consumidores adoptan y usan la nueva solución de Power BI.

### <a name="handle-additional-components"></a>Control de componentes adicionales

Durante el proceso de implementación, puede que tenga que trabajar con los administradores de Power BI a fin de abordar otros requisitos necesarios para admitir toda la solución, por ejemplo:

- **Mantenimiento de la puerta de enlace** : puede que se necesite el registro de [nuevos orígenes de datos](../connect-data/service-gateway-data-sources.md) en la puerta de enlace de datos.
- **Conectores y controladores de puerta de enlace** : es posible que un nuevo origen de datos de propiedad requiera la instalación de un nuevo controlador o un conector personalizado en cada servidor del clúster de puerta de enlace.
- **Creación de una capacidad Premium** : tal vez pueda usar una [capacidad Premium](../admin/service-premium-capacity-manage.md) existente. También puede haber situaciones en las que esté justificado usar una nueva capacidad Premium. Podría ser el caso cuando quiera separar deliberadamente una carga de trabajo de departamento.
- **Configuración de un flujo de datos de Power BI** : las actividades de preparación de datos se pueden configurar de una vez en un [flujo de datos de Power BI](../transform-model/service-dataflows-overview.md) mediante Power Query Online. Eso evita tener que replicar el trabajo de preparación de datos en muchos archivos distintos de Power BI Desktop.
- **Registro de un nuevo objeto visual de la organización** : el registro de [objetos visuales de la organización](../developer/visuals/power-bi-custom-visuals-organization.md) se puede realizar en el portal de administración en el caso de objetos visuales personalizados que no se originaron en AppSource.
- **Establecimiento de contenido destacado** : existe una opción de inquilino que controla quién puede [presentar contenido](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/) en la página principal del servicio Power BI.
- **Establecimiento de etiquetas de confidencialidad** : todas las [etiquetas de confidencialidad](../admin/service-security-data-protection-overview.md) se integran con Microsoft Information Protection.

### <a name="deploy-to-production-workspace"></a>Implementación en el área de trabajo de producción

Las actividades clave durante una implementación en el área de trabajo de producción suelen incluir lo siguiente:

- **Administración de cambios** : de ser necesario, obtenga la aprobación correspondiente para realizar la implementación; asimismo, comunique dicha implementación a la población de usuarios mediante sus prácticas estándar de administración de cambios. Puede que haya una ventana de administración de cambios aprobada durante la cual se permitan las implementaciones de producción. Normalmente, se aplica al contenido administrado por TI y, con mucha menos frecuencia, al contenido de autoservicio.
- **Plan de reversión** : en el caso de una migración, la expectativa es que se trate de la migración de una nueva solución por primera vez. Si ya existe contenido, conviene tener un plan para efectuar una reversión a la versión anterior, en caso necesario. Tener versiones anteriores de los archivos de Power BI Desktop (con el control de versiones de SharePoint o OneDrive) funciona bien a tal efecto.
- **Cadenas de conexión y parámetros** : ajuste las cadenas de conexión del conjunto de datos si el origen de datos difiere entre el entorno de prueba y de producción. Se puede usar la [parametrización](../connect-data/service-parameters.md) eficazmente a tal efecto.
- **Actualización de datos** : [programe la actualización del conjunto de datos](../connect-data/refresh-scheduled-refresh.md) para los valores importados.
- **Contenido del área de trabajo** : publique conjuntos de datos e informes en el área de trabajo de producción, y cree paneles. Las [canalizaciones de implementación](../create-reports/deployment-pipelines-overview.md) pueden simplificar el proceso de implementación en áreas de trabajo de desarrollo, prueba y producción si el contenido se ha publicado en áreas de trabajo de capacidad Premium.
- **Aplicación** : si las aplicaciones forman parte de la estrategia de distribución de contenido, publique una [aplicación](../consumer/end-user-apps.md) mediante el contenido del área de trabajo de producción.
- **Seguridad** : actualice y compruebe los [roles de área de trabajo](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) en función de su estrategia de distribución de contenido y colaboración.
- **Configuración del conjunto de datos** : actualice y compruebe la configuración de cada conjunto de datos, incluido lo siguiente:
  - [Aprobación](../collaborate-share/service-endorse-content.md) (por ejemplo, de certificados o promocionados)
  - Credenciales del origen de datos o la conexión de puerta de enlace
  - Actualización programada
  - [Preguntas y respuestas destacadas](../create-reports/service-q-and-a-create-featured-questions.md)
- **Uso compartido de paneles e informes** : actualice y compruebe la configuración de cada informe y panel. Entre los valores más importantes se incluyen los siguientes:
  - Descripción
  - Persona o grupo de contacto
  - [Etiqueta de confidencialidad](../admin/service-security-apply-data-sensitivity-labels.md)
  - [Contenido destacado](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **Suscripciones** : configure suscripciones de informe, si es necesario.

> [!IMPORTANT]
> Llegados a este punto, ha alcanzado un gran hito. Celebre su logro al completar la migración.

### <a name="communicate-with-users"></a>Comunicación con los usuarios

Anuncie la nueva solución a los consumidores. Indíqueles dónde pueden encontrar el contenido, así como documentación asociada, preguntas más frecuentes y tutoriales. Para presentar el nuevo contenido, considere la posibilidad de hospedar una sesión de tipo almuerzo y aprendizaje, o preparar algunos vídeos a petición.

Asegúrese de incluir instrucciones sobre cómo solicitar ayuda y cómo proporcionar comentarios.

### <a name="conduct-a-retrospective"></a>Realización de una retrospectiva

Valore la posibilidad de realizar una retrospectiva para examinar lo que ha ido bien en la migración y lo que se puede hacer mejor en la próxima.

## <a name="run-in-parallel"></a>Ejecución en paralelo

En muchas situaciones, la nueva solución se ejecutará en paralelo con la heredada durante un tiempo predeterminado. Entre las ventajas de la ejecución en paralelo se incluyen las siguientes:

- Reducción del riesgo, especialmente si los informes se consideran críticos.
- Deja tiempo para que los usuarios se acostumbren a la nueva solución de Power BI.
- Permite que la información presentada en Power BI haga referencias cruzadas a los informes heredados.

## <a name="decommission-the-legacy-report"></a>Retirada del informe heredado

En algún momento, los informes migrados a Power BI han de deshabilitarse en la plataforma de BI heredada. La retirada de los informes heredados puede producirse cuando:

- El tiempo predeterminado para ejecutarse en paralelo (que debería haberse comunicado a la población de usuarios) ha expirado. Normalmente es de entre 30 y 90 días.
- Todos los usuarios del sistema heredado tienen acceso a la nueva solución de Power BI.
- Ya no se produce una actividad importante en el informe heredado.
- No se ha producido ningún problema con la nueva solución de Power BI que podría afectar a la productividad de los usuarios.

## <a name="monitor-the-solution"></a>Supervisión de la solución

Los eventos del [registro de actividad de Power Bi](../admin/service-admin-auditing.md) se pueden utilizar para comprender los patrones de uso de la nueva solución (o del [registro de ejecución](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view) en el caso de contenido implementado en Power BI Report Server). El análisis del registro de actividad puede ayudar a determinar si el uso real difiere de las expectativas. También puede validar que la solución se admite adecuadamente.

Estas son algunas preguntas que pueden responderse revisando el registro de actividad:

- ¿Con qué frecuencia se ve el contenido?
- ¿Quién ve el contenido?
- ¿El contenido se ve normalmente a través de una aplicación o un área de trabajo?
- ¿La mayoría de los usuarios usan un explorador o una aplicación móvil?
- ¿Se usan suscripciones?
- ¿Se crean informes basados en esta solución?
- ¿Se actualiza con frecuencia el contenido?
- ¿Cómo se define la seguridad?
- ¿Se producen habitualmente problemas tales como errores de actualización de datos?
- ¿Se producen actividades preocupantes (por ejemplo, una importante actividad de exportación o numerosas participaciones en informes individuales) que pudieran justificar el aprendizaje adicional?

> [!IMPORTANT]
> Asegúrese de que alguien revise periódicamente el registro de actividad. La simple captura y almacenamiento del historial tiene valor a efectos de auditoría o cumplimiento. Sin embargo, el verdadero valor se produce cuando se puede realizar una acción proactiva.

## <a name="support-the-solution"></a>Soporte técnico de la solución

Aunque la migración se haya completado, el período posterior a la migración resulta fundamental para solucionar problemas y controlar las cuestiones de rendimiento. Con el tiempo, es probable que la solución migrada sufra cambios a medida que evolucionen las necesidades empresariales.

El soporte técnico tiende a prestarse de forma ligeramente diferente en función de cómo se administre BI con características de autoservicio en toda la organización. Los expertos en Power BI de todas las unidades de negocio suelen actuar como soporte técnico de primera línea. Aunque se trata de un rol informal, es algo fundamental que se debe fomentar.

Contar con un proceso de soporte técnico formal, con personal de TI capaz de atender incidencias de soporte técnico, también resulta esencial para controlar las solicitudes rutinarias orientadas al sistema y con fines de escalamiento.

También se puede tener un [Centro de excelencia (COE)](center-of-excellence-establish.md) que actúe como grupo de asesores internos que prestan asistencia e imparten cursos sobre Power BI y determinan su uso en la organización. Un COE puede ser responsable de mantener contenido útil sobre Power BI en un portal interno.

Por último, debe quedar claro a los consumidores del contenido con quién deben ponerse en contacto en caso de tener dudas al respecto, así como disponer de un mecanismo para proporcionar comentarios sobre problemas o mejoras.

## <a name="next-steps"></a>Pasos siguientes

En el [artículo final de esta serie](powerbi-migration-learn-from-customers.md) podrá aprender de los clientes cuándo realizar la migración a Power BI.

Otros recursos útiles incluyen los siguientes:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
