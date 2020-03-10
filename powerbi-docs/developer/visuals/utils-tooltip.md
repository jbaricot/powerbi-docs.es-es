---
title: Introducción al uso de las utilidades de información sobre herramientas en los objetos visuales de Power BI
description: En este artículo se describe cómo usar las utilidades de información sobre herramientas para simplificar la personalización de la información sobre herramientas para objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 6f4aa276438d84825c4c7aba6872210b5f3a6564
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2020
ms.locfileid: "78264229"
---
# <a name="tooltip-utils"></a>Utilidades de la información sobre herramientas
Este artículo le ayudará a instalar, importar y usar las utilidades de la información sobre herramientas. La resultará útil para cualquier personalización de la información sobre herramientas en objetos visuales de Power BI.

## <a name="requirements"></a>Requisitos
Para usar el paquete, debe tener lo siguiente:
* [node.js](https://nodejs.org) (se recomienda la versión más reciente de LTS).
* [npm](https://www.npmjs.com/) (la versión mínima admitida es 3.0.0).
* El objeto visual personalizado creado por [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools).

## <a name="installation"></a>Instalación

Para instalar el paquete, debe ejecutar el comando siguiente en el directorio con el objeto visual actual:

```bash
npm install powerbi-visuals-utils-colorutils --save
```
Este comando instala el paquete y agrega un paquete como una dependencia a su ```package.json```.

## <a name="usage"></a>Uso

> La guía de uso describe una API pública del paquete. Encontrará una descripción y algunos ejemplos de cada interfaz pública del paquete.

Este paquete contiene la manera de crear `TooltipServiceWrapper` y métodos para ayudar a controlar las acciones de la información sobre herramientas. Usa interfaces de información sobre herramientas: `ITooltipServiceWrapper`, `TooltipEventArgs`, `TooltipEnabledDataPoint`. 

También tiene métodos específicos (controladores de eventos táctiles) relacionados con el desarrollo móvil: `touchEndEventName`, `touchStartEventName`, `usePointerEvents`.

`TooltipServiceWrapper` proporciona la manera más sencilla de manipular la información sobre herramientas.

Este módulo proporciona la siguiente interfaz y función:
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [Interfaces](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [Touch events](#touch-events)

### `createTooltipServiceWrapper`
Esta función crea una instancia de ITooltipServiceWrapper.

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

```ITooltipService``` está disponible en [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335).

**Ejemplo**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

[Aquí](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391) puede echar un vistazo al código de ejemplo del objeto visual personalizado.

### `ITooltipServiceWrapper`
Esta interfaz describe los métodos públicos de TooltipService.

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

Este método agrega información sobre herramientas a la selección actual.

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**Ejemplo**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

[Aquí](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931) puede echar un vistazo al código de ejemplo del objeto visual personalizado.

Además, preste atención al siguiente ejemplo de personalización de la información sobre herramientas en el objeto personalizado de Gantt [aquí](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648).

### `ITooltipServiceWrapper.hide`

Este método oculta la información sobre herramientas.

```typescript
hide(): void;
```

**Ejemplo**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
Estas interfaces se usan durante la creación de TooltipServiceWrapper y su uso. También se han mencionado en ejemplos del tema anterior [aquí](#itooltipservicewrapperaddtooltip).

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

Ahora,las utilidades de la información sobre herramientas tienen la capacidad de administrar varios eventos táctiles útiles para el desarrollo móvil.

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
Este método devuelve el nombre de evento de inicio táctil.

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
Este método devuelve el nombre de evento de inicio táctil.

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
Este método devuelve el evento touchStart actual relacionado con el puntero (o no).
