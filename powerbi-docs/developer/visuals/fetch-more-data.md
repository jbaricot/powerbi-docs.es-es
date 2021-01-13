---
title: Captura de más datos desde Power BI en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se explica cómo habilitar la captura segmentada de grandes conjuntos de datos para objetos visuales de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 12/13/2020
ms.openlocfilehash: 345efe91be1af5ee61d713c576f04657b182ad47
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886313"
---
# <a name="fetch-more-data-from-power-bi"></a>Captura de más datos desde Power BI

La API `fetchMoreData` permite a los objetos visuales de Power BI omitir el límite máximo de una vista de datos de 30 000 filas. Con la nueva versión 3.4 de la API, la funcionalidad de la API `fetchMoreData` se amplía para admitir un nuevo enfoque de carga de fragmentos de datos. Además del enfoque existente que agrega todos los fragmentos solicitados, la API admitirá la carga solo de los fragmentos de datos incrementales.

El nuevo enfoque permite más flexibilidad en la forma de cargar los fragmentos de datos adicionales en el objeto visual. Para mejorar el rendimiento, puede configurar el tamaño del fragmento para que se adapte a su caso de uso.

## <a name="limitations-of-fetchmoredata"></a>Limitaciones de fetchMoreData

* El tamaño de la ventana está limitado a un intervalo de 2 a 30 000.
* El número total de filas de la vista de datos está limitado a 1 048 576.
* En el modo de agregación de segmentos, el tamaño de memoria de la vista de datos está limitado a 100 MB.

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>Habilitación de una captura segmentada de grandes conjuntos de datos

Para el modo de segmento `dataview`, defina un tamaño de ventana para `dataReductionAlgorithm` en el archivo *capabilities.json* del objeto visual para el elemento `dataViewMapping` necesario. `count` determina el tamaño de la ventana, que limita el número de las filas de datos nuevas que se pueden anexar a `dataview` en cada actualización.

Agregue el siguiente código en el archivo *capabilities.json*:

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

Los segmentos nuevos se anexan al objeto `dataview` existente y se proporcionan al objeto visual como una llamada a `update`.

## <a name="usage-in-the-power-bi-visual"></a>Uso en el objeto visual de Power BI

En Power BI, puede usar `fetchMoreData` en el modo de agregación de segmentos predeterminado o en el de actualizaciones incrementales. 

### <a name="using-segments-aggregation-mode-default"></a>Uso del modo de agregación de segmentos (valor predeterminado)

Con este modo, la vista de datos proporcionada al objeto visual contiene los datos acumulados para todas las solicitudes `fetchMoreData requests` anteriores. Por lo tanto, se espera que el tamaño de la vista de datos crezca con cada actualización. Por ejemplo, si se espera un total de 100 000 filas y el tamaño de la ventana se establece en 10 000, la primera vista de datos de actualización debe incluir 10 000 filas, la segunda debe incluir 20 000, etc.

Para seleccionar este modo, se llama a `fetchMoreData` con `aggregateSegments = true`.

Puede determinar si los datos existen comprobando si `dataView.metadata.segment` existe:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

También puede ver si es la primera actualización o una posterior comprobando `options.operationKind`. En el código siguiente, `VisualDataChangeOperationKind.Create` hace referencia al primer segmento, y `VisualDataChangeOperationKind.Append`, a los siguientes.

Para consultar una implementación de ejemplo, vea el fragmento de código siguiente:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

También puede invocar el método `fetchMoreData` mediante un controlador de eventos de la interfaz de usuario, como se muestra aquí:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Como respuesta a la llamada al método `this.host.fetchMoreData`, Power BI llama al método `update` del objeto visual con un nuevo segmento de datos.

> [!NOTE]
> Para evitar restricciones de memoria del cliente, actualmente Power BI limita el total de datos recuperados a 100 MB. Puede ver que se ha alcanzado el límite si `fetchMoreData()` devuelve `false`.

### <a name="using-incremental-updates-mode"></a>Uso del modo de actualizaciones incrementales

Con este modo, la vista de datos proporcionada al objeto visual contiene simplemente datos incrementales. Por lo tanto, el tamaño de la vista de datos no pasaría el tamaño de ventana definido. Por ejemplo, si se espera un total de 101 000 filas y el tamaño de la ventana se establece en 10 000, el objeto visual obtendría 10 actualizaciones con un tamaño de la vista de datos de 10 000 y una actualización con un tamaño de la vista de datos de 1000.

Para seleccionar este modo, se llama a `fetchMoreData` con `aggregateSegments = false`.

Puede determinar si los datos existen comprobando si `dataView.metadata.segment` existe:

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

También puede ver si es la primera actualización o una posterior comprobando `options.operationKind`. En el código siguiente, `VisualDataChangeOperationKind.Create` hace referencia al primer segmento y `VisualDataChangeOperationKind.Segment` hace referencia a los segmentos siguientes.

Para consultar una implementación de ejemplo, vea el fragmento de código siguiente:

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

También puede invocar el método `fetchMoreData` mediante un controlador de eventos de la interfaz de usuario, como se muestra aquí:

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

Como respuesta a la llamada al método `this.host.fetchMoreData`, Power BI llama al método `update` del objeto visual con un nuevo segmento de datos.

> [!NOTE]
> Aunque los datos de la vista de datos entre las diferentes actualizaciones son principalmente exclusivos, habrá cierta superposición entre las vistas de datos posteriores.
> En el caso de la asignación de datos de tablas y categorías, se espera que las N primeras filas de la vista de datos contengan datos copiados de la vista de datos anterior.
> Modo de determinar N: `(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`.