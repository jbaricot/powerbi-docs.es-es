---
title: La característica supportsKeyboardFocus en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se describe cómo usar la característica supportsKeyboardFocus en objetos visuales de Power BI y sus requisitos. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 5ba87db8118076de4bf13abc0280223f9f04f871
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887969"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>Uso de la característica supportsKeyboardFocus

En este artículo se describe cómo usar la característica `supportsKeyboardFocus` en objetos visuales de Power BI.
La característica `supportsKeyboardFocus` permite navegar por los puntos de datos del objeto visual usando solo el teclado.

Para más información sobre la navegación mediante el teclado para objetos visuales, consulte la sección [Navegación mediante el teclado](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation).

## <a name="example"></a>Ejemplo

Abra un objeto visual que use la característica `supportsKeyboardFocus`. Seleccione cualquier punto de datos en el objeto visual y seleccione el tabulador. El foco se desplaza al siguiente punto de datos para cada vez que seleccione el tabulador. Seleccione Entrar para seleccionar el punto de datos resaltado.

![Ejemplo de supportsKeyboardFocus](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>Requisitos

Esta característica requiere la API v2.1.0 o una versión posterior.

Esta característica se puede aplicar a todos los objetos visuales excepto a los objetos visuales de imagen.

## <a name="usage"></a>Uso

Para usar la característica `supportsKeyboardFocus`, agregue el código siguiente al archivo *capabilities.json* del objeto visual.
Esta funcionalidad permite al objeto visual recibir el foco con la navegación mediante el teclado.

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre las características de accesibilidad, consulte [Diseño de informes accesibles de Power BI](../../create-reports/desktop-accessibility-creating-reports.md).

Para probar el desarrollo de Power BI, consulte [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md).
