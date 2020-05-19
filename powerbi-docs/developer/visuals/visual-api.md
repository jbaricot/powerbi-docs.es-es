---
title: API de objeto visual
description: En este artículo se describe cómo usar la API de objeto visual para objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 6ec30fdd4812427ae855ff9a167d946d2a415c28
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302975"
---
# <a name="visual-api"></a>API de objeto visual
Todos los objetos visuales empiezan con una clase que implementa la interfaz `IVisual`. Puede asignar cualquier nombre a la clase siempre que haya exactamente una clase que implemente la interfaz `IVisual`.

> [!NOTE]
> El nombre de clase del objeto visual debe coincidir con lo que se define en el archivo *pbiviz.json*.

Vea la clase del objeto visual de ejemplo con los siguientes métodos que deben implementarse:

* `constructor`, un constructor estándar para inicializar el estado del objeto visual.
* `update`, para actualizar los datos del objeto visual.
* `enumerateObjectInstances`, para devolver los objetos para rellenar el panel de propiedades (opciones de formato), donde puede modificarlos según sea necesario.
* `destroy`, un destructor estándar para la limpieza.

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>constructor

Se llama al constructor de la clase del objeto visual cuando se crea una instancia del objeto visual. Se puede usar para cualquier operación de configuración que el objeto visual necesite.

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`, una referencia al elemento DOM que contendrá el objeto visual.
* `host: IVisualHost`, una colección de propiedades y servicios que se pueden usar para interactuar con el host del objeto visual (Power BI).

   `IVisualHost` contiene los servicios siguientes:

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`, genera y almacena los metadatos de los elementos seleccionables en el objeto visual.
   * `createSelectionManager`, crea el puente de comunicación que se usa para notificar al host del objeto visual los cambios en el estado de selección (consulte [API de selección](./selection-api.md)).
   * `createLocalizationManager`, genera un administrador para ayudar con la [localización](./localization.md).
   * `allowInteractions: boolean`, una marca booleana que sugiere si el objeto visual debe ser interactivo o no.
   * `applyJsonFilter`, aplica tipos de filtro específicos (consulte [API de filtros](./filter-api.md)).
   * `persistProperties`, permite a los usuarios conservar las propiedades y guardarlas junto con la definición del objeto visual, por lo que están disponibles en la siguiente recarga.
   * `eventService`, devuelve un [servicio de eventos](./event-service.md) para admitir eventos **Representar**.
   * `storageService`, devuelve un servicio para ayudar a usar el [almacenamiento local](./local-storage.md) en el objeto visual.
   * `authenticationService`, genera un servicio para ayudar con la autenticación de usuario.
   * `tooltipService`, devuelve un [servicio de información sobre herramientas](./add-tooltips.md) para ayudarle a usar informaciones sobre herramientas en el objeto visual.
   * `launchUrl`, ayuda a la [dirección URL de inicio](./launch-url.md) en la pestaña siguiente.
   * `locale`, devuelve una cadena de configuración regional (consulte [Localización](./localization.md)).
   * `instanceId`, devuelve una cadena para identificar la instancia del objeto visual actual.
   * `colorPalette`, devuelve el colorPalette que se necesita para aplicar colores a los datos.
   * `fetchMoreData`, admite el uso de más datos que el límite estándar (1000 filas).
   * `switchFocusModeState`, ayuda a cambiar el estado del modo de enfoque.

## <a name="update"></a>update

Todos los objetos visuales deben implementar un método public update al que se llama cada vez que hay un cambio en los datos o en el entorno de host.

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`, dimensiones de la ventanilla en la que se debe representar el objeto visual.
* `dataViews: DataView[]`, el objeto visual de vista de datos que contiene todos los datos necesarios para representar el objeto visual (el objeto visual normalmente usará la propiedad de categoría en DataView).
* `type: VisualUpdateType`, marcas para indicar los tipos de esta actualización (**Data** | **Resize** | **ViewMode** | **Style** | **ResizeEnd**).
* `viewMode: ViewMode`, marcas para indicar el modo de vista del objeto visual (**View** | **Edit** | **InFocusEdit**).
* `editMode: EditMode`, marca para indicar el modo de edición del objeto visual (**Default** | **Advanced**) (si el objeto visual admite **AdvancedEditMode**, debe representar sus controles de interfaz de usuario avanzados solo cuando **editMode** está establecido en **Advanced**; consulte [AdvancedEditMode](./advanced-edit-mode.md)).
* `operationKind?: VisualDataChangeOperationKind`, marca para indicar el tipo de cambio de datos (**Create** | **Append**).
* `jsonFilters?: IFilter[]`, colección de filtros json aplicados.
* `isInFocus?: boolean`, marca para indicar si el objeto visual está en modo de enfoque o no.
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

Se llama a este método para cada objeto que se enumera en las funcionalidades. Mediante las opciones (actualmente solo el nombre) se devuelve `VisualObjectInstanceEnumeration` con información sobre cómo mostrar esta propiedad.

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`, nombre del objeto.

## <a name="destroy-optional"></a>destroy `optional`

Se llama a la función destroy cuando el objeto visual se descarga y se puede usar para realizar tareas de limpieza, como quitar agentes de escucha de eventos.

``` typescript
public destroy(): void
```

> [!Note]
> Por lo general, Power BI no llama a `destroy` porque es más rápido quitar todo el IFrame que contiene el objeto visual.
