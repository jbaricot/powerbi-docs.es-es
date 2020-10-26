---
title: Selección múltiple de elementos de datos en objetos visuales, o varios objetos visuales, en Power BI Desktop
description: Puede seleccionar varios puntos de datos de los objetos visuales de Power BI Desktop con un sencillo CTRL + clic.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/12/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1c1e6ec9c6f6195f69af67da4ffbf1d0428b0fc2
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257062"
---
# <a name="multi-select-data-elements-data-points-and-visuals-in-power-bi-desktop"></a>Selección múltiple de elementos de datos, puntos de datos y objetos visuales en Power BI Desktop

Puede seleccionar varios elementos de datos en un solo objeto visual, varios puntos de datos en un objeto visual o varios objetos visuales en un informe mediante Power BI Desktop. En las secciones siguientes se describe cada opción de forma independiente.

## <a name="select-multiple-data-points"></a>Selección de varios puntos de datos

En Power BI Desktop puede resaltar un punto de datos en un objeto visual determinado simplemente haciendo clic en el punto de datos del objeto visual. Por ejemplo, si tiene una barra o un elemento de gráfico importante y desea que otros objetos visuales de la página del informe resalten los datos en función de su selección, puede hacer clic en el elemento de datos de un objeto visual y ver los resultados reflejados en otros objetos visuales de la página. Esto se conoce como el resaltado básico o de selección única. En la siguiente imagen se muestra el resaltado básico. 

![Único punto de datos seleccionado](media/desktop-multi-select/multi-select_01.png)

Con la selección múltiple, ahora puede seleccionar más de un punto de datos en su página de informe de **Power BI Desktop** y resaltar los resultados en todos los objetos visuales de la página. Esto equivale a la instrucción o funcionalidad **and** , como en "resaltar datos para Idaho **and** Virginia". Para seleccionar varios puntos de datos en objetos visuales, use **CTRL + clic** . En la imagen siguiente se muestran **múltiples puntos de datos** seleccionados (selección múltiple).

![Varios puntos de datos seleccionados](media/desktop-multi-select/multi-select_02.png)

Esto parece una funcionalidad sencilla, pero genera todo tipo de oportunidades al crear, compartir e interactuar con informes. 

## <a name="select-multiple-elements-using-rectangle-select-preview"></a>Selección de varios elementos con la selección de rectángulo (versión preliminar)

Puede seleccionar varios elementos de datos en un objeto visual, o varios objetos visuales en un informe, mediante la selección rectangular, que a menudo se conoce como *selección de lazo* . 

### <a name="select-multiple-visuals-on-the-canvas"></a>Selección de varios objetos visuales en el lienzo

Seleccione varios objetos visuales y otros elementos de informe haciendo clic y arrastrando sobre el lienzo para crear un lazo rectangular. Se seleccionan todos los objetos visuales que se encapsulan completamente dentro del lazo. Si presiona la tecla *Ctrl* o *Mayús* (mientras realiza una selección múltiple haciendo Ctrl+clic en los objetos visuales individuales), puede seguir haciendo selecciones de lazo que agregan objetos visuales a la selección múltiple actual. 

Si ya se ha seleccionado un objeto visual y ha aplicado el lazo, el uso de *Ctrl* o *Mayús* desactiva la selección. El lazo no selecciona objetos visuales únicos dentro de los grupos, sino que puede seleccionar grupos encapsulándolos por completo.

El lienzo no se desplaza automáticamente con la selección de lazo rectangular. 

### <a name="select-multiple-data-points-in-a-visual"></a>Selección de varios puntos de datos en un objeto visual

Puede seleccionar varios puntos de datos en un objeto visual usando los mismos pasos del lazo rectangular. Mientras mantiene presionada la tecla *Ctrl* , haga clic y arrastre dentro de un objeto visual para seleccionar varios puntos de datos. Al soltar el botón del mouse, se seleccionan todos los puntos que se superponen al rectángulo de la selección, y también se conservan las selecciones de lazo anteriores. Si selecciona mediante lazo un área que incorpora los puntos seleccionados anteriormente usando simultáneamente *Ctrl* , se anula la selección de esos puntos de datos (se desactiva). El uso del lazo tiene el mismo efecto que hacer *Ctrl* + clic en cada punto individualmente. 

Al usar la tecla *Mayús* mientras realiza una selección de lazo, se conservan las selecciones anteriores y los puntos de datos ya seleccionados permanecen seleccionados. Por lo tanto, si pulsa *Mayús* al realizar una selección de lazo, solo se agregan puntos de datos a la selección, en lugar de alternar la activación de los puntos de datos en el área seleccionada.

Puede borrar la selección actual haciendo clic en un espacio vacío en el área de trazado sin presionar una tecla del teclado.

Para obtener más información acerca de esta característica, consulte la [entrada de blog acerca de la publicación de esta característica](https://powerbi.microsoft.com/blog/power-bi-desktop-august-2020-feature-summary/#_Data_point).

Existen algunas limitaciones y consideraciones para la selección múltiple de puntos de datos en un objeto visual:

* Línea, área, gráfico de dispersión y gráfico de rectángulos compatible con selección de lazo
* El número máximo de puntos de datos que puede seleccionar a la vez es 300.
* Al ver un informe en el servicio Power BI, la selección de rectángulo solo está habilitada si se ha habilitado la característica de selección de lazo al guardar y publicar el informe.

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Usar líneas de cuadrícula y ajustar a la cuadrícula en los informes de Power BI Desktop](desktop-gridlines-snap-to-grid.md)
* [Acerca de filtros y resaltado en informes de Power BI](power-bi-reports-filters-and-highlighting.md)

