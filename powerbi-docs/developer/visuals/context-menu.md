---
title: Incorporar un menú contextual a un objeto visual de Power BI
description: Obtenga información sobre cómo agregar un menú contextual a un objeto visual de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 9e63a1196ddc7557fcf8b2fceb424415a63d4df9
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748089"
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
