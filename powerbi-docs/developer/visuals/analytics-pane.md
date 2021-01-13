---
title: El panel Analytics en objetos visuales de Power BI en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se describe cómo crear líneas de referencia dinámicas en objetos visuales de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: dd3d3a8a3553dc9c3ab8c2867c6fee319ad74a07
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889165"
---
# <a name="the-analytics-pane-in-power-bi-visuals"></a>Panel Analytics en objetos visuales de Power BI

El panel **Analytics** se introdujo para [objetos visuales nativos](../../transform-model/desktop-analytics-pane.md) en noviembre de 2018.
En este artículo se explica cómo los objetos visuales de Power BI con la API v2.5.0 pueden presentar y administrar sus propiedades en el panel **Analytics**.

![Panel Analytics](media/analytics-pane/visualization-pane-analytics-tab.png)

## <a name="manage-the-analytics-pane"></a>Administración del panel Analytics

Del mismo modo que administra las propiedades del [panel **Formato**](./custom-visual-develop-tutorial-format-options.md), administre el panel **Analytics** al definir un objeto en el archivo *capabilities.json* del objeto visual.

En el panel **Analytics**, las diferencias son las siguientes:

* En la definición del objeto, agregue un campo **objectCategory** con un valor de 2.

    > [!NOTE]
    > El campo opcional `objectCategory` se presentó en la API 2.5.0. Define el aspecto del objeto visual que controla el objeto (1 = formato, 2 = análisis). `Formatting` se usa para elementos como la apariencia, los colores, los ejes y las etiquetas. `Analytics` se usa para elementos como las previsiones, las líneas de tendencia, las líneas de referencia y las formas.
    >
    > Si no se especifica el valor, el valor predeterminado de `objectCategory` es "Formatting".

* El objeto debe tener estas dos propiedades:
    * `show` de tipo `bool`, con un valor predeterminado de `false`.
    * `displayName` de tipo `text`. El valor predeterminado que elija se convierte en el nombre para mostrar inicial de la instancia.

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

Puede definir otras propiedades de la misma manera que lo hace para los objetos de **Formato**. Además, puede enumerar objetos igual que en el panel **Formato**.

## <a name="known-limitations-and-issues-of-the-analytics-pane"></a>Limitaciones y problemas conocidos del panel Analytics

* El panel **Analytics** aún no es compatible con varias instancias. Los objetos no pueden tener un [selector](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector) que no sea estático (es decir, "selector": null), y los objetos visuales de Power BI no pueden tener varias instancias de una tarjeta definidas por el usuario.
* Las propiedades del tipo `integer` no se muestran correctamente. Como solución alternativa, use el tipo `numeric` en su lugar.

> [!NOTE]
> * Use el panel **Analytics** solo para los objetos que agreguen nueva información o proporcionen nuevas perspectivas sobre la información presentada (por ejemplo, líneas de referencia dinámicas que muestren tendencias importantes).
> * Cualquier opción que controle la apariencia del objeto visual (es decir, el formato) debe limitarse en el panel **Formato**.