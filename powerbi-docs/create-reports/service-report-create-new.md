---
title: 'Creación de un informe a partir de un archivo de Excel en el servicio Power BI '
description: Cree un informe a partir de un archivo de Excel en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: a971e0d0b35b0a3988a1c10ea2b7b801830229d6
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721556"
---
# <a name="create-a-report-from-an-excel-file-in-the-power-bi-service"></a>Creación de un informe a partir de un archivo de Excel en el servicio Power BI
Ha leído [Informes en Power BI](../consumer/end-user-reports.md) y ahora desea crear los suyos propios. Hay diferentes formas de crear un informe. En este artículo, comenzaremos por crear un informe básico en el servicio Power BI a partir de un archivo de Excel. Una vez que conozca los aspectos básicos de la creación de informes, consulte la sección [Pasos siguientes](#next-steps) al final de la página para ver temas de informes más avanzados.  

## <a name="prerequisites"></a>Requisitos previos
- [Suscribirse al servicio Power BI](../fundamentals/service-self-service-signup-for-power-bi.md). 
- [Descargar el archivo de Excel del Ejemplo de análisis de minoristas](https://go.microsoft.com/fwlink/?LinkId=529778) y guardarlo en el equipo o en OneDrive para la Empresa.

## <a name="import-the-excel-file"></a>Importación del archivo de Excel
Este método de creación de informes comienza con un archivo y un lienzo de informe en blanco. Puede continuar con el archivo del Ejemplo de análisis de minoristas.

1. En el panel de navegación, seleccione **Mi área de trabajo**.
   
   :::image type="content" source="media/service-report-create-new/power-bi-select-my-workspace.png" alt-text="Captura de pantalla de la selección de Mi área de trabajo.":::
2. Seleccione **Obtener datos** en la parte inferior del panel de navegación.
   
   ![Obtener datos](media/service-report-create-new/power-bi-get-data3.png)
3. Seleccione **Archivos** y navegue hasta la ubicación en que guardó el archivo Retail Analysis Sample.
   
    ![Selección de Archivos](media/service-report-create-new/power-bi-select-files.png)
4. Para este ejercicio, seleccione **Importar**.
   
   ![Selección de Importar](media/service-report-create-new/power-bi-import.png)
5. Seleccione **Abrir**.

   Una vez importado el archivo de Excel, se muestra como *conjunto de datos* en la lista de áreas de trabajo.

1. Seleccione **Más opciones (...)** junto al conjunto de datos y luego **Crear informe**.
   
   :::image type="content" source="media/service-report-create-new/power-bi-dataset-create-report.png" alt-text="Captura de pantalla de la selección de Crear informe.":::
6. Se abre el editor de informes. 
   
   ![Captura de pantalla del editor de informes.](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Seleccione el icono de menú para ocultar el panel de navegación y, de este modo, obtener más espacio.
> 
> :::image type="content" source="../media/power-bi-hide-navigation-pane.png" alt-text="Captura de pantalla con la selección del icono de menú para ocultar el panel de navegación.":::


## <a name="add-a-radial-gauge-to-the-report"></a>Adición de un medidor radial al informe
Una vez que ha importado el conjunto de datos, ha llegado el momento de responder algunas preguntas.  Nuestro director de marketing (CMO) desea saber lo cerca que estamos de cumplir los objetivos de ventas de este año. Un medidor es una [buena opción de visualización](../visuals/power-bi-report-visualizations.md) para mostrar este tipo de información.

1. En el panel Campos, seleccione **Ventas** > **Ventas de este año** > **Valor**.
   
    ![Gráfico de barras en el editor de informes](media/service-report-create-new/power-bi-report-step1.png)
2. Para convertir el objeto visual en un medidor, seleccione la plantilla Medidor ![icono de medidor](media/service-report-create-new/powerbi-gauge-icon.png) en el panel **Visualizaciones**.
   
    ![Objeto visual de medidor en el editor de informes](media/service-report-create-new/power-bi-report-step2.png)
3. Arrastre **Ventas** > **Ventas de este año** > **Objetivo** al área **Valor del objetivo**. Parece que estamos muy cerca de nuestro objetivo.
   
    ![Objeto visual de medidor con Objetivo como Valor del objetivo](media/service-report-create-new/power-bi-report-step3.png)
4. Este sería un buen momento para guardar el informe.
   
   ![Menú Archivo](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Adición de un gráfico de áreas y segmentación de datos al informe
Nuestro director de marketing quiere que respondamos a varias preguntas más. Quiere ver la comparación de las ventas de este año con las del año anterior. Y también quiere ver los resultados por distrito.

1. En primer lugar, vamos a hacer algo de espacio en el lienzo. Seleccione el medidor y muévalo a la esquina superior derecha. Después, arrastre una de las esquinas para hacerlo menor.
2. Anule la selección del medidor. En el panel Campos, seleccione **Ventas** > **Ventas de este año** > **Valor** y seleccione **Ventas** > **Ventas del año anterior**.
   
    ![Editor de informes con medidor y gráfico de barras](media/service-report-create-new/power-bi-report-step4.png)
3. Para convertir el objeto visual en un gráfico de áreas, seleccione la plantilla Gráfico de áreas ![icono de gráfico](media/service-report-create-new/power-bi-areachart-icon.png) en el panel **Visualizaciones**.
4. Seleccione **Tiempo** > **Período** para agregarlo al área **Ejes**.
   
    ![Editor de informes con gráfico de áreas activo](media/service-report-create-new/power-bi-report-step5.png)
5. Para ordenar la visualización por período de tiempo, seleccione los puntos suspensivos y elija **Sort by Period**.
6. Ahora vamos a agregar la segmentación de datos. Seleccione un área vacía en el lienzo y elija la plantilla ![icono de segmentación](media/service-report-create-new/power-bi-slicer-icon.png) Segmentación. Ahora tenemos una segmentación de datos vacía en nuestro lienzo.
   
    ![el lienzo del informe](media/service-report-create-new/power-bi-report-step6.png)    
7. En el panel Campos, seleccione **Distrito**  >  **Distrito**. Mueva la segmentación de datos y cámbiela de tamaño.
   
    ![Editor de informes, adición de Distrito](media/service-report-create-new/power-bi-report-step7.png)  
8. Use la segmentación de datos para buscar patrones e información por distrito.
   
   ![Vídeo de uso de la segmentación](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continúe explorando los datos y agregando visualizaciones. Cuando encuentre una información especialmente interesante, [ánclela a un panel](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Pasos siguientes

* [Anclar visualizaciones a un panel](service-dashboard-pin-tile-from-report.md)
* [Cambiar la configuración del informe en el servicio Power BI](power-bi-report-settings.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
