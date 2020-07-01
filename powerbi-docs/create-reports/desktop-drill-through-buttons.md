---
title: Creación de un botón de obtención de detalles en Power BI
description: Puede agregar botones de obtención de detalles en los informes de Power BI para que se comporten como aplicaciones y profundizar en la interacción con los usuarios.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/26/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: a6de32e93b79b45d700ad5de1607f580dff836cf
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239256"
---
# <a name="create-a-drill-through-button-in-power-bi"></a>Creación de un botón de obtención de detalles en Power BI

Puede crear un botón de *obtención de detalles* en Power BI. Se trata de un botón que obtiene los detalles de una página con información filtrada según un contexto específico.

Una manera de obtener detalles en un informe es hacer clic con el botón derecho en un objeto visual. Si quiere que la acción de obtención de detalles sea más obvia, puede crear un botón de obtención de detalles. Este botón puede aumentar la capacidad de detección de escenarios importantes de obtención de detalles en los informes. Puede determinar condicionalmente gran parte de la apariencia y el comportamiento del botón. Por ejemplo, puede mostrar texto diferente en un botón si se cumplen ciertas condiciones. Siga leyendo para más información. 

En este ejemplo, cuando selecciona la barra de Word en el gráfico, se habilita el botón **Ver detalles**.

![Botón Ver detalles](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Al seleccionar el botón **Ver detalles**, obtiene detalles de la página de análisis de la cesta de la compra. Como puede ver en el objeto visual de la izquierda, la página de obtención de detalles ahora está filtrada por Word.

![Objeto visual filtrado](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Configuración de un botón de obtención de detalles

Para configurar un botón de obtención de detalles, primero debe [configurar una página de obtención de detalles válida](desktop-drillthrough.md) en el informe. Después, debe crear un botón con **Obtener detalles** como el tipo de acción y seleccionar la página de obtención de detalles como **Destino**.

Como el botón de obtención de detalles tiene dos estados (habilitado o deshabilitado), verá que hay dos opciones de información sobre herramientas.

![Configuración del botón de obtención de detalles](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Si deja en blanco los cuadros de información sobre herramientas, Power BI genera dicha información de forma automática. La información sobre herramientas se basa en los campos de destino y obtención de detalles.

Este es un ejemplo de la información sobre herramientas generada de forma automática cuando el botón está deshabilitado:

"Para obtener detalles del análisis de la cesta de la compra (la página de destino), seleccione un único punto de datos de Producto (el campo de obtención de detalles)".

![Información sobre herramientas generada automáticamente deshabilitada](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Y este es un ejemplo de la información sobre herramientas generada de forma automática cuando el botón está habilitado:

"Haga clic para obtener detalles del análisis de la cesta de la compra (la página de destino)".

![Información sobre herramientas generada automáticamente habilitada](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Pero si quisiera proporcionar información sobre herramientas personalizada, siempre puede especificar una cadena estática. También puede aplicar [formato condicional a la información sobre herramientas](#set-formatting-for-tooltips-conditionally).

## <a name="pass-filter-context"></a>Paso del contexto de filtro

El botón funciona como la obtención de detalles normal, por lo que puede pasar filtros en campos adicionales mediante el filtrado cruzado de los objetos visuales que contienen el campo de obtención de detalles. Por ejemplo, si usa **Ctrl** + **clic** y el filtrado cruzado, puede pasar varios filtros por Tienda a la página de obtención de detalles porque las selecciones realizan el filtrado cruzado del objeto visual que contiene Producto, el campo de obtención de detalles:

![Paso del contexto de filtro](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

Tras seleccionar el botón de obtención de detalles, verá que los filtros de Tienda y Producto se pasan a la página de destino:

![Filtros de esta página](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Contexto de filtro ambiguo

Como el botón de obtención de detalles no está asociado a un único objeto visual, si la selección es ambigua, el botón se deshabilita.

En este ejemplo, el botón está deshabilitado porque dos objetos visuales contienen una sola selección en Producto. Existe ambigüedad sobre a qué punto de datos de qué objeto visual se va a enlazar la acción de obtención de detalles:

![Contexto de filtro ambiguo](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="customize-formatting-for-disabled-buttons"></a>Personalización del formato de los botones deshabilitados
Puede personalizar las opciones de formato para el estado deshabilitado de los botones de obtención de detalles.


:::image type="content" source="media/desktop-drill-through-buttons/drill-through-customize-disabled-button.png" alt-text="Personalización del formato de botón deshabilitado":::
 
Opciones de formato
- **Controles de texto de botón**: texto, color, relleno, alineación, tamaño y familia de fuentes

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-text.png" alt-text="Formato del texto de botón deshabilitado":::

- **Control de relleno de botón**: color, transparencia y *nueva* imagen de relleno (más información en la sección siguiente)

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-fill.png" alt-text="Relleno de botón deshabilitado":::

- **Controles de icono**: forma, relleno, alineación, color de línea, transparencia y grosor

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-icon.png" alt-text="Iconos de botón deshabilitado":::

- **Controles de contorno**: color, transparencia, grosor y bordes redondos

     :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-outline.png" alt-text="Contorno de botón deshabilitado":::

## <a name="set-formatting-for-button-text-conditionally"></a>Establecimiento del formato de texto de botón de forma condicional
Puede usar el formato condicional para cambiar el texto del botón en función del valor seleccionado de un campo. Para ello, debe crear una medida que genere la cadena deseada según la función SELECTEDVALUE de DAX.

Esta es una medida de ejemplo que genera "Ver detalles del producto" si NO se selecciona un valor de producto único; de lo contrario, genera "Ver detalles para [el producto seleccionado]":

```dax
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0, "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

Una vez que haya creado esta medida, seleccione la opción **Formato condicional** para el texto del botón:

![Selección de Formato condicional](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Después, seleccione la medida que ha creado para el texto del botón:

![Valor basado en el campo](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

Cuando se selecciona un único producto, el texto del botón muestra:

"Ver detalles de Word"

![Si se selecciona un solo valor](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Si no se selecciona ningún producto, o bien se selecciona más de uno, el botón estará deshabilitado. El texto de botón es el siguiente:

"Vea los detalles del producto"

![Si se seleccionan varios valores](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="set-formatting-for-tooltips-conditionally"></a>Establecimiento del formato de información sobre herramientas de forma condicional

Puede aplicar formato condicionalmente a la información sobre herramientas del botón de obtención de detalles cuando está habilitado o deshabilitado. Si ha usado el formato condicional para establecer dinámicamente el destino de obtención de detalles, es recomendable que la información sobre herramientas del estado del botón sea más informativa y que se base en la selección del usuario final. Estos son algunos ejemplos:

- Puede establecer la información sobre herramientas del estado deshabilitado para que sea prescriptiva según cada caso mediante una medida personalizada. Por ejemplo, si quiere que el usuario deba seleccionar un solo producto *y* una sola tienda para poder obtener los detalles de la página de análisis de mercado, puede crear una medida con la lógica siguiente:

    Si el usuario no ha seleccionado un único producto ni una única tienda, la medida devuelve lo siguiente: "Seleccione un solo producto y haga clic mientras pulsa Ctrl para seleccionar una sola tienda".

    Si el usuario ha seleccionado un único producto, pero no una única tienda, la medida devuelve lo siguiente: "Haga clic mientras pulsa Ctrl para seleccionar también una única tienda".

- De forma similar, puede establecer la información sobre herramientas para el estado habilitado para que sea específica de la selección del usuario. Por ejemplo, si quiere que el usuario sepa según qué producto y tienda se filtrará la página de obtención de detalles, puede crear una medida que devuelva lo siguiente:

    "Haga clic para obtener los detalles de [nombre de la página de obtención de detalles] y ver más detalles sobre las ventas de [nombre del producto] en las tiendas [nombre de las tiendas]".


## <a name="set-the-drill-through-destination-conditionally"></a>Establecimiento del destino de obtención de detalles de forma condicional

Puede usar el formato condicional para establecer el destino de obtención de detalles en función de la salida de una medida.

Estos son algunos escenarios en los que podría querer que el destino de obtención de detalles del botón sea condicional:

- Solo quiere que se habilite la obtención de detalles en una página **si se cumplen varias condiciones**. De lo contrario, el botón estará deshabilitado.

    Por ejemplo, quiere que los usuarios seleccionen un solo producto *y* una sola tienda para poder obtener los detalles de la página de detalles del mercado. De lo contrario, el botón estará deshabilitado.

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-store.png" alt-text="Selección de un producto y una tienda":::
 
- Quiere que el botón **admita varios destinos de obtención de detalles** en función de las selecciones de los usuarios.

    Por ejemplo, supongamos que ofrece varios destinos (detalles del mercado y detalles de la tienda) a los usuarios. Puede hacer que deban seleccionar un destino específico de obtención de detalles para que se habilite el botón para dicho destino.

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-destination.png" alt-text="Selección del producto y el destino":::
 
- También puede tener **casos de escenario híbrido** muy interesantes en los que se admitan varios destinos de obtención de detalles y condiciones específicas para que se deshabilite el botón. Siga leyendo para obtener más información sobre estas tres opciones.

### <a name="disable-the-button-until-multiple-conditions-are-met"></a>Deshabilitación del botón hasta que se cumplan varias condiciones

Echemos un vistazo al primer caso, en el que quiere mantener el botón deshabilitado hasta que se cumplan condiciones adicionales. Debe crear una medida de DAX básica que genere una cadena vacía ("") a menos que se cumpla la condición. Cuando se cumpla, se generará el nombre de la página de destino de obtención de detalles.

A continuación se proporciona un ejemplo de medida de DAX en la que se requiere que se seleccione una tienda para que el usuario pueda obtener los detalles de una página de detalles de producto y otra de tienda:

```dax
Destination logic = If(SELECTEDVALUE(Store[Store], “”)==””, “”, “Store details”)
```

Cuando haya creado la medida, seleccione el botón de formato condicional (fx) situado junto al **destino** del botón:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-formula.png" alt-text="Selección del botón de formato condicional":::
 
En el último paso, debe seleccionar la medida de DAX que ha creado como el valor de campo para la página de destino:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-based-formula.png" alt-text="Destino basado en un campo"::: 

Ahora verá que el botón está deshabilitado incluso cuando se selecciona un solo producto, ya que la medida también requiere que seleccione una sola tienda:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-button-disabled.png" alt-text="Botón de obtención de detalles deshabilitado":::

### <a name="support-multiple-destinations"></a>Admisión de varios destinos
 
Para el otro caso común en el que quiere admitir varios destinos, debe empezar creando una tabla de una sola columna con los nombres de los destinos de obtención de detalles:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-create-table.png" alt-text="de una tabla":::

Power BI usa la coincidencia exacta de cadenas para establecer el destino de obtención de detalles, por lo que debe comprobar que los valores especificados se alineen exactamente con los nombres de las páginas de obtención de detalles.

Cuando haya creado la tabla, agréguela a la página como segmentación de selección única:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-slicer.png" alt-text="Segmentación de obtención de detalles":::
 
Si necesita más espacio vertical, convierta la segmentación en una lista desplegable. Quite el encabezado de la segmentación y agregue un cuadro de texto con el título situado junto a él:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-drop-down-slicer.png" alt-text="Segmentación de obtención de detalles sin encabezado":::
 
También puede cambiar la orientación de la segmentación de lista de vertical a horizontal:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-horizontal-slicer.png" alt-text="Segmentación horizontal":::

En la entrada de destino de la acción de obtención de detalles, seleccione el botón de formato condicional (fx) situado junto al **destino** del botón:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-formula.png" alt-text="Selección del botón de formato condicional":::
 
Seleccione el nombre de la columna que ha creado; en este caso, **Selección de un destino**:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-destination.png" alt-text="Selección de un destino":::
 
Ahora verá que el botón de obtención de detalles solo está habilitado al seleccionar un producto *y* un destino:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-destination.png" alt-text="Selección del producto y el destino":::
 
### <a name="hybrid-of-the-two-scenarios"></a>Escenario híbrido

Si le interesa usar un escenario híbrido que mezcle ambos escenarios descritos anteriormente, puede crear una referencia de DAX y hacer referencia a esta para añadir lógica adicional a la selección del destino.

A continuación se proporciona un ejemplo de medida de DAX en la que se requiere que el usuario seleccione una tienda para poder obtener los detalles de un producto en cualquier página de obtención de detalles:

```dax
Destination logic = If(SELECTEDVALUE(Store[Store], “”)==””, “”, SELECTEDVALUE(‘Table'[Select a destination]))
```

Después, seleccione la medida de DAX que ha creado como el valor de campo para la página de destino.
En este ejemplo, el usuario debe seleccionar un producto, una tienda *y* una página de destino para que se habilite el botón de obtención de detalles:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-product-store-destination.png" alt-text="Selección del producto, la tienda y el destino":::

## <a name="limitations"></a>Limitaciones

- Este botón no permite varios destinos con un solo botón.
- Este botón solo admite la obtención de detalles dentro del mismo informe; es decir, no admite la obtención de detalles entre informes.
- El formato de estado deshabilitado del botón está enlazado a las clases de color del tema del informe. Obtenga más información sobre las [clases de color](desktop-report-themes.md#setting-structural-colors).
- La acción de obtención de detalles funciona con todos los objetos visuales integrados y también con *algunos* importados desde AppSource. Sin embargo, no se garantiza que funcione con *todos* los objetos importados desde AppSource.

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre las características que son similares o que interactúan con los botones, vea los siguientes artículos:

* [Creación de botones](desktop-buttons.md)
* [Uso de la obtención de detalles en informes de Power BI](desktop-drillthrough.md)
* [Uso de marcadores para compartir información detallada y crear historias en Power BI](desktop-bookmarks.md)

