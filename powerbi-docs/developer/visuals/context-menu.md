---
title: Adición de menús contextuales a objetos visuales de Power BI en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: Obtenga información sobre cómo agregar un menú contextual a un objeto visual de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1c19ba94588628e002cdb9e65f59bd4182020e1c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888705"
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
