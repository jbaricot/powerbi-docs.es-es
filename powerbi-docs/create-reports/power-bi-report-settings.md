---
title: Cambio de la configuración de los informes de Power BI
description: Cambio de la configuración de los informes del servicio Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: dbb173c65ecfc5d1ca464387ed43ae615cdcbca1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396185"
---
# <a name="change-settings-for-power-bi-reports"></a>Cambio de la configuración de los informes de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Con la configuración de los informes de Power BI Desktop y el servicio Power BI, puede controlar cómo interactúan los lectores con un informe. Por ejemplo, puede permitirles guardar filtros para el informe, personalizar los objetos visuales que contiene o mostrar sus páginas como pestañas en la parte inferior del informe en lugar de hacerlo en el lateral.

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Captura de pantalla del panel Configuración del informe en el servicio Power BI.":::

Puede que le resulte útil leer estos artículos en primer lugar:

- [Creación de un informe en el servicio Power BI mediante la importación de un conjunto de datos](service-report-create-new.md), para comprender la experiencia de creación de informes.
- [Informes en Power BI](../consumer/end-user-reports.md), para comprender la experiencia de los lectores de informes.

 Comencemos.

## <a name="prerequisites"></a>Requisitos previos

- Para crear informes con Power BI Desktop, consulte [Vista de informes en Power BI Desktop](desktop-report-view.md).
- [Suscribirse al servicio Power BI](../fundamentals/service-self-service-signup-for-power-bi.md). 
- Debe tener permiso de edición para el informe en el servicio Power BI. Vea [Roles en las áreas de trabajo nuevas](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) para obtener información más detallada sobre el permiso.
- Si aún no tiene un informe en el servicio Power BI, puede [instalar un paquete de contenido de ejemplo](sample-datasets.md#install-built-in-content-packs) que incluye un panel, un informe y un conjunto de datos.

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>Apertura del panel Configuración en Power BI Desktop

1. Seleccione **Archivo** > **Opciones y configuración** > **Opciones**.
1. En **Archivo actual**, seleccione **Configuración de informes**.

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Captura de pantalla del panel Configuración del informe en Power BI Desktop":::

    En el resto de este artículo se indican algunos de los valores de configuración específicos del informe.

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>Apertura del panel Configuración en el servicio Power BI

1. En la vista de lectura del informe, seleccione **Archivo** > **Configuración**.

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="Captura de pantalla del menú Archivo en Configuración.":::

1. En el panel **Configuración**, verá una serie de alternadores que se pueden establecer, solo para este informe. En el resto de este artículo se indican algunas de estas.

## <a name="set-featured-content"></a>Establecimiento de contenido destacado

Puede destacar paneles, informes y aplicaciones de forma que aparezcan en la sección Destacados de la página Inicio de Power BI de los compañeros. Obtenga más información sobre [cómo destacar contenido](../collaborate-share/service-featured-content.md).

## <a name="set-the-pages-pane"></a>Establecimiento del panel Páginas

Actualmente, solo se puede cambiar la configuración del panel Páginas en el servicio Power BI. Al activar el **panel Páginas**, en la vista de lectura los lectores de informes ven las pestañas de la página del informe en la parte inferior de este, en lugar de en el lateral. En la vista de edición, las pestañas de la página del informe ya están en la parte inferior del informe.

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="Captura de pantalla del establecimiento del panel Páginas.":::

## <a name="control-filters"></a>Filtros de control

El panel **Configuración** del informe tiene tres opciones para controlar las interacciones del lector con los filtros. Los vínculos siguientes llevan al artículo [Diseño de filtros en informes de Power BI](power-bi-report-filter.md) para obtener información detallada sobre cada opción.

- **Filtros persistentes** permite a los lectores [guardar filtros en el informe](power-bi-report-filter.md#allow-saving-filters).
- **Experiencia de filtrado** tiene dos opciones más:
    
    Permitir a los lectores de informes [cambiar los tipos del filtro](power-bi-report-filter.md#restrict-changes-to-filter-type).

    Habilitar la [búsqueda en el panel de filtros](power-bi-report-filter.md#filters-pane-search).

## <a name="export-data"></a>Exportar datos

De forma predeterminada, [los lectores de informes pueden exportar datos resumidos o subyacentes](../consumer/end-user-export.md) de los objetos visuales del informe. Con la opción **Exportar datos**, puede permitirles exportar solo los datos resumidos o no exportar ningún tipo de datos del informe.

## <a name="personalize-visuals"></a>Personalización de objetos visuales

Permita a los lectores cambiar y personalizar los objetos visuales del informe. Más información sobre cómo [permitir que los lectores de informes personalicen los objetos visuales](power-bi-personalize-visuals.md).

## <a name="next-steps"></a>Pasos siguientes

* [Destacar contenido en las páginas Inicio de otros usuarios](../collaborate-share/service-featured-content.md)
* [Permitir a los lectores de informes personalizar los objetos visuales en un informe](power-bi-personalize-visuals.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
