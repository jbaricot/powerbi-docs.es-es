---
title: Colaboración en Microsoft Teams con Power BI
description: Puede compartir y colaborar fácilmente en contenido de Power BI interactivo en los canales y chats de Microsoft Teams.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: 01e5b470e0beb189d64da18785a17e771bcaf59b
ms.sourcegitcommit: d9d67ee47954379c2df8db8d0dc8302de4c9f1e5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87478047"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Colaboración en Microsoft Teams con Power BI

Puesto que contar con personal distribuido y remoto cada vez es más habitual, más organizaciones confían en los equipos de Microsoft para mantener a los empleados sincronizados. Power BI ofrece varias opciones para compartir y colaborar en contenido de Power BI interactivo en los canales y chats de Microsoft Teams. 

- Con la pestaña **Power BI** para Microsoft Teams, puede [insertar informes interactivos en canales y chats de Microsoft Teams](service-embed-report-microsoft-teams.md). La pestaña **Power BI** ayuda a los compañeros de trabajo a encontrar los datos del equipo y analizar los datos en los canales del equipo. 
- Cree una [vista previa del vínculo](service-teams-link-preview.md) cuando pegue un vínculo a los informes, a los paneles y a las aplicaciones en el cuadro de mensaje de Microsoft Teams. La vista previa del vínculo muestra información sobre el vínculo. 
- Use [Compartir en Teams](service-share-report-teams.md) cuando vea informes y paneles en el servicio Power BI para iniciar conversaciones rápidamente en Teams.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Captura de pantalla de un informe de Power BI insertado en un canal de Teams.":::

## <a name="requirements"></a>Requisitos

En general, para que Power BI funcione en Microsoft Teams, asegúrese de lo siguiente:

- Los usuarios tienen una licencia de Power BI Pro o el informe está incluido en una [capacidad de Power BI Premium (SKU EM o P)](../admin/service-premium-what-is.md) con una licencia de Power BI.
- Los usuarios han iniciado sesión en el servicio Power BI para activar la licencia de Power BI.
- Los usuarios cumplen los requisitos para usar la pestaña **Power BI** en Microsoft Teams.

## <a name="grant-access-to-reports"></a>Concesión de acceso a los informes

El hecho de insertar un informe en Microsoft Teams o enviar un vínculo a un elemento no concede permiso a los usuarios para ver el informe de forma automática. Debe [permitir que los usuarios vean los informes en Power BI](service-share-dashboards.md). Para que esto sea más fácil, puede usar un grupo de Microsoft 365 para el equipo.

> [!IMPORTANT]
> Asegúrese de revisar quién puede ver el informe en el servicio Power BI y de conceder acceso a los usuarios que no están en la lista.

Una forma de garantizar que todos los miembros del equipo tengan acceso a los informes consiste en incluir los informes en una misma área de trabajo y dar acceso a ese grupo de Microsoft 365 del equipo al área de trabajo en cuestión.

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

- Power BI no admite los mismos idiomas localizados que Microsoft Teams. En consecuencia, es posible que no vea una localización correcta en el informe insertado.
- En la pestaña **Power BI** de Microsoft Teams no se pueden insertar paneles de Power BI.
- Los usuarios que no tengan una licencia o permiso de Power BI para acceder al informe verán el mensaje "El contenido no está disponible".
- Es posible que tenga problemas si usa Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- La pestaña **Power BI** de Microsoft Teams no admite [filtros de URL](service-url-filters.md).
- En nubes nacionales, la nueva pestaña **Power BI** no está disponible. Puede que haya disponible una versión anterior que no es compatible con la nueva experiencia de área de trabajo o los informes de aplicaciones de Power BI.
- Una vez que se guarde la pestaña, no se podrá cambiar su nombre en la configuración. Para cambiarlo, use la opción **Cambiar nombre**.
- No se admite el inicio de sesión único para el servicio de vista previa de vínculo.
- Las vistas previas de vínculo no funcionan en los canales privados o de chat.

## <a name="next-steps"></a>Pasos siguientes

- [Inserción de contenido de Power BI en Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Obtención de una vista previa del vínculo de Power BI en Microsoft Teams](service-teams-link-preview.md)
- [Uso compartido directo en Teams desde el servicio Power BI](service-share-report-teams.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).
