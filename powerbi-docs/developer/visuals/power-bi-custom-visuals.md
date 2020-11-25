---
title: Objetos visuales en Power BI
description: En este artículo se describen los objetos visuales personalizados de Power BI
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 07/14/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 8ea72198ded59f3ce5dce1362ab9320fc119fac6
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514404"
---
# <a name="visuals-in-power-bi"></a>Objetos visuales en Power BI

Power BI incluye de serie muchos objetos visuales de Power BI. Estos objetos visuales están disponibles en el panel de visualización de [Power BI Desktop](https://powerbi.microsoft.com/desktop/) y el [servicio Power BI](https://app.powerbi.com), y se pueden usar para crear y editar contenido de Power BI.

:::image type="content" source="media/power-bi-custom-visuals/power-bi-visualizations.png" alt-text="Captura de pantalla del panel de visualización de Power BI tal y como aparece en los servicios Power BI Desktop y Power BI.":::

Hay muchos más objetos visuales de Power BI disponibles en Microsoft [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) o a través de Power BI. Estos objetos visuales son creados por Microsoft y los partners de Microsoft, y validados por el equipo de validación de AppSource.

También puede desarrollar un objeto visual personal de Power BI para uso propio, de la organización o de toda la comunidad de Power BI.

## <a name="default-power-bi-visuals"></a>Objetos visuales predeterminados de Power BI

Estos son los objetos visuales de serie de Power BI disponibles en el panel de visualización de *Power BI Desktop* y el *servicio Power BI*.

Para desanclar un objeto visual de Power BI del panel de visualización, haga clic en él con el botón derecho y seleccione **Desanclar**.

Para restaurar los objetos visuales predeterminados de Power BI en el panel de visualización, haga clic en **Importar un objeto visual personalizado** y seleccione **Restaurar objetos visuales predeterminados**. 

## <a name="appsource-power-bi-visuals"></a>Objetos visuales de Power BI de AppSource

Microsoft y los miembros de la comunidad aportan objetos visuales de Power BI para el beneficio público y los publican en [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Puede descargar estos objetos visuales y agregarlos a los informes de Power BI. Microsoft ha probado y aprobado la funcionalidad y calidad de todos estos objetos visuales de Power BI.

>[!NOTE]
>* Mediante el uso de objetos visuales de Power BI creados con nuestro SDK, es posible que esté importando datos de terceros u otros servicios, o enviando datos a estos, que se encuentren fuera del área geográfica, el límite de cumplimiento o la instancia de la nube nacional del inquilino de Power BI.
>* Los objetos visuales certificados de Power BI son objetos visuales en AppSource que se han probado además para comprobar que el objeto visual no tiene acceso a recursos o servicios externos.
>* Una vez importados los objetos visuales de Power BI desde AppSource, estos pueden actualizarse automáticamente sin ningún aviso adicional.

### <a name="what-is-appsource"></a>¿Qué es AppSource?

[AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) es la ubicación de las aplicaciones, los complementos y las extensiones para el software de Microsoft. AppSource conecta a millones de usuarios de productos como Microsoft 365, Azure, Dynamics 365, Cortana y Power BI con soluciones que les ayudan a realizar su trabajo de forma más eficaz e informada que antes.

### <a name="certified-power-bi-visuals"></a>Objetos visuales de Power BI certificados

Los objetos visuales certificados de Power BI son objetos visuales de [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0) que cumplen determinados requisitos de código especificados que el equipo de Microsoft Power BI ha probado y aprobado. Las pruebas están diseñadas para comprobar que el objeto visual no accede a servicios o recursos externos.

Para ver la lista de objetos visuales certificados de Power BI o para enviar uno propio, vea [Objetos visuales de Power BI certificados](power-bi-custom-visuals-certified.md).

### <a name="samples-for-power-bi-visuals"></a>Ejemplos de objetos visuales de Power BI

Cada objeto visual de Power BI en AppSource tiene una muestra de datos que ilustra su funcionamiento. Para descargar el ejemplo, en [AppSource](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fappsource.microsoft.com%2Fen-us%2Fmarketplace%2Fapps%3Fpage%3D1%26product%3Dpower-bi-visuals&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C6d9286afacb3468d4cde08d740b76694%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637049028749147718&sdata=igWm0e1vXdgGcbyvngQBrHQVAkahPnxPC1ZhUPntGI8%3D&reserved=0), seleccione un objeto visual de Power BI y, en la sección *Probar uno de ejemplo*, haga clic en el vínculo **Informe de ejemplo**.

## <a name="organizational-store"></a>Almacén de la organización

Los administradores de Power BI aprueban e implementan los objetos visuales de Power BI en la organización. Esto permite a los autores de informes detectar fácilmente, actualizar y usar estos objetos visuales de Power BI. Los administradores pueden administrar fácilmente estos objetos visuales con acciones como la actualización de versiones y la deshabilitación y habilitación de objetos visuales de Power BI.

Para acceder al almacén de la organización, en el panel *Visualización*, haga clic en **Importar un objeto visual personalizado**, seleccione **Importar de Marketplace** y, en la parte superior de la ventana *Objetos visuales de Power BI*, seleccione la pestaña **Mi organización**.

[Más información sobre objetos visuales de la organización](power-bi-custom-visuals-organization.md).

## <a name="visual-files"></a>Archivos de objetos visuales

Los objetos visuales de Power BI son paquetes que contienen código para representar los datos que se les proporcionan. Cualquiera puede crear un objeto visual personalizado y empaquetarlo como un archivo `.pbiviz` único, que después se puede importar en un informe de Power BI.

Para importar un objeto visual de Power BI, en el panel *Visualización*, haga clic en **Importar un objeto visual personalizado** y seleccione **Importar desde archivo**.

Si es desarrollador web y está interesado en crear un objeto visual propio y agregarlo a AppSource, puede obtener información sobre cómo hacerlo en [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md) y [Publicación de un objeto visual de Power BI en AppSource](office-store.md).

> [!WARNING]
> Un objeto visual de Power BI puede contener código con riesgos para la seguridad o la privacidad. Asegúrese de que confía en el autor y el origen del objeto visual de Power BI antes de importarlo al informe.

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md)

>[!div class="nextstepaction"]
>[Estructura de proyectos de objetos visuales de Power BI](visual-project-structure.md)

>[!div class="nextstepaction"]
>[Instrucciones para objetos visuales de Power BI](guidelines-powerbi-visuals.md)

>[!div class="nextstepaction"]
>[Preguntas más frecuentes](power-bi-custom-visuals-faq.md)

>[!div class="nextstepaction"]
>[Comunidad de Power BI](https://community.powerbi.com/)