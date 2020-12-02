---
title: Establecimiento de un centro de excelencia
description: Conozca cómo un centro de excelencia ayudó a Microsoft a crear una plataforma de datos y análisis estandarizada para extraer conclusiones con el modelo operativo adecuado, la interacción con las partes interesadas y las inversiones dedicadas y compartidas.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: 90de33f85c0ede28b14e651414c311e4986a2172
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394575"
---
# <a name="establish-a-center-of-excellence"></a>Establecimiento de un centro de excelencia

Este artículo se dirige a los profesionales y administradores de TI. Aprenderá a configurar un centro de excelencia (COE) de BI y análisis en su organización, así como la forma en que Microsoft ha configurado el suyo.

Para algunos, existe la idea equivocada de que un COE es tan solo un departamento de soporte técnico; sin embargo, este concepto está muy lejos de la realidad.

Por lo general, un COE de BI y análisis es un equipo de profesionales que se encarga de establecer y mantener una plataforma de BI. También se encarga de crear una única fuente de confianza y de definir un conjunto de métricas coherentes de toda la empresa para extraer y acelerar las conclusiones. Sin embargo, un COE es un término amplio. Como tal, se puede implementar y administrar de distintas maneras, y su estructura y ámbito pueden variar de una organización a otra. En esencia, siempre se trata de una plataforma sólida que ofrece las funcionalidades de datos y de información adecuadas a las personas adecuadas en el momento adecuado. Idealmente, también fomenta la promoción, el entrenamiento y el soporte técnico. En Microsoft, se describe como _[disciplina en el núcleo](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ y se entrega como la plataforma de BI y única fuente de confianza.

En organizaciones de mayor tamaño, podría encontrar varios COE donde el COE principal _se amplíe_ con distintos COE satélite, a menudo a nivel de departamento. De este modo, un COE satélite es un grupo de expertos familiarizados con las taxonomías y las definiciones, que saben cómo transformar los datos principales en lo que tiene sentido _para su departamento_. A los analistas de departamento se les conceden permisos a los datos principales y confían en ellos para su uso en sus propios informes. Crean soluciones que se basan en las dimensiones, los hechos y la lógica de negocios principales cuidadosamente preparados. En ocasiones, también podrían ampliarse con conjuntos de datos y lógica de negocios más pequeños y específicos del departamento. Lo importante es que los COE satélite no se desconectan nunca ni actúan aisladamente. En Microsoft, los COE satélite promueven _[flexibilidad en el borde](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ .

Para que este escenario ampliado tenga éxito, los departamentos deben _pagar por reproducir_. En otras palabras, los departamentos deben invertir financieramente en el COE principal. De este modo, no hay que preocuparse de que "no obtengan lo que les corresponde" o de que sus requisitos tengan menos prioridad.

Para admitir este escenario, el COE principal debe escalarse a fin de satisfacer las necesidades de los departamentos financiados. Cuando se hayan incorporado varios conjuntos de datos, se generarán economías de escala. En Microsoft, en seguida se hizo evidente que trabajar de forma centralizada resulta más económico y produce resultados más rápidos. Cada vez que se incorporaba una nueva área temática, experimentábamos economías de escala aún mayores que permitían aprovechar y colaborar en toda la plataforma, lo que reforzaba nuestra referencia cultural de datos subyacente.

Veamos un ejemplo: Nuestra plataforma de BI ofrece dimensiones, hechos y lógica de negocios principales para finanzas, ventas y marketing. También define cientos de indicadores clave de rendimiento (KPI). Ahora, un analista de la empresa en Power Platform debe preparar un panel para la dirección. Algunos de los KPI, como los ingresos y las canalizaciones, proceden directamente de la plataforma de BI. Sin embargo, otros se basan en necesidades más pormenorizadas de la empresa. Una de estas necesidades se refiere a un KPI sobre la adopción del usuario de una característica específica de Power BI: los flujos de datos. Por lo tanto, el analista produce un [modelo compuesto](composite-model-guidance.md) en Power BI para integrar los datos de la plataforma principal de BI con los datos del departamento. Luego agrega lógica de negocios para definir los KPI de su departamento. Por último, crea su panel para la dirección en función del nuevo modelo, que aprovecha los recursos de COE de toda la empresa ampliados con los datos y el conocimiento local.

Lo importante es que una división de responsabilidad entre los COE satélite y el principal permite que los analistas departamentales se centren en abrir nuevos caminos y no en administrar una plataforma de datos. En ocasiones, incluso puede haber una relación mutuamente beneficiosa entre los COE satélite y el COE principal. Por ejemplo, un COE satélite puede definir nuevas métricas que, tras haber demostrado ser beneficiosas para su departamento, terminen siendo métricas principales beneficiosas para toda la empresa, disponibles en el COE principal y respaldadas por él.

## <a name="bi-platform"></a>Plataforma de BI

En su organización, el COE podría ser reconocido por otro nombre, como el equipo o grupo de BI. El nombre importa menos que lo que realmente hace. Si no tiene un equipo formalizado, le recomendamos que forme un equipo que reúna a sus expertos principales en BI para establecer su plataforma de BI.

En Microsoft, el COE se conoce como plataforma de BI. Tiene muchos grupos de partes interesadas que representan distintas divisiones dentro de la empresa, como finanzas, ventas y marketing. Está organizado para ejecutar [funcionalidades compartidas](#shared-capabilities) y [entregas dedicadas](#dedicated-deliveries).

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="En el diagrama se muestran las funcionalidades compartidas y las entregas dedicadas, que se describen en las secciones siguientes.":::

### <a name="shared-capabilities"></a>Funcionalidades compartidas

Se necesitan funcionalidades compartidas para establecer y usar la plataforma de BI. Admiten todos los grupos de partes interesadas que financian la plataforma. Comprenden los siguientes equipos:

- **Ingeniería de la plataforma principal:** Diseñamos la plataforma de BI con una mentalidad de ingeniería. En realidad, es un conjunto de marcos que admite la ingesta de datos, el procesamiento para enriquecer los datos y la entrega de esos datos en modelos semánticos de BI para consumo de los analistas. Los ingenieros son responsables del diseño técnico y la implementación de las funcionalidades de la plataforma principal de BI. Por ejemplo, diseñan e implementan las canalizaciones de datos.
- **Infraestructura y hospedaje:** Los ingenieros de TI se encargan del aprovisionamiento y la administración de todos los servicios de Azure.
- **Soporte técnico y operaciones:** Este equipo mantiene la plataforma en ejecución. El soporte técnico se ocupa de las necesidades del usuario como los permisos de datos. Las operaciones mantienen la plataforma en ejecución, lo que garantiza que se cumplan los contratos de nivel de servicio (SLA) y se comuniquen los retrasos o errores.
- **Administración de versiones:** Los administradores de programas (PM) técnicos publican los cambios. Los cambios pueden variar de las actualizaciones del marco de la plataforma a las solicitudes de cambio a los modelos semánticos de BI que se realicen. Son la última línea de defensa para garantizar que los cambios no interrumpan nada.

### <a name="dedicated-deliveries"></a>Entregas dedicadas

Hay un equipo de entrega dedicada para cada grupo de partes interesadas. Normalmente, se compone de un ingeniero de datos, un ingeniero de análisis y un PM técnico, todos financiados por su grupo de partes interesadas.

## <a name="bi-team-roles"></a>Roles de equipo de BI

En Microsoft, nuestra plataforma de BI funciona a través de equipos escalables de profesionales. Los equipos se alinean con recursos dedicados y compartidos. Actualmente, tenemos los siguientes roles:

- **Administradores de programas:** Los PM son un recurso dedicado. Actúan como contacto principal entre el equipo de BI y las partes interesadas. Su trabajo consiste en convertir los requisitos empresariales de las partes interesadas en una especificación técnica. Además, administran la clasificación por orden de prioridad de los resultados esperados de las partes interesadas.
- **Responsables de base de datos:** Se trata de un recurso dedicado que se encarga de la incorporación de nuevos conjuntos de datos al almacenamiento de datos centralizado. La incorporación de un conjunto de datos puede implicar la configuración de dimensiones compatibles, la adición de lógica de negocios y atributos personalizados, así como el formato y los nombres estándar.
- **Responsables de análisis:** Se trata de un recurso dedicado que se encarga del diseño y desarrollo de modelos semánticos de BI. Procuran aplicar una arquitectura coherente con la nomenclatura y el formato estándar. La optimización del rendimiento es una parte importante de su rol.
- **Operaciones e infraestructura:** Se trata de un recurso compartido que se encarga de administrar trabajos y canalizaciones de datos. También se ocupa de administrar suscripciones de Azure, funcionalidades de Power BI, máquinas virtuales y puertas de enlace de datos.
- **Soporte técnico:** Se trata de un recurso compartido que se encarga de redactar la documentación, organizar el entrenamiento, comunicar los cambios del modelo semántico de BI y responder a las preguntas de los usuarios.

## <a name="governance-and-compliance"></a>Gobernanza y cumplimiento

Para cada grupo de partes interesadas, los responsables de administración de proyectos se encargan de la gobernanza y supervisión entre programas. Su objetivo primordial es garantizar que las inversiones en TI generen valor empresarial y mitiguen el riesgo. Las reuniones del comité directivo se celebran periódicamente para revisar el progreso y aprobar iniciativas importantes.

## <a name="grow-your-own-community"></a>Crecimiento de su propia comunidad

Establezca una comunidad dentro de su organización y fomente su crecimiento mediante prácticas como las siguientes:

- Celebre de eventos regulares en "horario de oficina" que reserven tiempo con el equipo de BI para que los empleados puedan plantear preguntas, hacer sugerencias, compartir ideas e incluso presentar quejas.
- Cree un canal de equipos que ofrezca asistencia y anime a cualquier persona a preguntar y responder a las preguntas publicadas.
- Organice y promocione grupos informales de usuarios y el estímulo a los empleados para que se presenten o asistan.
- Organice eventos de aprendizaje más formales en productos específicos y en la propia plataforma de BI. Valore la posibilidad de impartir [Power BI Dashboard in a Day](https://powerbi.microsoft.com/diad/), que está disponible como kit de cursos gratuito y es una excelente manera de introducir a los empleados en Power BI por primera vez.

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Arquitectura de la solución de BI en el COE](center-of-excellence-business-intelligence-solution-architecture.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

En el [siguiente artículo de esta serie](center-of-excellence-business-intelligence-solution-architecture.md), conocerá la arquitectura de la solución de BI en el COE y las distintas tecnologías empleadas.

### <a name="professional-services"></a>Servicios profesionales

Hay partners de Power BI certificados a su disposición para ayudar a su organización a tener éxito en la configuración de un COE. Pueden ofrecerle un rentable aprendizaje o una auditoría de los datos. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).

También puede ponerse en contacto con partners de consultoría experimentados. Pueden ayudarle a [valorar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL), [evaluar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL) o [implementar](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI.
