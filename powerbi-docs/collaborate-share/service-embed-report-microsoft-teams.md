---
title: Inserción de informes de Power BI en Microsoft Teams
description: Puede insertar fácilmente informes interactivos de Power BI en canales y chats de Microsoft Teams. .
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 09/21/2020
ms.openlocfilehash: 0abaf886806ea783bb478f47d020daeea7829da5
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965131"
---
# <a name="embed-power-bi-content-in-microsoft-teams"></a>Inserción de contenido de Power BI en Microsoft Teams

Puede insertar fácilmente informes interactivos de Power BI en canales y chats de Microsoft Teams. 

## <a name="requirements"></a>Requisitos

Para usar la pestaña **Power BI** de Microsoft Teams, asegúrese de lo siguiente:

- Microsoft Teams tiene la pestaña **Power BI**.
- Para agregar un informe en Microsoft Teams con la pestaña **Power BI**, tiene como mínimo un rol de visor en el área de trabajo en la que se hospeda el informe. Consulte [Roles en las nuevas áreas de trabajo](service-new-workspaces.md#roles-in-the-new-workspaces) para obtener información sobre los distintos roles.
- Para ver el informe en la pestaña **Power BI** de Microsoft Teams, los usuarios deben tener permiso para ver el informe.
- Los usuarios deben ser usuarios de Microsoft Teams con acceso a canales y chats.

Vea [Colaboración en Microsoft Teams con Power BI](service-embed-report-microsoft-teams.md) para obtener información sobre el funcionamiento conjunto de Power BI y Microsoft Teams, incluidos otros requerimientos.

## <a name="embed-a-report-in-microsoft-teams"></a>Inserción de un informe en Microsoft Teams

Siga estos pasos para insertar el informe en un canal o un chat de Microsoft Teams.

1. Abra un canal o un chat en Microsoft Teams y seleccione el icono **+** .

    ![Captura de pantalla de la adición de una pestaña a un canal o chat.](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

1. Seleccione la pestaña **Power BI**.

    ![Captura de pantalla de la lista de pestañas de Microsoft Teams en la que se muestra Power BI.](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

1. Use las opciones proporcionadas para elegir un informe de un área de trabajo o una aplicación de Power BI.

    ![Captura de pantalla de la pestaña de Power BI para la configuración de Microsoft Teams.](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

1. El nombre de la pestaña se actualiza automáticamente para que coincida con el nombre del informe, pero puede cambiarlo.

1. Seleccione **Guardar**.

### <a name="reports-you-can-embed-on-the-power-bi-tab"></a>Informes que puede insertar en la pestaña Power BI

Puede insertar los siguientes tipos de informes en la pestaña **Power BI**:

- Informes paginados e interactivos.
- Informes de **Mi área de trabajo**, de una nueva experiencia de área de trabajo y de áreas de trabajo clásicas.
- Informes de aplicaciones de Power BI.

## <a name="start-a-conversation"></a>Iniciar una conversación

Cuando se agrega una pestaña de informe de Power BI a Microsoft Teams, esta aplicación crea de forma automática una pestaña de conversación para el informe.

- Seleccione el icono**Mostrar la ficha Conversación** en la esquina superior derecha.

    ![Captura de pantalla del icono Mostrar la ficha Conversación.](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    El primer comentario es un vínculo al informe. Todos los usuarios de ese canal de Microsoft Teams pueden ver y analizar el informe en la conversación.

    ![Captura de pantalla de la pestaña Conversación.](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>Limitaciones y problemas conocidos

- En Microsoft Teams, cuando se exportan datos de un objeto visual en un informe de Power BI, estos se guardan automáticamente en la carpeta de descargas. Se trata de un archivo de Excel denominado "data (*n*).xlsx", donde *n* es el número de veces que ha exportado los datos en la misma carpeta.
- En la pestaña **Power BI** de Microsoft Teams no se pueden insertar paneles de Power BI.
- La pestaña **Power BI** de Microsoft Teams no admite [filtros de URL](service-url-filters.md).
- En nubes nacionales, la nueva pestaña **Power BI** no está disponible. Puede que haya disponible una versión anterior que no es compatible con la nueva experiencia de área de trabajo o los informes de aplicaciones de Power BI.
- Después de guardar la pestaña, no cambie el nombre en la configuración. Para cambiarlo, use la opción **Cambiar nombre**.
- Vea la sección [Limitaciones y problemas conocidos](service-collaborate-microsoft-teams.md#known-issues-and-limitations) del artículo "Colaboración en Microsoft Teams" para obtener información sobre otros problemas.

## <a name="next-steps"></a>Pasos siguientes

- [Colaboración en Microsoft Teams con Power BI](service-collaborate-microsoft-teams.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).
