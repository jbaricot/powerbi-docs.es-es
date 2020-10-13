---
title: 'Tutorial: De libro de Excel a un informe sorprendente en Power BI Desktop'
description: En este tutorial se muestra cómo puede crear rápidamente un informe sorprendente a partir de un libro de Excel.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 07/21/2020
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: 275a83c8588bb9489361d467c6c6ab458abc86b2
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635341"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>Tutorial: De libro de Excel a un informe sorprendente en Power BI Desktop

En este tutorial, creará un atractivo informe de principio a fin en 20 minutos. 

La jefa quiere ver un informe sobre las cifras de ventas más recientes. Ha solicitado un resumen ejecutivo de lo siguiente: 

- Mes y año en los que se ha conseguido el mayor beneficio 
- Ubicaciones donde la empresa tiene más éxito (por país) 
- Producto y segmento en los que la empresa debe seguir centrando su inversión 

Con el libro de ejemplos financieros, este informe se puede crear sin dificultad. El informe final tendrá este aspecto. Comencemos. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI."::: 

En este tutorial, aprenderá a:

> [!div class="checklist"]
> * Descarga de los datos de ejemplo
> * Preparar los datos con algunas transformaciones
> * Crear un informe con un título, tres objetos visuales y una segmentación
> * Publicar el informe en el servicio Power BI para compartirlo con los compañeros de trabajo

## <a name="prerequisites"></a>Requisitos previos

- Antes de empezar, tendrá que [descargar Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Si tiene previsto publicar el informe en el servicio Power BI y todavía no se ha registrado, [regístrese para obtener una prueba gratuita](https://app.powerbi.com/signupredirect?pbi_source=web).

## <a name="download-the-sample"></a>Descarga del ejemplo

Para continuar, debe descargar el libro de ejemplo. 

1. Descargue el [libro de Excel de ejemplo financiero](https://go.microsoft.com/fwlink/?LinkID=521962).
1. Abra Power BI Desktop.
1. En la sección **Datos** de la cinta **Inicio**, seleccione **Excel**.
1. Vaya a la ubicación en la que haya guardado el libro de ejemplo y seleccione **Abrir**.

## <a name="prepare-your-data"></a>Preparar los datos 

En **Navegador**, tiene la opción de *transformar* o *cargar* los datos. El Navegador proporciona una vista previa de los datos para que pueda comprobar que tiene el intervalo correcto. Los tipos de datos numéricos se muestran en cursiva. Si tiene que realizar cambios, transforme los datos antes de cargarlos. Para que las visualizaciones sean más fáciles de leer más adelante, le interesa transformar los datos ahora. A medida que realiza cada transformación, verá que se agrega a la lista en **Configuración de la consulta**, en **Pasos aplicados** 

1. Seleccione la tabla **Financials** y elija **Transformar datos**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI."::: 

1. Seleccione la columna **Unidades vendidas**. En la pestaña **Inicio**, seleccione **Tipo de datos** y, después, **Número entero**. Elija **Sustituir actual** para cambiar el tipo de columna. 

    El principal paso de limpieza de datos que los usuarios realizan con mayor frecuencia es el cambio de los tipos de datos. En este caso, las unidades vendidas tienen formato decimal. No tiene sentido tener 0,2 o 0,5 de una unidad vendida, ¿verdad? Por tanto, se cambiará por un número entero. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI."::: 

1. Seleccione la columna **Segmento**. En la pestaña **Transformación**, seleccione **Formato** y **MAYÚSCULAS**.

    También quiere que los segmentos sean más fáciles de ver después en el gráfico. Ahora se aplicará formato a la columna Segmento. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. Ahora se acortará el nombre de la columna **Nombre del mes** a solo **Mes**. Haga doble clic en la columna **Nombre del mes** y cambie el nombre a solo **Mes**.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. En la columna **Producto**, seleccione la lista desplegable y desactive la casilla situada junto a **Montana**. 

     Sabe que el producto Montana dejó de estar disponible el mes pasado, por lo que quiere filtrar estos datos del informe para evitar confusiones. 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. Verá que cada transformación se ha agregado a la lista en **Configuración de la consulta** en **Pasos aplicados**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. De vuelta en la pestaña **Inicio**, seleccione **Cerrar y aplicar**. Los datos están casi listos para la creación de un informe. 

    ¿Ve el símbolo Sigma en la lista Campos? Power BI ha detectado que esos campos son numéricos. Power BI también indica el campo de fecha con un símbolo de calendario.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

### <a name="extra-credit-write-a-measure-in-dax"></a>Crédito adicional: Escritura de una medida en DAX

La escritura de *medidas* en el lenguaje de fórmulas *DAX* es muy eficaz para el modelado de datos. En la documentación de Power BI hay mucha más información sobre DAX. Por ahora, se escribirá una medida básica y se combinarán dos tablas. 

1. Seleccione **Vista de datos** en el lado izquierdo. 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. En la cinta **Inicio**, seleccione **Nueva tabla**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. Escriba esta medida para generar una tabla Calendario de todas las fechas entre el 1 de enero de 2013 y el 31 de diciembre de 2014.  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. Seleccione la marca de verificación para confirmar.

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. Ahora, seleccione **Vista de modelo** a la izquierda. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. Arrastre el campo **Fecha** de la tabla Financials al campo **Fecha** de la tabla Calendario para combinar las tablas y crear *una relación* entre ellas.  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

## <a name="build-your-report"></a>Crear el informe 

Ahora que ha transformado y cargado los datos, es el momento de crear el informe. En el panel Campos de la derecha, verá los campos del modelo de datos que ha creado. 

Ahora se creará el informe final, un objeto visual a la vez. 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

### <a name="visual-1-add-a-title"></a>Objeto visual 1: Agregar un título 

1. En la cinta **Insertar**, seleccione **Cuadro de texto**. Escriba "Resumen ejecutivo: Informe financiero". 
1. Seleccione el texto que escribió. Establezca el tamaño de fuente en 20 y negrita. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. En el panel Visualizaciones, establezca **Fondo** en **Desactivado**. 
1. Cambie el tamaño del cuadro para que quepa en una línea. 

### <a name="visual-2-profit-by-date"></a>Objeto visual 2: Beneficios por Fecha 

Ahora, cree un gráfico de líneas para ver en qué mes y año se ha obtenido el beneficio más alto. 

1. Desde el panel Campos, arrastre el campo **Beneficios** a una zona en blanco del lienzo del informe. De forma predeterminada, Power BI muestra un gráfico de columnas con una columna, Beneficios. 
1. Arrastre el campo **Fecha** al mismo objeto visual. Power BI actualiza el gráfico de columnas para mostrar los beneficios de los dos años.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. En la sección **Campos** del panel Visualizaciones, seleccione la lista desplegable del valor **Eje**. Cambie **Fecha** de **Jerarquía de fechas** a **Fecha**.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

    Power BI actualiza el gráfico de columnas para mostrar los beneficios de cada mes.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. En el panel Visualizaciones, cambie el tipo de visualización a **Gráfico de líneas**. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

    Ahora puede ver con facilidad que el máximo beneficio se obtuvo en diciembre de 2014.

### <a name="visual-3-profit-by-country"></a>Objeto visual 3: Beneficios por País 

Cree un mapa para ver en qué país se han obtenido los mayores beneficios.

1. Desde el panel Campos, arrastre el campo **País** a un área en blanco del lienzo del informe para crear un mapa.
1. Arrastre el campo **Beneficios** al mapa.

    Power BI crea un objeto visual de mapa con burbujas que representan el beneficio relativo de cada ubicación. 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

    Parece que en Europa se obtienen mayores beneficios que en Estados Unidos. 

### <a name="visual-4-sales-by-product-and-segment"></a>Objeto visual 4: Ventas por Producto y Segmento 

Cree un gráfico de barras para determinar en qué empresas y segmentos hay que invertir.

1. Arrastre los dos gráficos que ha creado para situarlos en paralelo en la mitad superior del lienzo. Deje espacio en el lado izquierdo del lienzo. 
1. Seleccione un área en blanco en la mitad inferior del lienzo del informe. 

1. En el panel Campos, seleccione los campos **Ventas**, **Producto** y **Segmento**. 

    Power BI crea automáticamente un gráfico de columnas agrupadas. 

1. Arrastre el gráfico para que sea lo suficientemente ancho como para rellenar el espacio bajo los dos gráficos superiores.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

    Parece que la empresa debe seguir invirtiendo en el producto Paseo y dirigirse a los segmentos Pequeña empresa y Administración Pública.  

### <a name="visual-5-year-slicer"></a>Objeto visual 5: Segmentación de año 

Las segmentaciones son una valiosa herramienta para filtrar los objetos visuales de una página de informe por una selección específica. En este caso, se puede crear una segmentación que se centre en el rendimiento de cada mes y año.  

1. En el panel Campos, seleccione el campo **Fecha** y arrástrelo hasta el área en blanco a la izquierda del lienzo. 
2. En el panel Visualizaciones, seleccione **Segmentación**. 
3. En la sección Campos del panel Visualizaciones, seleccione la lista desplegable de **Campos**. Quite Quarter (Trimestre) y Day (Día), de modo que solo queden Year (Año) y Month (Mes). 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

4. Expanda cada año y cambie el tamaño del objeto visual, para que se vean todos los meses.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

Ahora, si la jefa le pide ver solo los datos de 2013, puede usar la segmentación para cambiar entre años o meses concretos de cada año. 

### <a name="extra-credit-format-the-report"></a>Crédito adicional: Formato del informe

Si quiere aplicar un formato ligero a este informe para pulirlo más, puede seguir estos sencillos pasos. 

**Tema**

- En la cinta **Vista**, cambie el tema a **Ejecutivo**.  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI."::: 

**Mejora de los objetos visuales** 

Realice los cambios siguientes en la pestaña **Formato** del panel Visualizaciones.

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. Seleccione el objeto visual 2. En la sección **Título**, cambie **Texto de título** por "Beneficios por mes y año", y **Tamaño de texto** a **16 pt**. Establezca **Sombra** en **Activar**. 

1. Seleccione el objeto visual 3. En la sección **Estilos de mapa**, cambie **Tema** a **Escala de grises**. En la sección **Título**, cambie el **Tamaño del texto** del título a **16 pt**. Establezca **Sombra** en **Activar**.

1. Seleccione el objeto visual 4. En la sección **Título**, cambie el **Tamaño del texto** del título a **16 pt**. Establezca **Sombra** en **Activar**.

1. Seleccione el objeto visual 5. En la sección **Controles de selección**, establezca **Mostrar opción "Seleccionar todo"** en **Activar**. En la sección **Encabezado de segmentación**, aumente **Tamaño del texto** a **16 pt**. 

**Adición de una forma de fondo para el título**

1. En la cinta **Insertar**, seleccione **Formas** > **Rectángulo**. Colóquelo en la parte superior de la página y amplíelo para que tenga el ancho de la página y el alto del título. 
1. En el panel **Formato de forma**, en la sección **Línea**, cambie **Transparencia** a **100 %** . 
1. En la sección **Relleno**, cambie **Color de relleno** a **Color de tema 5 #6B91C9** (azul). 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

1. En la pestaña **Formato**, seleccione **Enviar atrás** > **Enviar al fondo**. 
1. Seleccione el texto del objeto visual 1, el título, y cambie el color de fuente a **Blanco**. 

**Adición de una forma de fondo para los objetos visuales 2 y 3**

1. En la cinta **Insertar**, seleccione **Formas** > **Rectángulo** y amplíelo para que tenga el ancho y el alto de los objetos visuales 2 y 3. 
1. En el panel **Formato de forma**, en la sección **Línea**, cambie **Transparencia** a **100 %** . 
1. En la pestaña **Formato**, seleccione **Enviar atrás** > **Enviar al fondo**. 

### <a name="finished-report"></a>Informe finalizado

Este es el aspecto que tendrá el informe acabado:  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

En resumen, este informe responde a las principales preguntas de la jefa: 

- Mes y año en los que se ha conseguido el mayor beneficio 

    Diciembre de 2014 

- Ubicaciones donde la empresa tiene más éxito (por país) 

    En Europa, concretamente en Francia y Alemania. 

- Producto y segmento en los que la empresa debe seguir centrando su inversión 

    La empresa debe seguir invirtiendo en el producto Paseo y dirigirse a los segmentos Pequeña empresa y Administración Pública. 

## <a name="save-your-report"></a>Guardar el informe

- En el menú **Archivo**, seleccione **Guardar**.

## <a name="publish-to-the-power-bi-service-to-share"></a>Publicación en el servicio Power BI para compartir 

Para compartir el informe con la jefa y los compañeros de trabajo, publíquelo en el servicio Power BI. Al compartirlo con compañeros que tienen una cuenta de Power BI, pueden interactuar con el informe, pero no guardar los cambios. 

1. En Power BI Desktop, seleccione **Publicar** en la cinta **Inicio**. 

    Es posible que tenga que iniciar sesión en el servicio Power BI. Si todavía no tiene una cuenta, puede [registrarse para obtener una evaluación gratuita](https://app.powerbi.com/signupredirect?pbi_source=web).

1. Seleccione un destino, como **Mi área de trabajo** en el servicio Power BI > **Seleccionar**.
1. Seleccione **Abrir "nombre_del_archivo" en Power BI**.

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

    El informe completado se abre en el explorador.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI."::: 

1. Seleccione **Compartir** en la parte superior del informe para compartirlo con otros usuarios.

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="Captura de pantalla del informe de Power BI en el servicio Power BI.":::

## <a name="next-steps"></a>Pasos siguientes

- [Tutorial: Análisis de datos de ventas de Excel y una fuente de OData](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/).
