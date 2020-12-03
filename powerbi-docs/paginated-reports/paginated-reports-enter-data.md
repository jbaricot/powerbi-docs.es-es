---
title: Escritura directa de datos en un informe paginado en el Generador de informes
description: En este artículo, verá cómo puede escribir datos directamente en un informe paginado en el Generador de informes.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 07/10/2020
ms.openlocfilehash: 5719a5d6e8f559f1dba9f87bc9937ed925195072
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418219"
---
# <a name="enter-data-directly-in-a-paginated-report-in-report-builder---power-bi"></a>Escritura directa de datos en un informe paginado en el Generador de informes: Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

En este artículo, obtendrá información sobre una característica de la nueva versión del Generador de informes de Microsoft Power BI que le permite escribir datos directamente en un informe RDL como un conjunto de datos insertado.  Esta característica es similar a Power BI Desktop. Puede escribir los datos directamente en un conjunto de datos del informe o pegarlos desde otro programa como Microsoft Excel. Después de escribir los datos para crear un conjunto de datos, puede usarlo tal como lo haría con cualquier otro conjunto de datos insertado que haya creado. Además, puede agregar más de una tabla y usar una como un filtro de la otra. Esta característica es especialmente útil para conjuntos de datos pequeños y estáticos que puede que deba usar en el informe, como los parámetros de informe.
 
## <a name="prerequisites"></a>Requisitos previos

- Para escribir datos directamente en un informe paginado, [descargue e instale el Generador de informes de Power BI](https://aka.ms/pbireportbuilder). 
- Para guardar el informe paginado en el servicio Power BI, necesita una [cuenta de Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md) y acceso de escritura a un área de trabajo en una [capacidad Premium de Power BI](../admin/service-premium-what-is.md).
- Para guardar el informe paginado en un servidor de informes, necesita permisos para [editar el archivo RsReportServer.config](#upload-the-paginated-report-to-a-report-server).

## <a name="create-a-data-source-and-dataset"></a>Creación de un origen de datos y un conjunto de datos

Una vez que haya descargado e instalado el Generador de informes, siga el mismo flujo de trabajo que usa para agregar un origen de datos y un conjunto de datos insertados al informe. En el siguiente procedimiento, en **Orígenes de datos** verá una nueva opción: **Especificar datos**.  Solo tiene que configurar este origen de datos una vez en un informe. Después, puede crear varias tablas de datos especificados como conjuntos de datos independientes, todo ello con ese único origen de datos.

1. En el panel **Datos de informe**, haga clic en **Nuevo** > **Conjunto de datos**.

    ![Captura de pantalla de Nuevo conjunto de datos en el Generador de informes.](media/paginated-reports-enter-data/paginated-new-dataset.png)

1. En el cuadro de diálogo **Propiedades del conjunto de datos**, seleccione **Usar un conjunto de datos insertado en el informe**.

1. Junto a **Origen de datos**, haga clic en **Nueva**.

    ![Captura de pantalla de Nuevo origen de datos insertado.](media/paginated-reports-enter-data/paginated-new-data-source.png)

1. En el cuadro de diálogo **Propiedades del origen de datos**, seleccione **Usar una conexión incrustada en el informe**.
2. En el cuadro **Seleccionar el tipo de conexión**, seleccione **ENTER DATA** > **Aceptar**.

    ![Captura de pantalla del origen ENTER DATA.](media/paginated-reports-enter-data/paginated-data-source-properties-enter-data.png)

1. En el cuadro de diálogo **Propiedades del conjunto de datos**, haga clic en **Diseñador de consultas**.
2. En el panel **Diseñador de consultas**, haga clic con el botón derecho y pegue los datos en la tabla.

    ![Captura de pantalla de Especificar datos en el Diseñador de consultas.](media/paginated-reports-enter-data/paginated-enter-data.png)

1. Para establecer los nombres de las columnas, haga doble clic en el encabezado **NuevaColumna** de cada una de ellas y escriba el nombre de la columna.

    ![Captura de pantalla de Establecer los nombres de las columnas.](media/paginated-reports-enter-data/paginated-column-name.png)

1. Si la primera fila contiene los encabezados de columna de los datos originales, haga clic con el botón derecho y elimínela.
    
9. De forma predeterminada, el tipo de datos de cada columna es Cadena. Para cambiar el tipo de datos, haga clic con el botón derecho en el encabezado de columna > **Cambiar tipo** y establézcalo en otro tipo de datos, como Fecha o Flotante.

    ![Captura de pantalla de Cambiar el tipo de datos.](media/paginated-reports-enter-data/paginated-data-type.png)

1. Cuando haya terminado de crear la tabla, haga clic en **Aceptar**.  

    La consulta que se genera es la misma que vería con un origen de datos XML. En segundo plano, usamos XML como el proveedor de datos.  Lo hemos adaptado para aceptar también este escenario.

    ![Captura de pantalla de la estructura de datos XML.](media/paginated-reports-enter-data/paginated-xml-data.png)

12. En el cuadro de diálogo **Propiedades del conjunto de datos**, haga clic en **Aceptar**.

13. Verá el origen de datos y el conjunto de datos en el panel **Datos de informe**.

    ![Captura de pantalla de Conjunto de datos en el panel Datos de informe.](media/paginated-reports-enter-data/paginated-report-data-pane.png)

Puede usar el conjunto de datos como base para las visualizaciones de datos en el informe. También puede agregar otro conjunto de datos y usar el mismo origen de datos para él.

## <a name="design-the-report"></a>Diseño del informe

Ahora que tiene un origen de datos y un conjunto de datos, está listo para crear el informe. En el procedimiento siguiente se crea un informe simple basado en los datos de la sección anterior.

1. En el menú **Insertar**, seleccione **Tabla** > **Asistente para tablas**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-table-wizard.png" alt-text="Captura de pantalla de la selección de la opción Asistente para tablas.":::

1. Seleccione el conjunto de datos que acaba de crear > **Siguiente**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-choose-dataset.png" alt-text="Captura de pantalla del cuadro de diálogo Elegir un conjunto de datos.":::

2.  En la página Organizar campos, arrastre los campos por los que quiera agrupar desde el cuadro **Campos disponibles** hasta el cuadro **Grupos de filas**. En este ejemplo:

    - CountryRegion
    - SalesYear

3.  Arrastre los campos que quiera agregar desde el cuadro **Campos disponibles** hasta el cuadro **Valores**. En este ejemplo:

    - ImporteVentas

    De forma predeterminada, Generador de informes suma los campos del cuadro **Valores**, pero puede elegir otra agregación.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-aggregation.png" alt-text="Captura de pantalla de las diferentes agregaciones para elegir.":::
 
1. Seleccione **Siguiente**.
4.  En la página **Elegir el diseño**, mantenga toda la configuración predeterminada, pero desactive **Expandir o contraer grupos**. En general, la expansión y contracción de grupos es magnífica, pero esta vez quiere ver todos los datos.

5.  Seleccione **Siguiente** > **Finalizar**. La tabla se muestra en la superficie de diseño.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-design-view-matrix.png" alt-text="Captura de pantalla del informe en vista Diseño.":::

### <a name="run-the-report"></a>Ejecución del informe

Para ver los valores reales y obtener una vista previa del informe, ejecútelo.

1. Seleccione **Ejecutar** en la cinta **Inicio**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-run-report.png" alt-text="Captura de pantalla de la selección de Ejecutar en la cinta Inicio.":::

    Ahora verá los valores. La matriz tiene más filas de las que ha visto en la vista Diseño.  Puede dar formato a la página o decidir usar la configuración predeterminada antes de guardarla en el equipo local o publicarla en el servicio.

1. Para ver el aspecto que tendrá el informe al imprimirlo, seleccione **Diseño de impresión**.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-select-print.png" alt-text="Captura de pantalla de la selección de Diseño de impresión.":::

    Ahora lo ve tal y como aparecerá en una página impresa.

    :::image type="content" source="media/paginated-reports-enter-data/paginated-print-layout.png" alt-text="Captura de pantalla del informe en la vista Diseño de impresión.":::

## <a name="upload-the-paginated-report-to-the-power-bi-service"></a>Carga del informe paginado en el servicio Power BI

Ahora que se admiten informes paginados en el servicio Power BI, puede cargar el informe paginado en una capacidad Premium. Vea [Carga de un informe paginado](paginated-reports-save-to-power-bi-service.md) para obtener más información.

## <a name="upload-the-paginated-report-to-a-report-server"></a>Carga del informe paginado en un servidor de informes

También puede cargar el informe paginado en un servidor de informes de Power BI Report Server o SQL Server Reporting Services 2016 o 2017. Antes de hacerlo, deberá agregar el siguiente elemento al archivo RsReportServer.config como una extensión de datos adicional. Haga una copia de seguridad del archivo RsReportServer.config antes de realizar el cambio, en caso de que surja algún problema.

```xml
<Extension Name="ENTERDATA" Type="Microsoft.ReportingServices.DataExtensions.XmlDPConnection,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <ConfigName>ENTERDATA</ConfigName>
    </Configuration>
</Extension>
```

Después de editarlo, la lista de proveedores de datos del archivo de configuración debería ser similar a esta:

![Captura de pantalla del archivo de configuración RsReportServer.](media/paginated-reports-enter-data/paginated-rsreportserver-config-file.png)

Eso es todo, ya puede publicar informes que usen esta nueva funcionalidad en su servidor de informes.

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [¿Qué es Power BI Report Server?](../report-server/get-started.md)
