---
title: Uso compartido directo en Teams desde el servicio Power BI
description: Puede compartir informes y paneles de Power BI directamente en Microsoft Teams desde el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/31/2020
ms.openlocfilehash: 0a6f73c14c8dd8ebb48f856f3079ec8f5922ef9e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411572"
---
# <a name="share-directly-to-microsoft-teams-from-the-power-bi-service"></a>Uso compartido directo en Teams desde el servicio Power BI

Puede compartir informes, paneles y objetos visuales de Power BI directamente en Microsoft Teams desde el servicio Power BI. Use la característica **Compartir en Teams** para iniciar conversaciones rápidamente mientras ve informes y paneles en el servicio Power BI.

## <a name="requirements"></a>Requisitos

Para usar la funcionalidad **Compartir en Teams** en Power BI, asegúrese de esta configuración:

- Los administradores de Power BI no han deshabilitado la configuración del inquilino **Compartir en Teams** en el portal de administración de Power BI. Este valor permite a las organizaciones ocultar los botones **Compartir en Teams**. Vea el artículo del [portal de administración de Power BI](../admin/service-admin-portal.md#share-to-teams) para obtener información.

Vea [Colaboración en Microsoft Teams con Power BI](service-collaborate-microsoft-teams.md) para obtener información sobre el funcionamiento conjunto de Power BI y Microsoft Teams, incluidos otros requerimientos.

## <a name="share-power-bi-content-to-microsoft-teams"></a>Uso compartido de contenido de Power BI con Microsoft Teams

Siga estos pasos para compartir vínculos a informes, paneles y objetos visuales del servicio Power BI en canales y chats de Microsoft Teams.

1. Seleccione una de estas opciones:

   * **Compartir en Teams** en la barra de acciones de un panel o informe:

       ![Captura de pantalla del botón Compartir en Teams en la barra de acciones.](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Compartir en Teams** en el menú contextual de un objeto visual:
    
      ![Captura de pantalla del botón Compartir en Teams en el menú contextual de un objeto visual.](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. En el cuadro de diálogo **Compartir en Microsoft Teams**, seleccione el equipo o el canal a los que quiera enviar el vínculo. Si lo desea, puede escribir un mensaje. Es posible que se le pida que inicie sesión primero en Microsoft Teams.

    ![Captura de pantalla del cuadro de diálogo Compartir en Microsoft Teams con información y mensaje.](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. Seleccione **Compartir** para enviar el vínculo.
    
1. El vínculo se agrega a las conversaciones existentes o inicia un nuevo chat.

    ![Captura de pantalla de la conversación de Microsoft Teams con vínculo a un elemento de Power BI.](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. Seleccione el vínculo para abrir el elemento en el servicio Power BI.

1. Si usa el menú contextual para un determinado objeto visual, este se resaltará cuando se abra el informe.

    ![Captura de pantalla del informe de Power BI abierto con un objeto visual específico resaltado.](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

- Los usuarios que no tengan una licencia o permiso de Power BI para acceder al informe verán el mensaje "El contenido no está disponible".
- Es posible que los botones de **Compartir en Teams** no funcionen si el explorador usa una configuración de privacidad estricta. Use la opción **¿Ha encontrado algún problema? Intente abrir en una nueva ventana** si el cuadro de diálogo no se abre correctamente.
- **Compartir en Teams** no incluye una vista previa de vínculo.
- Las vistas previas de vínculos y **Compartir en Teams** no conceden permisos a los usuarios para ver el elemento. Los permisos deben administrarse por separado.
- El botón **Compartir en Teams** no está disponible en los menús contextuales de los objetos visuales cuando el autor de un informe establece **Más opciones** en **Desactivado** para el objeto visual.
- Vea la sección [Limitaciones y problemas conocidos](service-collaborate-microsoft-teams.md#known-issues-and-limitations) del artículo "Colaboración en Microsoft Teams" para obtener información sobre otros problemas.

## <a name="next-steps"></a>Pasos siguientes

- [Colaboración en Microsoft Teams con Power BI](service-collaborate-microsoft-teams.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).
