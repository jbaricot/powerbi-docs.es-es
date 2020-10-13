---
title: Uso de gráficos de cinta de opciones en Power BI
description: Creación y uso de gráficos de cinta en Power BI Desktop
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 0e5687f9bb3f27af7bdfee28cd9753fbda4fa44f
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635778"
---
# <a name="create-ribbon-charts-in-power-bi"></a>Creación de gráficos de cinta en Power BI

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Puede usar gráficos de cinta para visualizar y detectar rápidamente qué categoría de datos tiene la clasificación más alta (el valor mayor). Los gráficos de cinta de opciones son eficaces para mostrar un cambio de clasificación, con el intervalo más alto (valor) siempre en la parte superior de cada período de tiempo. 

![La captura de pantalla muestra un gráfico de la barra de herramientas con datos para Audio, Teléfonos móviles y otras categorías mostradas por año y trimestre.](media/desktop-ribbon-charts/ribbon-charts-01.png)

> [!NOTE]
> Para compartir el informe con un compañero en Power BI es necesario que los dos tengan licencias de Power BI Pro individuales o que el informe esté guardado en la capacidad Premium. Consulte [cómo compartir informes](../collaborate-share/service-share-reports.md).

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se usa el [archivo PBIX del Ejemplo de análisis de minoristas](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de minoristas**.

1. Abra el **archivo PBIX del Ejemplo de análisis de minoristas** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.

## <a name="create-a-ribbon-chart"></a>Creación de un gráfico de cinta de opciones

1. Para crear un gráfico de cinta de opciones, seleccione **Gráfico de la barra de herramientas** en el panel **Visualizaciones**.

    ![Plantillas de visualización](media/desktop-ribbon-charts/power-bi-template.png)

    Los gráficos de la barra de herramientas conectan una categoría de datos en el universo de tiempo visualizado mediante cintas, lo que permite ver cómo se clasifica una categoría determinada a lo largo del intervalo del eje x del gráfico (normalmente la escala de tiempo).

2. Seleccione campos para **Eje**, **Leyenda** y **Valor**.  En este ejemplo, se ha seleccionado lo siguiente: **Store** > **OpenDate** (Tienda>Fecha abierta), **Item** > **Category** (Artículo>Categoría) y **Sales** > **This year sales** > **Value** (Ventas>Ventas de este año>Valor).  

    ![Campos seleccionados](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Como el conjunto de datos solo contiene datos de un año, se ha eliminado el campo **Year** (Año) y **Quarter** (Trimestre) de **Eje**.

3. En el gráfico de la barra de herramientas se muestra la clasificación para cada mes. Observe cómo cambia la clasificación en el tiempo. Por ejemplo, la categoría Home (Inicio) se desplaza de la segunda a la quinta posición, de febrero a marzo.

    ![La captura de pantalla muestra el gráfico de la barra de herramientas que creó con algunos datos convocados.](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Formato de un gráfico de cinta de opciones
Cuando se crea un gráfico de cinta de opciones, hay opciones de formato disponibles en la sección **Formato** del panel **Visualizaciones**. Las opciones de formato para los gráficos de cinta de opciones son similares a las de un gráfico de columnas apiladas, con opciones de formato adicionales que son específicas de las cintas de opciones.

![La captura de pantalla muestra el icono de formato seleccionado y el área Barras de herramientas expandida.](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Estas opciones de formato para los gráficos de la barra de herramientas permiten realizar ajustes.

* **Espaciado** le permite ajustar la cantidad de espacio que aparece entre las cintas de opciones. El número es el porcentaje del alto máximo de la columna.
* **Coincidir con el color de la serie** permite hacer coincidir el color de las cintas de opciones con el color de la serie. Cuando se establece en **desactivado**, las cintas aparecen en color gris.
* **Transparencia** especifica la transparencia de las cintas de opciones, con el valor predeterminado de 30.
* **Borde** le permite colocar un borde oscuro en la parte superior e inferior de las cintas de opciones. De forma predeterminada, los bordes están desactivados.

Como el gráfico de la barra de herramientas no tiene etiquetas en el eje Y, puede que le interese agregar etiquetas de datos. En el panel Formato, seleccione **Etiquetas de datos**. 

![Opciones de formato para las etiquetas de datos](media/desktop-ribbon-charts/power-bi-labels.png)

Establezca las opciones de formato para las etiquetas de datos. En este ejemplo, se ha establecido el color del texto en blanco y las unidades de visualización en miles.

![La captura de pantalla muestra el gráfico de la barra de herramientas con formato final.](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Pasos siguientes

[Gráficos de dispersión y de burbujas de Power BI](power-bi-visualization-scatter.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
