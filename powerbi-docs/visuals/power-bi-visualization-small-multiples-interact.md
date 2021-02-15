---
title: Interactuación con múltiplos pequeños en Power BI (versión preliminar)
description: En este artículo se explica cómo interactuar con múltiplos pequeños o entramados.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 6d700d4a4bb7453f7630c76c5a3f265ee022e02a
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628246"
---
# <a name="interact-with-small-multiples-in-power-bi-preview"></a>Interactuación con múltiplos pequeños en Power BI (versión preliminar)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Los múltiplos pequeños, o entramados, dividen un objeto visual en varias versiones de sí mismo. En este artículo se explica cómo sacar el máximo partido de la interacción con ellos.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Captura de pantalla de múltiplos pequeños para categoría y región":::

¿Quiere crear múltiplos pequeños? Vea [Creación de múltiplos pequeños en Power BI (versión preliminar)](power-bi-visualization-small-multiples.md).

## <a name="scroll-in-a-small-multiple"></a>Desplazarse en un múltiplo pequeño

Los múltiplos pequeños pueden contener más gráficos individuales de los que caben en la cuadrícula. Si es así, puede desplazarse hacia abajo para ver el resto de las categorías.

Para un eje X de categorías con muchas categorías, también verá una barra de desplazamiento para cada copia de ese eje. Al desplazarse por ese eje, se mueven todos juntos. Si utiliza la rueda del mouse, mantenga presionada la tecla Mayús para desplazarse por los ejes de categorías.

## <a name="select-data-to-cross-highlight"></a>Selección de datos para el resaltado cruzado

Puede seleccionar diferentes subconjuntos de datos seleccionando diferentes partes del objeto visual.

### <a name="select-data-points"></a>Selección de puntos de datos

Mantenga el mouse sobre el punto de datos de un múltiplo para mostrar la información sobre herramientas de ese múltiplo. También verá una línea guía en el eje X para los gráficos de líneas. Seleccione ese punto de datos para el resaltado cruzado de otros objetos visuales según el valor del eje y la categoría de múltiplos pequeños, y para atenuar los otros múltiplos.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-data-point.png" alt-text="Seleccionar un punto de datos en un múltiplo pequeño":::

### <a name="select-a-categorical-axis-value"></a>Selección de un valor del eje de categorías

Seleccione una etiqueta de categoría para resaltar de forma cruzada otros objetos visuales según ese valor del eje.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-category-axis.png" alt-text="Seleccionar un eje de categorías en un múltiplo pequeño":::

### <a name="select-a-title"></a>Selección de un título

Seleccione el título de un múltiplo para resaltar de forma cruzada otros objetos visuales por la categoría de ese subencabezado.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-title.png" alt-text="Seleccionar un título en un múltiplo pequeño":::

### <a name="legend"></a>Leyenda

Seleccione una categoría de leyenda para resaltar de forma cruzada otros objetos visuales y también otros múltiplos.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-legend.png" alt-text="Seleccionar un elemento en la leyenda de un múltiplo pequeño":::


## <a name="sort"></a>Sort

Con la nueva funcionalidad de ordenación, puede ordenar varios aspectos de un objeto visual al mismo tiempo. Ordene por categoría, y también por el eje de cada múltiplo. 

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-sort.png" alt-text="Ordenar los múltiplos pequeños":::

## <a name="next-steps"></a>Pasos siguientes

[Creación de múltiplos pequeños en Power BI (versión preliminar)](power-bi-visualization-small-multiples.md)
