---
title: Publicación de un informe paginado en el servicio Power BI
description: En este tutorial, aprenderá a publicar un informe paginado en el servicio Power BI cargándolo desde el equipo local.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 01/25/2021
ms.openlocfilehash: bbe88b206c4c07e2e296b9c85d46be7901f5972a
ms.sourcegitcommit: 5c5a27aa7ba21612df4c4096e635dfe4b9aaebcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98861293"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publicación de un informe paginado en el servicio Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

En este artículo, se ofrece información sobre cómo publicar un informe paginado en el servicio Power BI cargándolo desde el equipo local. Puede cargar informes paginados en Mi área de trabajo o en cualquier otra área de trabajo, siempre que tenga capacidad Premium. Busque el icono de diamante ![Icono de diamante de capacidad Premium de Power BI](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto al nombre del área de trabajo. 

Si el origen de datos del informe es local, debe crear una puerta de enlace después de cargar el informe. Vea la sección [Creación de una puerta de enlace](#create-a-gateway) más adelante en este artículo.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Adición de un área de trabajo a una capacidad Premium

Si el área de trabajo no tiene el icono de diamante ![Icono de diamante de capacidad Premium de Power BI](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto al nombre, deberá agregar el área de trabajo a una capacidad Premium. 

1. Seleccione **Áreas de trabajo**, seleccione el botón de puntos suspensivos (**...**) junto al nombre del área de trabajo y después seleccione **Editar área de trabajo**.

    ![Selección de Editar área de trabajo](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. En el cuadro de diálogo **Editar área de trabajo**, expanda **Avanzado** y después establezca la opción **Capacidad dedicada** en **Activado**.

    ![Selección de Capacidad dedicada](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Es posible que no pueda cambiar esta configuración. Si no puede, póngase en contacto con el administrador de capacidad Premium de Power BI para que le conceda derechos de asignación para agregar el área de trabajo a una capacidad Premium.

## <a name="from-report-builder-publish-a-paginated-report-to-the-power-bi-service"></a>Publicación de un informe paginado en el servicio Power BI desde Report Builder

1. Cree un informe paginado o abra uno existente desde el servicio Power BI en Report Builder. Si abre un informe paginado existente desde el servicio, la opción **Guardar** está deshabilitada porque va a actualizar un informe que está activo en el servicio Power BI.

1. En el menú **Archivo** de Report Builder, seleccione **Publicar**.

    ![Seleccione el menú Archivo y, después, Publicar.](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Si aún no ha iniciado sesión en Power BI, debe hacerlo o crear una cuenta. En la esquina superior derecha de Report Builder, seleccione **Iniciar sesión** y complete los pasos.

2. En la lista de áreas de trabajo de la izquierda, seleccione un área de trabajo con el icono de diamante ![Icono de diamante de capacidad de Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto a su nombre. Escriba un **Nombre de archivo** en el cuadro > **Guardar**. 

    ![Selección de un área de trabajo Premium](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Abra el servicio Power BI en un explorador y vaya al área de trabajo Premium donde ha publicado el informe paginado. En la pestaña **Informes**, se ve el informe.

    ![Informe paginado en la lista Informes](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Seleccione el informe paginado para abrirlo en el servicio Power BI. Si tiene parámetros, debe seleccionarlos para poder ver el informe.

    ![Selección de parámetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Si el origen de datos del informe es local, lea cómo [crear una puerta de enlace](#create-a-gateway) en este artículo a fin de acceder al origen de datos.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>En el servicio Power BI, cargue un informe paginado.

También puede empezar desde el servicio Power BI y cargar un informe paginado.

1. Cree el informe paginado en el generador de informes y guárdelo en el equipo local.

1. Abra el servicio Power BI en un explorador y vaya al área de trabajo Premium en el que desea publicar el informe. Observe el icono de diamante ![Icono de diamante de capacidad Premium de Power BI](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) junto al nombre. 

1. Seleccione **Obtener datos**.

    ![Obtención de datos de Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. En el cuadro **Archivos** , seleccione **Obtener**.

    ![Obtener archivos en Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Seleccione **Archivo local** > busque el informe paginado > **Abrir**.

    ![Selección de Archivo local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Seleccione **Continuar** > **Editar credenciales**.

    ![Selección de Editar credenciales](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure las credenciales > **Iniciar sesión**.

    ![Editar credenciales](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   En la pestaña **Informes**, se ve el informe.

    ![Informe paginado en la lista Informes](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecciónelo para abrirlo en el servicio Power BI. Si tiene parámetros, debe seleccionarlos para poder ver el informe.
 
    ![Selección de parámetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Si el origen de datos del informe es local, lea cómo [crear una puerta de enlace](#create-a-gateway) en este artículo a fin de acceder al origen de datos.

## <a name="create-a-gateway"></a>Crear una puerta de enlace

Al igual que cualquier otro informe de Power BI, si el origen de datos del informe es local, debe crear una puerta de enlace o conectarse a ella para acceder a los datos.

1. Junto al nombre del informe, seleccione **Administrar**.

   ![Administración del informe paginado](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Vea el artículo del servicio Power BI [Qué es una puerta de enlace de datos local](../connect-data/service-gateway-onprem.md) para obtener detalles y conocer los pasos siguientes.



## <a name="next-steps"></a>Pasos siguientes

- [Visualización de un informe paginado en el servicio Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Tutorial: Inserción de informes paginados de Power BI en una aplicación para los clientes](../developer/embedded/embed-paginated-reports-customers.md)
