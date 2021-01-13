---
title: La característica supportsMultiVisualSelection en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se describe cómo usar la característica supportsMultiVisualSelection en objetos visuales de Power BI y sus requisitos. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 9e6b17a4576f2354a5cbecc0c3a965a5611784ee
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887946"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Uso de la característica supportsMultiVisualSelection

La característica `supportsMultiVisualSelection` le permite usar la selección en varios objetos visuales en un informe.

## <a name="example"></a>Ejemplo

En un informe con más de un objeto visual, seleccione dos valores para que esos valores se apliquen a otros objetos visuales. Por ejemplo, en [Ejemplo de análisis de minoristas](../../create-reports/sample-retail-analysis.md), seleccione **Fashions Direct** en un objeto visual. Seleccione Ctrl y seleccione **Ene** en otro objeto visual. En el informe, las selecciones se aplican a los otros objetos visuales que admiten el uso de esta característica. Ahora, otros objetos visuales tienen el ámbito en **Fashions Direct **y** Ene**.

## <a name="requirements"></a>Requisitos

Esta característica requiere la API v3.2.0 o una versión posterior.

Esta característica no se puede aplicar a los objetos visuales de imagen. No puede aplicarla a algunos objetos visuales avanzados, como controladores de clave, árboles de descomposición, objetos visuales de preguntas y respuestas, cuadros de texto y gráficos de medidores.

## <a name="usage"></a>Uso

Para usar la característica `supportsMultiVisualSelection`, agregue el código siguiente al archivo `capabilities.json` del objeto visual.

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>Pasos siguientes

Para información sobre los conceptos de Power BI, vea [Objetos visuales en Power BI](power-bi-visuals-concept.md).

Para probar el desarrollo de Power BI, consulte [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md).
