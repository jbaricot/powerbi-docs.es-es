---
title: Más información sobre las migraciones de los clientes a Power BI
description: Obtenga información de los clientes al realizar la migración a Power BI.
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 7982598ac7a475cae4f0524c8d3d914b4f1a6341
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086772"
---
# <a name="learn-from-customer-power-bi-migrations"></a>Más información sobre las migraciones de los clientes a Power BI

En este artículo, que concluye la serie sobre la migración a Power BI, se comparten lecciones clave que han descubierto dos clientes que han realizado una correcta migración a Power BI.

## <a name="international-consumer-goods-company"></a>Empresa internacional de bienes de consumo

Una empresa internacional de bienes de consumo, que vende cientos de productos, tomó la decisión en 2017 de adoptar una estrategia priorización de la nube. Uno de los factores principales para seleccionar Power BI como su plataforma de inteligencia empresarial (BI) es su profunda integración con Azure y Microsoft 365.

### <a name="conduct-a-phased-migration"></a>Realización de una migración por fases

En 2017, la empresa comenzó a usar Power BI. El objetivo inicial de la organización era incorporar Power BI como una herramienta de BI adicional. La decisión proporcionó a los autores de contenido, consumidores y TI tiempo para adaptarse a las nuevas formas de ofrecer BI. También les permitió ganar experiencia en Power BI.

Durante la segunda mitad de 2018, se hizo un anuncio formal por el que se indicaba que Power BI pasaba a ser la herramienta de BI aprobada para la organización. Y, por lo tanto, todos los nuevos trabajos de desarrollo de BI debían realizarse en Power BI. La disponibilidad de Power BI Premium fue un factor clave para tomar esta decisión. En aquel momento, la organización desaconsejaba el uso de la plataforma de BI anterior y empezó la planeación de la transición.

Hacia finales de 2019, la empresa comenzó a migrar el contenido existente de la plataforma de BI heredada a Power BI. Algunos de los usuarios pioneros migraron rápidamente su contenido. Esto ayudó a impulsar Power BI todavía más dentro de la propia organización. Más adelante, se solicitó a los propietarios y autores de contenido que comenzaran a realizar la migración completa a Power BI a finales de 2020. La organización sigue enfrentándose a desafíos relacionados con las aptitudes, el tiempo y la financiación, aunque ninguno de estos está relacionado con la plataforma tecnológica propiamente dicha.

> [!IMPORTANT]
> Power BI ya tenía éxito y estaba afianzado en la organización antes de que se pidiera a las unidades de negocio que acometieran un esfuerzo de migración formal fuera de la plataforma de BI anterior.

### <a name="prepare-to-handle-varying-responses"></a>Preparación para el manejo de respuestas distintas

En esta gran organización descentralizada, había diferentes niveles de receptividad y disposición ante el cambio a Power BI. Más allá de las inquietudes relacionadas con el tiempo y el presupuesto, parte del personal había realizado inversiones considerables en el desarrollo de sus habilidades en la plataforma de BI anterior. Por lo tanto, el anuncio sobre la estandarización de Power BI no fue bienvenida por todo el personal. Puesto que cada unidad de negocio tiene su presupuesto, las unidades individuales podrían cuestionar decisiones de este tipo. A medida que las decisiones sobre las herramientas de TI se hicieron de forma centralizada, se produjeron algunos desafíos que tuvieron que tratar el patrocinador ejecutivo y los líderes de BI.

> [!IMPORTANT]
> La comunicación con los equipos de liderazgo a lo largo de las unidades de negocio fue fundamental para asegurarse de que comprendieran las ventajas organizativas de alto nivel derivadas de la estandarización en Power BI. La comunicación efectiva resultó todavía más esencial a medida que progresaba la migración y se aproximaba la fecha de retirada de la plataforma de BI heredada.

### <a name="focus-on-the-bigger-picture"></a>Enfoque en una visión general más amplia

La empresa descubrió que, aunque algunos informes migrados podían replicar cuidadosamente el diseño original, no todos los informes individuales podían replicarse con exactitud en Power BI. En cualquier caso, es lo que se esperaba, dado que todas las plataformas de BI son diferentes. Esto puso de manifiesto que era necesaria una mentalidad de diseño diferente.

Se proporcionaron instrucciones a los autores de contenido: atención a la creación de informes que se ajustaran a la finalidad del uso en Power BI, en lugar de intentar una réplica exacta del informe heredado. Por este motivo, los expertos en la materia deben estar disponibles activamente durante el proceso de migración para la consulta y la validación. Se han realizado esfuerzos para tener en cuenta el propósito del diseño del informe y mejorarlo cuando sea necesario.

> [!IMPORTANT]
> A veces, el mejor enfoque consiste en realizar mejoras durante la migración. En otras ocasiones, la mejor opción es ofrecer el mismo valor exacto que antes, sin mejoras significativas, para no poner en peligro la escala de tiempo de la migración.

### <a name="cautiously-assess-priorities"></a>Evaluación de las prioridades con precaución

Se llevó a cabo un análisis de la plataforma de BI anterior para comprender completamente su uso. La plataforma de BI anterior tenía miles de informes publicados, de los cuales se había accedido aproximadamente a la mitad en el año anterior. Al evaluar qué informes se consideraba que ofrecían un valor significativo a la organización, la cifra anterior se recortaba de nuevo a la mitad. A esos informes se les dio prioridad a la hora de la migración.

> [!IMPORTANT]
> Es muy fácil sobrestimar la importancia real del informe. En el caso de los informes que no se usan con frecuencia, evalúe si se pueden retirar completamente. A veces, lo más económico y más sencillo es no hacer nada.

### <a name="cautiously-assess-complexity"></a>Evaluación de la complejidad con precaución

De los primeros informes a los que se les dio prioridad, las estimaciones de tiempo se compilaron en función de los niveles de esfuerzo estimado: sencillo, medio o complejo. Aunque suene como un proceso relativamente sencillo, no espere que las estimaciones de tiempo sean precisas en cada informe. Puede encontrarse con que una estimación sea muy poco precisa. Por ejemplo, la compañía tenía un informe que consideró muy complejo. Los consultores estimaron una conversión de 50 días. Sin embargo, el informe rediseñado en Power BI se completó en aproximadamente 50 horas.

> [!IMPORTANT]
> Aunque las estimaciones de tiempo suelen ser necesarias para obtener la financiación y las asignaciones de personal, probablemente son más valiosas en el total agregado.

### <a name="decide-how-change-management-is-handled"></a>Decisión de cómo se controla la administración de cambios

Con un volumen tan alto de recursos de BI, cambiar la administración de los informes de propiedad empresarial suponía un desafío. Los informes administrados por TI se manejaron según las prácticas estándar de administración de cambios. Sin embargo, debido al gran volumen, producir un cambio para el contenido de propiedad empresarial de forma centralizada no era posible.

> [!IMPORTANT]
> La responsabilidad adicional recae en las unidades de negocio cuando no es práctico administrar los cambios desde un equipo central.

### <a name="create-an-internal-community"></a>Creación de una comunidad interna

La empresa estableció un Centro de excelencia (COE) para proporcionar clases y recursos internos de entrenamiento. El COE también actúa como un grupo de consultoría interno que está preparado para ayudar a los autores de contenido con incidencias técnicas, resolución de obstáculos e instrucciones de procedimientos recomendados.

También existe una comunidad interna de Power BI que cuenta con más de 1600 miembros, lo que ha resultado un éxito masivo. La comunidad se administra en Yammer. Los miembros pueden plantear preguntas de forma interna y recibir respuestas que se ciñen a los procedimientos recomendados y se enmarcan dentro de las restricciones de la organización. Este tipo de interacción entre usuarios reduce gran parte de la carga de soporte técnico del COE. Sin embargo, el COE supervisa las preguntas y respuestas, y participa en las conversaciones cuando es necesario.

Una extensión de la comunidad interna es la red de expertos más reciente de Power BI. Incluye un pequeño número de campeones de Power BI preseleccionados de dentro de la organización. Son profesionales de Power BI de las unidades de negocio muy cualificados, campeones entusiastas y que quieren resolver de forma activa los desafíos de la empresa. Se espera que los miembros de la red de expertos de Power BI cumplan los procedimientos recomendados y las directrices que establece el COE, y ayuden a que la comunidad interna de Power BI en sentido más amplio los entienda e implemente. Aunque la red de expertos de Power BI colabora con el COE y puede recibir entrenamiento dedicado, los expertos de Power BI funcionan independientemente del COE. Los expertos de Power BI pueden definir los parámetros de su funcionamiento, teniendo en cuenta que cuentan con otras responsabilidades y prioridades en su rol oficial.

> [!IMPORTANT]
> Tenga un ámbito muy bien definido de lo que hace el COE, por ejemplo, adopción, gobernanza, instrucciones, procedimientos recomendados, entrenamiento, soporte técnico y quizás incluso desarrollo práctico. Aunque un COE es increíblemente valioso, medir el retorno de la inversión puede resultar difícil.

### <a name="monitor-migration-progress-and-success"></a>Supervisión del progreso y el éxito de la migración

Los indicadores clave de rendimiento (KPI) se supervisan continuamente durante la migración a Power BI. Ayudan a la empresa a comprender las tendencias de las métricas, como el número de visitas a los informes, el número de informes activos y los usuarios distintos al mes. El mayor uso de Power BI se mide junto con el menor uso de la plataforma de BI anterior, con el objetivo de lograr una relación inversa. Los destinos se actualizan cada mes para adaptarse a los cambios. Si el uso no se produce al ritmo deseado, se identifican los cuellos de botella para que se puedan realizar las acciones pertinentes.

> [!IMPORTANT]
> Cree un cuadro de mandos de migración con inteligencia empresarial procesable para supervisar el éxito del trabajo de migración.

## <a name="large-transportation-and-logistics-company"></a>Empresa de transporte y logística de gran tamaño

Una gran empresa de transporte y logística de Norteamérica está invirtiendo de forma activa en la modernización de su infraestructura de datos y sistemas analíticos.

### <a name="allow-a-period-of-gradual-growth"></a>Habilitación de un período de crecimiento gradual

La compañía empezó a usar Power BI en 2018. A mediados de 2019, Power BI se convirtió en la plataforma preferida para todos los casos de uso de BI nuevos. Posteriormente, en 2020, la empresa se centró en la eliminación gradual de la plataforma de BI existente y de una serie de soluciones de BI de ASP.NET desarrolladas de forma personalizada.

> [!IMPORTANT]
> Power BI tenía muchos usuarios activos en la organización antes de comenzar la eliminación gradual de la plataforma y las soluciones de BI heredadas.

### <a name="balance-centralized-and-distributed-groups"></a>Equilibrio de los grupos centralizados y distribuidos

En la empresa, hay dos tipos de equipos de BI: un equipo central de BI y grupos de análisis distribuidos en toda la organización. El equipo central de BI tiene la responsabilidad de la propiedad de Power BI como plataforma, pero no posee ningún contenido. De esta manera, el equipo central de BI es un centro de habilitación técnica que admite los grupos de análisis distribuidos.

Cada uno de los grupos de análisis está dedicado a una unidad de negocio específica o a una función de servicios compartidos. Un grupo pequeño puede contener un solo analista, mientras que un grupo de mayor tamaño puede tener de 10 a 15.

> [!IMPORTANT]
> Los grupos de análisis distribuidos constan de expertos en la materia que están familiarizados con las necesidades del día a día de la empresa. Esta separación permite que el equipo principal de BI se centre mayormente en el soporte técnico y la habilitación de los servicios y herramientas de BI.

### <a name="focus-on-dataset-reusability"></a>Enfoque en la reusabilidad del conjunto de datos

Confiar en soluciones de BI personalizadas de ASP.NET suponía una barrera para desarrollar soluciones de BI nuevas. El conjunto de aptitudes necesario implicaba que el número de autores de contenido de autoservicio era pequeño. Dado que Power BI es una herramienta mucho más accesible, diseñada específicamente para BI de autoservicio, se difunde rápidamente en toda la organización una vez que se ha lanzado.

La capacitación de los analistas de datos dentro de la empresa dio lugar a resultados positivos inmediatos. Sin embargo, el enfoque inicial con el desarrollo de Power BI estaba en la visualización. Aunque dio como resultado soluciones de BI valiosas, este enfoque producía un gran número de archivos de Power BI Desktop, todos ellos con una relación uno a uno entre el informe y su conjunto de datos. Dio como resultado muchos conjuntos de datos y la duplicación de datos y lógica de negocios. Para reducir la duplicación de datos, la lógica y el esfuerzo, la empresa facilitó el entrenamiento y proporcionó soporte técnico a los autores de contenido.

> [!IMPORTANT]
> Incluya información sobre la importancia de la reusabilidad de los datos en los esfuerzos de entrenamiento internos. Solucione los conceptos importantes tan pronto como sea práctico.

### <a name="test-data-access-multiple-ways"></a>Prueba de acceso a datos de varias maneras

La plataforma de almacenamiento de datos de la empresa es DB2. En función del diseño actual del almacenamiento de datos, la compañía averiguó que los modelos DirectQuery, en lugar de los modelos de importación, funcionaban mejor para sus requisitos.

> [!IMPORTANT]
> Realice una prueba de concepto técnica para evaluar el modo de almacenamiento del modelo que mejor funcione. Además, enseñe a los modeladores de datos los modos de almacenamiento de los modelos y cómo pueden elegir un modo adecuado para su proyecto.

### <a name="educate-authors-about-premium-licensing"></a>Aprendizaje de los autores sobre las licencias Premium

Dado que era más fácil empezar a trabajar con Power BI (en comparación con su plataforma de BI heredada), muchos de los usuarios pioneros eran personas que no tenían una licencia para la herramienta de BI anterior. Tal como se esperaba, el número de autores de contenido aumentó de forma considerable. Estos autores de contenido querían compartir su contenido con otras personas, lo que daba como resultado una necesidad continua de licencias de Power BI Pro adicionales.

La empresa realizó una gran inversión en áreas de trabajo Premium, especialmente para distribuir contenido de Power BI a muchos usuarios con licencias de Power BI gratuitas. El equipo de soporte técnico trabaja con autores de contenido para asegurarse de que usan áreas de trabajo Premium cuando sea necesario. Evita la asignación innecesaria de licencias de Power BI Pro cuando un usuario solo necesita consumir contenido.

> [!IMPORTANT]
> Suelen surgir preguntas acerca de las licencias. Prepárese para educar y ayudar a los creadores de contenido a resolver las preguntas sobre las licencias. Compruebe que las solicitudes de usuario para licencias de Power BI Pro están justificadas.

### <a name="understand-the-data-gateways"></a>Descripción de las puertas de enlace de datos

En un primer momento, la empresa tenía muchas puertas de enlace personales. El uso de un clúster de puerta de enlace de datos local desplaza los esfuerzos de administración al equipo central de BI, lo que permite que la comunidad de autores de contenido se centre en la generación de contenido. El equipo central de BI trabajó con la comunidad de usuarios de Power BI interna para reducir el número de puertas de enlace personales.

> [!IMPORTANT]
> Cuente con un plan para crear y administrar puertas de enlace de datos locales. Decida quién tiene permiso para instalar y usar una puerta de enlace personal, y aplíquela a las directivas de puerta de enlace.

### <a name="formalize-your-support-plan"></a>Formalización del plan de soporte técnico

Dado que la adopción de Power BI aumentó en la organización, la empresa descubrió que un enfoque de compatibilidad con varios niveles funcionaba bien:

- **Nivel 1; entre el equipo**: los usuarios aprenden los unos de los otros a diario.
- **Nivel 2; comunidad de Power BI**: las personas formulan preguntas de la comunidad de equipos internos para que aprendan unos de otros y comuniquen información importante.
- **Nivel 3; equipo central de BI y COE**: las personas envían solicitudes de correo electrónico para obtener ayuda. Las sesiones en _horario de oficina_ se llevan a cabo dos veces al día para debatir problemas de forma colectiva y compartir ideas.

> [!IMPORTANT]
> Aunque los dos primeros niveles son menos formales, son tan importantes como el tercer nivel de soporte técnico. Los usuarios experimentados suelen confiar principalmente en las personas que conocen, mientras que los usuarios más recientes (o los que son el único analista de datos para una unidad de negocio o un servicio compartido) suelen confiar más en el soporte técnico formal.

### <a name="invest-in-training-and-governance"></a>Inversión en entrenamiento y gobernanza

En el último año, la empresa mejoró sus ofertas de entrenamiento internas y ha mejorado su programa de gobernanza de datos. El comité de gobernanza incluye miembros clave de cada uno de los grupos de análisis distribuidos, además del COE.

Ahora hay seis cursos de Power BI internos en su catálogo. El curso [Dashboard in a Day](https://powerbi.microsoft.com/diad/) (Panel en un día) sigue siendo un curso popular para principiantes. Para ayudar a los usuarios a profundizar en sus conocimientos, ofrecen una serie de tres cursos de Power BI y dos cursos de DAX.

Una de sus decisiones de gobernanza de datos más importante se relaciona con la administración de las capacidades Premium. La empresa ha decidido alinear su capacidad con áreas de análisis clave en unidades de negocio y servicios compartidos. Por lo tanto, si existen ineficiencias, el impacto solo se percibe dentro de esa área y los administradores de capacidad descentralizada cuentan con los conocimientos para administrarla tal como consideren oportuno.

> [!IMPORTANT]
> Preste atención a cómo se usan las capacidades Premium y cómo se asignan las áreas de trabajo.

## <a name="next-steps"></a>Pasos siguientes

Otros recursos útiles incluyen los siguientes:

- [Transformación de la BI de Microsoft](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [Notas del producto de la planeación de una implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)
- [Dashboard in a Day](https://powerbi.microsoft.com/diad/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)

Hay partners de Power BI experimentados a su disposición para ayudar a su organización a tener éxito en el proceso de migración. Para ponerse en contacto con un partner de Power BI, visite el [portal de partners de Power BI](https://powerbi.microsoft.com/partners/).
