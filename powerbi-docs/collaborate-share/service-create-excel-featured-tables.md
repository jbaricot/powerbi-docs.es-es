---
title: Establecimiento de tablas destacadas en Power BI Desktop (versión preliminar)
description: Cree tablas destacadas en Power BI Desktop para que aparezcan en la galería de tipos de datos de Excel.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: d2d87f16b8100424b47277360354d79ee834d467
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411940"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Establecimiento de tablas destacadas en Power BI Desktop (versión preliminar)

En la galería de tipos de datos de Excel, los usuarios pueden buscar datos de *tablas destacadas* de los conjuntos de datos de Power BI. En este artículo, aprenderá a establecer tablas como *destacadas* en los conjuntos de datos. Estas etiquetas facilitan a los usuarios la adición de datos empresariales a sus hojas de Excel. Estos son los pasos básicos para configurar y compartir tablas destacadas.

1. Debe identificar las tablas destacadas en los conjuntos de datos en Power BI Desktop (este artículo).
1. Debe guardar esos conjuntos de datos con las tablas destacadas en una de las nuevas áreas de trabajo. Los creadores de informes pueden crear informes con esas tablas destacadas. 
1. El resto de la organización puede conectarse a esas tablas destacadas, denominadas *tipos de datos* en Excel, para obtener datos pertinentes y actualizables. En el artículo [Acceso a tablas destacadas de Power BI en Excel (versión preliminar)](service-excel-featured-tables.md) se describe el consumo de estas tablas destacadas en Excel.

> [!NOTE]
> Puede [promover o certificar conjuntos de datos en Power BI](../collaborate-share/service-endorse-content.md). A esto se le denomina *aprobación*. Excel da prioridad a las tablas de los conjuntos de datos aprobados en la Galería de tipos de datos. Excel muestra en primer lugar las tablas destacadas en conjuntos de datos certificados y, después, las tablas de los conjuntos de datos promovidos. Después, Excel muestra las tablas destacadas en conjuntos de datos no aprobados. 

## <a name="turn-on-the-featured-table-preview"></a>Activación de la versión preliminar de una tabla destacada

1. En Power BI Desktop, seleccione **Archivo** > **Opciones y configuración** > **Opciones** > **Características en versión preliminar**.
2. Active la casilla **Tablas destacadas**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Opción de tablas destacadas en versión preliminar":::

3. Reinicie Power BI Desktop.

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
    - Algunos conjuntos de datos no se admiten en la versión preliminar, las tablas destacadas definidas en esos conjuntos de datos no aparecerán en Excel. Para obtener más información, vea la siguiente sección, Consideraciones y limitaciones.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Estas son las limitaciones de la versión preliminar inicial.

- En Excel no se muestran las tablas destacadas de los conjuntos de datos de Power BI que usan las funcionalidades siguientes:

    - Conjuntos de datos de DirectQuery.
    - Conjuntos de datos con una conexión dinámica.

- Excel solo muestra los datos en las columnas y las columnas calculadas en la tabla destacada. Las medidas definidas en las tablas relacionadas y las medidas implícitas calculadas a partir de las relaciones no se proporcionan en la versión preliminar inicial.
- Excel solo muestra las tablas destacadas que se almacenan en las áreas de trabajo nuevas de Power BI. Las tablas destacadas almacenadas en las áreas de trabajo clásicas no se muestran como tipos de datos en Excel. Puede [actualizar las áreas de trabajo clásicas a las áreas de trabajo nuevas](service-upgrade-workspaces.md) en Power BI.
- Vea [Consideraciones y limitaciones](service-excel-featured-tables.md#considerations-and-limitations) en el artículo "Acceso a tablas destacadas de Power BI en Excel" para obtener otras consideraciones de Excel.

## <a name="next-steps"></a>Pasos siguientes

- [Acceso a tablas destacadas de Power BI en Excel](service-excel-featured-tables.md)
- Obtenga información sobre el [uso de tipos de datos de Excel desde Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) en la documentación de Excel.
- ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

