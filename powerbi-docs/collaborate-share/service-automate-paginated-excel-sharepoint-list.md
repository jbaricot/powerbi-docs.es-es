---
title: Exportación de un informe paginado para cada fila de una tabla de Excel Online o de una lista de SharePoint
description: En este artículo, se usa Power Automate para automatizar la exportación de un informe paginado para cada fila de una tabla de Excel Online o una lista de SharePoint Online.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/17/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: acb90e65d63871925fe39c38d2141b85652fd68a
ms.sourcegitcommit: b2693047fce6a4e0c3ea07013404e99fc9cc1901
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94905335"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>Exportación de un informe paginado para cada fila de una tabla de Excel Online o de una lista de SharePoint

Con [Power Automate](/power-automate/getting-started), puede automatizar la exportación y la distribución de informes paginados de Power BI a diversos formatos y escenarios admitidos. En este artículo, se usa una plantilla de Power Automate para automatizar la configuración de exportaciones periódicas de uno o varios informes paginados. Se exportan en un formato deseado para cada fila de una tabla de Excel Online o una lista de SharePoint Online. Puede distribuir el informe paginado exportado a OneDrive para la Empresa o un sitio de SharePoint Online, o bien enviarlo por correo electrónico a través de Office 365 Outlook.

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="Exportación de un informe paginado mediante una tabla de Excel Online.":::

Cada fila de la tabla de Excel Online o de la lista de SharePoint Online puede representar un solo usuario para recibir un informe paginado según una suscripción. O bien, cada fila puede representar un informe paginado único que se quiere distribuir. En la tabla o lista se necesita una columna que especifique cómo distribuir un informe, ya sea OneDrive, SharePoint Online u Outlook. El flujo de Power Automate usa esta columna en su instrucción Switch.

¿Busca otras plantillas de Power Automate para informes paginados de Power BI? Vea [Exportación de informes paginados de Power BI con Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Prerrequisitos  

Para continuar, asegúrese de que tiene lo siguiente:

- Al menos un área de trabajo en el inquilino de Power BI respaldada por una capacidad reservada. Esta capacidad puede ser cualquiera de las SKU A4/P1 – A6/P3. Obtenga más información sobre las [capacidades reservadas en Power BI Premium](../admin/service-premium-what-is.md).
- Acceso a los conectores estándar de Power Automate, incluidos en todas las suscripciones de Office 365.
- Si usa una tabla de Excel Online, debe tener el formato de una tabla en Excel. Vea [Creación de una tabla](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) para obtener información sobre cómo hacerlo.

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>Exportación de un informe paginado para cada fila de una tabla o lista

> [!NOTE]
> En los pasos e imágenes siguientes se muestra cómo configurar un flujo mediante la plantilla **Exportar un informe paginado de Power BI para cada fila de una tabla de Excel Online**. Puede seguir los mismos pasos para crear un flujo mediante la plantilla **Exportar un informe paginado de Power BI para los elementos de una lista de SharePoint Online**. En lugar de una tabla de Excel Online, una lista de SharePoint Online contendrá la información sobre cómo exportar el informe paginado.  

1. Inicie sesión en Power Automate [flow.microsoft.com](https://flow.microsoft.com/). 
1. Seleccione **Plantillas** y busque  **informes paginados**. 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Captura de pantalla de las plantillas de Power Automate para informes paginados de Power BI.":::

1. Seleccione la plantilla **Exportar un informe paginado de Power BI para cada fila de una tabla de Excel Online** o **Exportar un informe paginado de Power BI para los elementos de una lista de SharePoint Online**. Asegúrese de que ha iniciado sesión en Excel Online, Power BI, OneDrive para la Empresa, SharePoint Online y Office 365 Outlook. Seleccione **Continuar**.  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="Exportación de un informe paginado de Power BI para cada fila de una tabla de Excel Online.":::

1. Para establecer la **Periodicidad** del flujo, seleccione una opción en **Frecuencia** y especifique el valor **Intervalo** que prefiera.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="Selección de la periodicidad para el flujo.":::

1. (Opcional) Seleccione **Mostrar opciones avanzadas** para establecer parámetros adicionales de **Periodicidad**, incluidos los de **Zona horaria**, **Hora de inicio**, **En estos días**, **A estas horas** y **En estos minutos**.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="Selección opcional de las opciones avanzadas de periodicidad.":::

1. En el cuadro **Ubicación**, seleccione OneDrive para la Empresa o el sitio de SharePoint Online donde se ha guardado la tabla de Excel Online o la lista de SharePoint Online. Después, seleccione **Biblioteca de documentos** en la lista desplegable.

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="Seleccione la ubicación de la tabla de Excel Online.":::

1. Seleccione el archivo de Excel Online o la lista de SharePoint Online en el cuadro **Archivo**. Seleccione el nombre de la tabla o lista en la lista desplegable del cuadro **Tabla**. 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="Selección del archivo de Excel Online y el nombre de la tabla.":::

    > [!TIP]
    > Vea [Creación de una tabla](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f) para obtener información sobre cómo dar formato a los datos como una tabla en Excel. 

1. Inicialice una variable para usarla como nombre de archivo. Puede conservar o modificar los valores predeterminados de **Nombre** y **Valor**, pero deje **Tipo** establecido en **Cadena**.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="Rellenado de Nombre y Valor; Tipo se mantiene establecido en Cadena.":::

1. En **Aplicar a cada uno**, el cuadro **Seleccione una salida del paso anterior** se establece en **valor** de forma predeterminada. Este valor itera por las acciones contenidas en **Aplicar a cada uno** para cada fila de la tabla de Excel Online o de la lista de SharePoint Online.  

1. En el cuadro **Área de trabajo**, seleccione un área de trabajo de una capacidad dedicada. En el cuadro **Informe**, seleccione el informe paginado en el área de trabajo seleccionada que quiera exportar. Si establece **Escriba un valor personalizado** en la lista desplegable, puede establecer **Área de trabajo** e **Informe** en una columna de la tabla de Excel Online o de la lista de SharePoint Online. Estas columnas deben contener identificadores de área de trabajo y de informe, respectivamente.  

1. Seleccione un **Formato de exportación** en la lista desplegable o establézcalo en una columna de la tabla de Excel Online que contenga formatos de exportación deseados. Por ejemplo, PDF, DOCX o PPTX. Opcionalmente, puede especificar parámetros para el informe paginado. Busque descripciones detalladas de los parámetros en la [referencia de conectores para la API REST de Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="Rellene Exportar a archivo para los informes paginados.":::

1. En el cuadro **Valor**, escriba un nombre para el informe paginado una vez que se haya exportado. Asegúrese de escribir una extensión de archivo. Puede establecerla de forma estática, por ejemplo, .pdf, .docx o .pptx. O bien, establézcala de forma dinámica; para ello, seleccione la columna de la tabla de Excel correspondiente al formato de exportación que quiera. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="Selección del nombre del informe y de una extensión de archivo.":::

1. En la acción **Switch**, rellene el cuadro **Por** con la columna de la tabla de Excel Online correspondiente al método de entrega deseado: **OneDrive**, **SharePoint** o **Correo electrónico**. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="En Switch, rellene el cuadro Por con la columna de la tabla de Excel Online.":::

1. En **Caso**, **Caso 2** y **Caso 3**, escriba los valores presentes en la columna de la tabla de Excel Online seleccionada en el paso anterior.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="Escriba valores para Caso, Caso 2 y Caso 3.":::

1. En el caso en el que guarde el informe paginado en OneDrive, seleccione la **Ruta de acceso de la carpeta** donde se deba guardar.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="Caso en el se va a guardar en OneDrive.":::

1. En el caso en el que guarde el informe paginado en SharePoint Online, escriba la **Dirección del sitio** y la **Ruta de acceso de la carpeta** donde se deba guardar. 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="Caso en el que el informe paginado se guarda en SharePoint Online.":::

1. En el caso en el que envíe el informe paginado como un correo electrónico a través de Outlook, rellene los cuadros **Para**, **Asunto** y **Cuerpo**. Estos cuadros pueden incluir contenido estático o dinámico de la tabla de Excel Online o de la lista de SharePoint Online. Power Automate adjunta automáticamente el informe paginado a este correo electrónico.  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="Caso en el que el informe paginado se envía como un correo electrónico a través de Outlook.":::

1. Cuando haya terminado, seleccione  **Paso siguiente** o **Guardar**. Power Automate crea y evalúa el flujo, y le notifica si encuentra errores. 

1. Si hay errores, seleccione **Editar flujo** para corregirlos. En caso contrario, seleccione la flecha **Atrás** para ver los detalles del flujo y ejecutar el nuevo flujo. 


## <a name="next-steps"></a>Pasos siguientes

- [Exportación de informes paginados de Power BI con Power Automate](service-automate-paginated-integration.md)
- [Introducción a Power Automate](/power-automate/getting-started/)
- ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

