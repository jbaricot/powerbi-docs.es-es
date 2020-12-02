---
title: Conexión a los archivos en OneDrive de un área de trabajo de Power BI
description: Lea la información no solo acerca de cómo almacenar archivos de Excel, CSV y Power BI Desktop, sino también de cómo conectarse a ellos en el la instancia de OneDrive de su área de trabajo de Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 10/15/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 6c3c43d8aad26249ac1b8afab09bdcbf1414f0cf
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411986"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>Conexión a los archivos almacenados en OneDrive del área de trabajo de Power BI
Cuando [crea un área de trabajo en Power BI](service-create-workspaces.md), también está creando un grupo de Microsoft 365, con una instancia asociada de OneDrive para la Empresa. En este artículo se explica cómo almacenar y actualizar archivos de Excel, CSV y Power BI Desktop en esa instancia de OneDrive para la empresa. Esas actualizaciones se reflejan automáticamente en los informes y paneles de Power BI según los archivos.

> [!NOTE]
> La nueva experiencia de áreas de trabajo cambiará la relación entre las áreas de trabajo de Power BI y los grupos de Microsoft 365. Ya no se crea automáticamente un grupo de Microsoft 365 cada vez que crea una de las nuevas áreas de trabajo. Lea sobre la [creación de las nuevas áreas de trabajo](service-create-the-new-workspaces.md).

La incorporación de archivos al área de trabajo es un proceso que consta de dos pasos: 

1. En primer lugar, [cargue los archivos en OneDrive para la Empresa](#1-upload-files-to-the-onedrive-for-business-for-your-workspace) del área de trabajo.
2. Después, [conéctese a esos archivos desde Power BI](#2-import-excel-files-as-datasets-or-as-excel-online-workbooks).

> [!NOTE]
> Las áreas de trabajo solo están disponibles con una [licencia de Power BI Pro](../fundamentals/service-features-license-type.md).
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 Cargue los archivos en OneDrive para la Empresa del área de trabajo
1. En el servicio Power BI, seleccione la flecha situada junto a Áreas de trabajo y, después, el botón de puntos suspensivos ( **...** ) junto al nombre del área de trabajo. 
   
   ![Captura de pantalla del área de trabajo de Power BI, en la que se muestra el nombre del área de trabajo seleccionada.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. Seleccione **Archivos** para abrir OneDrive para la Empresa del área de trabajo en Microsoft 365.
   
   > [!NOTE]
   > Si no ve **Archivos** en el área de trabajo, seleccione **Miembros** para abrir OneDrive para la Empresa del área de trabajo. Una vez ahí, seleccione **Archivos**. Microsoft 365 configura una ubicación de almacenamiento en OneDrive para los archivos del área de trabajo de su aplicación. Este proceso puede tardar algún tiempo.
   > 
   > 
3. Aquí puede cargar los archivos en OneDrive para la Empresa del área de trabajo. Seleccione **Cargar** y vaya a los archivos.
   
   ![Captura de pantalla de OneDrive para la Empresa, en la que se muestra cómo navegar para cargar un archivo.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Importación de archivos de Excel como conjuntos de datos o como libros de Excel Online
Ahora que los archivos se encuentran en OneDrive para la Empresa del área de trabajo, tiene dos opciones. Puede: 

* [Importar los datos desde el libro de Excel como un conjunto de datos](../connect-data/service-get-data-from-files.md). Usar luego los datos para crear informes y paneles que se puedan ver en un explorador web y en dispositivos móviles.
* O bien, [conectarse a un libro de Excel completo en Power BI](../connect-data/service-excel-workbook-files.md) y mostrarlo exactamente como aparece en Excel Online.

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>Importación o conexión de los archivos del área de trabajo
1. En Power BI, cambie al área de trabajo para que su nombre aparezca en la esquina superior izquierda. 
2. Seleccione **Obtener datos** en la parte inferior del panel de navegación. 
   
   ![Captura de pantalla del botón Obtener datos, mostrado en el panel de navegación.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. En el cuadro **Archivos** , seleccione **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Archivos, en el que se muestra el botón Obtener.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. Seleccione **OneDrive** - *Nombre del área de trabajo*.
   
    ![Captura de pantalla de tres iconos para seleccionar el área de trabajo, en la que se muestran Archivo local, OneDrive y SharePoint.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. Seleccione el archivo que quiera > **Conectar**.
   
    En este punto, debe decidir si [importar los datos desde el libro de Excel](../connect-data/service-get-data-from-files.md) o [conectarse a los libros de Excel completos](../connect-data/service-excel-workbook-files.md).
6. Seleccione **Importar** o **Conectarse**.
   
    ![Captura de pantalla del cuadro de diálogo OneDrive para la Empresa, en la que se muestra Importar desde Excel o Conectarse a Excel.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. Si selecciona **Importar**, el libro aparecerá en la pestaña **Conjuntos de datos**. 
   
    ![Captura de pantalla de las áreas de trabajo de Power BI, en la que se muestra la pestaña Conjuntos de datos.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    Si selecciona **Conectar**, el libro aparecerá en la pestaña **Libros**.
   
    ![Captura de pantalla de las áreas de trabajo de Power BI, en la que se muestra la pestaña Libros.](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>Pasos siguientes
* [Creación de aplicaciones y áreas de trabajo en Power BI](../collaborate-share/service-create-distribute-apps.md)
* [Importar datos desde libros de Excel](../connect-data/service-get-data-from-files.md)
* [Conectarse a libros de Excel completos](../connect-data/service-excel-workbook-files.md
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
* Comentarios Visite [Ideas sobre Power BI](https://ideas.powerbi.com/forums/265200-power-bi)
