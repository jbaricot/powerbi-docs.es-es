---
title: Registro de cambios de la API de objetos visuales de Power BI
description: En este artículo se describen los principales cambios de las diferentes versiones de la API de objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: 3cf415cbd14da28d523a042fdf4099fe464a4a8b
ms.sourcegitcommit: a07fa723bb459494c60cf6d749b4554af723482a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2020
ms.locfileid: "84739193"
---
# <a name="power-bi-visuals-api-changelog"></a>Registro de cambios de la API de objetos visuales de Power BI
Esta página contiene un resumen rápido de las versiones de API. Las versiones que se enumeran aquí se consideran estables y no cambiarán.

## <a name="api-v320"></a>API v3.2.0
  * Admite **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * Agrega **isInFocus** a la opción de actualización y el método **switchFocusModeState** al host del objeto visual.
  * Admite la personalización de **subtotales**.

## <a name="api-v250"></a>API v2.5.0
  * Admite el **[panel Análisis](./analytics-pane.md)** .
  * Admite los métodos `SelectionIdBuilder` **withMatrixNode** y **withTable**.
  * Ya no admite la interfaz `DataRepetitionSelector`, se ha reemplazado por la interfaz `data.CustomVisualOpaqueIdentity`.

## <a name="api-v230"></a>API v2.3.0
  * **[API de la página de aterrizaje](./landing-page.md)**
  * **[API de almacenamiento local](./local-storage.md)**
  * **[API de filtro de tupla (varias columnas)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API de representación de eventos](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * Admite la **[restauración de filtros JSON desde DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)** .
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * Mejoras de rendimiento:
    * Tiempos de carga más rápidos
    * Menor superficie de memoria
    * Optimización de transacciones de eventos y datos  

**Notas de la versión**
* Las API de filtrado refactorizadas estarán disponibles en la API 2.2 y no se admiten en la API 2.1.
* Los objetos visuales solo recibirán el tipo dataView que se declaró en sus capacidades. Los objetos visuales que usan varios tipos de vistas de datos se romperán como resultado de esta actualización.
* Ya no admite la interfaz `DataViewScopeIdentity`, se ha reemplazado por la interfaz `data.DataRepetitionSelector`. Si ha usado la propiedad clave de la interfaz `DataViewScopeIdentity`, puede reemplazarla por `JSON.stringify(identity)`.
* `undefined` se reemplaza por `null` dentro de dataView. Al recorrer en iteración una matriz mediante `var item in myArray`, se omite en `undefined`, pero no en `null`. Es posible que esta actualización interrumpa los objetos visuales que usan este patrón. Asegúrese de buscar `null` en las matrices:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* La propiedad `proto` ya no almacena metadatos o datos ocultos dentro de dataView. Esta actualización puede invalidar los objetos visuales que tienen acceso a las propiedades a través de `proto`.

## <a name="api-v1130"></a>API v1.13.0
* Admite **[segmentaciones de sincronización](./enable-sync-slicers.md)** . Tenga en cuenta que esto solo funciona con segmentaciones de campo único debido al estado actual del código de PBI. [Más información](/power-bi/desktop-slicers).
* Accesibilidad: [Compatibilidad con contraste alto](./high-contrast-support.md) 
* Accesibilidad: permite la marca de foco de teclado.

## <a name="api-v1120"></a>API v1.12.0
* Admite temas.
* Admite **[fetchMoreData](./fetch-more-data.md)** ; tenga en cuenta que la **API de captura de más datos** supera el límite máximo de 30 000 puntos de datos.
* **[API de información sobre herramientas de lienzo](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[API de FilterManager](./filter-api.md)**
* Admite **[marcadores](./bookmarks-support.md)** . 

## <a name="api-v1100"></a>API v1.10.0
* Agrega `ILocalizationManager`.
* **API de Autenticación**

## <a name="api-v190"></a>API v1.9.0
* **[API de launchUrl](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* Admite el nuevo tipo **fillRule** (gradiente) en el esquema de capacidades.
* Admite la propiedad **rule** en el esquema de capacidades de las propiedades de objeto.

## <a name="api-v170"></a>API v1.7.0
* Admite **[RESJSON](./localization.md#resource-file)** .

## <a name="api-v162"></a>API v1.6.2
* Admite el **[modo de edición](./advanced-edit-mode.md)** para que los objetos visuales entren en modo de edición.
* Admite **[objetos visuales interactivos (html) de Power BI con tecnología de R](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** , basados en HTML.

## <a name="api-v150"></a>API v1.5.0
* Admite **[Permitir interacciones](./visuals-interactions.md)** para la interactividad de los objetos visuales.

## <a name="api-v140"></a>API v1.4.0
* Admite **[localización](./localization.md)** .

## <a name="api-v130"></a>API v1.3.0
* Admite **[información sobre herramientas](./add-tooltips.md)** .

## <a name="api-v120"></a>API v1.2.0
* Agrega **colorPalette** para administrar los colores utilizados en el objeto visual.
* Admite **selección múltiple**: selectionManager puede aceptar una matriz de `SelectionId`.
* Admite **[objetos visuales de R](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** mediante scripts de R.

## <a name="api-v110"></a>API v1.1.0
* Admite objetos visuales de depuración en iFrame.
* Agrega espacio aislado ligero con inicialización más rápida del iFrame
* Soluciona el problema de que [Capabilities.objects no admite el tipo "text"](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12).
* Admite `pbiviz update` para actualizar las definiciones de tipo y el esquema de la API de objetos visuales.
* Admite la marca `--api-version` en `pbiviz new` para crear objetos visuales con una versión específica de API.
* Admite la versión alpha de la API v1.2.0.

**Host de objetos visuales**
* Agrega **createSelectionIdBuilder** para crear identificadores únicos que se usan para la selección de datos.
* Agrega **createSelectionManager** para administrar el estado de selección del objeto visual y comunica los cambios al host de objetos visuales.
* Agrega una matriz de **colores** predeterminados para usar en los objetos visuales.

## <a name="api-v100"></a>API v1.0.0
* Versión inicial de la API
