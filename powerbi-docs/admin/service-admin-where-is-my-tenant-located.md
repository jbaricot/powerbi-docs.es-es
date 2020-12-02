---
title: ¿Dónde se encuentra mi inquilino de Power BI?
description: Obtenga información sobre dónde se encuentra su inquilino de Power BI y cómo se selecciona esa ubicación. Es importante saber esto, ya que puede afectar las interacciones que tiene con el servicio.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Administration
ms.openlocfilehash: 632eca1fdcb1bed380ad699a36264bc0239baef5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412400"
---
# <a name="where-is-my-power-bi-tenant-located"></a>¿Dónde se encuentra mi inquilino de Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Obtenga información sobre dónde se encuentra su inquilino de Power BI y cómo se selecciona esa ubicación. Saber la ubicación es importante, ya que puede afectar las interacciones que tiene con el servicio.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Cómo determinar dónde se encuentra el inquilino de Power BI

Para buscar la región en la que se encuentra su inquilino, siga estos pasos.

1. En el servicio Power BI, en el menú superior, seleccione Ayuda ( **?** ) y, a continuación, **Acerca de Power BI**.

1. Busque el valor situado junto a **Los datos están almacenados en**. Es la región donde se encuentra el inquilino. El valor también es la región donde se almacenan los datos, a menos que use capacidades de otras regiones para las áreas de trabajo.

    ![Región de datos](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Cómo se selecciona la región de datos

La región de datos se basa en el país o la región que seleccione al crear el inquilino. La selección se aplica para suscribirse a Microsoft 365 y Power BI, porque esta información se comparte. Si se trata de un inquilino nuevo, seleccione el país o la región correspondiente en la lista cuando se registre.

![Selección de país](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI selecciona una región de datos más cercana a su selección, que determina dónde se almacenan los datos del inquilino.

> [!IMPORTANT]
> No se puede cambiar la selección después de crear el inquilino.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
