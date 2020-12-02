---
title: Solución de problemas con el uso compartido de paneles e informes
description: Resolución de problemas para compartir paneles e informes de Power BI con colegas dentro y fuera de su organización.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: troubleshooting
ms.date: 06/23/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 89d0ddbbcdd5caf47256fc85864590e55a1caa86
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406679"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>Solución de problemas con el uso compartido de paneles e informes

Estos son algunos problemas comunes que pueden aparecer cuando comparte un panel o un informe, o bien cuando alguien más comparte contenido con usted. 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>Los destinatarios del panel ven un icono de candado en un icono

Las personas con las que comparte puede que vean un icono de bloqueo en un panel o un mensaje "Permisos requeridos" al intentar ver un informe.

![Icono de bloqueo de Power BI](media/service-share-dashboards/power-bi-locked_tile_small.png)

Si es así, debe concederles permiso al conjunto de datos subyacente.

1. Vaya a la pestaña **Conjuntos de datos** en la lista de contenido.

1. Seleccione el símbolo de puntos suspensivos ( **…** ) junto al conjunto de datos y, después, haga clic en **Administrar permisos**.

    ![Administrar permisos](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. Seleccione **Agregar usuario**.

    ![Seleccionar Agregar usuario](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. Escriba las direcciones de correo electrónico completas de las personas, los grupos de distribución o los grupos de seguridad. No se puede compartir con listas de distribución dinámicas.

    ![Agregar direcciones de correo electrónico](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. Seleccione **Agregar**.

## <a name="i-cant-share-a-dashboard-or-report"></a>No se puede compartir un panel o informe

Para compartir un panel o informe, necesita permiso para volver a compartir el contenido subyacente (es decir, los informes y conjuntos de datos relacionados). Si ve un mensaje que indica que no se puede compartir, solicite al autor del informe que le conceda permisos para volver a compartir los informes y los conjuntos de datos.

![Mensaje "No se puede compartir"](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>No tengo acceso a un panel o informe

Si ve un mensaje "Solicitar acceso" cuando selecciona el vínculo a un informe o panel, es porque no tiene permiso para verlo. Debe [solicitar acceso a él](service-request-access.md).

## <a name="next-steps"></a>Pasos siguientes

- [Uso compartido de informes y paneles de Power BI con compañeros y otros usuarios](service-share-dashboards.md)
- [¿Cómo debo compartir paneles e informes y colaborar en ellos?](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [Uso compartido de informes de Power BI con los compañeros](service-share-reports.md)
- ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
