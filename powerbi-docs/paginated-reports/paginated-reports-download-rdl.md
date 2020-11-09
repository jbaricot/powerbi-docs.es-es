---
title: Descarga de un archivo .rdl para un informe paginado desde un conjunto de datos
description: En este artículo, aprenderá a crear el archivo .rdl para un informe paginado de Power BI mediante su descarga desde un conjunto de datos compartido en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 10/15/2020
ms.openlocfilehash: c5c8f61a7253da46529a83276366044560d4f030
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297614"
---
# <a name="download-the-rdl-for-a-power-bi-paginated-report-from-a-dataset"></a>Descarga de un archivo .rdl para un informe paginado de Power BI desde un conjunto de datos

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

En este artículo, aprenderá a crear el archivo .rdl para un informe paginado de Power BI mediante su descarga desde un conjunto de datos compartido en el servicio Power BI. Los informes paginados tienen el formato de archivo *.rdl*. Puede crear un archivo. rdl directamente desde un conjunto de datos en el servicio Power BI.

1. Vaya a la vista de lista de cualquier área de trabajo, incluida Mi área de trabajo. 
1. Seleccione **Más opciones (...)** para un conjunto de datos y, a continuación, seleccione **Download the .rdl** (Descargar el archivo .rdl).

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-download-rdl.png" alt-text="Captura de pantalla de la opción de descarga del archivo .rdl en el servicio Power BI.":::
1. Verá un mensaje que le indica que necesita algunas actualizaciones en Power BI Report Builder. Seleccione **Descargar**. 

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-updates.png" alt-text="Captura de pantalla de la instalación de actualizaciones de Power BI Report Builder.":::

    Si sabe que tiene la versión más reciente de Power BI Report Builder, seleccione **Ya instalé estas actualizaciones**.

1. Siga los pasos del proceso de instalación de Power BI Report Builder: 

    1. Seleccione **Descargar**.  
    2. Seleccione **Abrir archivo** y siga los pasos del Asistente para la instalación de Power BI Report Builder.

1. Una vez finalizada la instalación de Report Builder, vuelva al servicio Power BI y seleccione **Download the .rdl** (Descargar el archivo .rdl).

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-finished-installing.png" alt-text="Captura de pantalla del cuadro de diálogo de descarga del archivo .rdl.":::

1. Seleccione **Abrir archivo** en la ventana del explorador.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-paginated-open-file.png" alt-text="Captura de pantalla de la selección de Abrir archivo en un explorador.":::

1. Power BI Report Builder se abre con un título generado automáticamente, y el archivo .pbix del conjunto de datos de Power BI en la carpeta **Orígenes de datos**. El origen de datos tiene el mismo nombre que el conjunto de datos de Power BI.

    :::image type="content" source="media/paginated-reports-download-rdl/power-bi-report-builder-design-canvas.png" alt-text="Captura de pantalla de Power BI Report Builder en la vista de diseño.":::

    La superficie de diseño también incluye un vínculo a un curso basado en vídeo [Informes paginados de Power BI en un día](../learning-catalog/paginated-reports-online-course.md). Si no está familiarizado con la creación de informes paginados, el curso es una buena manera de ponerse al día.  Puede eliminarlo al empezar a diseñar el informe.

    Está listo para empezar a diseñar el informe paginado.
 
## <a name="next-steps"></a>Pasos siguientes 

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Tutorial: Crear un informe paginado y cargarlo en el servicio Power BI](paginated-reports-quickstart-aw.md)
- [Publicación de un informe paginado en el servicio Power BI](paginated-reports-save-to-power-bi-service.md)

