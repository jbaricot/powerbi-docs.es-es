---
title: Establecimiento de tablas destacadas en Power BI Desktop
description: Cree tablas destacadas en Power BI Desktop para que aparezcan en la galería de tipos de datos de organización.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906897"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>Establecimiento de tablas destacadas en Power BI Desktop para que aparezcan en la galería de tipos de datos de organización de Excel

En la galería de tipos de datos de Excel, los usuarios pueden buscar datos de *tablas destacadas* de los conjuntos de datos de Power BI. En este artículo, aprenderá a establecer tablas como *destacadas* en los conjuntos de datos. Estas etiquetas facilitan a los usuarios la adición de datos empresariales a sus hojas de Excel. Estos son los pasos básicos para configurar y compartir tablas destacadas.

1. Debe identificar las tablas destacadas en los conjuntos de datos en Power BI Desktop (este artículo).
1. Debe guardar esos conjuntos de datos con las tablas destacadas en una de las nuevas áreas de trabajo. Los creadores de informes pueden crear informes con esas tablas destacadas. 
1. El resto de la organización puede conectarse a esas tablas destacadas, denominadas *tipos de datos* en Excel, para obtener datos pertinentes y actualizables. En el artículo [Acceso a tablas destacadas de Power BI en Excel](service-excel-featured-tables.md) se describe el consumo de estas tablas destacadas en Excel.

> [!NOTE]
> Puede [promover o certificar conjuntos de datos en Power BI](../collaborate-share/service-endorse-content.md). A esto se le denomina *aprobación*. Excel da prioridad a las tablas de los conjuntos de datos aprobados en la Galería de tipos de datos. Excel muestra en primer lugar las tablas destacadas en conjuntos de datos certificados y, después, las tablas de los conjuntos de datos promovidos. Después, Excel muestra las tablas destacadas en conjuntos de datos no aprobados. 

> [!NOTE]
> A partir de la versión de Power BI Desktop de diciembre de 2020, la creación de tablas destacadas está disponible de forma predeterminada. Si usa una versión anterior, actualice Power BI Desktop o habilite la función **Tablas presentadas** yendo a **Archivo** > **Opciones y configuraciones** > **Opciones** > **Características de versión preliminar**.

## <a name="select-a-table"></a>Selección de una tabla

1. En Power BI Desktop, vaya a la vista Modelo.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Vista Modelo":::
 
2. Seleccione una tabla y establezca la opción **Es una tabla destacada** en **Sí**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Establecer Es una tabla destacada en Sí":::

4. En **Configurar esta tabla destacada**, proporcione los campos obligatorios:

    - Una **descripción**. 
        > [!TIP]
        > Comience la descripción con "Tabla destacada" para ayudar a los creadores de informes de Power BI a identificarla.
    - El valor del campo **Etiqueta de fila** se usa en Excel para que los usuarios puedan identificar fácilmente la fila. Aparece como el valor de celda de una celda vinculada, en el panel **Selector de datos** y en la tarjeta de **Información**. 
    - El valor del campo **Columna clave** proporciona el id. único de la fila. Este valor permite que Excel vincule una celda a una fila específica de la tabla.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Configuración de la tabla destacada":::

1. Después de publicar o importar el conjunto de datos al servicio Power BI, la tabla destacada se muestra en la galería de tipos de datos de Excel. Usted y otros creadores de informes también pueden crear informes basados en este conjunto de datos.

1. En Excel: 
    - Excel almacena en caché la lista de tipos de datos, por lo que necesita reiniciar Excel para ver las tablas destacadas recién publicadas.
    - Algunos conjuntos de datos no pueden usarse. Las tablas destacadas definidas en esos conjuntos de datos no aparecerán en Excel. Para obtener más información, vea la siguiente sección, Consideraciones y limitaciones.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Estas son las limitaciones actuales:

- La integración está disponible en Excel en el canal actual.
- En Excel no se muestran las tablas destacadas de los conjuntos de datos de Power BI que usan las funcionalidades siguientes: 

    - Conjuntos de datos de DirectQuery.
    - Conjuntos de datos con una conexión dinámica.

- Excel solo muestra datos en columnas, columnas calculadas y mediciones definidas en la tabla destacada. No se proporciona lo siguiente:
   
    - Medidas definidas en las tablas relacionadas
    - Medidas implícitas calculadas a partir de relaciones

- Excel solo muestra las tablas destacadas (*tipos de datos*) que se almacenan en las áreas de trabajo nuevas de Power BI. Las tablas destacadas almacenadas en las áreas de trabajo clásicas no se muestran como tipos de datos en Excel. Puede [actualizar las áreas de trabajo clásicas a las áreas de trabajo nuevas](service-upgrade-workspaces.md) en Power BI.

La experiencia de los tipos de datos en Excel es similar a la de una función de búsqueda. Toma un valor de celda proporcionado por la hoja de Excel y busca filas coincidentes en las tablas destacadas de Power BI. La experiencia de búsqueda tiene estos comportamientos:

- La coincidencia de filas se basa en las columnas de texto de la tabla destacada. Usa la misma indexación que la funcionalidad de preguntas y respuestas de Power BI, que está optimizada para una búsqueda en inglés. La búsqueda en otros idiomas podría no generar coincidencias precisas. 
- La mayoría de las columnas numéricas no se tienen en cuenta para hallar coincidencias. Si la etiqueta de fila o la columna clave son numéricas, se incluyen para la búsqueda de coincidencias.
- La coincidencia se basa en las coincidencias exacta y de prefijo para los términos de búsqueda individuales. El valor de una celda se divide en función de los espacios u otros caracteres de espacio en blanco, como los caracteres de tabulación. Luego, cada palabra se considera un término de búsqueda. Los valores de campo de texto de una fila se comparan con cada término de búsqueda para buscar coincidencias exactas y de prefijo. Se devuelve una coincidencia de prefijo si el campo de texto de la fila comienza con el término de búsqueda. Por ejemplo, si una celda contiene "Reino Unido", "Reino" y "Unido" son términos de búsqueda distintos. 

    - Se devuelven las filas con columnas de texto cuyos valores coinciden exactamente con "Reino" o "Unido". 
    - Se devuelven las filas con columnas de texto cuyos valores empiezan con "Reino" o "Unido". 
    - Y hay que considerar que no se devuelven las filas que incluyen "Reino" o "Unido", pero que no empiezan con esos términos.

- Power BI devuelve como máximo 100 sugerencias de fila para cada celda.
- Algunos símbolos no se pueden usar.
- En los puntos de conexión XMLA no se puede establecer ni actualizar la tabla destacada.
- Los archivos de Excel con un modelo de datos se pueden usar para publicar tablas destacadas. Cargue los datos en Power BI Desktop y, a continuación, publique la tabla destacada.
- Cambiar el nombre de la tabla, la etiqueta de la fila o la columna clave de la tabla destacada puede afectar a los usuarios de Excel con celdas vinculadas a las filas de la tabla. 
- Excel muestra cuando se recuperaron los datos del conjunto de datos de Power BI. Esto no es necesariamente la hora en que los datos se han actualizado en Power BI ni la hora del punto de datos más reciente en un conjunto de datos. Por ejemplo, suponga que un conjunto de datos de Power BI se actualizó hace una semana, pero los datos de origen subyacentes tenían ya una semana cuando se produjo la actualización. Los datos reales tendrían dos semanas, pero Excel mostraría los datos recuperados con la fecha y hora en que los datos se han extraído en Excel.
- Vea [Consideraciones y limitaciones](service-excel-featured-tables.md#considerations-and-limitations) en el artículo "Acceso a tablas destacadas de Power BI en Excel" para obtener otras consideraciones de Excel.

## <a name="next-steps"></a>Pasos siguientes

- [Acceso a tablas destacadas de Power BI en Excel](service-excel-featured-tables.md)
- Obtenga información sobre el [uso de tipos de datos de Excel desde Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) en la documentación de Excel.
- ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

