---
title: 'Tutorial: Introducción a la creación en el servicio Power BI'
description: Introducción al servicio Power BI en línea (app.powerbi.com)
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.date: 07/08/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: eeda30e5a075166af3718084c2c9f7737f876cbe
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861116"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>Tutorial: Introducción a la creación en el servicio Power BI
Este tutorial es una introducción a algunas de las características del *servicio Power BI*. En este servicio se conecta a los datos, se crea un informe y un panel y se formulan preguntas de los datos. Puede hacer mucho más en el servicio Power BI; este tutorial es solo para abrir boca. Para entender cómo encaja el servicio Power BI con otras ofertas de Power BI, es recomendable leer primero [¿Qué es Power BI?](power-bi-overview.md).

¿Es usted un *lector*, no un creador? Le recomendamos que comience por [Moverse por el servicio Power BI](../consumer/end-user-experience.md)

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Captura de pantalla del panel de ejemplo financiero.":::

En este tutorial, realizaremos los siguientes pasos:

> [!div class="checklist"]
> * Iniciar sesión en la cuenta de Power BI en línea (o bien registrarse, si todavía no tiene una).
> * Abrir el servicio Power BI.
> * Obtener algunos datos y abrirlos en la vista de informe.
> * Usar esos datos para crear visualizaciones y guardarlos como un informe.
> * Crear un panel anclando iconos desde el informe.
> * Agregar otras visualizaciones al panel mediante la herramienta de lenguaje natural Preguntas y respuestas.
> * Cambiar el tamaño, reorganizar y editar los detalles de los iconos en el panel.
> * Limpiar los recursos mediante la eliminación del conjunto de datos, el informe y el panel.

## <a name="sign-up-for-the-power-bi-service"></a>Suscribirse al servicio Power BI
Para crear contenido en Power BI, hace falta una licencia de Power BI Pro. Si no tiene una cuenta de Power BI, [regístrese para obtener una versión de prueba gratuita de Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web) antes de empezar.

## <a name="step-1-get-data"></a>Paso 1: Obtener datos

A menudo, cuando quiere crear un informe de Power BI, empieza en Power BI Desktop. Power BI Desktop ofrece más posibilidades. Puede transformar y modelar los datos, así como darles forma, antes de empezar a diseñar el informe. Aunque, esta vez, vamos a empezar desde cero creando un informe en el servicio Power BI.

En este tutorial, obtenemos datos de un archivo sencillo de Microsoft Excel. ¿Desea seguir adelante? [Descarga del archivo de ejemplo financiero](https://go.microsoft.com/fwlink/?LinkID=521962).

1. Para empezar, abra el servicio Power BI (app.powerbi.com) en el explorador. 

    ¿No tiene una cuenta? No se preocupe, puede [registrarse para obtener una versión de evaluación gratuita de Power BI Pro](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Seleccione **Mi área de trabajo** en el panel de navegación.

1. En **Mi área de trabajo**, seleccione **Nuevo** > **Cargar un archivo**.

    Se abre la página **Obtener datos**.   

3. En la sección **Crear contenido**, asegúrese de que **Archivos** está seleccionado y luego seleccione la ubicación en la que guardó el archivo de Excel.
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="Captura de pantalla de la sección Crear contenido > Archivos.":::

5. Busque el archivo en el equipo y elija **Abrir**.

5. En este tutorial, seleccionamos **Importar** para agregar el archivo de Excel como un conjunto de datos, que después se puede usar para crear informes y paneles. Si selecciona **Cargar**, se carga todo el libro de Excel en Power BI, donde lo puede abrir y editar en Excel Online.
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="Captura de pantalla de la selección de Importar.":::
6. Cuando el conjunto de datos esté listo, seleccione **Más opciones (...)** junto al conjunto de datos Ejemplo financiero y elija **Crear informe**.
1. Abra el editor de informes. 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="Captura de pantalla de Todo el contenido > Crear informe.":::

    El lienzo del informe está en blanco. En el lado derecho se ven los paneles **Filtros**, **Visualizaciones** y **Campos**.

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="Captura de pantalla del lienzo de informe en blanco.":::

    > [!TIP]
    > Seleccione el botón de navegación global de la esquina superior izquierda para contraer el panel de navegación. Así queda más espacio para el lienzo.
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="Botón de navegación global":::.
    >

7. Actualmente se encuentra en la vista de edición. Observe la opción **Vista de lectura** en la barra de menús. 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="Captura de pantalla de la opción Vista de lectura.":::

    En la vista de edición puede crear y modificar los informes, ya que es el *propietario* y el *creador* del informe. Cuando comparte el informe con compañeros de trabajo, a menudo ellos solo pueden interactuar con el informe en la vista de lectura. Son *consumidores* de informes en su sección **Mi área de trabajo**. 

## <a name="step-2-create-a-chart-in-a-report"></a>Paso 2: Crear un gráfico en un informe
Ahora que se ha conectado a los datos, empiece a explorar. Cuando haya encontrado algo interesante, puede guardarlo en el lienzo del informe. Después, puede anclarlo a un panel para supervisarlo y ver cómo cambia con el tiempo. Pero lo primero es lo primero.
    
1. En el editor de informes, comience en el panel **Campos** del lado derecho de la página para crear una visualización. Seleccione el campo **Ventas brutas** y luego el campo **Fecha**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="Captura de pantalla de la lista de campos.":::

    Power BI analiza los datos y crea una visualización del gráfico de columnas. 

    > [!NOTE]
    > Si seleccionó el campo **Fecha** primero en lugar de **Ventas brutas**, verá una tabla. No se preocupe. Cambiaremos la visualización en el paso siguiente.

    Algunos campos tienen símbolos sigma junto a ellos porque Power BI detectó que contienen valores numéricos.

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="Campos con símbolos sigma":::.

2. Vamos a cambiar a otra forma de mostrar los datos. Los gráficos de líneas son buenos objetos visuales para mostrar valores a lo largo del tiempo. En el panel **Visualizaciones**, seleccione el icono **Gráfico de líneas**.
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="Captura de pantalla del editor de informes con el gráfico de líneas seleccionado.":::

3. Este gráfico parece interesante, así que lo vamos a *anclar* a un panel. Mantenga el mouse sobre la visualización y seleccione el icono Anclar.
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="Captura de pantalla del icono Anclar seleccionado.":::

4. Como se trata de un informe nuevo, se le pide que lo guarde antes de poder anclar una visualización a un panel. Asigne un nombre al informe (por ejemplo, *Informe de ejemplo financiero*) y luego seleccione **Guardar**. 

    Ahora está examinando el informe en la vista de lectura. 

6. Vuelva a seleccionar el icono **Anclar**.
 
5. Seleccione **Nuevo panel** y asígnele el nombre *Panel de ejemplo financiero*, por ejemplo. 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="Captura de pantalla de Nombre del panel.":::
  
    Un mensaje de confirmación (junto a la esquina superior derecha) indica que la visualización se ha agregado al panel como un icono.
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="Captura de pantalla del cuadro de diálogo Anclado al panel.":::

    Ahora que ha anclado esta visualización, se almacenará en el panel. Los datos permanecen actualizados para que pueda realizar un seguimiento del valor más reciente de un vistazo. Aunque, si cambia el tipo de visualización del informe después de anclarla, la visualización en el panel no cambiará.

7. Seleccione **Ir al panel** para ver el panel nuevo con el gráfico de líneas que se ha anclado al mismo como un icono. 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="Captura de pantalla del panel con la visualización anclada.":::
   
8. Seleccione el nuevo icono en el panel. Power BI le devuelve al informe en la vista de lectura.

1. Para volver a la vista de edición, seleccione **Más opciones** (...) en la barra de menús > **Editar**.

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="Captura de pantalla de selección de Editar para editar el informe.":::

    Una vez en la vista de edición, puede seguir explorando y anclando iconos.

## <a name="step-3-explore-with-qa"></a>Paso 3: Explorar con Preguntas y respuestas

Para realizar una exploración rápida de los datos, pruebe a formular una pregunta en el cuadro Preguntas y respuestas. Preguntas y respuestas le permite formular consultas en lenguaje natural sobre los datos. En un panel, el cuadro Preguntas y respuestas se encuentra en la parte superior (**Pregunte algo sobre sus datos**). En un informe, se encuentra en la barra de menús superior (**Hacer una pregunta**).

1. Para volver al panel, seleccione **Mi área de trabajo** en la barra de encabezado negra de **Power BI**.

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="Captura de pantalla de Volver a Mi área de trabajo.":::

1. En **Mi área de trabajo**, seleccione el panel.

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="Captura de pantalla de selección del panel.":::

1. Seleccione **Pregunte algo sobre sus datos**. Preguntas y respuestas ofrece automáticamente un número de sugerencias. 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="Captura de pantalla de un lienzo Preguntas y respuestas.":::

    > [!NOTE]
    > Si no ve las sugerencias, active la opción **Nueva experiencia de Preguntas y respuestas**.

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="Captura de pantalla de activación de Nueva experiencia de Preguntas y respuestas.":::

1. Algunas de las sugerencias devuelven un solo valor. Por ejemplo, seleccione **cuál es el promedio de cog**.

    Preguntas y respuestas busca una respuesta y la presenta en forma de visualización de una *tarjeta*.

3. Seleccione **Anclar visualización** y ancle esta visualización al panel de ejemplo financiero.

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="Captura de pantalla del anclaje del objeto visual.":::

1. Vuelva a Preguntas y respuestas y seleccione **Mostrar todas las sugerencias**.
1. Seleccione **beneficio total por país**. 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="Captura de pantalla de beneficio total por país.":::

1. Ancle también el mapa al panel de ejemplo financiero.

1. En el panel, seleccione el mapa que acaba de anclar. ¿Ve cómo se abre de nuevo la sección Preguntas y respuestas? 
1. En el cuadro Preguntas y respuestas, coloque el cursor después de *por país* y escriba *como barra*. Power BI crea un gráfico de barras con los resultados.

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="Captura de pantalla de la visualización de gráfico de barras.":::

1. Ancle también el gráfico de barras al panel de ejemplo financiero.

4. Seleccione **Salir de preguntas y respuestas** para volver al panel, donde verá los nuevos iconos que se han creado. 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="Captura de pantalla del panel con objetos visuales de Preguntas y respuestas anclados.":::

   Verá que, aunque haya cambiado el mapa por un gráfico de barras en Preguntas y respuestas, el icono sigue siendo un mapa porque era un mapa cuando lo ancló. 

## <a name="step-4-reposition-tiles"></a>Paso 4: Cambiar la posición de los iconos

Podemos reorganizar los iconos para mejorar el uso del espacio del panel.

1. Arrastre la esquina inferior derecha del icono del gráfico de líneas *Ventas brutas* hacia arriba, hasta que se ajuste a la misma altura que el icono de ventas y, después, suéltelo.

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="Captura de pantalla del cambio de tamaño del icono.":::

    Ahora los dos iconos tienen la misma altura.

1. Seleccione **Más opciones (...)** en el icono Promedio de COGS > **Editar detalles**. 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="Captura de pantalla del menú Más opciones de un icono.":::

1. En el cuadro **Título**, escriba *Costo promedio de los bienes vendidos* > **Aplicar**.

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="Captura de pantalla del cuadro de diálogo Editar detalles.":::

1. Reorganice los demás objetos visuales para que queden juntos.

    Esto ya se ve mejor.

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="Captura de pantalla del panel reorganizado.":::


## <a name="clean-up-resources"></a>Limpieza de recursos
Ahora que ya hemos finalizado el tutorial, podemos eliminar el conjunto de datos, el informe y el panel. 

1. Seleccione **Mi área de trabajo** en la barra de encabezado negra de **Power BI**.
2. Seleccione **Más opciones (...)** junto al conjunto de datos Ejemplo financiero > **Eliminar**.

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="Captura de pantalla de la eliminación del conjunto de datos.":::

    Verá una advertencia que indica que **También se eliminarán todos los iconos del panel y los informes que contengan datos de este conjunto de datos**.

4. Seleccione **Eliminar**.

## <a name="next-steps"></a>Pasos siguientes

Explore estas colecciones de contenido de Microsoft Learn para Power BI:

- [Aprender a usar Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
- [Conviértase en un analista de datos de Power BI](/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm)