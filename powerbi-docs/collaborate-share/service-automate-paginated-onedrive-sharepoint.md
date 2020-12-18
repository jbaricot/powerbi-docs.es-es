---
title: Guardado de un informe paginado en OneDrive para la Empresa o SharePoint Online
description: En este artículo, se usa Power Automate para automatizar el guardado de un informe paginado de Power BI en OneDrive para la empresa o en una carpeta de SharePoint Online.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 6aaad48fb3e97aa6c1b4fc51834ee593a49a8192
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097740"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>Guardado de un informe paginado en OneDrive para la Empresa o SharePoint Online

Con [Power Automate](/power-automate/getting-started), puede automatizar la exportación y la distribución de informes paginados de Power BI a diversos formatos y escenarios admitidos. En este artículo, se usa Power Automate para automatizar el guardado de un informe paginado de Power BI en OneDrive para la empresa o en una carpeta de SharePoint Online.


:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="Captura de pantalla del flujo de Power Automate para guardar un informe paginado en OneDrive o SharePoint Online":::

¿Busca otras plantillas de Power Automate para informes paginados de Power BI? Vea [Exportación de informes paginados de Power BI con Power Automate](service-automate-paginated-integration.md). 

## <a name="prerequisites"></a>Prerrequisitos  

Para continuar, asegúrese de que tiene lo siguiente:

- Al menos un área de trabajo en el inquilino de Power BI respaldada por una capacidad reservada. Esta capacidad puede ser cualquiera de las SKU A4/P1 – A6/P3. Obtenga más información sobre las [capacidades reservadas para informes paginados en Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Acceso a los conectores estándar de Power Automate, incluidos en todas las suscripciones de Office 365.

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>Guardado de un informe paginado en OneDrive para la Empresa o en una carpeta de SharePoint Online 

Con cualquiera de estas plantillas, las exportaciones periódicas de un informe paginado se configuran en un formato deseado para OneDrive para la Empresa o una carpeta de SharePoint Online. Vea los requisitos previos si es la primera vez que usa la acción Exportar a archivo para informes paginados en un flujo de Power Automate. 

> [!NOTE]
> En los pasos e imágenes siguientes se muestra cómo configurar un flujo mediante la plantilla **Guardar un informe paginado de Power BI para OneDrive para la Empresa**. Siga los mismos pasos para crear un flujo mediante la plantilla **Guardar un informe paginado de Power BI en una carpeta de SharePoint Online**. Al seleccionar dónde quiere exportar el informe paginado, seleccione una carpeta de SharePoint Online en lugar de una de OneDrive para la Empresa. 

1. Inicie sesión en Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Seleccione **Plantillas** y busque  **informes paginados**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Captura de pantalla de las plantillas de Power Automate para informes paginados de Power BI.":::

1. Seleccione **Guardar un informe paginado de Power BI en OneDrive para la empresa** o **Guardar un informe paginado de Power BI en una carpeta de SharePoint Online**. Asegúrese de que ha iniciado sesión en Power BI y en OneDrive para la Empresa o SharePoint Online.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="Captura de pantalla de la selección de la plantilla de Power BI y OneDrive para la Empresa.":::
1. Seleccione **Continuar**.  


1. Para establecer la **Periodicidad** del flujo, seleccione una opción en **Frecuencia** y especifique el valor **Intervalo** que prefiera.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="Selección de la periodicidad del flujo.":::

1. (Opcional) Seleccione **Mostrar opciones avanzadas** para establecer parámetros adicionales de **Periodicidad**, incluidos los de **Zona horaria**, **Hora de inicio**, **En estos días**, **A estas horas** y **En estos minutos**.  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="Se muestran las opciones avanzadas de periodicidad.":::

1. En el cuadro **Área de trabajo**, seleccione un área de trabajo de una capacidad reservada. En el cuadro **Informe**, seleccione el informe paginado en el área de trabajo seleccionada que quiera exportar. En el cuadro **Formato de exportación**, seleccione el formato de exportación que quiera. Opcionalmente, puede especificar parámetros para el informe paginado. Encontrará descripciones detalladas de los parámetros en la [referencia de los conectores para la API REST de Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="Selección del informe paginado, el área de trabajo y el formato de exportación.":::

1. En **Ruta de acceso de la carpeta**, seleccione la carpeta de OneDrive para la Empresa o SharePoint Online en la que quiera exportar el informe paginado.

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="Selección del destino y creación del archivo.":::

1. Power Automate genera automáticamente **Nombre de archivo** y **Contenido del archivo**. Puede cambiar el nombre de archivo, pero mantenga el valor **Contenido del archivo** generado de forma dinámica. 

1. Cuando haya terminado, seleccione  **Paso siguiente** o **Guardar**. Power Automate crea y evalúa el flujo, y le notifica si encuentra errores. 

1. Si hay errores, seleccione **Editar flujo** para corregirlos. En caso contrario, seleccione la flecha **Atrás** para ver los detalles del flujo y ejecutar el nuevo. 

    Al ejecutar el flujo, Power Automate exporta un informe paginado en el formato especificado a OneDrive para la Empresa o SharePoint Online.  

## <a name="next-steps"></a>Pasos siguientes

- [Exportación de informes paginados de Power BI con Power Automate](service-automate-paginated-integration.md)
- [Introducción a Power Automate](/power-automate/getting-started/)
- ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
