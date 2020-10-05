---
title: ¿Qué es Power BI?
description: 'Información general de Power BI y cómo encajan entre sí los distintos elementos: Power BI Desktop, el servicio Power BI, Power BI Mobile, Report Server y Power BI Embedded.'
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 09/23/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 2c793cf0b7af6f6a7fdbc6196052ac357b6ddd12
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/26/2020
ms.locfileid: "91375355"
---
# <a name="what-is-power-bi"></a>¿Qué es Power BI?
**Power BI** es una colección de servicios de software, aplicaciones y conectores que funcionan conjuntamente para convertir orígenes de datos sin relación entre sí en información coherente, interactiva y atractiva visualmente. Sus datos pueden ser una hoja de cálculo de Excel o una colección de almacenes de datos híbridos locales y basados en la nube. Power BI permite conectarse con facilidad a los orígenes de datos, visualizar y descubrir qué es importante y compartirlo con cualquiera o con todos los usuarios que desee.

## <a name="the-parts-of-power-bi"></a>Las partes de Power BI
Power BI consta de varios elementos que funcionan de manera conjunta, empezando por estos tres conceptos básicos: 
- Aplicación de escritorio de Windows llamada **Power BI Desktop**.
- Servicio SaaS (*software como servicio*) en línea denominado **servicio Power BI**. 
- **Aplicaciones móviles** de Power BI para dispositivos Windows, iOS y Android.

![Captura de pantalla del diagrama de Power BI Desktop, el servicio Power BI y Power BI Mobile en la que se muestra su integración.](media/power-bi-overview/power-bi-overview-blocks.png)

Estos tres elementos, &mdash;Power BI Desktop, el servicio y las aplicaciones móviles&mdash;, están diseñados para permitirle crear, compartir y usar información empresarial de la forma que le resulte más eficaz para usted y para su rol.

Además de estos tres elementos, Power BI también incluye otros dos:

- **Power BI Report Builder**, para crear informes paginados y compartirlos en el servicio Power BI. Obtenga más información sobre los [informes paginados](#paginated-reports-in-the-power-bi-service) más adelante en este artículo.
- **Power BI Report Server**, un servidor de informes local en el que puede publicar los informes de Power BI, después de crearlos en Power BI Desktop. Obtenga más información sobre [Power BI Report Server](#on-premises-reporting-with-power-bi-report-server) más adelante en este artículo.

## <a name="how-power-bi-matches-your-role"></a>Adaptación de Power BI a su rol
Es posible que la forma en que utilice Power BI dependa de su rol en un proyecto o equipo. Es posible que otros usuarios con otros roles usen Power BI de forma diferente.

Por ejemplo, podría utilizar principalmente el **servicio Power BI** para ver informes y paneles. Un compañero de trabajo, dedicado a procesar números y crear informes empresariales, podría usar ampliamente **Power BI Desktop** o **Power BI Report Builder** para crear informes y, después, publicarlos en el servicio Power BI, donde puede verlos. Otro compañero de trabajo, del departamento de ventas, podría usar principalmente la **aplicación móvil de Power BI** con el fin de supervisar el progreso de las cuotas de venta y profundizar en los detalles de nuevos clientes potenciales.

Si es un desarrollador, puede usar las API de Power BI para insertar datos en conjuntos de datos o para insertar informes y paneles en sus propias aplicaciones personalizadas. ¿Tiene alguna idea de un nuevo objeto visual? Compílelo usted mismo y compártalo con los demás.  

También podría usar cada elemento de Power BI en distintos momentos, en función de los objetivos o de su rol en un proyecto determinado.

Su modo de usar Power BI puede basarse en la característica o servicio de Power BI que es la mejor herramienta para su situación. Por ejemplo, puede usar Power BI Desktop para crear informes para el equipo sobre estadísticas de involucración de los clientes y ver el progreso de inventario y fabricación en un panel en tiempo real en el servicio Power BI. Puede crear un informe paginado de facturas para enviar por correo, en función de un conjunto de datos de Power BI. Cada una de las partes de Power BI está a su disposición, razón por la cual es tan flexible e interesante.

Examine los documentos que pertenecen al rol:
- Power BI para [*usuarios profesionales*](../consumer/end-user-consumer.md)
- Power BI Desktop para [*creadores de informes*](desktop-what-is-desktop.md)
- Power BI Report Builder para [*creadores de informes empresariales*](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- Power BI para [*administradores*](../admin/service-admin-administering-power-bi-in-your-organization.md)
- Power BI para *desarrolladores*
    * [Análisis integrado con Power BI](../developer/embedded/embedding.md)
    * [¿Qué es Power BI Embedded de Azure?](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md)
    * [Objetos visuales en Power BI](../developer/visuals/power-bi-custom-visuals.md)
    * [¿Qué pueden hacer los desarrolladores con la API de Power BI?](../developer/automation/overview-of-power-bi-rest-api.md)

## <a name="the-flow-of-work-in-power-bi"></a>El flujo de trabajo en Power BI
Un flujo de trabajo habitual en Power BI comienza con la conexión a orígenes de datos en Power BI Desktop y la creación de un informe. Después, ese informe se publica desde Power BI Desktop en el servicio Power BI y se comparte para que los usuarios profesionales del servicio Power BI y los dispositivos móviles puedan verlo e interactuar con él.

Este flujo de trabajo es habitual y muestra cómo los tres elementos principales de Power BI se complementan entre sí.

Esta es una [comparación de Power BI Desktop y el servicio Power BI](../fundamentals/service-service-vs-desktop.md) detallada.

## <a name="paginated-reports-in-the-power-bi-service"></a>Informes paginados en el servicio Power BI

Otro flujo de trabajo implica informes paginados en el servicio Power BI. Los creadores de informes empresariales diseñan informes paginados para imprimirlos o compartirlos. También pueden compartir estos informes en el servicio Power BI. Se denominan *paginados* porque presentan un formato apto para encajar en una página. A menudo se usan para informes operativos, o bien para imprimir formularios como facturas o transcripciones. Muestran todos los datos en una tabla, incluso si esta abarca varias páginas. Power BI Report Builder es la herramienta independiente para crear informes paginados.

:::image type="content" source="media/power-bi-overview/paginated-report-invoice-power-bi-service.png" alt-text="Captura de pantalla del informe paginado en el servicio Power BI.":::

Más información sobre los [informes paginados](../paginated-reports/paginated-reports-report-builder-power-bi.md) en el servicio Power BI.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Elaboración de informes en el entorno local con Power BI Report Server

¿Qué ocurre si tiene que mantener los informes en un entorno local, por ejemplo, detrás de un firewall?  Siga leyendo.

Puede crear, implementar y administrar informes de Power BI en Power BI Desktop e informes paginados en Report Builder, con las herramientas y servicios listos para usar que proporciona Power BI Report Server.

![Captura de pantalla del diagrama de Power BI Desktop, el servicio Report Server y Power BI Mobile en la que se muestra su integración.](media/power-bi-overview/power-bi-report-server2.png)

Power BI Report Server es una solución que se implementa detrás del firewall y entrega informes a los usuarios correspondientes de diferentes maneras, que pueden ser para visualizarlos en un explorador web, en un dispositivo móvil o como correo electrónico. Además, como Power BI Report Server es compatible con Power BI en la nube, puede pasarse a la nube cuando esté listo. 

Obtenga más información sobre el [servidor de informes de Power BI](../report-server/get-started.md).

## <a name="next-steps"></a>Pasos siguientes
- [Inicio rápido: Moverse por el servicio Power BI](../consumer/end-user-experience.md)   
- [Tutorial: Introducción al servicio Power BI](service-get-started.md)
- [Inicio rápido: Conectarse a los datos en Power BI Desktop](../connect-data/desktop-quickstart-connect-to-data.md)
