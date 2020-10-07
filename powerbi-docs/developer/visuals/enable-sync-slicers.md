---
title: Habilitación de la característica Segmentaciones de sincronización en objetos visuales de Power BI
description: En este artículo se describe cómo agregar la característica Segmentaciones de sincronización a objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 4e9989bb7a34a89cb6244a2378d6660a5079fc82
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748112"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Segmentaciones de sincronización en objetos visuales de Power BI

Para admitir la característica [Segmentaciones de sincronización](../../visuals/power-bi-visualization-slicers.md), el objeto visual de segmentación personalizado debe usar la versión de API 1.13.0 o posterior.

Además, debe habilitar la opción en el archivo *capabilities.json*, tal y como se muestra en el código siguiente:

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

Después de actualizar el archivo *capabilities.json*, puede ver el panel de opciones **Segmentaciones de sincronización** al seleccionar el objeto visual de segmentación personalizado.

> [!NOTE]
> La característica Segmentaciones de sincronización no admite más de un campo. Si su segmentación tiene más de un campo (**Categoría** o **Medida**), la característica se deshabilita.

![Panel "Segmentaciones de sincronización"](media/enable-sync-slicers/sync-slicers-panel.png)

En el panel **Segmentaciones de sincronización**, puede ver que la visibilidad de la segmentación y su filtración se pueden aplicar en varias páginas del informe.