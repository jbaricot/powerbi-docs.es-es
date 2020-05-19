---
title: Característica supportsMultiVisualSelection
description: En este artículo se describe cómo usar la característica supportsMultiVisualSelection en objetos visuales de Power BI y sus requisitos.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 6ad986308fb82f8191829d29654bb96b55d0fbd0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83272704"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>Uso de la característica supportsMultiVisualSelection

La característica `supportsMultiVisualSelection` le permite usar la selección en varios objetos visuales en un informe.

## <a name="example"></a>Ejemplo

En un informe con más de un objeto visual, seleccione dos valores para que esos valores se apliquen a otros objetos visuales. Por ejemplo, en [Ejemplo de análisis de minoristas](../../create-reports/sample-retail-analysis.md), seleccione **Fashions Direct** en un objeto visual. Seleccione Ctrl y seleccione **Ene** en otro objeto visual. En el informe, las selecciones se aplican a los otros objetos visuales que admiten el uso de esta característica. Ahora, otros objetos visuales tienen el ámbito en **Fashions Direct**y**Ene**.

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

Para probar el desarrollo de Power BI, vea [Desarrollar un objeto visual de Power BI](custom-visual-develop-tutorial.md).
