---
title: Establecimiento de tablas destacadas en Power BI Desktop (versión preliminar)
description: Cree tablas destacadas en Power BI Desktop para que aparezcan en la galería de tipos de datos de Excel.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: e39d2fe11a58691b259784c292fec6e5ee6cb322
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254222"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Establecimiento de tablas destacadas en Power BI Desktop (versión preliminar)

En la galería de tipos de datos de Excel, los usuarios pueden buscar datos de *tablas destacadas* de los conjuntos de datos de Power BI. En este artículo, aprenderá a establecer tablas como *destacadas* en los conjuntos de datos. Estas etiquetas facilitan a los usuarios la adición de datos empresariales a sus hojas de Excel. Estos son los pasos básicos para configurar y compartir tablas destacadas.

1. Debe [promocionar o certificar los conjuntos de datos en Power BI](../connect-data/service-datasets-promote.md). 
1. Debe identificar las tablas destacadas en los conjuntos de datos en Power BI Desktop (este artículo).
1. Debe guardar esos conjuntos de datos con las tablas destacadas en una de las nuevas áreas de trabajo. Los creadores de informes pueden crear informes con esas tablas destacadas. 
1. El resto de la organización puede conectarse a esas tablas destacadas, denominadas *tipos de datos* en Excel, para obtener datos pertinentes y actualizables. En el artículo [Acceso a tablas destacadas de Power BI en Excel (versión preliminar)](service-excel-featured-tables.md) se describe el consumo de estas tablas destacadas en Excel.

## <a name="turn-on-the-featured-table-preview"></a>Activación de la versión preliminar de una tabla destacada

1. En Power BI Desktop, seleccione **Archivo** > **Opciones y configuración** > **Opciones** > **Características en versión preliminar**.
2. Active la casilla **Tablas destacadas**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Opción de tablas destacadas en versión preliminar":::

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

    - Conjuntos de datos de seguridad de nivel de fila.
    - Conjuntos de datos habilitados para Microsoft Information Protection.
    - Conjuntos de datos de DirectQuery.
    - Conjuntos de datos con una conexión dinámica.

- Excel solo muestra los datos en las columnas y las columnas calculadas en la tabla destacada. Los siguientes elementos no se proporcionan en la versión preliminar inicial:

    - Medidas definidas en la tabla destacada.
    - Medidas definidas en las tablas relacionadas y medidas implícitas calculadas a partir de las relaciones.

- Excel solo muestra las tablas destacadas que se almacenan en las áreas de trabajo nuevas de Power BI. Las tablas destacadas almacenadas en las áreas de trabajo clásicas o en Mi área de trabajo no se muestran como tipos de datos en Excel. Puede [actualizar las áreas de trabajo clásicas a las áreas de trabajo nuevas](service-upgrade-workspaces.md) en Power BI.
- Vea [Consideraciones y limitaciones](service-excel-featured-tables.md#considerations-and-limitations) en el artículo "Acceso a tablas destacadas de Power BI en Excel" para obtener otras consideraciones de Excel.

## <a name="next-steps"></a>Pasos siguientes

- [Acceso a tablas destacadas de Power BI en Excel](service-excel-featured-tables.md)
- Obtenga información sobre el [uso de tipos de datos de Excel desde Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) en la documentación de Excel.
- ¿Tiene alguna pregunta? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

