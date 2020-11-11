---
title: Gráficos combinados en Power BI
description: Este tutorial acerca de los gráficos combinados explica cuándo utilizarlos y cómo se crean en el servicio Power BI y Power BI Desktop.
author: msftrien
ms.reviewer: mihart
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 89fdd0852db9560a6e2b0d43e03b9f89c61dd33e
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93411576"
---
# <a name="create-and-use-combo-charts-in-power-bi"></a>Creación y uso de gráficos combinados en Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

En Power BI, un gráfico combinado es una visualización única que combina un gráfico de líneas y un gráfico de columnas. La combinación de los dos gráficos en uno permite realizar una comparación más rápida de los datos.

Los gráficos combinados pueden tener uno o dos ejes Y.

## <a name="when-to-use-a-combo-chart"></a>Cuándo usar un gráfico combinado
Los gráficos combinados son una excelente opción:

* Si tiene un gráfico de líneas y un gráfico de columnas con el mismo eje X.
* Para comparar varias medidas con distintos intervalos de valores.
* Para ilustrar la correlación entre dos medidas en una visualización.
* Para comprobar si una medida cumple el objetivo que se define mediante otra medida.
* Para ahorrar espacio en el lienzo.

> [!NOTE]
> Para compartir el informe con un compañero en Power BI es necesario que los dos tengan licencias de Power BI Pro individuales o que el informe esté guardado en la capacidad Premium.

### <a name="prerequisites"></a>Requisitos previos
En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.



## <a name="create-a-basic-single-axis-combo-chart"></a>Crear un gráfico combinado básico con un eje único
Vea cómo Will crea un gráfico combinado con el Ejemplo de marketing y ventas.
   > [!NOTE]
   > En este vídeo se usa una versión anterior de Power BI Desktop.
   > 
   > 
<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

<a name="create"></a>

1. Empiece en una página de informe en blanco y cree un gráfico de columna que muestre las ventas de este año y el margen bruto por mes.

    a.  En el panel Campos, seleccione **Ventas** \> **Ventas de este año** > **Valor**.

    b.  Arrastre **Ventas** \> **Margen bruto de este año** al área **Valor**.

    c. Seleccione **Tiempo** \> **Mes fiscal** para agregarlo al área **Eje**.

    ![Ejemplo de tutorial combinado](media/power-bi-visualization-combo-chart/combotutorial1new.png)
5. Seleccione **Más opciones** (...) en la esquina superior derecha de la visualización y, después, seleccione **Ordenar por > FiscalMonth** (MesFiscal). Para cambiar el criterio de ordenación, vuelva a hacer clic en los puntos suspensivos y elija **Orden ascendente** u **Orden descendente**. En este ejemplo, se usará **Orden ascendente**.

6. Convierta el gráfico de columnas en un gráfico combinado. Hay dos gráficos combinados disponibles: **Gráfico de columnas apiladas y de líneas** y **Gráfico de columnas agrupadas y de líneas**. Con el gráfico de columnas seleccionado, en el panel **Visualizaciones** , seleccione el **Gráfico de columnas agrupadas y de líneas**.

    ![Ejemplo de conversión de gráfico combinado](media/power-bi-visualization-combo-chart/converttocombo-new2.png)
7. En el panel **Campos** , arrastre **Ventas** \> **Ventas del año anterior** al cubo **Valores de líneas**.

   ![Área Valores de línea en la que se muestran las ventas del año anterior](media/power-bi-visualization-combo-chart/linevaluebucket.png)

   El gráfico combinado debe tener un aspecto similar al siguiente:

   ![Ejemplo de gráfico combinado terminado](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>Crear un gráfico combinado con dos ejes
En esta tarea, compararemos el margen bruto y las ventas.

1. Cree un nuevo gráfico de líneas que realice un seguimiento del **Porcentaje de margen bruto del último año** por **FiscalMonth**. Haga clic en los puntos suspensivos para ordenar por **Mes** y **Ascendente**.  
En enero el porcentaje de margen bruto fue de un 35 %, en abril alcanzó un máximo de un 45 %, en julio descendió y luego volvió a alcanzar otro máximo en agosto. ¿Se verá un patrón similar en las ventas del año anterior y este año?

   ![Ventas de ejemplo de gráfico combinado](media/power-bi-visualization-combo-chart/combo1-new.png)
2. Agregue **Ventas de este año > Valor** y **Ventas del último año** al gráfico de líneas. La escala de **porcentaje de margen bruto del último año** es mucho menor que la escala de **Ventas** , lo que dificulta la comparación.      

   ![Ejemplo de línea plana de gráfico combinado](media/power-bi-visualization-combo-chart/flatline-new.png)
3. Para que el objeto visual sea fácil de leer e interpretar, convierta el gráfico de líneas en un gráfico de columnas apiladas y de líneas.

   ![Ejemplo de conversión de gráfico combinado](media/power-bi-visualization-combo-chart/converttocombo-new.png)

4. Arrastre el **Porcentaje de margen bruto del último año** de **Valores de columnas** a **Valores de líneas**. Power BI crea dos ejes, lo que permite escalar los conjuntos de datos de forma distinta; el izquierdo mide ventas en dólares y el derecho mide porcentajes. Y vemos la respuesta a nuestra pregunta; sí, vemos un patrón similar.

   ![Ejemplo de clúster de gráfico combinado](media/power-bi-visualization-combo-chart/power-bi-clustered-combo.png)    

## <a name="add-titles-to-the-axes"></a>Agregar títulos a los ejes
1. Seleccione el icono de rodillo de pintura ![Icono de rodillo de pintar](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) para abrir el panel Formato.
1. Seleccione la flecha hacia abajo para expandir las opciones del **eje Y** .
1. Para **Eje Y (columna)** , establezca **Posición** en **Izquierda** , **Título** en **Activado** , **Estilo** en **Mostrar solo el título** y **Mostrar unidades** en **Millones**.

   ![Ejemplo de apertura de y de gráfico combinado](media/power-bi-visualization-combo-chart/power-bi-open-y.png)
4. En **Eje Y (columna)** , desplácese hacia abajo hasta que vea **Mostrar secundario**. Dado que hay tantas opciones para los ejes Y, puede que tenga que usar ambas barras de desplazamiento. La sección Mostrar secundario muestra opciones para dar formato a la parte de gráfico de líneas del gráfico combinado.

   ![Ejemplo de gráfico combinado secundario](media/power-bi-visualization-combo-chart/power-bi-secondary.png)
5. Para **Eje Y (línea)** , deje **Posición** como **Derecha** , establezca **Título** como **Activado** y **Estilo** como **Mostrar solo el título**.

   El gráfico combinado ahora muestra los dos ejes, ambos con títulos.

   ![Ejemplo de títulos de gráfico combinado](media/power-bi-visualization-combo-chart/power-bi-2-titles.png)

6. Si lo desea, modifique la fuente, tamaño y color del texto y establezca otras opciones de formato para mejorar la legibilidad del gráfico y la presentación.

Desde aquí puede realizar las siguientes acciones:

* [Agregue el gráfico combinado como un icono de panel](../create-reports/service-dashboard-tiles.md).
* [Guarde el informe](../create-reports/service-report-save.md).
* [Haga que el informe sea más accesible para personas con discapacidades](../create-reports/desktop-accessibility-overview.md).

## <a name="cross-highlighting-and-cross-filtering"></a>Resaltado cruzado y filtrado cruzado

Al resaltar una columna o una línea en un gráfico combinado, se realiza un resaltado cruzado y un filtrado cruzado de las demás visualizaciones en la página del informe y viceversa. Para cambiar este comportamiento predeterminado, use [Interacciones de objetos visuales](../create-reports/service-reports-visual-interactions.md).

## <a name="next-steps"></a>Pasos siguientes

[Gráficos de anillos en Power BI](power-bi-visualization-doughnut-charts.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
