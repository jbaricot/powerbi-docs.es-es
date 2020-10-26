---
title: Adición de colores a los objetos visuales de Power BI
description: En este artículo se describe cómo agregar colores a los objetos visuales de Power BI y cómo controlar los puntos de datos de un objeto visual con color.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: 3a68f3dedbef9e97b6c29d3a0923d43872a5f01a
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048818"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>Adición de colores a los objetos visuales de Power BI

En este artículo se describe cómo agregar colores a los objetos visuales y cómo controlar los puntos de datos de un objeto visual de color.

`IVisualHost` expone el color como uno de sus servicios.
En el código de ejemplo de este artículo se modifica el [objeto visual SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).
Para ver el código fuente, consulte [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts).

Para empezar a crear objetos visuales, vea [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md).

## <a name="add-color-to-data-points"></a>Adición de color a puntos de datos

Cada punto de datos viene representado por un color diferente.
Agregue el color a la interfaz `BarChartDataPoint`, como en el ejemplo siguiente:

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>Uso del servicio de la paleta de colores

El servicio `colorPalette` administra los colores usados en el objeto visual.
Una instancia del servicio está disponible en `IVisualHost`.

Defínala en el método `update`.

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>Asignación de color a los puntos de datos

Luego, especifique `dataPoints`.
En este ejemplo, cada uno de los elementos `dataPoints` incluye el valor, la categoría y el color.
`dataPoints` también puede incluir otras propiedades.

En `SampleBarChart`, el método `visualTransform` encapsula el cálculo de `dataPoints`.
Ese método forma parte del modelo de vista de gráfico de barras.
Dado que el método recorre en iteración el cálculo de `dataPoints` en `visualTransform`, es el lugar ideal para asignar colores, como en el código siguiente:

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

A continuación, aplique los datos de `dataPoints` en la selección de [d3](https://d3js.org/) `barSelection` dentro del método `update`:

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre los objetos visuales de Power BI, consulte [Funcionalidades y propiedades de objetos visuales de Power BI](capabilities.md).

Para más información sobre el desarrollo de objetos visuales de Power BI, consulte [Depuración de objetos visuales de Power BI](visuals-how-to-debug.md) y [Solución de problemas con los objetos visuales de Power BI](power-bi-custom-visuals-troubleshoot.md).
