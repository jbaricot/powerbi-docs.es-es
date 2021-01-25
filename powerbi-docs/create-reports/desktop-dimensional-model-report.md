---
title: 'Tutorial: De modelo dimensional a impresionante informe en Power BI Desktop'
description: En este tutorial se empieza con un modelo dimensional y se compila un atractivo informe de principio a fin en 20 minutos.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/11/2021
LocalizationGroup: Reports
ms.openlocfilehash: f5d35d7fc189f055a6f51e493fd313eb31f0564f
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565986"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>Tutorial: De modelo dimensional a impresionante informe en Power BI Desktop 

En este tutorial se empieza con un modelo dimensional y se compila un atractivo informe de principio a fin en 45 minutos.

Trabaja en AdventureWorks y su superior quiere ver un informe sobre las cifras de ventas más recientes. Ha solicitado un resumen ejecutivo de: 

- En qué día de febrero de 2019 se produjeron más ventas 
- Ubicaciones donde la empresa tiene más éxito (por país) 
- En qué categoría de producto y tipos de negocio de reventa debería seguir invirtiendo la empresa 

Con el [libro de Excel de ejemplo AdventureWorks Sales](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx) se puede crear este informe rápidamente. El informe final tendrá este aspecto. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Informe terminado de AdventureWorks.":::

¿Quiere ver el producto final? También puede descargar el [archivo .pbix de Power BI completado](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix).

Comencemos. 

En este tutorial, obtendrá información sobre cómo:

> [!div class="checklist"]
> * Preparar los datos con algunas transformaciones
> * Crear un informe con un título, tres objetos visuales y una segmentación
> * Publicar el informe en el servicio Power BI para compartirlo con los compañeros de trabajo

## <a name="prerequisites"></a>Requisitos previos

- Antes de empezar, tendrá que [descargar Power BI Desktop](../fundamentals/desktop-get-the-desktop.md). 
- Si tiene previsto publicar el informe en el servicio Power BI y todavía no se ha registrado, [regístrese para obtener una prueba gratuita](../fundamentals/service-self-service-signup-for-power-bi.md). 

## <a name="get-data-download-the-sample"></a>Obtención de datos: Descarga del ejemplo 

1. Descargue el [libro de Excel de ejemplo AdventureWorks Sales](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx). 

1. Abra Power BI Desktop. 

1. En la sección **Datos** de la cinta **Inicio**, seleccione **Excel**. 

1. Vaya a la ubicación en la que haya guardado el libro de ejemplo y seleccione **Abrir**. 

## <a name="prepare-your-data"></a>Preparar los datos 

En el panel Navegador, tiene la opción de  *transformar*  o de  *cargar*  los datos. El Navegador proporciona una vista previa de los datos para que pueda comprobar que tiene el intervalo correcto. Los tipos de datos numéricos se muestran en cursiva. En este tutorial se van a transformar los datos antes de cargarlos.

Seleccione todas las tablas y luego  **Transformar datos**. Asegúrese de no seleccionar las hojas (con la etiqueta *_data*). 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="Carga de tablas en Navegador.":::

Compruebe que los tipos de datos de las columnas coinciden con los de la tabla siguiente. Para realizar cambios, seleccione una consulta y luego una o varias columnas.

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="Comprobación de los tipos de datos de las columnas.":::

En la pestaña **Inicio**, seleccione **Tipo de datos** y, luego, el tipo de datos adecuado de la tabla.

|Consultar  |Columna  |Tipo de datos  |
|---------|---------|---------|
|Customer  |  CustomerKey | Whole Number |
|Date | DateKey |    Whole Number     |
|     | Date | Date      |
|     | MonthKey  | Whole Number |
|Producto  | ProductKey | Whole Number  | 
|     | Standard Cost | Decimal Number  | 
|     | List Price | Decimal Number  | 
|Reseller  | ResellerKey | Whole Number  | 
|Sales   | SalesOrderLineKey | Whole Number  | 
|     | ResellerKey  | Whole Number  | 
|     | CustomerKey | Whole Number  | 
|     | ProductKey  | Whole Number  | 
|     | OrderDateKey | Whole Number  | 
|     | DueDateKey  | Whole Number  | 
|     | ShipDateKey | Whole Number  | 
|     | SalesTerritoryKey | Whole Number  | 
|     | Cantidad del pedido   | Whole Number  | 
|     | Unit Price  | Decimal Number  | 
|     | Extended Amount  | Decimal Number  | 
|     | Porcentaje de descuento del precio por unidad | Porcentaje  | 
|     | Product Standard Cost | Decimal Number  | 
|     | Total Product Cost | Decimal Number  | 
|     | Sales Amount | Decimal Number  | 
| SalesTerritory  | SalesTerritoryKey | Whole Number  | 
|  SalesOrder   |  SalesOrderLineKey | Whole Number  | 

De nuevo en la pestaña  **Inicio** , seleccione  **Cerrar y aplicar**. 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Botón Cerrar y aplicar de Power Query.":::

## <a name="model-your-data"></a>Modelar los datos 

Los datos cargados están casi listos para la creación del informe. Vamos a inspeccionar el modelo de datos y a realizar algunos cambios. 

Seleccione **Vista de modelo** a la izquierda. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="Selección de Vista de modelo en Power BI Desktop.":::

El modelo de datos debe tener un aspecto similar al de la siguiente imagen, con cada tabla en un cuadro. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="Modelo de datos inicial.":::

### <a name="create-relationships"></a>Crear relaciones

Este modelo es un *esquema de estrella* típico que se puede ver en los almacenamientos de datos: Parece una estrella. El centro de la estrella es una tabla de hechos. Las tablas circundantes se denominan tablas de dimensiones, y se relacionan con la tabla de hechos mediante relaciones. La tabla de hechos contiene información numérica sobre las transacciones de ventas, como el importe de ventas y el costo estándar del producto. Las dimensiones proporcionan contexto para poder analizar, entre otras cosas: 

- Qué producto se ha vendido... 
- a qué cliente... 
- qué revendedor... 
- en qué territorio de ventas.  

Si observa detenidamente, verá que todas las tablas de dimensiones se relacionan con el hecho mediante una relación, excepto la tabla de fechas. Vamos a agregar algunas relaciones a esa tabla. Arrastre DateKey desde la tabla Fecha a OrderDateKey en la tabla Ventas. Ha creado lo que se denomina una relación "uno a varios" entre Fecha y Ventas, como indican **1** y el asterisco * (varios) en los dos extremos de la línea.  

La relación es "uno a varios" porque hay uno o varios pedidos de ventas en una fecha determinada. Si cada fecha solo tuviera un pedido de ventas, la relación sería "uno a uno". La pequeña flecha en el centro de la línea indica la "dirección de filtrado cruzado". Indica que puede usar valores de la tabla Fecha para filtrar la tabla Ventas, por lo que la relación permite analizar cuándo se ha realizado un pedido de ventas.  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Relación entre las tablas Ventas y Fecha.":::

La tabla Ventas contiene más información sobre fechas relacionadas con pedidos de ventas, como la fecha de vencimiento y la de envío. Vamos a agregar dos relaciones más a la tabla de fechas si arrastramos: 

- DateKey a DueDateKey 
- DateKey a ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Tres relaciones entre las tablas Ventas y Fecha.":::

Observe que la primera relación, en OrderDateKey, está activa, lo que se indica mediante la línea continua. Las otras dos están inactivas, lo que se indica mediante las líneas discontinuas. De manera predeterminada, Power BI usa la relación activa para relacionar Ventas y Fecha. Por lo tanto, la suma de SalesAmount se calcula por fecha de pedido, no por fecha de vencimiento ni de envío. Puede influir en este comportamiento. Vea [Crédito adicional: Escritura de una medida en DAX](#extra-credit-write-a-measure-in-dax) más adelante en este tutorial.

### <a name="hide-key-columns"></a>Ocultación de columnas de clave

El esquema de estrella típico contiene varias claves que contienen las relaciones entre hechos y dimensiones. Normalmente no se recomienda usar ninguna columna de clave en los informes. Vamos a ocultar las columnas de clave para que la lista de campos muestre menos campos y el modelo de datos sea más fácil de usar. 

Desplácese por todas las tablas y oculte cualquier columna cuyo nombre termine por *Key*: 

Seleccione el icono de **ojo** situado junto a la columna y luego **Ocultar en la vista de informes**.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="Columna visible con el icono de ojo.":::

También puede seleccionar el icono de **ojo** situado junto a la columna en el panel Propiedades.

Los campos ocultos tienen este icono, un ojo con una línea que lo atraviesa. 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="Campo con el icono de ojo oculto.":::
 
Oculte estos campos.

|Tabla  |Columna  |
|---------|---------|
|Customer  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|Producto     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| SalesOrder    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

El modelo de datos ahora debe tener el mismo aspecto que este, con relaciones entre Ventas y todas las demás tablas, y todos los campos de clave ocultos: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="Modelo de datos con columnas de clave ocultas.":::

### <a name="create-hierarchies"></a>Crear jerarquías

Ahora que el modelo de datos es más fácil de consumir debido a las columnas ocultas, se pueden agregar algunas *jerarquías* para que sea aún más fácil de usar. Las jerarquías facilitan la navegación por las agrupaciones. Por ejemplo, las ciudades se encuentran en un estado o provincia, que a su vez está en un país o región. 

Cree las jerarquías siguientes. 

1. Haga clic con el botón derecho en el campo de nivel superior, o el menos pormenorizado, de la jerarquía y, después, seleccione **Crear jerarquía**. 

1. En el panel **Propiedades**, establezca el **Nombre** de la jerarquía y los niveles. 

1. Luego seleccione **Aplicar cambios en el nivel**. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="Panel Propiedades de la jerarquía.":::

También puede cambiar el nombre de los niveles de una jerarquía en el panel Propiedades después de agregarlos. Tiene que cambiar el nombre del nivel Año y Trimestre de la jerarquía Fiscal de la tabla Fecha. 

Estas son las jerarquías que debe crear.

| Tabla |Nombre de la jerarquía |Niveles  |
|---------|---------|---------|
|Customer     | Geography   | País-región  |
|     | | State-Province  |
|     |         | City (Ciudad) |
|Row4     |         | Código postal |
|Row5     |         | Customer   |
|Fecha     | Fiscal  | Año (año fiscal)  |
|     |         | Trimestre (trimestre fiscal) |
|     |         | Month |
|     |         | Fecha |
| Product  | Productos | Category |
|     |         | Subcategoría |
|     |         | Modelo |
|     |         | Product |
| Reseller   | Geography | País-región |
|     |         | State-Province |
|     |         | City (Ciudad)  |
|     |         | Código postal  |
|     |         | Reseller |
| SalesOrder  | Pedidos de ventas | Pedido de venta |
|     |         | Sales Order Line |
| SalesTerritory    | Territorios de ventas | Group (Grupo) |
|     |         | Country (País) |
|     |         | Region |
 
El modelo de datos ahora debe ser similar al siguiente. Tiene las mismas tablas, pero cada tabla de dimensiones contiene una jerarquía: 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="Modelo de datos con tablas de dimensiones con jerarquías.":::

### <a name="rename-tables"></a>Cambio del nombre de las tablas

Para finalizar el modelo, vamos a cambiar el nombre de las tablas siguientes en el panel Propiedades: 

|Antiguo nombre de la tabla  |Nombre de la nueva tabla  |
|---------|---------|
|SalesTerritory    |  Territorio de ventas   |
|SalesOrder  |  Pedido de venta   |

Este paso es necesario porque los nombres de tabla de Excel no pueden contener espacios.

El modelo de datos final ya está listo.

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="Modelo de datos completado con tablas cuyo nombre ha cambiado.":::

## <a name="extra-credit-write-a-measure-in-dax"></a>Crédito adicional: Escritura de una medida en DAX 

La escritura de *medidas* en el lenguaje de fórmulas DAX es muy eficaz para el modelado de datos. [En la documentación de Power BI hay mucha información sobre DAX](/dax/). Por ahora, vamos a escribir una medida básica que calcula el importe de ventas total por fecha de vencimiento del pedido de ventas en lugar de por fecha de pedido predeterminada. Esta medida usa la función [USERELATIONSHIP](/dax/userelationship-function-dax) para activar la relación entre Ventas y Fecha en DueDate para el contexto de la medida. Luego usa [CALCULATE](/dax/calculate-function-dax) para sumar el importe de ventas de ese contexto.

1. Seleccione Vista de datos a la izquierda. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="Selección de Vista de datos en el lado izquierdo.":::

1. Seleccione la tabla Ventas en la lista Campos.

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="Selección de la tabla Ventas en la lista Campos.":::

1. En la cinta de opciones  **Inicio** , seleccione  **Nueva medida**. 

1. Seleccione esta medida para calcular el importe de ventas total por fecha de vencimiento del pedido de ventas en lugar de por fecha de pedido predeterminada:

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. Seleccione la marca de verificación para confirmar. 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="Activación de la casilla de verificación para confirmar la medida de DAX.":::

## <a name="build-your-report"></a>Crear el informe 

Ahora que ha modelado los datos, es hora de crear el informe. Vaya a Vista de informe. En el panel Campos de la derecha, verá los campos del modelo de datos que ha creado.

Ahora se creará el informe final, un objeto visual a la vez. 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="Informe terminado con números que marcan cada objeto visual":::

### <a name="visual-1-add-a-title"></a>Objeto visual 1: Agregar un título 

1. En la cinta **Insertar**, seleccione **Cuadro de texto**. Escriba "Resumen ejecutivo: informe de ventas". 

1. Seleccione el texto que escribió. Establezca el tamaño de fuente en **20** y **Negrita**. 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="Formato del texto Resumen Ejecutivo.":::

1. En el panel Visualizaciones, establezca **Fondo** en **Desactivado**. 

1. Cambie el tamaño del cuadro para que quepa en una línea. 

### <a name="visual-2-sales-amount-by-date"></a>Objeto visual 2: Importe de ventas por fecha 

Ahora cree un gráfico de líneas para ver en qué mes y en qué año se ha conseguido el importe de ventas más alto.

1. En el panel Campos, arrastre el campo **Importe de ventas** de la tabla **Ventas** a un área en blanco del lienzo del informe. De manera predeterminada, Power BI muestra un gráfico de columnas con una columna, Importe de ventas. 

1. Arrastre el campo **Mes** de la jerarquía **Fiscal** de la tabla **Fecha** y colóquelo en el gráfico de columnas. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="Creación de un gráfico de columnas con una columna para cada año.":::

1. En la sección **Campos** del panel Visualizaciones, quite los campos **Año** y **Trimestre**: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="En la sección Campos del panel Visualizaciones, eliminación de los campos Año y Trimestre.":::

1. En el panel Visualizaciones, cambie el tipo de visualización a **Gráfico de áreas**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="Cambio del gráfico de columnas a un gráfico de áreas.":::

1. Si ha agregado la medida de DAX en el crédito adicional anterior, agréguela también a **Valores**. 
1. Abra el panel Formato, abra Colores de datos y cambie el color de **Importe de ventas por fecha de vencimiento** a uno más vistoso, como rojo.

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="Importe de ventas por fecha de vencimiento como gráfico de áreas.":::

    Como puede ver, Importe de ventas por fecha de vencimiento se traza ligeramente por detrás de Importe de ventas. Esto muestra que usa la relación entre las tablas Ventas y Fecha que emplea DueDateKey. 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>Objeto visual 3: Cantidad de pedidos por país del revendedor 

Ahora vamos a crear un mapa para ver en qué país tienen los revendedores la máxima cantidad de pedidos.

1. En el panel Campos, arrastre el campo **País o región** de la tabla **Revendedor** a un área en blanco del lienzo del informe. Power BI crea un mapa. 

1. Arrastre el campo **Cantidad de pedidos** de la tabla **Ventas** y colóquelo en el mapa. Asegúrese de que **País o región** esté en el área **Ubicación** y **Cantidad de pedidos** en el área **Tamaño**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="Mapa de la cantidad de pedidos por país o región.":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>Objeto visual 4: Importe de ventas por categoría de producto y tipo de negocio de reventa 

A continuación vamos a crear un gráfico de columnas para investigar qué productos son vendidos por qué tipo de negocio de reventa.

1. Arrastre los dos gráficos que ha creado para situarlos en paralelo en la mitad superior del lienzo. Deje espacio en el lado izquierdo del lienzo. 

1. Seleccione un área en blanco en la mitad inferior del lienzo del informe. 

1. En el panel Campos, seleccione **Importe de ventas** de **Ventas**, **Categoría de producto** de **Producto** y **Tipo de negocio** de **Revendedor**. 

    Power BI crea automáticamente un gráfico de columnas agrupadas. Cambie la visualización a una **matriz**: 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="Cambio del gráfico de columnas agrupadas a una matriz.":::

1. Con la matriz aún seleccionada, en el panel Filtros, en **Tipo de negocio**, seleccione **Seleccionar todo** y desactive la casilla **[No aplicable]** . 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="Filtro por el tipo de negocio No aplicable.":::

1. Arrastre la matriz para que sea lo suficientemente ancha como para rellenar el espacio bajo los dos gráficos superiores. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="Ampliación de la matriz para rellenar el informe.":::

1. En el panel Formato de la matriz, abra la sección **Formato condicional** y active **Barras de datos**. Seleccione **Controles avanzados** y establezca un color más claro para la barra positiva. Seleccione **Aceptar**. 

1. Aumente el ancho de la columna Importe de ventas para que cubra toda el área. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="Matriz con barras de datos de Importe de ventas.":::

Parece que las Bicicletas tienen un importe de ventas mayor en general y que los Revendedores de valor agregado venden más, seguidos de los Almacenes. En cuanto a Componentes, los Almacenes venden más que los Revendedores de valor agregado. 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>Objeto visual 5: Segmentación de calendario fiscal 

Las segmentaciones son una valiosa herramienta para filtrar los objetos visuales de una página de informe por una selección específica. En este caso se puede crear una segmentación que se centre en el rendimiento de cada mes, trimestre y año. 

1. En el panel Campos, seleccione la jerarquía **Fiscal** de la tabla **Fecha** y arrástrela al área en blanco a la izquierda del lienzo. 

1. En el panel Visualizaciones, seleccione **Segmentación**. 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="Incorporación de una segmentación de calendario de ventas de informe.":::

1. En la sección Campos del panel Visualizaciones, quite **Trimestre** y **Fecha** para que solo queden **Año** y **Mes**. 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="Eliminación de Trimestre y Fecha de la segmentación Fiscal.":::

Ahora, si su superior le pide ver solo los datos de un mes determinado, puede usar la segmentación para cambiar entre años o meses concretos de cada año. 

## <a name="extra-credit-format-the-report"></a>Crédito adicional: Formato del informe 

Si quiere aplicar un formato ligero a este informe para pulirlo más, puede seguir estos sencillos pasos. 

### <a name="theme"></a>Tema 

- En la cinta de opciones  **Vista** , seleccione **Temas** y cambie el tema a  **Ejecutivo**. 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="Selección del tema Ejecutivo.":::

### <a name="spruce-up-the-visuals"></a>Mejora de los objetos visuales 

Realice los cambios siguientes en la pestaña  **Formato**  del panel Visualizaciones. 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="Captura de pantalla de la pestaña Formato del panel Visualizaciones.":::

**Objeto visual 2: Importe de ventas por fecha**

1. Seleccione Objeto visual 2: Importe de ventas por fecha. 
1. En la sección **Título** , si no ha agregado la medida de DAX, cambie el texto  **Título** a "Importe de ventas por fecha de pedido". 

    Si ha agregado la medida de DAX, cambie **Texto de título** a "Importe de ventas por fecha de pedido o fecha de vencimiento". 

1. Establezca el tamaño de **Texto** en  **16**. 
1. Cambie  **Sombra**  a  **Activado**. 

**Objeto visual 3: Cantidad de pedidos por país del revendedor**

1. Seleccione Objeto visual 3: Cantidad de pedidos por país del revendedor. 
1. En la sección  **Estilos de mapa** , cambie  **Tema**  a  **Escala de grises**. 
1. En la sección  **Título** , cambie **Texto del título** a "Cantidad de pedidos por país del revendedor".
1. Establezca **Tamaño del texto**  en  **16**. 
1. Cambie  **Sombra**  a  **Activado**.  

**Objeto visual 4: Importe de ventas por categoría de producto y tipo de negocio de reventa**

1. Seleccione Objeto visual 4: Importe de ventas por categoría de producto y tipo de negocio de reventa. 
1. En la sección  **Título** , cambie **Texto del título** a "Importe de ventas por categoría de producto y tipo de negocio de reventa".
1. Establezca **Tamaño del texto**  en  **16**. 
1. Cambie  **Sombra**  a  **Activado**. 

**Objeto visual 5: Segmentación de calendario fiscal**

1. Seleccione Objeto visual 5: Segmentación de calendario fiscal.
1. En la sección  **Controles de selección** , cambie la opción  **Mostrar "Seleccionar todo"** a  **Activado**. 
1. En la sección  **Encabezado de segmentación** , establezca **Tamaño de texto**  en  **16**. 

### <a name="add-a-background-shape-for-the-title"></a>Adición de una forma de fondo para el título 

1. En la cinta de opciones  **Insertar**, seleccione **Formas** > **Rectángulo**. 
1. Colóquelo en la parte superior de la página y amplíelo para que tenga el ancho de la página y el alto del título. 
1. En el panel  **Formato de forma** , en la sección  **Línea** , cambie  **Transparencia**  a  **100%** . 
1. En la sección  **Relleno** , cambie  **Color de relleno**  a  **Color de tema 5 #6B91C9 (azul)** . 
1. En la pestaña  **Formato** , seleccione  **Enviar atrás** > **Enviar al fondo**. 
1. Seleccione el texto del objeto visual 1, el título, y cambie **Color de fuente** a  **Blanco**. 

## <a name="finished-report"></a>Informe finalizado 

Seleccione **FY2019** en la segmentación.

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="Informe final completado.":::

En resumen, este informe responde a las principales preguntas de la jefa: 

- En qué día de febrero de 2019 se produjeron más ventas 
    25 de febrero, con un importe de ventas de 253 915,47 USD. 

- Ubicaciones donde la empresa tiene más éxito (por país) 
    En los Estados Unidos, con una cantidad de pedidos de 132 748. 

- En qué categoría de producto y tipos de negocio de reventa debería seguir invirtiendo la empresa 
    La empresa debe seguir invirtiendo en la categoría Bicicletas y en los negocios de reventa Revendedores de valor agregado y Almacenes. 

## <a name="save-your-report"></a>Guardar el informe 

- En el menú  **Archivo** , seleccione  **Guardar**. 


## <a name="publish-to-the-power-bi-service-to-share"></a>Publicación en el servicio Power BI para compartir 

Para compartir el informe con la jefa y los compañeros de trabajo, publíquelo en el servicio Power BI. Al compartirlo con compañeros que tienen una cuenta de Power BI, pueden interactuar con el informe, pero no guardar los cambios.

1. En Power BI Desktop, en la cinta de opciones  **Inicio** , seleccione  **Publicar**. 
1. Es posible que tenga que iniciar sesión en el servicio Power BI. Si todavía no tiene ninguna cuenta,  [regístrese para obtener una evaluación gratuita](https://app.powerbi.com/signupredirect?pbi_source=web). 

1. Seleccione un destino, como Mi área de trabajo, del servicio Power BI >  **Seleccionar**. 

1. Seleccione  **Abrir "nombre_del_archivo" en Power BI**. El informe completado se abre en el explorador. 

1. Seleccione  **Compartir**  en la parte superior del informe para compartirlo con otros usuarios.

## <a name="next-steps"></a>Pasos siguientes 

- Descargue el [archivo .pbix de Power BI completado](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- Obtenga más información sobre [DAX y el modelado de datos en Power BI Desktop](/learn/modules/dax-power-bi-models/)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
