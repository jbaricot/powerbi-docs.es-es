---
title: Transformación de la BI de Microsoft
description: Obtenga información sobre cómo Microsoft impulsa correctamente una referencia cultural de datos para la toma de decisiones empresariales. Describe su estrategia y visión de BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/02/2020
ms.author: v-pemyer
ms.openlocfilehash: 8e1e590f871e1840209e72eb611bde7b21610c6e
ms.sourcegitcommit: c18130ea61e67ba111be870ddb971c6413a4b632
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2020
ms.locfileid: "86162376"
---
# <a name="microsofts-bi-transformation"></a>Transformación de la BI de Microsoft

Este artículo se dirige a los profesionales y administradores de TI. Conocerá nuestra estrategia y visión de BI, que nos permite aprovechar continuamente nuestros datos como recurso. También aprenderá a impulsar correctamente una referencia cultural de datos de toma de decisiones empresariales con Power BI.

Alguna información previa primero: En la actualidad, la explosión de datos afecta a los consumidores y a las empresas a velocidades de vértigo. Para tener éxito en este entorno con un uso intensivo de datos se requieren analistas y ejecutivos que puedan sintetizar una enorme cantidad de datos en conclusiones concisas. Las innovaciones en las herramientas de BI de Microsoft han cambiado la forma en que Microsoft explora sus datos y obtiene las conclusiones adecuadas que se necesitan para impulsar el impacto en la empresa.

Por lo tanto, ¿cómo puede su organización revolucionar también la manera en que trabaja con los datos? Para ayudarle a comprenderlo, vamos a contarle la historia de nuestro recorrido de transformación de BI.

## <a name="microsoft-journey"></a>Recorrido de Microsoft

Hace varios años, en Microsoft, nuestra referencia cultural de la organización animaba a los usuarios a buscar la plena propiedad de los datos y las conclusiones. También experimentó una fuerte resistencia cultural a hacer cosas de forma estandarizada. Por lo tanto, la referencia cultural de la organización nos condujo a desafíos de informes y análisis. En concreto, nos condujo a:

- Definiciones de datos, jerarquías, métricas e indicadores clave de rendimiento (KPI) incoherentes. Por ejemplo, cada país tenía su propia forma de informar sobre nuevos ingresos. No había ninguna coherencia, pero sí mucha confusión.
- Los analistas dedican el 75 % del tiempo en recopilar y compilar los datos.
- El 78 % de los informes se crean en un "entorno sin conexión".
- Más de 350 herramientas y sistemas de finanzas centralizados.
- Aproximadamente 30 millones de dólares en gasto anual en "aplicaciones en la sombra".

Estos desafíos nos llevaron a pensar en cómo podríamos hacer mejor las cosas. Finanzas y otros equipos internos recibieron el apoyo de los ejecutivos para transformar el proceso de revisión de negocio, lo que nos llevó a crear una plataforma de BI unificada como nuestra única fuente de confianza. (Más adelante en este capítulo hablaremos más sobre nuestra plataforma de BI). En última instancia, estas innovaciones llevaron a que las revisiones de negocio se transformasen de vistas tabulares densas en objetos visuales más sencillos y comprensibles centrados en temas empresariales clave.

¿Cómo logramos este acertado resultado? La entrega de una BI centralizada y administrada por TI y su ampliación con BI de autoservicio (SSBI) se tradujo en éxito. Lo describiremos de dos formas creativa: _disciplina en el núcleo_ y _flexibilidad en el borde_.

### <a name="discipline-at-the-core"></a>Disciplina en el núcleo

Disciplina en el núcleo significa que el equipo de TI conserva el control al mantener un único origen de datos maestros. La entrega de BI corporativa estandarizada y la definición de taxonomías y jerarquías de KPI coherentes forma parte de esa disciplina. Lo importante es que los permisos de datos se aplican de forma centralizada para garantizar que las personas solo puedan leer los datos que necesitan.

En primer lugar, entendimos que nuestra transformación de BI no era un problema tecnológico. Para lograr el éxito, aprendimos a definir primero el éxito y luego a convertirlo en métricas clave. No se puede subestimar lo importante que era para nosotros lograr la coherencia de la definición en todos nuestros datos.

Nuestra transformación no se produjo de una sola vez. Priorizamos la entrega del cuadro de mandos subsidiario que consta de unos 30 KPI. Luego, a lo largo de varios años, ampliamos gradualmente el número y la profundidad de las áreas temáticas y creamos jerarquías de KPI más complejas. Hoy en día, nos permite acumular KPI de nivel inferior en el nivel de cliente a los más altos en el nivel de la empresa. El número total de KPI supera ahora 2000 y cada uno de ellos es una medida clave de éxito y está alineado con los objetivos corporativos. Ahora, en toda la empresa, los informes corporativos y las soluciones de SSBI presentan KPI bien definidos, coherentes y seguros.

### <a name="flexibility-at-the-edge"></a>Flexibilidad en el borde

En el borde del núcleo, nuestros analistas de los equipos de finanzas, ventas y marketing se han convertido en más flexibles y ágiles. Ahora se benefician de la capacidad de analizar los datos con mayor rapidez. Más formalmente, este escenario se describe como _BI de autoservicio (SSBI) administrado_. Ahora sabemos que el SSBI administrado supone _beneficios mutuos_ para el departamento de TI y los analistas. Lo importante es que experimentamos optimizaciones impulsando la estandarización, el conocimiento y la reutilización de nuestros datos y soluciones de BI. Y, como empresa, derivamos más valor sinérgicamente, ya que encontramos el equilibrio adecuado entre BI centralizada y SSBI administrado.

### <a name="our-solution"></a>La solución

**Starlight** es el nombre que damos a nuestra plataforma interna de unificación y análisis de datos, que admite finanzas, ventas, marketing e ingeniería. Su misión es ofrecer una plataforma de datos sólida, compartida y escalable. La plataforma fue creada completamente por finanzas y continúa en funcionamiento hoy en día con los productos más recientes de Microsoft.

**KPI Lake** no es una instancia de Azure Data Lake. Más bien, se trata de un modelo tabular con tecnología de Starlight hospedado en IaaS de Azure que usa Microsoft SQL Server Analysis Services. El modelo tabular ofrece datos procedentes de más de 100 orígenes internos y define numerosas jerarquías e indicadores KPI. Su misión es habilitar equipos de análisis e informes de rendimiento empresarial en finanzas, marketing y ventas. Lo hace para obtener conclusiones oportunas, precisas y eficaces mediante modelos unificados de los correspondientes orígenes.

Cuando se implementó por primera vez, fue un momento emocionante porque el modelo tabular se tradujo en ventajas inmediatas y medibles. La primera versión centralizada de las plataformas de BI de finanzas y marketing de C+E. Después, en los últimos seis años, se ha ampliado para consolidar soluciones de información empresarial adicionales. En la actualidad, sigue evolucionando, con lo que se impulsan las revisiones de negocio globales y comerciales, así como la capacidad SSBI y los informes estándar. Su adopción se ha multiplicado por cinco desde su lanzamiento, lo que supera con creces nuestras expectativas iniciales.

Aquí se muestra un resumen de las principales ventajas:

- Impulsa nuestro cuadro de mandos subsidiario, las revisiones de negocio mundiales, además del análisis y los informes de finanzas, marketing y ventas.
- Admite el análisis de autoservicio, lo que permite a los analistas detectar conclusiones ocultas en los datos.
- Impulsa la elaboración de informes y análisis para la compensación de incentivos, el análisis de marketing y operaciones, las métricas de rendimiento de ventas, las revisiones de alta dirección y el proceso de planeamiento anual.
- Ofrece informes y análisis dinámicos y automatizados a partir de una _única fuente de confianza_.

**KPI Lake** es una gran historia de éxito. A menudo, se presenta a nuestros clientes para mostrar un ejemplo de cómo utilizar eficazmente nuestras tecnologías más recientes. No resulta sorprendente que tenga gran resonancia en muchos de ellos.

#### <a name="how-it-works"></a>Cómo funciona

La plataforma Starlight administra el flujo de datos de la adquisición al procesamiento, y luego hasta la publicación:

1. La integración de datos sólida y ágil se realiza de forma programada, y se consolidan los datos de más de 100 orígenes sin procesar dispares. Los sistemas de datos de origen incluyen bases de datos relacionales, Azure Data Lake Storage y bases de datos de Azure Synapse. Entre las áreas temáticas se incluyen finanzas, marketing, ventas e ingeniería.
2. Una vez que se almacenan provisionalmente, los datos se ajustan y se enriquecen con lógica de negocios y datos maestros. Luego se cargan en tablas de almacenamiento de datos. El modelo tabular se actualiza entonces.
3. Los analistas de toda la empresa usan Excel y Power BI para ofrecer conclusiones y análisis a partir del modelo tabular. Además, permite a los propietarios de empresas obtener definiciones de métricas para su propia empresa. Cuando sea necesario, el escalado se consigue con IaaS de Azure con equilibrio de carga.

## <a name="deliver-success"></a>Lograr el éxito

Curiosamente, todo el mundo quiere una versión de la verdad... siempre y cuando sea la suya. Pero para algunas organizaciones es su realidad. Tienen varias versiones de la verdad como consecuencia de que las personas reivindican la plena propiedad de los datos y las conclusiones. Para estas organizaciones, no es probable que este enfoque no administrado conduzca al éxito empresarial.

Por eso creemos que necesita un _Centro de excelencia (COE)_ . Un COE es un equipo central que se encarga de definir las métricas y definiciones de toda la empresa, y mucho más. También es una función empresarial que organiza a las personas, los procesos y los componentes tecnológicos en un conjunto completo de competencias y funcionalidades empresariales.

Vemos muchas pruebas que respaldan que un COE amplio y robusto es fundamental para ofrecer valor y maximizar el éxito empresarial. Puede incluir iniciativas de cambio, procesos estándar, roles, instrucciones, procedimientos recomendados, soporte técnico, entrenamiento y mucho más.

Le invitamos a leer los artículos de esta serie COE para saber más. Vamos a ayudarle a descubrir el modo en que su organización puede adoptar el cambio para lograr el éxito.

## <a name="next-steps"></a>Pasos siguientes

En el [siguiente artículo de esta serie](center-of-excellence-establish.md), consulte cómo un COE nos ayudó en Microsoft a crear una plataforma de datos y análisis estandarizada para extraer conclusiones a partir de nuestros datos.

Para más información sobre este artículo, consulte los recursos siguientes:

- [Establecimiento de un centro de excelencia](center-of-excellence-establish.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
