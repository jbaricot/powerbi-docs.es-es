---
title: Acceso a tablas destacadas de Power BI en Excel (versión preliminar)
description: En Excel, puede buscar datos de tablas destacadas en conjuntos de datos de Power BI en la galería de tipos de datos.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d8ef72f25509fe41c983e7385095fdad5985f5de
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2020
ms.locfileid: "83793534"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Acceso a tablas destacadas de Power BI en Excel (versión preliminar)

En Excel, puede buscar datos de tablas destacadas en conjuntos de datos de Power BI en la galería de tipos de datos. Las tablas destacadas permiten agregar fácilmente datos a las hojas de Excel. Con las funcionalidades de los conjuntos de datos certificados y promovidos de Power BI, las organizaciones permiten que más usuarios busquen y usen datos pertinentes y actualizables para tomar mejores decisiones. Obtenga más información sobre cómo usar los [tipos de datos de Excel de Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) en la documentación de Excel.

La galería de tipos de datos solo muestra las tablas destacadas que un modelador ha mantenido en los conjuntos de datos de Power BI. También puede examinar cualquier conjunto de datos de Excel al que pueda acceder en Power BI. En Excel, seleccione la opción **Conjuntos de datos de Power BI** bajo **Obtener datos** en la cinta de opciones **Datos**.

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Acceso a datos de Power BI a través de la galería de tipos de datos de Excel
Las tablas destacadas de los conjuntos de datos de Power BI aparecen en la galería de tipos de datos de Excel en la cinta de opciones Datos.

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Cinta de opciones Datos de Excel":::

Cuando se expande, la galería muestra los tipos de datos principales disponibles.

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Galería de tipos de datos de Excel":::
 
Para buscar datos en una tabla destacada de Power BI, seleccione una celda o un rango de la hoja de Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="Seleccionar una celda":::
 
Seleccione la opción **Datos de la organización** en la galería para buscar datos en las tablas destacadas de los conjuntos de datos certificados a los que tiene acceso.

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Datos de la organización de Excel":::
 
Seleccione un tipo de datos específico si sabe qué tipo de datos busca o no encuentra filas coincidentes con la opción Datos de la organización.

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="Seleccionar un tipo de datos":::
 
Al buscar, si se encuentra una fila coincidente con confianza alta, la celda se vincula de inmediato a esa fila. El icono de elemento vinculado indica que la celda está vinculada a la fila en Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Icono de elemento vinculado":::

Si una celda tiene varias filas posiblemente coincidentes, se muestra un panel de selector de datos. La celda muestra el icono de signo de interrogación, que abre el panel de selector de datos en esa fila. A continuación se muestra un ejemplo de qué pasa después de que el usuario seleccionó un rango desde A2:A7 y buscó una tabla destacada de Power BI.

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="Varias filas posiblemente coincidentes":::

En el panel **Selector de datos** se muestran las filas potencialmente coincidentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Panel Selector de datos de Excel":::
 
La opción Datos de la organización puede devolver filas de varios tipos de datos. Excel agrupa las filas potencialmente coincidentes según el tipo de datos del que proceden. Excel ordena los tipos de datos en función de su fila potencialmente coincidente más fuerte. Use las flechas de contenido adicional para contraer y expandir los tipos de datos a las filas coincidentes.

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Panel Selector de datos de Excel":::
 
En cada fila, seleccione el nombre de la fila para ver más detalles dentro de la fila para poder elegir la fila correcta. Una vez que encuentre una fila, presione **Seleccionar** para vincular la fila con la celda en Excel. 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="Detalles del selector de datos":::
 
Cuando se selecciona una fila, la celda está vinculada a la fila y su valor está con el valor del campo **Etiqueta de fila** en la tabla destacada de Power BI. 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Elemento vinculado de Excel":::
 
Al seleccionar el icono **Celda vinculada**, se muestra una tarjeta con datos de cualquier campo y los campos calculados de la tabla destacada. El título de la tarjeta muestra el valor del campo de etiqueta de fila de la tabla destacada.
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="Detalles del elemento vinculado":::

Seleccione el icono **Insertar datos** para agregar valores de campo a la cuadrícula.

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="Inserción de datos"::: 

Seleccione un nombre de campo en la lista de campos para agregar su valor a la cuadrícula.  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="Seleccionar un nombre de campo":::

El valor del campo se coloca en la celda adyacente. La fórmula de la celda hace referencia a la celda vinculada y al nombre del campo, por lo que puede usar los datos en las funciones de Excel.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Fórmula de celda de Excel":::
 
Cuando da formato a los datos como una tabla de Excel, al agregar campos se expande la tabla y se establece el encabezado de columna para que coincida con el nombre del campo. Las filas vinculadas a los mismos tipos de datos también se rellenan con sus respectivos valores.

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="El campo es el nombre de columna"::: 

## <a name="cell-formulas"></a>Fórmulas de celda

Al usar una tabla de Excel, puede hacer referencia a la columna de la tabla vinculada y, a continuación, agregar campos de datos mediante la referencia `.` (punto).

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Referencia de punto de Excel":::

Del mismo modo, cuando usa una celda, puede hacer referencia a la celda y usar la referencia `.` (punto) para recuperar los campos.

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="Referencia de punto de celda":::
 
## <a name="data-caching-and-refresh"></a>Almacenamiento en caché y actualización de datos

Cuando Excel vincula una celda a una fila de tabla destacada de Power BI, recupera y guarda todos los valores de campo en el archivo de Excel. Cualquier persona con la que comparta el archivo puede hacer referencia a cualquiera de los campos, sin solicitar datos de Power BI.  

Use el botón **Actualizar todo** de la cinta de opciones **Datos** para actualizar los datos de las celdas vinculadas. 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="Actualizar todo":::
 
También puede actualizar celdas individuales. Haga clic con el botón derecho en la celda y seleccione **Tipos de datos** > **Actualizar**.

## <a name="show-a-card-change-or-convert-to-text"></a>Visualización de una tarjeta, actualización o conversión en texto

Las celdas vinculadas han agregado opciones del menú contextual. Haga clic con el botón derecho en una celda > seleccione **Tipo de datos** >  

- **Mostrar tarjeta**
- **Actualizar**
- **Cambio** 
- **Convertir en texto**

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="Clic con el botón derecho, convertir en texto":::
 
**Convertir en texto** quita el vínculo a la fila en la tabla destacada de Power BI. Lo importante es que el texto de la celda será el valor de la etiqueta de fila de la celda vinculada. Si vinculó una celda a una fila por accidente, seleccione **Deshacer** en Excel para restaurar los valores iniciales de la celda.

## <a name="licensing"></a>Licencias
La galería de tipos de datos de Excel y las experiencias conectadas a las tablas destacadas de Power BI solo están disponibles para los clientes de Excel E5 y G5. 

## <a name="security"></a>Seguridad

Solo verá las tablas destacadas de los conjuntos de datos a los que tiene permiso en Power BI. Al actualizar los datos, debe tener permiso de acceso al conjunto de datos en Power BI para recuperar las filas. Esto requiere el permiso de compilación o de escritura en el conjunto de datos. Excel almacena en caché los datos devueltos para toda la fila. Cualquier persona con la que comparta el archivo de Excel puede ver los datos de todos los campos en todas las celdas vinculadas.

Si un conjunto de datos de Power BI tiene una seguridad de nivel de fila o una etiqueta de confidencialidad de Microsoft Information Protection aplicada, las tablas destacadas de ese conjunto de datos no se incluyen en la galería de tipos de datos de Excel. Esta es una limitación de la versión preliminar inicial.

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Mantenimiento de una tabla destacada en Power BI Desktop
La galería de tipos de datos de Excel muestra las tablas destacadas en los conjuntos de datos cargados en el servicio Power BI. Use Power BI Desktop para mantener las tablas destacadas en el modelo de datos y, a continuación, cárguelas en el servicio Power BI.

### <a name="turn-on-the-featured-table-preview"></a>Activación de la versión preliminar de una tabla destacada

1. En Power BI Desktop, seleccione **Archivo** > **Opciones y configuración** > **Opciones** > **Características en versión preliminar**.
2. Active la casilla **Tablas destacadas**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Opción de tablas destacadas en versión preliminar":::

### <a name="select-a-table"></a>Selección de una tabla

1. En Power BI Desktop, vaya a la vista Modelo.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Vista Modelo":::
 
2. Seleccione una tabla y establezca la opción **Es una tabla destacada** en **Sí**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Establecer Es una tabla destacada en Sí":::

4. En **Configurar esta tabla destacada**, proporcione los campos obligatorios:

    - Una **descripción**.
    - El valor del campo **Etiqueta de fila** se usa en Excel para que los usuarios puedan identificar fácilmente la fila. Aparece como el valor de celda de una celda vinculada, en el panel **Selector de datos** y en la tarjeta de **Información**. 
    - El valor del campo **Columna clave** proporciona el id. único de la fila. Este valor permite que Excel vincule una celda a una fila específica de la tabla.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configuración de la tabla destacada":::

Después de publicar o importar el conjunto de datos al servicio Power BI, la tabla destacada se muestra en la galería de tipos de datos de Excel.

- Excel almacena en caché la lista de tipos de datos, por lo que necesita reiniciar Excel para ver las tablas destacadas recién publicadas.
- Algunos conjuntos de datos no se admiten en la versión preliminar, las tablas destacadas definidas en esos conjuntos de datos no aparecerán en Excel. Para detalles, consulte las consideraciones y limitaciones.

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

- Excel solo muestra las tablas destacadas que se almacenan en las áreas de trabajo nuevas de Power BI. Las tablas destacadas almacenadas en las áreas de trabajo clásicas o en Mi área de trabajo no se muestran como tipos de datos en Excel. Puede [actualizar las áreas de trabajo clásicas a las áreas de trabajo nuevas](service-upgrade-workspaces.md) en Power BI.

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

- ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

