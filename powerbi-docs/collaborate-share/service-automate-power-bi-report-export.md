---
title: Exportación y envío por correo electrónico de un informe con Power Automate
description: En este artículo, se usa Power Automate para automatizar la exportación y distribución de informes de Power BI en diversos escenarios y formatos admitidos.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098835"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>Exportación y envío por correo electrónico de un informe de Power BI con Power Automate

Con [Power Automate](/power-automate/getting-started), puede automatizar la exportación y la distribución de informes de Power BI a diversos formatos y escenarios. En este artículo, creará su propio flujo desde cero. Use la acción Exportar a archivo para informes de Power BI para distribuir automáticamente un informe de Power BI por correo electrónico.

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="Pasos de Power Automate para exportar y enviar por correo electrónico un informe.":::

## <a name="prerequisites"></a>Prerrequisitos  

Para continuar, asegúrese de que tiene lo siguiente:

- Al menos un área de trabajo en el inquilino de Power BI respaldada por una capacidad reservada. Esta capacidad puede ser cualquiera de las SKU A1/EM1 - A6/P3. Obtenga más información sobre las [capacidades reservadas en Power BI Premium](../admin/service-premium-what-is.md).
- Acceso a los conectores estándar de Power Automate, incluidos en todas las suscripciones de Office 365.

## <a name="create-a-flow-from-scratch"></a>Creación de un flujo desde cero 

En esta tarea, creará un sencillo flujo desde cero. El flujo exporta un informe de Power BI como un archivo PDF y lo adjunta a un correo electrónico para que se envíe semanalmente.  

1. Inicie sesión en Power Automate (flow.microsoft.com).
2. Seleccione **Crear** > **Flujo programado**. 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="Cree un flujo programado en Power Automate.":::

3. En **Crear un flujo automatizado**, asigne un nombre al flujo. 
4. En **Ejecutar este flujo**, seleccione la fecha y hora de inicio del flujo, así como la frecuencia de repetición.
5. En **En estos días**, seleccione los días en los que desea que se ejecute el flujo y seleccione **Crear**.

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power automatice, programar el flujo.":::

6. En **Periodicidad**, seleccione **Mostrar opciones avanzadas** y escriba un valor en **A estas horas** y **En estos minutos** para establecer una hora específica para que se ejecute el flujo.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="Establezca la periodicidad en Power Automate.":::

7. Seleccione **Nuevo paso**.
8. En **Elegir una acción**, busque **Power BI** y seleccione **Export to File for Power BI Reports** (Exportar a archivo para informes de Power BI).
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="Elija una acción en Power Automatic.":::

9. En **Export to File for Power BI Reports** (Exportar a archivo para informes de Power BI), seleccione un área de trabajo en **Área de trabajo** y un informe en **Informe** en las listas desplegables.
10. Seleccione un formato en **Formato de exportación** para el informe de Power BI.
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="Seleccione el formato de exportación en Power Automatic.":::

11. Opcionalmente, indique las páginas específicas que se van a exportar en el campo **Pages pageName -1** (Páginas pageName: 1). Tenga en cuenta que el parámetro del nombre de página es diferente del nombre de página para mostrar. Busque el nombre de la página. Para ello, vaya a la página en el servicio Power BI y copie la última parte de la dirección URL.
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="Seleccione el nombre del panel en la dirección URL.":::

12. Opcionalmente, indique un marcador específico para mostrar en el campo **Pages Bookmark Name** (Nombre de marcador de páginas). Al igual que con el parámetro del nombre de página, encontrará el parámetro del nombre del marcador en la dirección URL del informe. Puede especificar parámetros adicionales para el informe de Power BI. Busque descripciones detalladas de estos parámetros en la [referencia de conectores para la API REST de Power BI](/connectors/powerbi/#export-to-file-for-power-bi-reports).

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="Seleccione el nombre del marcador en la dirección URL.":::

13. Seleccione **Nuevo paso**.
14. En **Elija una acción**, busque **Outlook** y seleccione **Enviar correo electrónico (V2)** .
15. En **Enviar correo electrónico (V2)** , complete los campos **Para**, **Asunto** y **Cuerpo** del correo electrónico.
16. Seleccione **Mostrar opciones avanzadas**. En **Attachments Name – 1** (Nombre de datos adjuntos: 1), escriba un nombre para los datos adjuntos. Agregue una extensión de archivo al nombre de archivo (por ejemplo, .PDF) que coincida con el campo **Formato de exportación** deseado.
17. En **Attachment Content** (Contenido de datos adjuntos), seleccione **Contenido del archivo** para adjuntar el informe de Power BI exportado.  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="Seleccione el informe exportado para enviarlo por correo electrónico.":::

18. Cuando haya terminado, seleccione **Siguiente paso** o **Guardar**. Power Automate crea y evalúa el flujo, y le notifica si encuentra errores.
1. Si hay errores, seleccione **Editar flujo** para corregirlos. En caso contrario, seleccione la flecha **Atrás** para ver los detalles del flujo y ejecutar el nuevo flujo.
    Al ejecutar el flujo, Power Automate exporta un informe de Power BI en el formato especificado y lo envía como datos adjuntos de correo electrónico según lo programado.  

## <a name="next-steps"></a>Pasos siguientes

- [Integre alertas de datos de Power BI con Power Automate](service-flow-integration.md)
- [Introducción a Power Automate](/power-automate/getting-started/)
- ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
