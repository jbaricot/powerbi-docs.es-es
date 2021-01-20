---
title: Creación de un vínculo a una ubicación específica en las aplicaciones móviles de Power BI
description: Obtenga información sobre cómo crear un vínculo profundo a un panel, icono o informe específicos en la aplicación móvil de Power BI con un identificador uniforme de recursos (URI).
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 11/16/2020
ms.openlocfilehash: 8c5b3c394d54df390d690d58b56e9084f9829733
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565655"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Creación de un vínculo a una ubicación específica en las aplicaciones móviles de Power BI
Puede usar vínculos para acceder directamente a contenido de Power BI específico, como un informe específico, una página del informe, un panel, un icono, etc.

Existen principalmente dos escenarios para usar vínculos para acceder al contenido en las aplicaciones móviles de Power BI: 

* Para abrir Power BI desde **fuera de la aplicación móvil** y aterrizar en contenido específico. Normalmente se trata de un escenario de integración en el que se abre la aplicación móvil de Power BI desde otra aplicación. 
* Para **navegar** dentro de Power BI. Esto suele ocurrir cuando se quiere crear una navegación personalizada en Power BI.

En este artículo se tratan los casos siguientes:
* Uso de vínculos para abrir contenido de Power BI específico desde fuera de la aplicación móvil. Se describen dos formatos de vínculo. Uno utiliza un método de redireccionamiento y se puede usar independientemente de dónde se abra Power BI. El otro se abre directamente en la aplicación móvil de Power BI y solo funcionará en dispositivos móviles que tengan instalada la aplicación móvil.
* Uso de vínculos dentro de Power BI para navegar a contenido de Power BI específico.

## <a name="use-links-from-outside-the-mobile-app"></a>Uso de vínculos desde fuera de la aplicación móvil
Si desea vincular a un elemento específico de Power BI desde fuera de la aplicación móvil, hay dos opciones, dependiendo de dónde se vaya a abrir el vínculo:

* Si desea que el vínculo se abra correctamente, independientemente de si se hace clic en él en el explorador de un equipo o en un dispositivo móvil, puede crear un vínculo que garantice que se abrirá correctamente, con independencia de dónde se haga clic. Este vínculo tiene una sintaxis de redireccionamiento especial para habilitar este comportamiento inteligente.

* Si sabe que el vínculo se va a abrir solo en un dispositivo móvil que tiene instalada la aplicación móvil de Power BI, puede evitar la sobrecarga de redireccionamiento del método anterior y usar otra sintaxis de vínculo que abra el vínculo directamente en la aplicación móvil de Power BI en el dispositivo móvil. Sin embargo, es importante tener en cuenta que, aunque este vínculo evita la sobrecarga de redireccionamiento del primer método, no funcionará si se abre en cualquier lugar que no sea un dispositivo móvil que tenga instalada la aplicación móvil de Power BI.

### <a name="create-a-link-that-works-anywhere"></a>Creación de un vínculo que funcione en cualquier lugar
El formato de vínculo descrito en esta sección usa el redireccionamiento para asegurarse de que el vínculo funciona independientemente de dónde se haga clic en él.
* Si se hace clic en el vínculo en un dispositivo móvil, se asegura de que el dispositivo use la aplicación móvil de Power BI para abrir el vínculo. Si la aplicación móvil no está instalada en el dispositivo, sugiere al usuario que vaya a la tienda para obtenerla.
* Si se hace clic en el vínculo en un equipo, se abrirá el elemento correspondiente en el portal web de Power BI.

El vínculo debe comenzar con un prefijo especial, seguido de los parámetros de la consulta:

https<nolink>://app.powerbi.com/Redirect? **[PARÁMETROSDECONSULTA]** </code>

> [!IMPORTANT]
> Si el contenido está hospedado en un centro de datos especial como Government, China, etc., el vínculo debe comenzar con la dirección de Power BI adecuada, como **app.powerbigov.us** o **app.powerbi.cn**.

Los parámetros de consulta son los siguientes:

|Parámetro  | Value  | Descripción |
|---------|---------|---------|
|**action** (obligatorio)    | OpenApp<br>OpenReport<br>OpenDashboard<br>OpenTile | |
|**appId**| GUID de 36 caracteres | Debe especificarse si quiere abrir un informe o un panel que forme parte de una aplicación.<br>Ejemplo: **appId=baf4b16d-b5bd-4360-8a3a-51d11242c09b** |
|**groupObjectId**| GUID de 36 caracteres | Especifica el área de trabajo si quiere abrir un informe o un panel que no forma parte de Mi área de trabajo.<br>Ejemplo: **groupObjectId=9a3841c6-74b3-46f1-85fd-bdd78f27b30e** |
| **dashboardObjectId** | GUID de 36 caracteres | Identificador de objeto de panel (si action es OpenDashboard u OpenTile).<br>Ejemplo: **dashboardObjectId=033bb049-5b68-4392-b3ef-ae9a43738a4a** |
| **reportObjectId** | GUID de 36 caracteres | Identificador de objeto de informe (si action es OpenReport).<br>Ejemplo: **reportObjectId=6114cec7-78e1-4926-88ff-0bc5338452cf** |
| **tileObjectId** | GUID de 36 caracteres | Identificador de objeto de icono (si action es OpenTile).<br>Ejemplo: **tileObjectId=a845dcb8-a289-43a8-94ea-67a8c0a068f9** |
| **reportPage** | ReportSection&lt;num&gt; | Nombre de la página si desea abrir una página específica del informe (si action es OpenReport).<br>Ejemplo: **reportPage=ReportSection6**  |
| **bookmarkGuid** | GUID de 36 caracteres | Identificador de marcador, si desea abrir una vista con marcadores específica (si action es OpenReport).<br>Ejemplo: **bookmarkGuid=18e8872f-6db8-4cf8-8298-3b2ab254cc7f** |
| **ctid** | GUID de 36 caracteres | Identificador de organización del elemento (relevante para escenarios B2B. Se puede omitir si el elemento pertenece a la organización del usuario).<br>Ejemplo: **ctid=5367c770-09d0-4110-bf6a-d760cb5ef681** . |
||||

**Ejemplos:**

En los ejemplos siguientes, los marcadores de posición para los valores de parámetro se resaltan en negrita. Para obtener los valores reales, vaya al servicio Power BI, abra el elemento al que desea vincular y extraiga los valores que necesita de la dirección URL del elemento.

* **Abrir una aplicación**

    https<nolink>://app.powerbi.com/Redirect?action=OpenApp&appId= **&lt;appid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**
   
* **Abrir un panel que forma parte de una aplicación**

    https<nolink>://app.powerbi.com/Redirect?action=OpenDashboard&appId= **&lt;appid-guid&gt;** &dashboardObjectId= **&lt;dashboardid-guid&gt;** &ctid= **&lt;ctid-guid&gt;**

* **Abrir un informe que forma parte de un área de trabajo distinta de Mi área de trabajo**

    https<nolink>://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId= **&lt;reportid-guid&gt;** &groupObjectId= **&lt;groupobjectid-guid&gt;** &reportPage=**ReportSection&lt;num&gt;**

### <a name="how-to-get-the-correct-link-format"></a>Cómo obtener el formato de vínculo correcto

#### <a name="links-to-apps-and-items-in-apps"></a>Vínculos a aplicaciones y elementos de las aplicaciones

En el caso de **aplicaciones, informes y paneles que forman parte de una aplicación**, la forma más sencilla de obtener el vínculo es ir al área de trabajo de la aplicación y seleccionar **Actualizar aplicación**. Se abrirá la experiencia "Publicar aplicación". Abra la pestaña de permisos y expanda la sección de vínculos para ver los vínculos a la aplicación y todo su contenido. Puede usar estos vínculos desde fuera de Power BI para acceder directamente a la aplicación y su contenido.

![Vínculos de aplicación de publicación de Power BI ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-to-items-that-are-not-in-an-app"></a>Vínculos a elementos que no están en una aplicación 

En el caso de los informes y paneles que no forman parte de una aplicación, es necesario extraer los identificadores de objetos necesarios de la dirección URL del elemento. Para ello, vaya al servicio Power BI, navegue hasta el elemento al que desea vincular y busque los valores que necesita en la dirección URL que aparece en la barra de direcciones del explorador.

Los ejemplos siguientes muestran dónde puede buscar los identificadores que necesita en las direcciones URL de los elementos a los que desea vincular.

* Para buscar un identificador de objeto de panel de 36 caracteres, vaya al panel específico al que desea vincular en el servicio Power BI y busque el identificador de objeto del panel y cualquier otro identificador necesario en los lugares indicados a continuación:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;dashboard-object-id&gt;** ?ctid= **&lt;org-object-id&gt;**

* Para buscar un identificador de objeto de informe de 36 caracteres, desplácese hasta el informe específico al que desea vincular en el servicio Power BI y busque los identificadores necesarios como se muestra a continuación. Tenga en cuenta que este ejemplo contiene una referencia a una página de informe específica y a un marcador específico.

    https<nolink>://app.powerbi.com/groups/me/reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;num&gt;** ?bookmarkGuid= **&lt;bookmark-id&gt;**

* Para vincular a un elemento en un área de trabajo distinta de Mi área de trabajo, debe extraer el identificador del objeto de grupo. En este ejemplo se muestra un informe de un área de trabajo distinta de Mi área de trabajo.

    https<nolink>://app.powerbi.com/groups/ **&lt;group-object-id&gt;** /reports/ **&lt;report-object-id&gt;** /**ReportSection&lt;report-section-num&gt;** ?ctid= **&lt;org-object-id&gt;**

### <a name="create-a-link-that-opens-only-on-a-device-that-has-the-power-bi-mobile-app-installed"></a>Creación de un vínculo que solo se abra en un dispositivo que tenga instalada la aplicación móvil de Power BI

El formato de vínculo descrito en esta sección se vincula a una ubicación específica dentro de las aplicaciones móviles de Power BI en todas las plataformas móviles: iOS, dispositivos Android y Windows 10. Este formato de vínculo abre directamente la ubicación, sin ninguno de los redireccionamientos implicados en el método descrito en la sección anterior. **Este formato solo se puede abrir en dispositivos móviles que tengan instalada la aplicación móvil de Power BI**.

Los vínculos de este formato pueden apuntar directamente a paneles, iconos e informes. El destino del vínculo profundo determina su formato. Siga estos pasos para crear vínculos profundos a ubicaciones diferentes. 

* **Abrir la aplicación móvil de Power BI**

    Use este vínculo para abrir la aplicación móvil de Power BI en cualquier dispositivo:

    mspbi://app/

* **Abrir en un panel específico**

    Este vínculo abre la aplicación móvil de Power BI en un panel específico:

    mspbi://app/OpenDashboard?DashboardObjectId= **<36-character-dashboard-id>**

    Para obtener el identificador de objeto de panel de 36 caracteres, vaya al panel específico del servicio Power BI y extráigalo de la dirección URL. Por ejemplo, el identificador de objeto de panel se resalta en la siguiente dirección URL del servicio Power BI:

    https<nolink>://app.powerbi.com/groups/me/dashboards/ **&lt;61b7e871-cb98-48ed-bddc-6572c921e270&gt;**

    Si el panel no está en Mi área de trabajo, debe agregar también el identificador de objeto de grupo, ya sea antes o después del identificador del panel. El vínculo profundo que se muestra a continuación tiene el parámetro de identificador de objeto de grupo agregado después del identificador de objeto de panel:

    mspbi://app/OpenDashboard?DashboardObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**</code>

    Observe la Y comercial (&) entre los dos parámetros.

* **Abrir en un icono concreto en modo de enfoque**

    Este vínculo abre un icono específico en modo de enfoque en la aplicación móvil de Power BI:

    mspbi://app/OpenTile?DashboardObjectId= **<36-character-dashboard-id>** &TileObjectId= **<36-character-tile-id>**

    Para buscar el identificador de objeto y de icono de panel de 36 caracteres, vaya al panel específico en el servicio Power BI y abra el icono en modo de enfoque. En el ejemplo siguiente, se resaltan los identificadores de icono y panel.

    https<nolink>://app.powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

    Para abrir directamente este icono, el vínculo sería:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

    Observe la Y comercial (&) entre los dos parámetros.

    Si el panel no está en Mi área de trabajo, agregue el parámetro GroupObjectId; por ejemplo, &GroupObjectId=<36-character-group-id>.

* **Abrir en un informe específico**

    Este vínculo abre un informe específico en la aplicación móvil de Power BI:

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>**

    Para buscar el identificador del objeto de informe de 36 caracteres, vaya al informe específico en el servicio Power BI. La siguiente dirección URL del servicio Power BI ilustra el identificador de informe que necesita extraer.

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

    Si el informe no está en Mi área de trabajo, necesita agregar también **&GroupObjectId=<36-character-group-id>** , ya sea antes o después del identificador de informe. Por ejemplo, en este caso, el vínculo profundo sería:

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**

    Observe la Y comercial (&) entre los dos parámetros.

* **Abrir una página de informe específica**

    Este vínculo abre una página específica del informe en la aplicación móvil de Power BI:

    mspbi://app/OpenReport?ReportObjectId= **<36-character-report-id>** &reportPage=**ReportSection&lt;number&gt;**

    La página del informe se denomina **ReportSection** y va seguida de un número. De nuevo, para buscar los valores que necesita, abra el informe en el servicio Power BI, vaya a la página específica del informe y extraiga los valores que necesita de la dirección URL. Por ejemplo, las secciones resaltadas de esta dirección URL representan los valores que necesitaría abrir en una página específica del informe:

    https<nolink>://app.powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**/**ReportSection11**</code>

* **Abrir en modo de pantalla completa (solo para dispositivos Windows)**

    Si se trata de dispositivos Windows, también puede agregar el parámetro **openFullScreen** para abrir un informe específico en modo de pantalla completa. En el ejemplo siguiente, se abre una página de informe en modo de pantalla completa:

    mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&**openFullScreen=true**

* **Agregar contexto** (opcional)

    También puede agregar contexto a la cadena. Si más adelante necesita ponerse en contacto con nosotros, podemos usar ese contexto para filtrar los datos, a fin de encontrar lo que es relevante para la aplicación. Para agregar contexto, agregue el parámetro **context=&lt;app-name&gt;** al vínculo:

    Por ejemplo, en el ejemplo siguiente, se muestra un vínculo que incluye un parámetro de contexto: 

    mspbi://app/OpenReport?ReportObjectId=**e684af3a-9e7f-44ee-b679-b9a1c59b5d60**&GroupObjectId=**8cc900cc-7339-467f-8900-fec82d748248**&**context=SlackDeepLink**

## <a name="use-links-inside-power-bi"></a>Empleo de vínculos dentro de Power BI

En las aplicaciones móviles de Power BI, los vínculos dentro de Power BI funcionan tal cual lo hacen en el servicio Power BI.

Si quiere agregar un vínculo al informe que apunte a otro elemento de Power BI, solo tiene que copiar la dirección URL de ese elemento desde la barra de direcciones del explorador. Obtenga más información sobre cómo [Agregar un hipervínculo a un cuadro de texto de un informe](../../create-reports/service-add-hyperlink-to-text-box.md).

## <a name="next-steps"></a>Pasos siguientes
Sus comentarios nos ayudan a decidir qué implementaremos en el futuro; no olvide votar por otras características que le gustaría ver en aplicaciones móviles de Power BI. 

* [Aplicaciones de Power BI para dispositivos móviles](mobile-apps-for-mobile-devices.md)
* Siga @MSPowerBI en Twitter
* Únase a la conversación en la [comunidad de Power BI](http://community.powerbi.com/)
* [¿Qué es Power BI?](../../fundamentals/power-bi-overview.md)