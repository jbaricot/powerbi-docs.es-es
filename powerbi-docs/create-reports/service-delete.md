---
title: Eliminación de un panel, informe, libro, conjunto de datos o área de trabajo
description: Aprenda a eliminar prácticamente cualquier cosa de Power BI
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/11/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: b2263a1eddfdbc51f0e345443f7bbb75b11da6e7
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2020
ms.locfileid: "91632741"
---
# <a name="delete-almost-anything-in-power-bi-service"></a>Eliminar prácticamente cualquier cosa en el servicio Power BI
Este artículo le enseña a eliminar un panel, un informe, un libro, un conjunto de datos, una aplicación, una visualización y un área de trabajo en el servicio Power BI.

## <a name="delete-a-dashboard"></a>Eliminar un panel
Los paneles se pueden quitar. Al quitar el panel, no se eliminan el conjunto de datos subyacente ni los informes asociados con ese panel.

* Si es el propietario del panel, puede quitarlo. Si compartió el panel con sus compañeros y quita el panel del área de trabajo de Power BI, este no se quitará de las áreas de trabajo de Power BI de los compañeros.
* Si un panel se ha compartido con usted y ya no desea verlo, puede quitarlo.  Quitar el panel de su área de trabajo no lo quita del área de trabajo de Power BI de nadie más.
* Si un panel forma parte de un [paquete de contenido organizativo](../collaborate-share/service-organizational-content-pack-disconnect.md), la única forma de quitarlo es quitar el conjunto de datos asociado.

### <a name="to-delete-a-dashboard"></a>Para eliminar un panel
1. En el área de trabajo, seleccione la pestaña **Paneles**.
2. Busque el panel que desea eliminar y seleccione el icono Eliminar :::image type="icon" source="media/service-delete/power-bi-delete-icon.png" border="false":::.

    ![Vídeo](media/service-delete/power-bi-delete-dash.gif)

## <a name="delete-a-report"></a>Eliminación de un informe
No se preocupe, la eliminación de un informe no elimina el conjunto de datos en el que se basa el informe.  Y las visualizaciones del informe que haya anclado tampoco corren peligro, seguirán en el panel hasta que las elimine individualmente.

### <a name="to-delete-a-report"></a>Para eliminar un informe
1. En el área de trabajo, seleccione la pestaña **Informes**.
2. Busque el informe que desea eliminar y seleccione el icono Eliminar :::image type="icon" source="media/service-delete/power-bi-delete-icon.png" border="false":::.   

    ![Pestaña Informes de área de trabajo](media/service-delete/power-bi-delete-reportnew.png)
3. Confirme la eliminación.

   ![Cuadro de diálogo Eliminar](media/service-delete/power-bi-delete-report.png)

   > [!NOTE]
   > Si el informe es parte de un [paquete de contenido](../collaborate-share/service-organizational-content-pack-introduction.md), no podrá eliminarse mediante este método.  Consulte [Quitar la conexión a un paquete de contenido organizativo](../collaborate-share/service-organizational-content-pack-disconnect.md).
   >
   >

## <a name="delete-a-workbook"></a>Eliminar un libro
Los libros se pueden quitar. Sin embargo, al quitar un libro, se quitan también todos los informes y los iconos de panel que contengan datos del libro.

Si el libro está almacenado en OneDrive para la Empresa, al eliminarlo de Power BI no se elimina de OneDrive.

### <a name="to-delete-a-workbook"></a>Para eliminar un libro
1. En el área de trabajo, seleccione la pestaña **Libros**.
2. Busque el libro que desea eliminar y seleccione el icono Eliminar :::image type="icon" source="media/service-delete/power-bi-delete-report2.png" border="false":::.

    ![Pestaña Libros](media/service-delete/power-bi-delete-workbooknew.png)
3. Confirme la eliminación.

   ![Cuadro de diálogo Quitar libro](media/service-delete/power-bi-delete-confirm.png)

## <a name="delete-a-dataset"></a>Eliminación de un conjunto de datos
Los conjuntos de datos se pueden eliminar. Sin embargo, si elimina un conjunto de datos, también se eliminarán todos los informes y los iconos de panel que contengan datos de ese conjunto de datos.

Si un conjunto de datos forma parte de uno o varios [paquetes de contenido organizativos](../collaborate-share/service-organizational-content-pack-disconnect.md), la única forma de eliminarlo es quitarlo de los paquetes de contenido donde se utiliza, esperar a que se procese e intentar eliminarlo de nuevo.

### <a name="to-delete-a-dataset"></a>Para eliminar un conjunto de datos
1. En el área de trabajo, seleccione la pestaña **Conjuntos de datos**.
2. Busque el conjunto de datos que desea eliminar y seleccione **Más opciones** (...).  

    ![Pestaña Conjuntos de datos](media/service-delete/power-bi-delete-datasetnew.png)
3. En la lista desplegable, seleccione **Eliminar**.

   ![Menú del botón de puntos suspensivos](media/service-delete/power-bi-delete-datasetnew2.png)
4. Confirme la eliminación.

   ![Cuadro de diálogo Eliminar panel](media/service-delete/power-bi-delete-dataset-confirm.png)

## <a name="delete-a-workspace"></a>Eliminación de un área de trabajo
> [!WARNING]
> Al crear un área de trabajo, creará un grupo de Microsoft 365. Y al eliminar un área de trabajo, eliminará este grupo de Microsoft 365. Esto significa que el grupo se eliminará también de otros productos de Microsoft 365, como SharePoint y Microsoft Teams.
>
>

Como autor del área de trabajo, puede eliminarla. Cuando la elimina, también se elimina la aplicación asociada para todos los miembros del grupo y se quita de su AppSource si había publicado la aplicación en toda la organización. Eliminar un área de trabajo no es igual que abandonar un área de trabajo.

### <a name="to-delete-a-workspace---if-you-are-an-admin"></a>Para eliminar un área de trabajo, si es un administrador
1. En el panel de navegación, seleccione **Áreas de trabajo**.

2. Seleccione el botón **Más opciones** (...) a la derecha del área de trabajo que desea eliminar y elija **Editar área de trabajo**.

    ![áreas de trabajo](media/service-delete/power-bi-delete-workspace.png)

3. En la ventana **Edit workspace** (Editar área de trabajo), seleccione **Eliminar área de trabajo** > **Eliminar**.

    ![Eliminar área de trabajo](media/service-delete/power-bi-delete-workspace2.png)

### <a name="to-remove-a-workspace-from-your-list"></a>Para quitar un área de trabajo de la lista
Si ya no desea ser miembro de un área de trabajo, puede ***abandonarla*** y se quitará de su lista. Al abandonar un área de trabajo, se deja como estaba para todos los demás miembros del área de trabajo.  

> [!IMPORTANT]
> Si es el único administrador del área de trabajo, Power BI no permitirá que la abandone.
>
>

1. Empiece en el área de trabajo que desee quitar.

2. En la esquina superior derecha, seleccione **Más opciones** (...) y elija **Abandonar área de trabajo** > **Abandonar**.

      :::image type="icon" source="media/service-delete/power-bi-leave-workspace.png" border="false":::

   > [!NOTE]
   > Las opciones que ve en la lista desplegable dependen de si es administrador o miembro de esa área de trabajo.
   >
   >

## <a name="delete-or-remove-an-app"></a>Eliminar o quitar una aplicación
Las aplicaciones se pueden quitar fácilmente de la página con la lista de aplicaciones. Sin embargo, solo el administrador de una aplicación puede eliminarla de forma permanente.

### <a name="remove-an-app-from-your-app-list-page"></a>Quitar una aplicación de la página con la lista de aplicaciones
Al eliminarse una aplicación de la página con la lista de aplicaciones, no se elimina para los demás miembros.

1. En el panel de navegación, seleccione **Aplicaciones** para abrir la página con la lista de aplicaciones.
2. Mantenga el puntero sobre la aplicación que desea eliminar y seleccione el icono Eliminar :::image type="icon" source="media/service-delete/power-bi-delete-report2.png" border="false":::.

   ![Selección de aplicaciones](media/service-delete/power-bi-delete-app.png)

   Si quita una aplicación accidentalmente, tiene varias opciones para recuperarla.  Puede pedir al creador de la aplicación que la vuelva a enviar, encontrar el mensaje original con el vínculo a la aplicación, consultar su [centro de notificaciones](../consumer/end-user-notification-center.md) para ver si sigue apareciendo la notificación para esa aplicación o mirar en [AppSource](../consumer/end-user-apps.md) para su organización.

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
En este artículo se trata cómo eliminar los principales bloques de creación del servicio Power BI. Pero hay más cosas que puede eliminar en Power BI.  

* [Quitar el panel destacado](../consumer/end-user-featured.md)
* [Quitar un panel de Favoritos](../consumer/end-user-favorite.md)
* [Eliminar una página del informe](service-delete.md)
* [Quitar un icono de panel](service-dashboard-edit-tile.md)
* [Eliminar una visualización de informe](service-delete.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
