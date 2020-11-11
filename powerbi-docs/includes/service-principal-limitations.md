---
title: Limitaciones de la entidad de servicio
description: Limitaciones de la entidad de servicio
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: f55cf56edbc26d58dcfb5d67f46a908625ebcf30
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94424807"
---
## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* La entidad de servicio solo funciona con [áreas de trabajo nuevas](../collaborate-share/service-create-the-new-workspaces.md).
* Cuando se usa la entidad de servicio, no se admite **Mi área de trabajo**.
* Para pasar a producción, se necesita una capacidad.
* No se puede iniciar sesión en el portal de Power BI con la entidad de servicio.
* Se necesitan derechos de administrador de Power BI para habilitar la entidad de servicio en la configuración de desarrollador en el portal de administración de Power BI.
* Las aplicaciones de [inserción para la organización](../developer/embedded/embed-sample-for-your-organization.md) no pueden usar la entidad de servicio.
* No se admite la administración de [flujos de datos](../transform-model/dataflows/dataflows-introduction-self-service.md).
* Actualmente la entidad de servicio no admite ninguna API de administración.
* Al usar una entidad de servicio con un origen de datos de [Azure Analysis Services](/azure/analysis-services/analysis-services-overview), la propia entidad de servicio debe tener permisos de una instancia de Azure Analysis Services. El uso de un grupo de seguridad que contiene la entidad de servicio para este propósito no funciona.