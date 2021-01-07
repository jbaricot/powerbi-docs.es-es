---
title: Chat en Microsoft Teams directamente en el servicio Power BI
description: Puede compartir informes y paneles de Power BI directamente en Microsoft Teams desde el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 01/04/2020
ms.openlocfilehash: 63ea4772610bd7112823f38c66abced1f0654b77
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926967"
---
# <a name="chat-in-microsoft-teams-directly-from-the-power-bi-service"></a>Chat en Microsoft Teams directamente en el servicio Power BI

Puede chatear sobre informes, paneles y objetos visuales de Power BI directamente en Microsoft Teams desde el servicio Power BI. Use la característica **Chatear en Teams** para iniciar conversaciones rápidamente mientras consulta informes y paneles en el servicio Power BI.

## <a name="requirements"></a>Requisitos

Para usar la funcionalidad **Chatear en Teams** en Power BI, asegúrese de que el administrador de Power BI no haya deshabilitado la opción de configuración del inquilino **Compartir en Teams** en el portal de administración de Power BI. Este valor permite a las organizaciones ocultar los botones **Chatear en Teams**. Vea el artículo del [portal de administración de Power BI](../admin/service-admin-portal.md#share-to-teams) para obtener información.

Vea [Colaboración en Microsoft Teams con Power BI](service-collaborate-microsoft-teams.md) para obtener información sobre el funcionamiento conjunto de Power BI y Microsoft Teams, incluidos otros requerimientos.

## <a name="chat-about-power-bi-content-in-microsoft-teams"></a>Chat sobre el contenido de Power BI en Microsoft Teams

Siga estos pasos para compartir vínculos a informes, paneles y objetos visuales del servicio Power BI, y chatear en los canales y chats de Microsoft Teams.

1. Seleccione una de estas opciones:

   * **Chatear en Teams** en la barra de acciones de un panel o informe:

       ![Captura de pantalla del botón Chatear en Teams en la barra de acciones.](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * **Chatear en Teams** en el menú contextual de un objeto visual:
    
      ![Captura de pantalla del botón Chatear en Teams en el menú contextual de un objeto visual.](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

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
- Es posible que los botones de **Chatear en Teams** no funcionen si el explorador usa una configuración de privacidad estricta. Use la opción **¿Ha encontrado algún problema? Intente abrir en una nueva ventana** si el cuadro de diálogo no se abre correctamente.
- **Chatear en Teams** no incluye una vista previa de los vínculos.
- Las vistas previas de los vínculos y **Chatear en Teams** no conceden permisos a los usuarios para ver el elemento. Los permisos deben administrarse por separado.
- El botón **Chatear en Teams** no está disponible en los menús contextuales de los objetos visuales cuando el autor de un informe establece **Más opciones** en **Desactivado** para el objeto visual.
- Vea la sección [Limitaciones y problemas conocidos](service-collaborate-microsoft-teams.md#known-issues-and-limitations) del artículo "Colaboración en Microsoft Teams" para obtener información sobre otros problemas.

## <a name="next-steps"></a>Pasos siguientes

- [Colaboración en Microsoft Teams con Power BI](service-collaborate-microsoft-teams.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).
