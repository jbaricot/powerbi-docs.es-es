---
title: Acceso a tablas destacadas de Power BI en Excel (versión preliminar)
description: En Excel, puede buscar datos de tablas destacadas en conjuntos de datos de Power BI en la galería de tipos de datos.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00fba391a6ad92f1e3edaf0e2af9691452724f6e
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251653"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Acceso a tablas destacadas de Power BI en Excel (versión preliminar)

En la galería de tipos de datos de Excel, puede buscar datos de *tablas destacadas* en conjuntos de datos de Power BI. Las tablas destacadas permiten agregar fácilmente datos a las hojas de Excel. Estos son los pasos para pasar de datos de Power BI a hojas de Excel.

- Un modelador de datos de Power BI [promueve o certifica un conjunto de datos en Power BI](../connect-data/service-datasets-promote.md).
- El modelador de datos [identifica las tablas destacadas](service-create-excel-featured-tables.md) en el conjunto de datos y lo guarda en el servicio Power BI.
- El resto de la organización puede conectarse a esas tablas destacadas en Excel para obtener datos pertinentes y actualizables. Excel hace referencia a esas tablas como *tipos de datos* y las enumera en la galería de tipos de datos.

> [!NOTE]
> En Excel, también puede obtener datos de cualquier conjunto de datos al que pueda acceder en Power BI. En la cinta **Datos**, seleccione **Obtener datos** > **De Power BI (Microsoft)** .
> :::image type="content" source="media/service-excel-featured-tables/excel-get-data-power-bi.png" alt-text="Captura de pantalla de la opción Obtener datos de Power BI en la cinta de datos.":::

## <a name="the-excel-data-types-gallery"></a>Galería de tipos de datos de Excel
Las tablas destacadas de los conjuntos de datos de Power BI aparecen como *tipos de datos* en la cinta **Datos**, en la galería **Tipos de datos** de Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Captura de pantalla de la galería de tipos de datos en la cinta Datos de Excel.":::

Cuando se expande, en la galería se muestran los tipos de datos genéricos, como **Acciones** y **Geografía**, además de los diez tipos de datos de la **organización** principales disponibles: tablas destacadas de conjuntos de datos de Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Captura de pantalla de la galería de tipos de datos de Excel.":::

## <a name="format-a-range-of-cells-as-a-table-optional"></a>Aplicación de formato de tabla a un intervalo de celdas (opcional)

 Antes de empezar, se recomienda dar formato a los datos como una tabla de Excel. De este modo, los cambios que realice en una fila se aplicarán a las demás filas de la tabla. 

1. Agregue un encabezado de columna. 
2. Después, seleccione una celda en los datos y presione Ctrl+T. 
3. Active **La tabla tiene encabezados** > **Aceptar**.

    :::image type="content" source="media/service-excel-featured-tables/excel-format-table.png" alt-text="Captura de pantalla de la conversión del intervalo en tabla.":::

## <a name="search-for-power-bi-data-in-the-excel-data-types-gallery"></a>Búsqueda de datos de Power BI en la galería de tipos de datos de Excel

Para buscar datos en una tabla destacada de Power BI, seleccione una celda o un rango de la hoja de Excel que contenga un valor que coincida con el valor de una tabla destacada. Seleccione **Organización**. Excel busca una coincidencia en todas las tablas destacadas a las que tenga acceso.

:::image type="content" source="media/service-excel-featured-tables/excel-table-organization.png" alt-text="Captura de pantalla de la selección de una celda o un rango de celdas.":::
 
Si conoce la tabla destacada que busca, seleccione **De su organización (versión preliminar)** en la galería y selecciónela.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data-table.png" alt-text="Captura de pantalla de datos de la organización de Excel, tabla de tipo de datos Proveedores.":::
 
Al realizar la búsqueda, si Excel encuentra filas coincidentes con confianza alta, las celdas se vinculan de inmediato a esas filas. El icono de elemento vinculado indica que las celdas están vinculadas a las filas en Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="Captura de pantalla del icono de elemento vinculado.":::

Si una celda tiene más de una posible fila coincidente, muestra un icono de signo de interrogación y se abre el panel **Selector de datos**. En el ejemplo siguiente, el usuario ha seleccionado el intervalo B2:B10 y ha buscado una tabla destacada de Power BI. Todas las filas tenían coincidencias excepto la celda B5, "Ma Maison". En el **Selector de datos** se muestran dos posibles coincidencias.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Captura de pantalla del panel Selector de datos de Excel.":::
 
La opción Datos de la organización puede devolver filas de varias tablas destacadas. Excel agrupa las filas potencialmente coincidentes según el tipo de datos del que proceden. Excel ordena los tipos de datos en función de su fila potencialmente coincidente más fuerte. Use las flechas de contenido adicional para contraer y expandir los tipos de datos a las filas coincidentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Captura de pantalla del panel Selector de datos de Excel con varias posibilidades.":::
 
En cada fila, seleccione el nombre de la fila para ver más detalles dentro de la fila para poder elegir la fila correcta. Cuando la haya encontrado, presione **Seleccionar** para vincular la fila con la celda en Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="Captura de pantalla de los detalles del Selector de datos.":::
 
Al seleccionar el icono **Tarjeta** en la celda se muestra una tarjeta con datos de todos los campos y campos calculados de la tabla destacada. El título de la tarjeta muestra el valor del campo de etiqueta de fila de la tabla destacada.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Captura de pantalla de los detalles del elemento vinculado.":::

Seleccione el icono **Insertar datos** y, después, el nombre de un campo en la lista de campos para agregar su valor a la cuadrícula.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Captura de pantalla de la selección de un nombre de campo.":::

El valor (o valores) del campo se coloca en las celdas adyacentes. La fórmula de la celda hace referencia a la celda vinculada y al nombre del campo, por lo que puede usar los datos en las funciones de Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Captura de pantalla de la fórmula de celda de Excel.":::

## <a name="cell-formulas"></a>Fórmulas de celda

Al usar una tabla de Excel, puede hacer referencia a la columna de la tabla vinculada y, a continuación, agregar campos de datos mediante la referencia `.` (punto).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Captura de pantalla de la referencia de punto de Excel.":::

Del mismo modo, cuando usa una celda, puede hacer referencia a la celda y usar la referencia `.` (punto) para recuperar los campos.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Captura de pantalla de la referencia de punto de celda.":::
 
## <a name="data-caching-and-refresh"></a>Almacenamiento en caché y actualización de datos

Cuando Excel vincula una celda a una fila de tabla destacada de Power BI, recupera y guarda todos los valores de campo en el archivo de Excel. Cualquier persona con la que comparta el archivo puede hacer referencia a cualquiera de los campos, sin solicitar datos de Power BI.  

Use el botón **Actualizar todo** de la cinta de opciones **Datos** para actualizar los datos de las celdas vinculadas. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Captura de pantalla de Actualizar todo.":::
 
También puede actualizar celdas individuales. Haga clic con el botón derecho en la celda y seleccione **Tipos de datos** > **Actualizar**.

## <a name="show-a-card-change-or-convert-to-text"></a>Visualización de una tarjeta, actualización o conversión en texto

Las celdas vinculadas han agregado opciones del menú contextual. Haga clic con el botón derecho en una celda. Junto con las opciones habituales, también verá lo siguiente:

- **Mostrar tarjeta de tipo de datos**.
- **Actualice**.
- **Cambiar**.
- **Convertir en texto**

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Captura de pantalla del menú contextual, Convertir en texto.":::
 
**Convertir en texto** quita el vínculo a la fila en la tabla destacada de Power BI. Lo importante es que el texto de la celda será el valor de la etiqueta de fila de la celda vinculada. Si vinculó una celda a una fila por accidente, seleccione **Deshacer** en Excel para restaurar los valores iniciales de la celda.

## <a name="licensing"></a>Licencias

La galería de tipos de datos de Excel y las experiencias conectadas a las tablas destacadas de Power BI solo están disponibles para los clientes de Excel E5 y G5. 

## <a name="security"></a>Seguridad

Solo verá las tablas destacadas de los conjuntos de datos a los que tiene permiso en Power BI. Al actualizar los datos, debe tener permiso de acceso al conjunto de datos en Power BI para recuperar las filas. Esto requiere el permiso de compilación o de escritura en el conjunto de datos. Excel almacena en caché los datos devueltos para toda la fila. Cualquier persona con la que comparta el archivo de Excel puede ver los datos de todos los campos en todas las celdas vinculadas.

Si un conjunto de datos de Power BI tiene una seguridad de nivel de fila o una etiqueta de confidencialidad de Microsoft Information Protection aplicada, las tablas destacadas de ese conjunto de datos no se incluyen en la galería de tipos de datos de Excel. Esta es una limitación de la versión preliminar inicial.

## <a name="administrative-control"></a>Control administrativo

Los administradores de Power BI pueden controlar qué usuarios de la organización pueden usar las tablas destacadas en la galería de tipos de datos de Excel. Para más información, consulte [Configuración de tablas destacadas](../admin/service-admin-portal.md#featured-tables-settings) en el artículo del portal de administración. 
 
### <a name="auditing"></a>Auditoría

Los registros de auditoría de la administración muestran estos eventos para las tablas destacadas:

- **AnalyzedByExternalApplication**: da a los administradores visibilidad sobre qué usuarios acceden a qué tablas destacadas.
- **UpdateFeaturedTables**: da a los administradores visibilidad sobre qué usuarios publican y actualizan las tablas destacadas.

Para una lista completa de los eventos de registro de auditoría, consulte [Seguimiento de actividades de usuario en Power BI](../admin/service-admin-auditing.md).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

A continuación se indican las limitaciones de la versión preliminar inicial:

- La integración está disponible en las compilaciones de Excel Insider.
- La galería de tipos de datos de Excel incluye tablas destacadas para los usuarios con la licencia adecuada en el servicio Power BI y Power BI Desktop. Es posible que la compatibilidad con el servicio Power BI no esté disponible en el momento del lanzamiento de la versión preliminar, pero se agregará.
- En Excel no se muestran las tablas destacadas de los conjuntos de datos de Power BI que usan las funcionalidades siguientes: 

    - Conjuntos de datos de seguridad de nivel de fila.
    - Conjuntos de datos habilitados para Microsoft Information Protection.
    - Conjuntos de datos de DirectQuery.
    - Conjuntos de datos con una conexión dinámica.

- Excel solo muestra los datos en las columnas y las columnas calculadas en la tabla destacada. Los siguientes elementos no se proporcionan en la versión preliminar inicial:

    - Medidas definidas en la tabla destacada.
    - Medidas definidas en las tablas relacionadas y medidas implícitas calculadas a partir de las relaciones.

- Excel solo muestra las tablas destacadas (*tipos de datos*) que se almacenan en las áreas de trabajo nuevas de Power BI. Las tablas destacadas almacenadas en las áreas de trabajo clásicas o en Mi área de trabajo no se muestran como tipos de datos en Excel. Puede [actualizar las áreas de trabajo clásicas a las áreas de trabajo nuevas](service-upgrade-workspaces.md) en Power BI.

La experiencia de los tipos de datos en Excel es similar a la de una función de búsqueda. Toma un valor de celda proporcionado por la hoja de Excel y busca filas coincidentes en las tablas destacadas de Power BI. La experiencia de búsqueda tiene estos comportamientos:

- Al usar el botón **Datos de la organización** para hacer búsquedas, Excel solo busca tablas destacadas en los conjuntos de datos certificados.
- La coincidencia de filas se basa en las columnas de texto de la tabla destacada. Usa la misma indexación que la funcionalidad de preguntas y respuestas de Power BI, que está optimizada para una búsqueda en inglés. La búsqueda en otros idiomas podría no generar coincidencias precisas. Las columnas numéricas no toman en cuenta para la coincidencia.
- La coincidencia se basa en las coincidencias exacta y de prefijo para los términos de búsqueda individuales. El valor de una celda se divide en función de los espacios u otros caracteres de espacio en blanco, como los caracteres de tabulación. Luego, cada palabra se considera un término de búsqueda. Los valores de campo de texto de una fila se comparan con cada término de búsqueda para buscar coincidencias exactas y de prefijo. Se devuelve una coincidencia de prefijo si el campo de texto de la fila comienza con el término de búsqueda. Por ejemplo, si una celda contiene "Reino Unido", "Reino" y "Unido" son términos de búsqueda distintos. 

    - Se devuelven las filas con columnas de texto cuyo valor coincide exactamente con "Reino" y "Unido". 
    - Se devuelven las filas con columnas de texto cuyo valor empieza con "Reino" o "Unido". 
    - Y hay que considerar que no se devuelven las filas que incluyen "Reino" o "Unido", pero que no empiezan con esos términos.

- Power BI devuelve como máximo 100 sugerencias de fila para cada celda.
- No se admite establecer ni actualizar la tabla destacada en el punto de conexión de XMLA.
- Los archivos de Excel con un modelo de datos se pueden usar para publicar tablas destacadas. Cargue los datos en Power BI Desktop y, a continuación, publique la tabla destacada.
- Cambiar el nombre de la tabla, la etiqueta de la fila o la columna clave de la tabla destacada puede afectar a los usuarios de Excel con celdas vinculadas a las filas de la tabla. 
- Excel muestra cuando se recuperaron los datos del conjunto de datos de Power BI. Esto no es necesariamente la hora en que los datos se actualizaron en Power BI ni la hora del punto de datos más reciente en un conjunto de datos. Por ejemplo, suponga que un conjunto de datos de Power BI se actualizó hace una semana, pero los datos de origen subyacentes tenían ya una semana cuando se produjo la actualización. Los datos reales tendrían 2 semanas, pero Excel mostraría los datos recuperados con la fecha y hora en que los datos se extrajeron de Excel.

## <a name="next-steps"></a>Pasos siguientes

- [Establecimiento de tablas destacadas en Power BI Desktop](service-create-excel-featured-tables.md)
- Obtenga información sobre el [uso de tipos de datos de Excel desde Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) en la documentación de Excel.
- ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

