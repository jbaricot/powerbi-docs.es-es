---
title: Colaboración en Microsoft Teams con Power BI
description: Puesto que contar con personal distribuido es cada vez es más habitual, más organizaciones confían en Microsoft Teams para habilitar el trabajo remoto y mantener a los empleados sincronizados.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: 7c8fa59521be1cfc8bb25fb04c3904f257fb62be
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926684"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Colaboración en Microsoft Teams con Power BI

Puesto que contar con personal distribuido es cada vez es más habitual, más organizaciones confían en Microsoft Teams para habilitar el trabajo remoto y mantener a los empleados sincronizados. En este artículo se describen las opciones para compartir contenido de Power BI interactivo y colaborar en él en los canales y chats de Microsoft Teams. 

- Con la pestaña **Power BI** para Microsoft Teams, puede [insertar informes interactivos en canales y chats de Microsoft Teams](service-embed-report-microsoft-teams.md). La pestaña Power BI ayuda a los compañeros de trabajo a encontrar los datos del equipo y analizar los datos en los canales del equipo. 
- Cree una [vista previa del vínculo](service-teams-link-preview.md) cuando pegue un vínculo a los informes, a los paneles y a las aplicaciones en el cuadro de mensaje de Microsoft Teams. La vista previa del vínculo muestra información sobre el vínculo. 
- Use [Chatear en Microsoft Teams](service-share-report-teams.md) al consultar informes y paneles en el servicio Power BI para iniciar conversaciones rápidamente en Microsoft Teams.
- Use la aplicación [Power BI de Microsoft Teams](service-microsoft-teams-app.md) para aportar toda la experiencia del servicio básico de Power BI a Microsoft Teams.
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Captura de pantalla de un informe de Power BI insertado en un canal de Microsoft Teams.":::

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

## <a name="share-with-external-users"></a>Uso compartido con usuarios externos

Puede integrar un informe de Power BI en Teams y compartirlo con usuarios externos. Estos son los pasos que debe seguir.

1.  Hay que invitar al usuario externo a la organización y que este acepte dicha invitación. Vea [Distribuir contenido de Power BI a usuarios externos invitados mediante Azure Active Directory B2B](../guidance/whitepaper-azure-b2b-power-bi.md) para obtener información detallada.
2.  Conceda al usuario externo permiso en el informe. La asignación de permisos individuales es la que mejor funciona.
3.  Asegúrese de que el usuario externo tiene asignada una licencia de Power BI. Si el contenido está en una capacidad Premium, el usuario solo necesita una licencia gratuita; si no, el usuario puede [registrarse para obtener una prueba gratuita individual de Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

- Power BI no admite los mismos idiomas localizados que Microsoft Teams. En consecuencia, es posible que no vea una localización correcta en el informe insertado.
- En la pestaña **Power BI** de Microsoft Teams no se pueden insertar paneles de Power BI.
- Los usuarios que no tengan una licencia o permiso de Power BI para acceder al informe verán el mensaje "El contenido no está disponible".
- Es posible que tenga problemas si usa Internet Explorer 10. <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- La pestaña **Power BI** de Microsoft Teams no admite [filtros de URL](service-url-filters.md).
- En nubes nacionales, la nueva pestaña **Power BI** no está disponible. Puede que haya disponible una versión anterior que no es compatible con la nueva experiencia de área de trabajo o los informes de aplicaciones de Power BI.
- Una vez que se guarde la pestaña, no se podrá cambiar su nombre en la configuración. Para cambiarlo, use la opción **Cambiar nombre**.
- No se admite el inicio de sesión único para el servicio de vista previa de vínculo.
- Las vistas previas de vínculo no funcionan en los canales privados o de chat.

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Power Platform en Microsoft Teams

Las otras aplicaciones de Microsoft Power Platform también se integran con Microsoft Teams.

- [Experiencia de administración de Power Platform](/power-platform/admin/about-teams-environment)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>Pasos siguientes

- [Inserción de contenido de Power BI en Microsoft Teams](service-embed-report-microsoft-teams.md)
- [Obtención de una vista previa del vínculo de Power BI en Microsoft Teams](service-teams-link-preview.md)
- [Chat en Microsoft Teams directamente en el servicio Power BI](service-share-report-teams.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).
