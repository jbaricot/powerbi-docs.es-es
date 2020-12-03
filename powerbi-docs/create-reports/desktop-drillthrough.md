---
title: Configuración de la obtención de detalles en informes de Power BI
description: Obtenga información sobre cómo usar la obtención de detalles para explorar en profundidad datos, en una nueva página de informe, en informes de Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 03/12/2020
LocalizationGroup: Create reports
ms.openlocfilehash: cec22acab7cc44b96f3137df04777671964707a8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414240"
---
# <a name="set-up-drill-through-in-power-bi-reports"></a>Configuración de la obtención de detalles en informes de Power BI
Con la *obtención de detalles* en informes de Power BI, puede crear una página en el informe que se centre en una entidad específica, como un proveedor, un cliente o un fabricante. Cuando los lectores del informe usan la obtención de detalles, hacen clic con el botón derecho en un punto de datos de otras páginas del informe y, después, exploran la página que tiene el foco para obtener detalles filtrados por ese contexto. También puede [crear un botón que profundice](desktop-drill-through-buttons.md) en los detalles al hacer clic en él.

Puede configurar la obtención de detalles en los informes en Power BI Desktop o en el servicio Power BI.

![Uso de la obtención de detalles](media/desktop-drillthrough/power-bi-drill-through-right-click.png)

## <a name="set-up-the-drill-through-destination-page"></a>Configuración de la página de destino de obtención de detalles
1. Para configurar la obtención de detalles, cree una página del informe que contenga los objetos visuales que quiera para el tipo de entidad en la que va a ofrecer la obtención de detalles. 

    Por ejemplo, imagine que quiere proporcionar obtención de detalles para los fabricantes. En este caso, podría crear una página de obtención de detalles con objetos visuales que muestren las ventas totales, el total de unidades enviadas, las ventas por categoría y por región, y así sucesivamente. De este modo, cuando se realiza la obtención de detalles mediante esa página, los objetos visuales son específicos del fabricante que haya seleccionado.

2. Después, en esa página de obtención de detalles, en la sección **Campos** del panel **Visualizaciones**, arrastre el campo para el que quiera habilitar la obtención de detalles al área **Filtros de obtención de detalles**.

    ![Área de obtención de detalles](media/desktop-drillthrough/drillthrough_02.png)

    Cuando se agrega un campo al área **Filtros de obtención de detalles**, Power BI crea de forma automática un objeto visual de botón *Atrás*. Ese objeto visual se convierte en un botón en los informes publicados. Los usuarios que consumen el informe en el servicio Power BI pueden usar este botón para volver a la página del informe de la que proceden.

    ![Imagen de obtención de detalles](media/desktop-drillthrough/drillthrough_03.png)

> [!IMPORTANT]
> Puede configurar y llevar a cabo la obtención de detalles de una página del mismo informe, pero no de una página de otro informe.  



## <a name="use-your-own-image-for-a-back-button"></a>Uso de su propia imagen para un botón Atrás    
 Dado que el botón Atrás es una imagen, puede reemplazar la imagen de ese objeto visual por cualquier imagen que desee. Sigue funcionando como botón Atrás para que los consumidores del informe puedan volver a la página original. 

Para usar una imagen propia para un botón Atrás, siga estos pasos:

1. En la pestaña **Inicio**, seleccione **Imagen**. Después, busque la imagen y colóquela en la página de obtención de detalles.

2. Seleccione la nueva imagen en la página de obtención de detalles. En el panel **Formato de imagen**, establezca el control deslizante **Acción** en **Activado** y luego establezca el **tipo** en **Atrás**. Ahora su imagen funciona como botón Atrás.

    ![Carga de la imagen y establecimiento del tipo en Atrás](media/desktop-drillthrough/drillthrough_05.png)

    
     Ahora los usuarios pueden hacer clic con el botón derecho en un punto de datos del informe y obtener un menú contextual que admite la obtención de detalles de esa página. 

    ![Menú de obtención de detalles](media/desktop-drillthrough/drillthrough_04.png)

    Cuando los consumidores del informe eligen la obtención de detalles, la página se filtra para mostrar información acerca del punto de datos en el que se hizo clic con el botón derecho. Por ejemplo, imagine que los usuarios han hecho clic con el botón derecho en un punto de datos sobre Contoso (un fabricante) y han seleccionado obtener detalles. La página de obtención de detalles a la que acceden está filtrada para Contoso.

## <a name="pass-all-filters-in-drill-through"></a>Paso de todos los filtros en la obtención de detalles

Puede pasar todos los filtros aplicados a la ventana de obtención de detalles. Por ejemplo, puede seleccionar solo una determinada categoría de productos y los objetos visuales filtrados por esa categoría y, luego, seleccionar la obtención de detalles. Es posible que le interese saber cuál será el aspecto de esa obtención de detalles con todos los filtros aplicados.

Para mantener todos los filtros aplicados, en la sección **Obtención de detalles** del panel **Visualizaciones**, establezca **Pasar todos los filtros** en **Activado**. 

![Mantener todos los filtros](media/desktop-drillthrough/drillthrough_06.png)

Cuando se obtienen detalles sobre un objeto visual, puede ver los filtros que se han aplicado como resultado de la aplicación de filtros temporales en el objeto visual de origen. En la sección **Obtención de detalles** del panel **Visualización**, esos filtros transitorios se muestran en cursiva. 

![Filtros temporales en cursiva](media/desktop-drillthrough/drillthrough_07.png)

Aunque esto se podría hacer con páginas de información sobre herramientas, sería una experiencia extraña, porque daría la impresión de que la información sobre herramientas no funciona correctamente. Por este motivo, no se recomienda hacerlo con información sobre herramientas.

## <a name="add-a-measure-to-drill-through"></a>Adición de una medida para la obtención de detalles

Además de pasar todos los filtros a la ventana de obtención de detalles, puede agregar una medida o una columna numérica de resumen al área sometida a la obtención de detalles. Arrastre el campo de obtención de detalles a la tarjeta **Obtención de detalles** para aplicarlo. 

![Adición de una medida para la obtención de detalles](media/desktop-drillthrough/drillthrough_08.png)

Al agregar una medida o una columna numérica de resumen, si usa el campo en el área *Valor* de un objeto visual, puede obtener detalles relativos a la página.

Eso es todo lo necesario para usar la obtención de detalles en los informes. Es una excelente manera de obtener una vista ampliada de la información de la entidad seleccionada para el filtro de obtención de detalles.

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Uso de la obtención de detalles entre varios informes de Power BI](desktop-cross-report-drill-through.md)
* [Uso de segmentaciones de datos en Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
