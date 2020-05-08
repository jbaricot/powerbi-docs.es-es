---
title: Utilidades de interactividad de objetos visuales de Power BI
description: En el artículo se describe cómo agregar selecciones en objetos visuales de Power BI mediante el uso de utilidades de interactividad
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: f4d47347c98d19afdfbf07615842bfb4649dc1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379269"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Utilidades de interactividad de objetos visuales de Power BI

Las utilidades de interactividad (`InteractivityUtils`) son un conjunto de funciones y clases que se pueden usar para simplificar la implementación de selección cruzada y filtrado cruzado.

> [!NOTE]
> Las actualizaciones nuevas de las utilidades de interactividad solo admiten la versión más reciente de las herramientas (3.x.x y superior).

## <a name="installation"></a>Instalación

1. Para instalar el paquete, ejecute el comando siguiente en el directorio con el proyecto visual actual de Power BI.

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. Si usa la versión 3.0 o posterior o la herramienta, instale `powerbi-models` para resolver las dependencias.

    ```bash
    npm install powerbi-models --save
    ```

3. Para usar las utilidades de interactividad, importe el componente necesario en el código fuente del objeto visual de Power Bi.

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>Inclusión de los archivos CSS

Para usar el paquete con el objeto visual de Power BI, importe el siguiente archivo CSS al archivo `.less`.

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

Importe el archivo CSS como un archivo `.less`, ya que la herramienta de objetos visuales de Power BI encapsula reglas de CSS externas.

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>Propiedades de SelectableDataPoint

Por lo general, los puntos de datos contienen selecciones y valores. La interfaz extiende la interfaz de `SelectableDataPoint`.

`SelectableDataPoint` ya contiene propiedades como se describe a continuación.

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>Definición de una interfaz para puntos de datos

1. Cree una instancia de utilidades de interactividad y guarde el objeto como una propiedad del objeto visual.

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. Extienda la clase de comportamiento base.

    > [!NOTE]
    > `BaseBehavior` se introdujo en la [versión 5.6. x de las utilidades de interactividad](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0). Si usa una versión anterior, cree una clase de comportamiento en el ejemplo siguiente.

3. Defina la interfaz para las opciones de clase de comportamiento.

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. Defina una clase para `visual behavior`. O bien, extienda la clase `BaseBehavior`.

    **Definición de una clase para `visual behavior`**

    La clase es responsable de administrar los eventos de mouse `click`, `contextmenu`.

    Cuando un usuario hace clic en los elementos de datos, el objeto visual llama al controlador de selección para seleccionar puntos de datos. Si el usuario hace clic en el elemento de fondo del objeto visual, llama al controlador para borrar la selección.

    La clase tiene los siguientes métodos correspondientes:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **Extensión de la clase `BaseBehavior`** 

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. Para controlar la acción de hacer clic en los elementos, llame al método *del objeto de selección*d3`on`. Esto también se aplica a `elementsSelection` y `clearCatcherSelection`.

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. Agregue un controlador similar para el evento `contextmenu`, para llamar al método `showContextMenu` del administrador de selección.

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. Para asignar funciones a los controladores, las utilidades de interactividad llaman al método `bindEvents`. Agregue las siguientes llamadas al método `bindEvents`:
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. El método `renderSelection` es responsable de actualizar el estado del objeto visual de los elementos del gráfico. Este es un ejemplo de implementación de `renderSelection`.

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. El último paso es crear una instancia de `visual behavior` y llamar al método `bind` de la instancia de utilidades de interactividad.

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` es el objeto de selección *d3*, que representa todos los elementos seleccionables del objeto visual.
    * `select(this.target)` es el objeto de selección *d3*, que representa los elementos DOM principales del objeto visual.
    * `this.categories` son puntos de datos con elementos, donde la interfaz es `VisualDataPoint` o `categories: VisualDataPoint[];`.
    * `this.behavior` es una nueva instancia de `visual behavior` creada en el constructor del objeto visual, como se muestra a continuación.

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>Pasos siguientes

* [Lea cómo controlar las selecciones en el cambio de marcadores](bookmarks-support.md#visuals-with-selection).

* [Lea cómo agregar un menú contextual para los puntos de datos de objetos visuales](context-menu.md).

* [Lea cómo usar el administrador de selección para agregar selecciones a los objetos visuales de Power BI](selection-api.md)
