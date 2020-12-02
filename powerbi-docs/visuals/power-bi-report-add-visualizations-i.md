---
title: 'Parte 1: Incorporación de visualizaciones a un informe de Power BI'
description: 'Parte 1: Incorporación de visualizaciones a un informe de Power BI'
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 4d4b04b10e45d67fdd4d7cb183e300587d4f2cc6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412492"
---
# <a name="add-visuals-to-a-power-bi-report-part-1"></a>Adición de objetos visuales a un informe de Power BI (parte 1)

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

En este artículo, se ofrece una introducción rápida a la creación de una visualización en un informe. Se aplica al servicio Power BI y a Power BI Desktop. Para obtener contenido más avanzado, [vea la parte 2](power-bi-report-add-visualizations-ii.md) de esta serie.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa el [archivo Sales & marketing PBIX](https://download.microsoft.com/download/9/7/6/9767913A-29DB-40CF-8944-9AC2BC940C53/Sales%20and%20Marketing%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús de Power BI Desktop, seleccione **Archivo** > **Abrir**.
   
2. Busque su copia del **archivo .PBIX del ejemplo de ventas y marketing**.

1. Abra el **archivo PBIX de Ventas y marketing** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.

> [!NOTE]
> Para compartir el informe con un compañero en Power BI es necesario que los dos tengan licencias de Power BI Pro individuales o que el informe esté guardado en la capacidad Premium. Consulte [cómo compartir informes](../collaborate-share/service-share-reports.md).

## <a name="add-visualizations-to-the-report"></a>Agregar visualizaciones al informe

1. Cree una visualización seleccionando un campo en el panel **Campos** .

    Comience con un campo numérico como **Sales** (Ventas) > **TotalSales** (Ventas totales). Power BI crea un gráfico de columnas con una sola columna.

    ![Captura de pantalla de un gráfico de columnas con una sola columna.](media/power-bi-report-add-visualizations-i/power-bi-column-chart.png)

    O bien, comience con un campo de categoría, como **Nombre** o **Producto**. Power BI crea una tabla y agrega ese campo también a **Valores**.

    ![Captura de pantalla de una tabla con cuatro categorías](media/power-bi-report-add-visualizations-i/power-bi-product.png)

    O bien, comience con un campo de geografía, como **Geografía** > **Ciudad**. Power BI y mapas de Bing crean una visualización de mapa.

    ![Captura de pantalla de una visualización de mapa.](media/power-bi-report-add-visualizations-i/power-bi-maps.png)

## <a name="change-the-type-of-visualization"></a>Cambio del tipo de visualización

 Cree una visualización y, a continuación, cambie su tipo. 
 
 1. Seleccione **Producto** > **Categoría** y después **Producto** > **Recuento de productos** para agregarlos al área **Valores**.

    ![Captura de pantalla del panel Campos con los valores resaltados.](media/power-bi-report-add-visualizations-i/power-bi-create-visual.png)

1. Cambie la visualización a un gráfico de columnas mediante la selección del icono **Gráfico de columnas apiladas**.

   ![Captura de pantalla del panel Visualizaciones con el icono Gráfico de columnas apiladas resaltado.](media/power-bi-report-add-visualizations-i/power-bi-convert.png)

1. Para cambiar la forma en que se ordena el objeto visual, seleccione **Más opciones** (...).  Use las opciones de ordenación para cambiar la dirección de la ordenación (ascendente o descendente) y cambiar la columna que se usa para ordenar (**Ordenar por**).

   ![Captura de pantalla de la lista desplegable Más opciones.](media/power-bi-report-add-visualizations-i/power-bi-sort.png)
  
## <a name="next-steps"></a>Pasos siguientes

 Continúe con:

* [Parte 2: Incorporación de visualizaciones a un informe de Power BI](power-bi-report-add-visualizations-ii.md)

* [Interactuar con las visualizaciones](../consumer/end-user-reading-view.md) en el informe.
