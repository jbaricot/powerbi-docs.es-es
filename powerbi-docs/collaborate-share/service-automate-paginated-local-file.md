---
title: Almacenamiento de un informe paginado en una carpeta local con Power Automate
description: En este artículo, se usa una plantilla para configurar las exportaciones periódicas de un informe paginado en el sistema de archivos, en un formato deseado.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098814"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>Almacenamiento de un informe paginado de Power BI en una carpeta local con Power Automate

Con [Power Automate](/power-automate/getting-started), puede automatizar la exportación y la distribución de informes paginados de Power BI a diversos formatos y escenarios admitidos. En este artículo, se usa una plantilla para configurar las exportaciones periódicas de un informe paginado en el sistema de archivos, en un formato deseado. Vea los requisitos previos si es la primera vez que usa la acción Exportar a archivo para informes paginados en un flujo de Power Automate.

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="Configure exportaciones periódicas de un informe paginado.":::

¿Busca otras plantillas de Power Automate para informes paginados de Power BI? Vea [Exportación de informes paginados de Power BI con Power Automate](service-automate-paginated-integration.md).

## <a name="prerequisites"></a>Prerrequisitos  

Para continuar, asegúrese de que tiene lo siguiente:

- Al menos un área de trabajo en el inquilino de Power BI respaldada por una capacidad reservada. Esta capacidad puede ser cualquiera de las SKU A4/P1 – A6/P3. Obtenga más información sobre las [capacidades reservadas para informes paginados en Power BI Premium](../admin/service-premium-what-is.md#paginated-reports).
- Acceso a los conectores estándar de Power Automate, incluidos en todas las suscripciones de Office 365.

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>Guardar un informe paginado de Power BI en una carpeta local

1. Seleccione la plantilla **Guardar un informe paginado de Power BI en un sistema de archivos local**. Asegúrese de que ha iniciado sesión en Power BI y que está conectado al sistema de archivos local. Seleccione **Continuar**. 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="Guardar un informe paginado de Power BI en un sistema de archivos local.":::

2. Es posible que tenga que seleccionar **Agregar nueva conexión** para conectarse al sistema de archivos. 
1. Escriba un nombre de conexión en **Nombre de conexión**, la ruta de acceso a la carpeta raíz que desee en **Carpeta raíz** y autentíquese escribiendo la información correspondiente en **Nombre de usuario** y **Contraseña**. Seleccione una **puerta de enlace** en la lista desplegable si usa una puerta de enlace de datos local.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="En Nombre de conexión y Carpeta raíz, escriba la información correspondiente.":::
 
3. Para establecer un valor para la periodicidad del flujo en **Periodicidad**, seleccione una opción en el cuadro desplegable **Frecuencia** y especifique el valor que prefiera para **Intervalo**.  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="Establezca la frecuencia del flujo en Periodicidad.":::

4. Si lo desea, seleccione **Mostrar opciones avanzadas**. Establezca parámetros adicionales de **Periodicidad**, incluidos los de **Zona horaria**, **Hora de inicio**, **En estos días**, **A estas horas** y **En estos minutos**. 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="Establezca opciones avanzadas de periodicidad.":::

5. En el cuadro **Área de trabajo**, seleccione un área de trabajo de una capacidad reservada donde se encuentra el informe. En el cuadro **Informe**, seleccione el informe paginado que desea exportar en el área de trabajo. En el cuadro **Formato de exportación**, seleccione el formato de exportación que quiera. Opcionalmente, puede especificar parámetros para el informe paginado. Vea descripciones detalladas de los parámetros en la [referencia de conectores para la API REST de Power BI](/connectors/powerbi/#export-to-file-for-paginated-reports).  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="Seleccione el área de trabajo y el informe.":::

6. En el cuadro de diálogo **Crear archivo**, en **Ruta de acceso de la carpeta** seleccione la carpeta en la que desea exportar el informe paginado.
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="Seleccionar la carpeta en la que desea exportar el informe paginado":::

7. Power Automate genera automáticamente los campos **Nombre de archivo** y **Contenido del archivo**. Puede modificar el campo **Nombre de archivo**, pero mantenga el valor de **Contenido del archivo** generado de forma dinámica.
8. Cuando haya terminado, seleccione **Siguiente paso** o **Guardar**. Power Automate crea y evalúa el flujo.
9. Si Power Automate encuentra errores, seleccione **Editar flujo** para corregirlos. En caso contrario, seleccione la flecha Atrás para ver los detalles del flujo y ejecutar el nuevo flujo.
10. Al ejecutar el flujo, Power Automate exporta un informe paginado en el formato especificado a la carpeta seleccionada en el sistema de archivos.

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automatic exporta un informe paginado en el formato especificado.":::

## <a name="next-steps"></a>Pasos siguientes

- [Exportación de informes paginados de Power BI con Power Automate](service-automate-paginated-integration.md)
- [Introducción a Power Automate](/power-automate/getting-started/)
- ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

