---
title: Introducción al uso de utilidades de prueba en objetos visuales de Power BI
description: En este artículo se describe cómo usar las utilidades de prueba para simplificar el uso de elementos ficticios y métodos específicos en pruebas unitarias de objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: c50ad894b2e1f5eb838abdd4442f473f8bcbbb10
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196615"
---
# <a name="power-bi-visuals-test-utils"></a>Utilidades de prueba en objetos visuales de Power BI

Este artículo le ayuda a instalar, importar y usar las utilidades de prueba en objetos visuales de Power BI. Estas utilidades de prueba se pueden usar para las pruebas unitarias e incluyen elementos ficticios y métodos para componentes como vistas de datos, selecciones y esquemas de color.

## <a name="requirements"></a>Requisitos

Para usar este paquete, deberá instalar lo siguiente:

* [node.js](https://nodejs.org) (se recomienda usar la versión de LTS).
* [npm](https://www.npmjs.com/), versión 3.0.0 o posterior.
* El paquete [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools).

## <a name="installation"></a>Instalación

Para instalar las utilidades de prueba y agregar su dependencia a *package.json*, ejecute el siguiente comando desde el directorio de objetos visuales de Power BI:

```bash
npm install powerbi-visuals-utils-testutils --save
```

A continuación se proporcionan descripciones y ejemplos de la API pública de utilidades de prueba.

## <a name="visualbuilderbase"></a>VisualBuilderBase

Lo usa **VisualBuilder** en pruebas unitarias con los métodos `build`, `update` y `updateRenderTimeout` más usados. 

El método `build` devuelve una instancia creada del objeto visual.

Los métodos `enumerateObjectInstances` y `updateEnumerateObjectInstancesRenderTimeout` son necesarios para comprobar los cambios en el cubo y las opciones de formato.

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> Para obtener más ejemplos, consulte cómo [escribir pruebas unitarias de VisualBuilderBase](./unit-tests-introduction.md#create-a-visual-instance-builder) y un [escenario de uso real de VisualBuilderBase](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts).

## <a name="dataviewbuilder"></a>DataViewBuilder

Lo usa **TestDataViewBuilder**. Este módulo proporciona una clase **CategoricalDataViewBuilder** que se usa en el método `createCategoricalDataViewBuilder`. También especifica las interfaces y los métodos necesarios para trabajar con objetos **DataView** ficticios en pruebas unitarias.

* `withValues` agrega columnas de serie estática, mientras que `withGroupedValues` agrega columnas de serie dinámica.

  No aplique a la vez la serie dinámica y estática en un objeto visual **DataViewCategorical**. Solo puede usarlas juntas en la consulta **DataViewCategorical**, donde se espera que **DataViewTransform** las divida en objetos visuales **DataViewCategorical** independientes.

* `build` devuelve el elemento DataView con metadatos y DataViewCategorical.

  `build` devuelve **Undefined** si la combinación de parámetros no es válida, por ejemplo, si incluye la serie dinámica y estática al compilar el objeto visual **DataView**.

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

Se usa para la creación de objetos **VisualData** en pruebas unitarias. Al colocar datos en cubos de campos de datos, Power BI genera un objeto **DataView** categórico basado en los datos. **TestDataViewBuilder** ayuda a simular la creación de objetos **DataView** categóricos.

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  A continuación se enumeran las interfaces usadas con mayor frecuencia al crear un objeto `testDataView`:

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> Para obtener más ejemplos, consulte cómo [escribir pruebas unitarias de TestDataViewBuilder](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests) y un [escenario de uso real de TestDataViewBuilder](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts).

## <a name="mocks"></a>Objetos ficticios

### <a name="mockivisualhost"></a>MockIVisualHost

Implementa **IVisualHost** para probar objetos visuales de Power BI sin dependencias externas, como el marco de Power BI.

Entre los métodos útiles se incluyen `createSelectionIdBuilder`, `createSelectionManager`, `createLocalizationManager` y las propiedades de captador.

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` crea y devuelve una instancia de **IVisualHost**, más concretamente, **MockIVisualHost**.
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    Ejemplo
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** es una implementación falsa de **IVisualHost** y solo se debe usar con pruebas unitarias.

### <a name="mockicolorpalette"></a>MockIColorPalette

Implementa **IColorPalette** para probar objetos visuales de Power BI sin dependencias externas, como el marco de Power BI.

**MockIColorPalette** proporciona propiedades útiles para comprobar el esquema de color o el modo de contraste alto en pruebas unitarias.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` crea y devuelve una instancia de **IColorPalette**, más concretamente, **MockIColorPalette**.
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    Ejemplo
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** es una implementación falsa de **IColorPalette** y solo se debe usar con pruebas unitarias.

### <a name="mockiselectionid"></a>MockISelectionId

Implementa **ISelectionId** para probar objetos visuales de Power BI sin dependencias externas, como el marco de Power BI.

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` crea y devuelve una instancia de **ISelectionId**, más concretamente, **MockISelectionId**.
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    Ejemplo
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** es una implementación falsa de **ISelectionId** y solo se debe usar con pruebas unitarias.

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

Implementa **ISelectionIdBuilder** para probar objetos visuales de Power BI sin dependencias externas, como el marco de Power BI. 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` crea y devuelve una instancia de **ISelectionIdBuilder**, más concretamente, **MockISelectionIdBuilder**.
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    Ejemplo
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** es una implementación falsa de **ISelectionIdBuilder** y solo se debe usar con pruebas unitarias.

### <a name="mockiselectionmanager"></a>MockISelectionManager

Implementa **ISelectionManager** para probar objetos visuales de Power BI sin dependencias externas, como el marco de Power BI. 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` crea y devuelve una instancia de **ISelectionManager**, más concretamente, **MockISelectionManager**.
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    Ejemplo
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** es una implementación falsa de **ISelectionManager** y solo se debe usar con pruebas unitarias.

### <a name="mockilocale"></a>MockILocale

  Establece la configuración regional y la cambia según sus necesidades durante el proceso de pruebas unitarias.
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` crea y devuelve una instancia de **MockILocale**.
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
Simula el objeto `TooltipService` y lo cambia según sus necesidades durante el proceso de pruebas unitarias.
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` crea y devuelve una instancia de **MockITooltipService**.
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` crea y devuelve una instancia de **MockIAllowInteractions**.
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
Proporciona las capacidades básicas de **LocalizationManager** que se necesitan para las pruebas unitarias.
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` crea y devuelve una instancia de **ILocalizationManager**, más concretamente, **MockILocalizationManager**.
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    Ejemplo
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
Simula el uso de **TelemetryService**.
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  Creación de `MockITelemetryService`.
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
Simula el trabajo de **AuthenticationService** proporcionando un token de AAD ficticio.
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` crea y devuelve una instancia de **IAuthenticationService**, más concretamente, **MockIAuthenticationService**.
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
Permite usar **ILocalVisualStorageService** con el mismo comportamiento que **LocalStorage**.
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` crea y devuelve una instancia de **ILocalVisualStorageService**, más concretamente, **MockIStorageService**.
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` crea y devuelve una instancia de **IVisualEventService**, más concretamente, **MockIEventService**.
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>Utilidades

Las utilidades incluyen métodos auxiliares para las pruebas unitarias en objetos visuales de Power BI, incluidas aplicaciones auxiliares relacionadas con colores, números y eventos.

- `renderTimeout` devuelve el tiempo de espera.
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` ayuda a establecer un accesorio en las pruebas unitarias.
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  Ejemplo
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>Métodos auxiliares relacionados con colores

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  Devuelve la estructura siguiente:

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` compara objetos **RgbColor** analizados desde cadenas de entrada.
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` analiza el color de la cadena de entrada y lo devuelve en la interfaz especificada **RgbColor**.
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>Métodos auxiliares relacionados con números

- `getRandomNumbers` genera un número aleatorio con valores mínimos y máximos. Puede especificar `exceptionList` y proporcionar una función para el cambio del resultado.
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` proporciona una matriz de números aleatorios generados por el método `getRandomNumber` con valores mínimos y máximos especificados.
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>Métodos auxiliares relacionados con eventos
Los métodos siguientes se escriben para la simulación de eventos de páginas web en pruebas unitarias.

- `clickElement` simula un clic en el elemento especificado.
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` devuelve un objeto **Touch** para ayudar a simular un evento táctil.
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` devuelve una lista de eventos **Touch** simulados.
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` devuelve un objeto **MouseEvent**.
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` crea y devuelve un objeto **MouseEvent**.
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>Métodos auxiliares relacionados con eventos D3

Los métodos siguientes se usan para simular eventos D3 en pruebas unitarias.

- `flushAllD3Transitions` obliga a que se completen todas las transiciones D3.

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > Normalmente, las transiciones con retraso cero se ejecutan después de un retraso instantáneo (<10 ms), pero esto puede producir un breve parpadeo si el explorador representa la página dos veces: una vez al final del primer bucle de eventos y otra vez inmediatamente en la primera devolución de llamada del temporizador.
  >
  > Estos parpadeos son más perceptibles en IE y con un gran número de vistas web, y no se recomiendan para iOS.
  > 
  > Si vacía la cola del temporizador al final del primer bucle de eventos, puede ejecutar cualquier transición con retraso cero de inmediato y evitar el parpadeo.

También se incluyen los métodos siguientes:
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Interfaces auxiliares
La interfaz y las enumeraciones siguientes se usan en la función auxiliar.

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>Pasos siguientes

Para escribir pruebas unitarias para objetos visuales de Power BI basados en webpack, y para realizar pruebas unitarias con `karma` y `jasmine`, consulte, por ejemplo, [Tutorial: Adición de pruebas unitarias en proyectos de objetos visuales de Power BI](./unit-tests-introduction.md).
