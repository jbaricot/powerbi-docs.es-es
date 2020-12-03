---
title: Uso de la lista de campos en Power BI Desktop (versión preliminar)
description: Use la lista de campos para modelar datos y crear informes en Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 11/11/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 834df274d4cc75af1087ab4fa7d24c2fd7dd4fec
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416011"
---
# <a name="using-the-field-list-in-power-bi-desktop-preview"></a>Uso de la lista de campos en Power BI Desktop (versión preliminar)

A partir de la actualización de noviembre de 2020, estamos unificando las listas de **campos** en la vista de modelo, la vista de datos y la vista de informes de Power BI Desktop. Al unificar estas vistas, se creará coherencia para la funcionalidad y la interfaz de usuario en todas las vistas, y se abordarán los comentarios de los clientes.

Los cambios que observará en las vistas son los siguientes:

* Iconografía
* Funcionalidad de búsqueda
* Elementos del menú contextual
* Comportamiento similar de arrastrar y colocar
* Información sobre herramientas
* Mejoras de accesibilidad

La intención es facilitar aún más el uso de Power BI Desktop. Los cambios deben tener un impacto mínimo en el flujo de trabajo de datos típico.

## <a name="enabling-the-new-field-list-preview"></a>Habilitar la nueva lista de campos (versión preliminar)

La lista de campos unificada comienza con la vista de **modelo** y, posteriormente, se habilitará en otras vistas. Para habilitar la vista de campos unificada, en Power BI Desktop, vaya a **Archivo > Opciones y configuración > Opciones** y, después, seleccione **Características de versión preliminar** en el panel izquierdo. En la sección Características de versión preliminar, marque la casilla situada junto a **Nueva lista de campos**.

![Habilitar la nueva lista de campos](media/desktop-field-list/field-list-01.png)

Para que la selección se aplique, se le pedirá que reinicie Power BI Desktop.

## <a name="field-list-changes"></a>Cambios en la lista de campos

En la tabla siguiente se muestran las actualizaciones de la lista de campos. 


|**Lista de campos original (vista de modelo)**  | **Nueva lista de campos (vista de modelo)**  |
|:---------:|:---------:|
|**Original** |**Nuevo** |
|**Iconos e interfaz de usuario**       ||
|![lista de campos original](media/desktop-field-list/field-list-01a.png)     |![nueva lista de campos](media/desktop-field-list/field-list-01b.png)    |
|**Menú contextual: Campo**       ||
|![menú contextual original para el campo](media/desktop-field-list/field-list-02a.png)     |![menú contextual original para el campo](media/desktop-field-list/field-list-02b.png)    |
|**Menú contextual: Tabla**       ||
|![menú contextual original para la tabla](media/desktop-field-list/field-list-03a.png)     |![nuevo menú contextual para la tabla](media/desktop-field-list/field-list-03b.png)    |
|**Información sobre herramientas**       ||
|![información sobre herramientas original](media/desktop-field-list/field-list-04a.png)     |![nueva información sobre herramientas](media/desktop-field-list/field-list-04b.png)    |

También hay nuevos iconos en la lista de campos. En la tabla siguiente se muestran los iconos originales y su nuevo equivalente, y se proporciona una breve descripción de cada uno. 


|Icono original  |Icono nuevo  |Descripción  |
|:---------:|:---------:|:---------|
|![icono original de carpeta](media/desktop-field-list/field-list-05a.png)     |![icono nuevo de carpeta](media/desktop-field-list/field-list-05b.png)           |Carpeta en la lista de campos         |
|![icono original de campo numérico](media/desktop-field-list/field-list-06a.png)     |![icono nuevo de campo numérico](media/desktop-field-list/field-list-06b.png)         |Campo numérico: los campos numéricos son agregados que se pueden sumar o promediar, por ejemplo. Los agregados se importan con los datos y se definen en el modelo de datos en el que se basa el informe. Para obtener más información, consulte [Agregados en los informes de Power BI](../create-reports/service-aggregates.md).         |
|![icono original de columna calculada](media/desktop-field-list/field-list-07a.png)     |![icono nuevo de columna calculada](media/desktop-field-list/field-list-07b.png)         |Columna calculada con un tipo de datos no numérico: columna no numérica que se crea con una fórmula de Expresiones de análisis de datos (DAX) que define los valores de la columna. Más información sobre las [columnas calculadas](desktop-calculated-columns.md).        |
|![icono original de columna calculada numérica](media/desktop-field-list/field-list-08a.png)     |![icono nuevo de columna calculada numérica](media/desktop-field-list/field-list-08b.png)          |Columna calculada numérica: columna que se crea con una fórmula de Expresiones de análisis de datos (DAX) que define los valores de la columna. Más información sobre las [columnas calculadas](desktop-calculated-columns.md).         |
|![icono original de medida](media/desktop-field-list/field-list-09a.png)     |![icono nuevo de medida](media/desktop-field-list/field-list-09b.png)          |Medida: una medida tiene su propia fórmula codificada de forma rígida. Los visores de informes no pueden cambiar el cálculo; por ejemplo, si es una suma, solo podrá ser una suma. Los valores no se almacenan en una columna. Se calculan sobre la marcha, únicamente en función de su ubicación en un objeto visual. Para más información, lea [Descripción de las medidas](desktop-measures.md).         |
|![icono original de grupo de medida](media/desktop-field-list/field-list-10a.png)     |![icono nuevo de grupo de medida](media/desktop-field-list/field-list-10b.png)         |Grupo de medida.         |
|![icono original de KPI](media/desktop-field-list/field-list-11a.png)     |![icono nuevo de KPI](media/desktop-field-list/field-list-11b.png)         |KPI: una indicación visual que comunica el progreso realizado para lograr un objetivo cuantificable. Obtenga más información sobre objetos visuales de [ Indicador clave de rendimiento (KPI)](../visuals/power-bi-visualization-kpi.md).         |
|![icono original de jerarquía de campos](media/desktop-field-list/field-list-12a.png)     |![icono nuevo de jerarquía de campos](media/desktop-field-list/field-list-12b.png)           |Jerarquía de campos: seleccione la flecha para ver los campos que componen la jerarquía. Para más información, vea este vídeo de Power BI en YouTube sobre [cómo crear y trabajar con jerarquías](https://www.youtube.com/watch?v=q8WDUAiTGeU).         |
|![icono original de datos geográficos](media/desktop-field-list/field-list-13a.png)     |![icono nuevo de datos geográficos](media/desktop-field-list/field-list-13b.png)         |Datos geográficos: estos campos de ubicación se pueden usar para crear visualizaciones de mapa.         |
|![icono original de campo de identidad](media/desktop-field-list/field-list-14a.png)     |![icono nuevo de campo de identidad](media/desktop-field-list/field-list-14b.png)          |Campo de identidad: los campos con este icono son campos únicos, configurados para mostrar todos los valores, incluso si tienen duplicados. Por ejemplo, es posible que los datos tengan dos registros para dos personas distintas llamadas "Robin Smith", y cada uno se tratará de forma única. No se sumarán.         |
|![icono original de parámetro](media/desktop-field-list/field-list-15a.png)     |![icono nuevo de parámetro](media/desktop-field-list/field-list-15b.png)          |Parámetro: establezca parámetros para que elementos de los informes y los modelos de datos (como un filtro de consulta, una referencia de origen de datos, una definición de medida, etc.) dependan de uno o más valores de parámetro. Para más información, vea esta entrada de blog de Power BI sobre los [parámetros de consulta](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).         |
|![icono original del campo de fecha del calendario](media/desktop-field-list/field-list-16a.png)     |![icono nuevo del campo de fecha del calendario](media/desktop-field-list/field-list-16b.png)         |Campo de fecha del calendario con una tabla de fechas integrada.         |
|![icono original de tabla calculada](media/desktop-field-list/field-list-17a.png)     |![icono nuevo de tabla calculada](media/desktop-field-list/field-list-17b.png)          |Tabla calculada: una tabla creada con una fórmula de expresiones de análisis de datos (DAX) basada en los datos ya cargados en el modelo. Son los más útiles para los cálculos intermedios que desea almacenar como parte del modelo.         |
|![icono original de advertencia](media/desktop-field-list/field-list-18a.png)     |![icono nuevo de advertencia](media/desktop-field-list/field-list-18b.png)         |Advertencia: un campo calculado con un error. Por ejemplo, la sintaxis de la expresión DAX podría ser incorrecta.         |
|![icono original de grupo](media/desktop-field-list/field-list-19a.png)     |![icono nuevo de grupo](media/desktop-field-list/field-list-19b.png)         |Agrupar: los valores de esta columna se basan en la agrupación de valores de otra columna, mediante la característica de grupos y discretizaciones. Puede obtener información sobre cómo [Usar la agrupación y la discretización](../create-reports/desktop-grouping-and-binning.md).         |
| ningún icono original    |![icono nuevo para cambiar medida de detección](media/desktop-field-list/field-list-20b.png)          |Cambiar medida de detección: al configurar una página para la actualización automática de páginas, puede configurar una [medida de detección de cambios](../create-reports/desktop-grouping-and-binning.md) que se consulta para determinar si se debe actualizar el resto de los objetos visuales de una página.         |


## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Creación de columnas calculadas en Power BI Desktop](desktop-calculated-columns.md)
* [Usar la agrupación y la discretización en Power BI Desktop](../create-reports/desktop-grouping-and-binning.md)
* [Usar líneas de cuadrícula y ajustar a la cuadrícula en los informes de Power BI Desktop](../create-reports/desktop-gridlines-snap-to-grid.md)

