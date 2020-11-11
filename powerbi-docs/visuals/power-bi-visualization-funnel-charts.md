---
title: Gráficos de embudo
description: Gráficos de embudo en Power BI
author: msftrien
ms.reviewer: mihart
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 2719127825dc94f1f1bd83fe4d36dc47dfc355f7
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412910"
---
# <a name="create-and-use-funnel-charts"></a>Creación y uso de gráficos de embudo

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

Los gráficos de embudo ayudan a visualizar un proceso lineal con fases secuenciales conectadas. Por ejemplo, un embudo de ventas que realiza el seguimiento de los clientes a través de las fases: cliente potencial \> cliente potencial calificado \> prospecto \> contrato \> cierre.  De un vistazo, la forma del embudo indica el estado del proceso del que está realizando el seguimiento.

Cada fase del embudo representa un porcentaje del total. Por lo tanto, en la mayoría de los casos, un gráfico de embudo tiene la forma de embudo: la primera fase es la más grande y cada fase posterior es menor que su predecesora.  Los embudos en forma de pera también son útiles, porque pueden identificar un problema en el proceso.  Pero por lo general, la primera fase, la fase de "entrada", es la de mayor tamaño.

![Embudo de color azul de ejemplo](media/power-bi-visualization-funnel-charts/funnelplain.png)

> [!NOTE]
> Para compartir el informe con un compañero en Power BI es necesario que los dos tengan licencias de Power BI Pro individuales o que el informe esté guardado en la capacidad Premium.    

## <a name="when-to-use-a-funnel-chart"></a>Cuándo usar un gráfico de embudo
Los gráficos de embudo son una excelente opción:

* Cuando los datos son secuenciales y se mueven por al menos 4 fases.
* Cuando se espera que el número de "elementos" de la primera fase sea mayor que el número de la fase final.
* Para calcular el potencial (ingresos, ventas, ofertas, etc.) por fases.
* Para calcular las tasas de conversión y retención y realizar un seguimiento de las mismas.
* Para mostrar cuellos de botella en un proceso lineal.
* Para realizar el seguimiento del flujo de trabajo de un carro de la compra.
* Para realizar el seguimiento del progreso y el éxito de las campañas de marketing y publicidad de click-through.

## <a name="working-with-funnel-charts"></a>Trabajar con gráficos de embudo
Gráficos de embudo:

* Se pueden ordenar.
* Se admiten múltiples gráficos.
* Otras visualizaciones pueden resaltarlo y realizar un filtrado cruzado en la misma página del informe.
* Se pueden usar para resaltar y realizar un filtrado cruzado de otras visualizaciones en la misma página del informe.
   > [!NOTE]
   > Vea este vídeo para observar cómo se crea un gráfico de embudo con el Ejemplo de marketing y ventas. Después, siga los pasos que aparecen debajo del vídeo para probarlo usted mismo mediante el archivo PBIX del Ejemplo de análisis de oportunidades.
   > 
   > 
## <a name="prerequisite"></a>Requisito previo

Este tutorial usa el [archivo PBIX del Ejemplo de análisis de oportunidades](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix
).

1. En la sección superior izquierda de la barra de menús, seleccione **Archivo** > **Abrir**.
   
2. Busque la copia del **archivo PBIX del Ejemplo de análisis de oportunidades**.

1. Abra el **archivo PBIX del Ejemplo de análisis de oportunidades** en la vista de informe ![Captura de pantalla del icono de vista de informe](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Seleccionar ![Captura de pantalla de la pestaña amarilla.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para agregar una nueva página.


## <a name="create-a-basic-funnel-chart"></a>Crear un gráfico de embudo básico
Vea este vídeo para observar cómo se crea un gráfico de embudo con el Ejemplo de marketing y ventas.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


Ahora cree su propio gráfico de embudo que muestre la cantidad de oportunidades que cada uno de nosotros tiene en nuestras fases de ventas.

1. Comience en una página de informe en blanco y seleccione el campo **Fase de ventas** \> **Fase de ventas**.
   
    ![Selección de Fase de ventas](media/power-bi-visualization-funnel-charts/funnelselectfield-new.png)

1. Seleccione el icono de embudo ![Icono de gráfico de embudo](media/power-bi-visualization-funnel-charts/power-bi-funnel-icon.png) para convertir el gráfico de columnas en un gráfico de embudo.

2. En el panel **Campos** , seleccione **Hecho** \> **Recuento de oportunidades**.
   
    ![Creación del gráfico de embudo](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. Al mantener el mouse sobre una barra se muestra una gran cantidad de información.
   
   * El nombre de la fase
   * El número de oportunidades en esta fase
   * La tasa de conversión general (% de Clientes potenciales) 
   * Tasa de etapa a etapa (también conocida como tasa de abandono) que es el porcentaje de la fase anterior (en este caso, fase propuesta/fase de solución)
     
     ![Detalles de la barra Propuesta](media/power-bi-visualization-funnel-charts/funnelhover-new.png)

6. [Guarde el informe](../create-reports/service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Resaltado y filtrado cruzado
Para más información acerca de cómo usar el panel Filtros, consulte [Agregar un filtro a un informe](../create-reports/power-bi-report-add-filter.md).

Al resaltar una barra en un gráfico de embudo, se realiza un filtrado cruzado de las demás visualizaciones en la página del informe, y viceversa. Para poder continuar, agregue algunos objetos visuales más a la página de informe que contiene el gráfico de embudo.

1. En el embudo, seleccione la barra **Propuesta**. Esto realiza un resaltado cruzado de las demás visualizaciones de la página. Use CTRL para realizar una selección múltiple.
   
   ![Vídeo breve en el que se muestran las interacciones de objetos visuales](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. Para establecer las preferencias del resaltado cruzado y del filtrado cruzado de los objetos visuales, consulte [Interacciones visuales en Power BI](../create-reports/service-reports-visual-interactions.md).

## <a name="next-steps"></a>Pasos siguientes

[Medidores en Power BI](power-bi-visualization-radial-gauge-charts.md)

[Tipos de visualización en Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)



