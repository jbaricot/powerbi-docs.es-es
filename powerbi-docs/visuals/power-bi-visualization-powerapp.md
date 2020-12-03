---
title: Insertar una nueva instancia de Power Apps en un informe de Power BI
description: Inserte una aplicación que use el mismo origen de datos y se pueda filtrar como otros elementos de informe.
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: tapan maniar
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 06/01/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 1c4086d6ab71bd96ba7ac6c6985161d28a4dcb8b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418886"
---
# <a name="tutorial-embed-a-power-apps-visual-in-a-power-bi-report"></a>Tutorial: Insertar un objeto visual de Power Apps en un informe de Power BI

En este tutorial, se usa el objeto visual de Power Apps para crear una aplicación que se inserta en un informe de Power BI de ejemplo. Esta aplicación interactúa con otros objetos visuales de ese informe.

Si no tiene una suscripción a Power Apps, [cree una cuenta gratuita](https://make.powerapps.com/signup?redirect=marketing&email=) antes de comenzar.

En este tutorial, obtendrá información sobre cómo:
> [!div class="checklist"]
> * Agregar un objeto visual de Power Apps en un informe de Power BI
> * Trabajar en Power Apps para crear una aplicación que use datos del informe de Power BI
> * Ver e interactuar con el objeto visual de Power Apps en el informe

## <a name="prerequisites"></a>Requisitos previos

* El explorador [Google Chrome](https://www.google.com/chrome/browser/) o [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge)
* Una [suscripción a Power BI](../fundamentals/service-self-service-signup-for-power-bi.md), con el [Ejemplo de análisis de oportunidades](../create-reports/sample-opportunity-analysis.md#get-the-content-pack-for-this-sample) instalado
* Conocimientos sobre cómo [crear aplicaciones en Power Apps](/powerapps/maker/canvas-apps/data-platform-create-app-scratch) y cómo [editar informes de Power BI](../create-reports/service-the-report-editor-take-a-tour.md)



## <a name="create-a-new-app"></a>Crear una aplicación
Al agregar el objeto visual de Power Apps al informe, se inicia Power Apps Studio con una conexión de datos dinámica entre Power Apps y Power BI.

1. Abra el informe Ejemplo de análisis de oportunidades y seleccione la página *Próximas oportunidades*. 


2. Mueva y cambie el tamaño de algunos de los iconos de informe para dejar espacio para el nuevo objeto visual.

    ![Mover y cambiar el tamaño de los iconos de informe](media/power-bi-visualization-powerapp/power-bi-report-page.jpg)

2. En el panel Visualizaciones, seleccione el icono de Power Apps y, a continuación, cambie el tamaño del objeto visual para ajustarlo al espacio que dejó.

    ![Panel Visualizaciones con el icono de Power Apps seleccionado](media/power-bi-visualization-powerapp/power-bi-powerapps-icon.jpg)

3. En el panel **Campos**, seleccione **Nombre**, **Código de producto** y **Fase de ventas**. 

    ![seleccionar campos](media/power-bi-visualization-powerapp/power-bi-fields.png)

4. En el objeto visual de Power Apps, seleccione el entorno de Power Apps donde quiera crear la aplicación y, después, seleccione **Crear nuevo**.

    ![Crear la aplicación](media/power-bi-visualization-powerapp/power-bi-create-new-powerapp.png)

    En Power Apps Studio, verá que se ha creado una aplicación básica, con una *galería* en la que se muestra uno de los campos seleccionados en Power BI.

    ![Se abre Power Apps](media/power-bi-visualization-powerapp/power-bi-power-app.png)

5.  Cambie el tamaño de la galería para que solo ocupe la mitad de la pantalla. 

6. En el panel de la izquierda, seleccione **Screen1** y, después, establezca la propiedad **Relleno** de la pantalla en "LightBlue" (para que se presente mejor en el informe).

    ![paleta de colores](media/power-bi-visualization-powerapp/power-bi-powerapps-fill.png)

6. Deje algo de espacio para un control de etiqueta. 

    ![cambiar las dimensiones de la galería](media/power-bi-visualization-powerapp/power-bi-powerapps-gallery.png)


8. En **Galería**, inserte un control de etiqueta de texto.

   ![control de etiqueta](media/power-bi-visualization-powerapp/power-bi-label.png)

7. Arrastre la etiqueta hasta la parte inferior del objeto visual. Establezca la propiedad **Texto** en `"Opportunity Count: " & CountRows(Gallery1.AllItems)`. Ahora se muestra el número total de oportunidades en el conjunto de datos.

    ![Aplicación con la galería cambiada de tamaño](media/power-bi-visualization-powerapp/power-bi-power-app-label.png)

    ![Aplicación con la etiqueta actualizada](media/power-bi-visualization-powerapp/power-bi-label-live.png)

7. Guarde la aplicación con el nombre "Aplicación Oportunidades". 

    ![guardar la aplicación](media/power-bi-visualization-powerapp/power-bi-save-powerapp.png)


## <a name="view-the-app-in-the-report"></a>Ver la aplicación en el informe
Ahora la aplicación está disponible en el informe de Power BI e interactúa con otros objetos visuales porque comparte el mismo origen de datos.

![Aplicación en el informe de Power BI](media/power-bi-visualization-powerapp/power-bi-powerapps-visual.png)

En el informe de Power BI, haga clic en **Jan** (enero) en la segmentación de datos, para que se filtre todo el informe, incluidos los datos de la aplicación.

![informe filtrado](media/power-bi-visualization-powerapp/power-bi-last.png)

Tenga en cuenta que el recuento de oportunidades en la aplicación coincide con el número de la parte superior izquierda del informe. Puede seleccionar otros elementos en el informe y los datos de la aplicación se actualizarán.


## <a name="clean-up-resources"></a>Limpiar los recursos
Si ya no quiere usar el Ejemplo de análisis de oportunidades, puede eliminar el panel, el informe y el conjunto de datos.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones
Para obtener información de solución de problemas, vea [Objeto visual de Power Apps para Power BI](/powerapps/maker/canvas-apps/powerapps-custom-visual#limitations-of-the-power-apps-visual)

## <a name="next-steps"></a>Pasos siguientes
[Objeto visual Preguntas y respuestas](power-bi-visualization-types-for-reports-and-q-and-a.md)    
[Tutorial: Inserción de un objeto visual de Power Apps en un informe de Power BI](/powerapps/maker/canvas-apps/powerapps-custom-visual)