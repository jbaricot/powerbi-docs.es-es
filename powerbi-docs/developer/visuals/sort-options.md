---
title: Opciones de ordenación en objetos visuales de Power BI en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se describe el comportamiento de ordenación predeterminado de los objetos visuales de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 0d24719b486608c283ec73f0188092a1ece3155e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889257"
---
# <a name="sorting-options-for-power-bi-visuals"></a>Opciones de ordenación para objetos visuales de Power BI

En este artículo se describe cómo las opciones de *ordenación* especifican el comportamiento de ordenación de los objetos visuales de Power BI. 

La funcionalidad de ordenación requiere uno de los siguientes parámetros.

## <a name="default-sorting"></a>Ordenación predeterminada

La opción `default` es la forma más simple. Permite ordenar los datos presentados en la sección “DataMappings”. La opción permite ordenar las asignaciones de datos por el usuario y especifica la dirección de ordenación.

```json
    "sorting": {
        "default": {   }
    }
```

![Opciones de ordenación en el menú contextual](media/sort-options/sorting.png)

## <a name="implicit-sorting"></a>Ordenación implícita

La ordenación implícita ordena con el parámetro de matriz `clauses`, que describe la ordenación de cada rol de datos. `implicit` significa que el usuario del objeto visual no puede cambiar el criterio de ordenación. Power BI no muestra las opciones de ordenación en el menú del objeto visual, pero sí que ordena los datos según la configuración especificada.

Los parámetros de `clauses` pueden contener varios objetos con dos parámetros:

- `role`: determina `DataMapping` para la ordenación.
- `direction`: determina la dirección de ordenación (1 = ascendente; 2 = descendente).

```json
    "sorting": {
        "implicit": {
            "clauses": [
                {
                    "role": "category",
                    "direction": 1
                },
                {
                    "role": "measure",
                    "direction": 2
                }
            ]
        }
    }
```

## <a name="custom-sorting"></a>Ordenación personalizada

La ordenación personalizada implica que el desarrollador administra la ordenación en el código del objeto visual.
