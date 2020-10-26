---
title: Iconos de paneles del servicio Power BI para usuarios profesionales
description: Todo acerca de los iconos de paneles de Power BI para usuarios profesionales. Se incluyen los iconos que se crean desde SQL Server Reporting Services (SSRS).
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/06/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: ab8cfefab74d3120451b56c3ea30518e538ad543
ms.sourcegitcommit: d2f633b4bfa271051ba1d2ef0e6e8da7dcf42818
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830501"
---
# <a name="dashboard-tiles-in-power-bi"></a>Iconos de paneles en Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Un icono es una instantánea de los datos, anclada a un panel mediante un *diseñador* . Los *diseñadores* pueden crear iconos desde un informe, un conjunto de datos, un panel, el cuadro de pregunta de Preguntas y respuestas, Excel, SQL Server Reporting Services (SSRS), etc.  Esta captura de pantalla muestra muchos iconos diferentes anclados a un panel.

![Panel de Power BI](./media/end-user-tiles/power-bi-dash.png)


Además de los iconos anclados de los informes, los *diseñadores* puede agregar iconos independientes directamente en el panel mediante **Agregar icono** . Los iconos independientes incluyen: cuadros de texto, imágenes, vídeos, datos de transmisión y contenido web.

¿Necesita ayuda para comprender los bloques de creación que conforman Power BI?  Vea [Power BI: Conceptos básicos](end-user-basic-concepts.md).


## <a name="interacting-with-tiles-on-a-dashboard"></a>Interactuar con los iconos en un panel

1. Mantenga el puntero sobre el icono para que se muestren los puntos suspensivos.
   
    ![Icono de botón de puntos suspensivos](./media/end-user-tiles/power-bi-ellipsis.png)
2. Seleccione los puntos suspensivos (...) para abrir el menú de acciones del icono. Las opciones disponibles varían según los permisos, el tipo de objeto visual y el método utilizado para crear el icono. Por ejemplo, los elementos de menú disponibles para los iconos anclados desde Preguntas y respuestas son diferentes de los anclados desde un informe. Este es un menú de acción de un icono creado con Preguntas y respuestas.


   
    ![Captura de pantalla que muestra el menú con nueve opciones.](./media/end-user-tiles/power-bi-qna-menu.png)

   
    Algunas de las acciones disponibles en estos menús son:
   
   * [Abrir el informe que se ha usado para crear el icono ](end-user-reports.md) ![icono de informe](./media/end-user-tiles/chart-icon.jpg)  
   
   * [Abrir la pregunta de Preguntas y respuestas que se ha usado para crear el icono ](end-user-reports.md) ![icono de Preguntas y respuestas](./media/end-user-tiles/qna-icon.png)  
   

   * [Abrir el libro que se usó para crear este icono ](end-user-reports.md) ![icono de hoja de cálculo](./media/end-user-tiles/power-bi-open-worksheet.png)  
   * [Ver el icono en modo de enfoque ](end-user-focus.md) ![icono de enfoque](./media/end-user-tiles/fullscreen-icon.jpg)  
   * [Ver conclusiones ](end-user-insights.md) ![icono de conclusiones](./media/end-user-tiles/power-bi-insights.png)
   * [Agregar un comentario e iniciar una discusión](end-user-comment.md) ![icono de comentario](./media/end-user-tiles/comment-icons.png)
   * [Administrar las alertas establecidas en un icono del panel](end-user-alerts.md) ![icono de alerta](./media/end-user-tiles/power-bi-alert-icon.png)
   * [Abrir los datos en Excel](end-user-export.md) ![icono de exportación](./media/end-user-tiles/power-bi-export-icon.png)


3. Para cerrar el menú Acción, seleccione un área en blanco en el lienzo.

### <a name="select-click-a-tile"></a>Seleccionar (hacer clic en) un icono
Al seleccionar un icono, lo que sucede después depende de cómo se creó el icono y de si tiene un [vínculo personalizado](../create-reports/service-dashboard-edit-tile.md). Si tiene un vínculo personalizado, al seleccionar el icono se le lleva a ese vínculo. En caso contrario, al seleccionar el icono se le dirigirá al informe, al libro de Excel Online, al informe de SSRS local o a la pregunta de Preguntas y respuestas que se usó para crear el icono.

> [!NOTE]
> La excepción a esto son los iconos de vídeo agregados a los paneles por los *diseñadores* . Al seleccionar un icono de vídeo (que se creó de este modo), el vídeo se reproduce directamente en el panel.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas
* Si no ocurre nada al seleccionar (hacer clic en) un icono o recibe un mensaje de error, estas son algunas razones posibles:
  - El informe que se usó para crear la visualización no se guardó o se ha eliminado.
  - El icono se creó a partir de un libro de Excel Online, y no tiene al menos permisos de lectura para ese libro.
  - El icono se creó a partir de SSRS y no tiene permiso para el informe de SSRS, o no tiene acceso a la red en la que se encuentra el servidor de SSRS.
* En el caso de los iconos creados directamente en el panel con **Agregar icono** , si se estableció un hipervínculo personalizado, al seleccionar el título, el subtítulo o el icono se abrirá esa dirección URL.  De lo contrario, y de manera predeterminada, seleccionar uno de estos iconos creados directamente en el panel para una imagen, un código web o un cuadro de texto no generará ninguna acción.
* Si la visualización original usada para crear el icono cambia, no se produce ningún cambio en el icono.  Por ejemplo, si el *diseñador* ha anclado un gráfico de líneas desde un informe y posteriormente ha cambiado el gráfico de líneas a un gráfico de barras, el icono del panel seguirá mostrando un gráfico de líneas. Los datos se actualizan, pero no el tipo de visualización.

## <a name="next-steps"></a>Pasos siguientes
[Actualización de datos](../connect-data/refresh-data.md)

[Power BI: Conceptos básicos](end-user-basic-concepts.md)


