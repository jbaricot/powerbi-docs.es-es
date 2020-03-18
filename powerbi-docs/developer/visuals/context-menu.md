---
title: Funcionalidades y propiedades de objetos visuales de Power BI
description: En este artículo se describen las funcionalidades y propiedades de los objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1e2fbe3288e5dbb759a56ad1c299db2e277408b2
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380764"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Incorporar un menú contextual a un objeto visual de Power BI

Puede usar `selectionManager.showContextMenu()` con parámetros `selectionId` y una posición (como un objeto `{x:, y:}`) para que Power BI muestre un menú contextual para el objeto visual.

> [!IMPORTANT]
> `selectionManager.showContextMenu()` se presentó en Visuals API 2.2.0.

Por lo general, se agrega como un evento de clic con el botón derecho (o un evento que se mantiene presionado en los dispositivos táctiles). El menú contextual se agregó al BarChart de ejemplo como referencia:

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
