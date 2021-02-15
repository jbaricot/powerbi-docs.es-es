---
title: Creación de múltiplos pequeños en Power BI (versión preliminar)
description: Los múltiplos pequeños, o entramados, dividen un objeto visual en varias versiones de sí mismo, que se presentan en paralelo, con sus datos divididos en estas versiones por una dimensión seleccionada.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: bc1f890e588227f9d0dc30202474a8f77f93fc38
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628252"
---
# <a name="create-small-multiples-in-power-bi-preview"></a>Creación de múltiplos pequeños en Power BI (versión preliminar)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Los múltiplos pequeños, o entramados, dividen un objeto visual en varias versiones de sí mismo. Las versiones se presentan en paralelo, con los datos divididos en estas versiones por una dimensión seleccionada. Por ejemplo, un múltiplo pequeño podría dividir un gráfico de columnas "ventas por categoría" entre líneas de productos o regiones. En esta versión preliminar, los múltiplos pequeños tienen un pequeño conjunto de funcionalidades, con más información en las versiones posteriores.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="Captura de pantalla de múltiplos pequeños para categoría y región":::

## <a name="enable-the-preview-feature"></a>Habilitación de la característica en versión preliminar

En el menú **Archivo**, seleccione **Opciones y configuración** > **Opciones** > **Características en versión preliminar** y seleccione la casilla **Múltiplos pequeños**.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-enable-preview.png" alt-text="Habilitar la versión preliminar de los múltiplos pequeños":::

Reinicie Power BI Desktop, y ya podrá probar los múltiplos pequeños.

## <a name="create-small-multiples"></a>Creación de múltiplos pequeños

Actualmente, puede crear múltiplos pequeños en los gráficos de barras, de columnas, de líneas y de áreas. 

Para empezar, cree uno de los objetos visuales anteriores y elija un campo de cuyos datos desea realizar particiones. Arrastre ese campo al área **Múltiplos pequeños** en la sección Campos del panel Visualizaciones. El gráfico se divide en una cuadrícula de 2×2, con los datos divididos por la dimensión elegida. La cuadrícula se rellena con los gráficos de múltiplos pequeños. Se ordenan según el criterio de ordenación elegido, de izquierda a derecha y de arriba abajo.

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-two-by-two-grid.png" alt-text="Múltiplos pequeños en una cuadrícula de dos por dos":::

Verá que los ejes están sincronizados. Hay un eje Y a la izquierda de cada fila y un eje X en la parte inferior de cada columna.

Ahora que ha creado múltiplos pequeños, vea [Interactuación con múltiplos pequeños en Power BI (versión preliminar)](power-bi-visualization-small-multiples-interact.md).

## <a name="format-a-small-multiples-visual"></a>Dar formato a un objeto visual de múltiplos pequeños

Algunas opciones nuevas del panel Formato le permiten controlar la apariencia de la cuadrícula.

### <a name="change-the-grid-dimensions"></a>Modificación de las dimensiones de la cuadrícula

Puede cambiar las dimensiones de la cuadrícula en la tarjeta Diseño de cuadrícula:

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-grid-layout-card.png" alt-text="Tarjeta de diseño de cuadrícula de múltiplos pequeños":::

El valor predeterminado es una cuadrícula de 2×2 de múltiplos pequeños, pero puede ajustar el número de filas y columnas hasta 6×6. Los múltiplos que no caben en esa cuadrícula se cargan a medida que se desplaza hacia abajo.


### <a name="adjust-the-small-multiples-titles"></a>Ajuste de los títulos de múltiplos pequeños

Al igual que con otros títulos de objetos visuales, puede ajustar el estilo y la posición de los diversos títulos de múltiplos pequeños en la tarjeta **Small multiple title** (Título de múltiplos pequeños).

## <a name="preview-limitations"></a>Limitaciones de vista previa

Aunque la característica está en versión preliminar, estamos trabajando constantemente para garantizar que interactúa bien con el resto de las características. Estas son algunas limitaciones actuales.

### <a name="fields-pane"></a>Panel Campos

- Fecha y otras jerarquías continuas: supongamos que tiene un objeto visual, como un gráfico de líneas, con una jerarquía de fechas en el eje X. Cuando crea múltiplos pequeños, Power BI convierte ese eje de un eje continuo a un eje de categorías.
- Mostrar elementos sin datos: la opción sigue existiendo, pero es posible que el comportamiento no satisfaga sus expectativas.

### <a name="visual-interactions"></a>Interacciones de objetos visuales

- Desplazarse para cargar más datos en el eje de categorías: en los objetos visuales estándar con muchas categorías en el eje, cuando se desplaza hasta el final del eje, el objeto visual carga más categorías. Actualmente, un objeto visual de múltiplos pequeños no carga más categorías.
- Ordenar múltiplos pequeños por medida: la ordenación en múltiplos pequeños es una nueva funcionalidad. Es posible que espere ordenar los múltiplos pequeños por una medida. Actualmente, solo puede ordenar los múltiplos por el criterio de ordenación natural del campo.
- Clic con el botón derecho/menú contextual -> Analizar: deshabilitado por ahora.
- Clic con el botón derecho/menú contextual -> Resumir: deshabilitado por ahora.
- Seleccionar varios puntos de datos con selección rectangular: deshabilitado por ahora.
- Zoom de eje: deshabilitado por ahora.
- Accesibilidad: puede ajustar la navegación mediante el teclado y las indicaciones en pantalla para mejorar la compatibilidad con la nueva capa "Cuadrícula" que los múltiplos pequeños aportan a los objetos visuales. Falta algún comportamiento, como la navegación mediante el teclado por la barra de desplazamiento del eje de categorías.

### <a name="formatting-options"></a>Opciones de formato

**General**

- Alternancia dinámica: la opción sigue existiendo, pero es posible que el comportamiento no satisfaga sus expectativas. Dado que muchos dispositivos móviles están vinculados a esta alternancia, la experiencia móvil también refleja fielmente la experiencia propia de Power BI Desktop y del servicio Power BI.
- Muestreo de alta densidad: para los gráficos de líneas, la alternancia de muestreo de alta densidad todavía existe, pero actualmente no es compatible con los múltiplos pequeños.

**Eje**

- Concatenar etiquetas: deshabilitado por ahora.

**Etiquetas totales**

- Total de etiquetas para gráficos apilados: deshabilitado por ahora.

**Control deslizante de zoom**

- Controles deslizantes de zoom: deshabilitado por ahora.

**Panel de análisis** 

- Líneas de tendencia: deshabilitado por ahora.
- Previsión: deshabilitado por ahora.

Formato dinámico para etiquetas de resaltado: actualmente no se admite.
Disponibilidad del servicio

## <a name="authoring-in-the-power-bi-service"></a>Creación en el servicio Power BI

No se admite la creación de múltiplos pequeños en la Web mientras la característica está en versión preliminar. Puede ver un informe con un objeto visual de múltiplos pequeños, e incluso dar formato a dicho objeto visual. Sin embargo, no puede convertir un objeto visual estándar en un objeto visual de múltiplos pequeños en el servicio Power BI. Un objeto visual también tiene que tener un campo en el área del campo de múltiplos pequeños, o bien el área de múltiplos pequeños no aparecerá para dicho objeto visual.

## <a name="share-your-feedback"></a>Compartir sus comentarios

Díganos qué piensa sobre el objeto visual de múltiplos pequeños:

- [Comunidad de Power BI](https://community.powerbi.com/)
- [Página de ideas de Power BI](https://ideas.powerbi.com/ideas/) 

## <a name="next-steps"></a>Pasos siguientes

[Interactuación con múltiplos pequeños en Power BI (versión preliminar)](power-bi-visualization-small-multiples-interact.md)
