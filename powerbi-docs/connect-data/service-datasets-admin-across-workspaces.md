---
title: 'Control del uso de conjuntos de datos entre áreas de trabajo: Power BI'
description: Obtenga información sobre cómo restringir el flujo de información en el inquilino de Power BI.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 6cc602b96207b1662f0738c0936ca816bbfd0a03
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2020
ms.locfileid: "92681052"
---
# <a name="control-the-use-of-datasets-across-workspaces"></a>Control del uso de conjuntos de datos entre áreas de trabajo

El uso de conjuntos de datos entre áreas de trabajo es una manera eficaz de impulsar la cultura y la democratización de los datos dentro de una organización. Pero si es un administrador de Power BI, a veces le interesará restringir el flujo de información dentro del inquilino de Power BI. Con la configuración del inquilino **Uso de conjuntos de datos entre áreas de trabajo** , puede restringir la reutilización de los conjunto de datos de forma completa o parcial por grupos de seguridad.

![Configuración del área de trabajo del administrador de Power BI](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

Si desactiva esta configuración, estos son los efectos en los creadores de informes:

- El botón para copiar informes entre áreas de trabajo no está disponible. 
- En un informe basado en un conjunto de datos compartido, el botón **Editar informe** no está disponible.
- En el servicio Power BI, la experiencia de detección solo muestra los conjuntos de datos del área de trabajo actual.
- En Power BI Desktop, la experiencia de detección solo muestra los conjuntos de datos de las áreas de trabajo de las que sea miembro.
- En Power BI Desktop, si los usuarios abren un archivo .pbix con una conexión dinámica a un conjunto de datos fuera de las áreas de trabajo de la que son miembros, verán un mensaje de error en el que se les pide que se conecten a otro conjunto de datos.

## <a name="provide-a-link-for-the-certification-process"></a>Inclusión de un vínculo para el proceso de certificación

Como administrador de Power BI, puede proporcionar una dirección URL para el vínculo **Más información** de la página de configuración **Aprobación** .  Vea [Habilitación de la certificación de contenido](../admin/service-admin-setup-certification.md) para obtener detalles. Este vínculo puede ir a la documentación sobre el proceso de certificación. Si no proporciona un destino para el vínculo **Más información** , de forma predeterminada apuntará al artículo sobre [Aprobación del contenido](../collaborate-share/service-endorse-content.md).

![Más información de la certificación del conjunto de datos](media/service-datasets-admin-across-workspaces/service-admin-certification-setup-dialog.png)

## <a name="next-steps"></a>Pasos siguientes

- [Uso de conjuntos de datos entre áreas de trabajo](service-datasets-across-workspaces.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
