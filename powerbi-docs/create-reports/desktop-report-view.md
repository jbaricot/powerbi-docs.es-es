---
title: Vista de informes en Power BI Desktop
description: Vista de informes en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/12/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 859fb6156af38fc5333e9c94281255369d9ee413
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256989"
---
# <a name="work-with-report-view-in-power-bi-desktop"></a>Trabajo con la Vista de informes en Power BI Desktop

Si ha estado trabajando con Power BI, sabrá lo fácil que es crear informes que ofrecen perspectivas dinámicas e información sobre los datos. Power BI también tiene características más avanzadas en Power BI Desktop. Con Power BI Desktop, cree consultas avanzadas, mezcle datos de varios orígenes, cree relaciones entre tablas y mucho más.

Power BI Desktop incluye una *vista de informes* , donde puede crear varias páginas del informe con visualizaciones. La vista de informes de Power BI Desktop proporciona una experiencia de diseño similar a la vista de edición del informe en el *servicio Power BI* . Puede mover visualizaciones, copiar y pegar, combinar, etc.

La diferencia entre ellas es que al usar Power BI Desktop, también puede trabajar con las consultas y modelar los datos para asegurarse de que los datos admiten las mejores perspectivas en los informes. A continuación, puede guardar el archivo de Power BI Desktop donde quiera, ya sea en la unidad local o en la nube.

## <a name="lets-take-a-look"></a>¡Eche un vistazo!

Al cargar los datos por primera vez en Power BI Desktop, verá la vista de informes con un lienzo en blanco, con vínculos que le ayudarán a agregar datos al informe.

![Power BI Desktop](media/desktop-report-view/report-view-blank-canvas.png)

Puede cambiar entre las vistas **Informe** , **Datos** y **Relación** seleccionando los iconos de la barra de navegación izquierda:

![Icono Vista de informe](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

Una vez haya agregado algunos datos, puede agregar campos a una nueva visualización en el lienzo.

![Agregar un objeto visual arrastrándolo desde el panel Campos](media/desktop-report-view/pbid_reportview_addvis.gif)

Para cambiar el tipo de visualización, puede seleccionarlo en el lienzo y, a continuación, seleccionar un nuevo tipo en **Visualizaciones** .

![Cambiar un objeto visual mediante la selección de uno nuevo](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> No deje de experimentar con diferentes tipos de visualización. Es importante que la visualización transmita la información de los datos de manera clara.

Un informe tendrá al menos una página en blanco al inicio. Las páginas aparecen en el panel de navegación a la izquierda del lienzo. Puede agregar todo tipo de visualizaciones a una página, pero es importante no abusar. Demasiadas visualizaciones en una página le dan un aspecto ocupado y dificultarán la búsqueda de información adecuada. Puede agregar nuevas páginas a un informe. Solo tiene que hacer clic en **Nueva página** en la cinta de opciones.

![Icono Nueva página](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Para eliminar una página, haga clic en la **X** en la pestaña de la página en la parte inferior de la vista de informes.

![Agregar una página a un informe](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Los informes y las visualizaciones no se pueden anclar a un panel desde Power BI Desktop. Para ello, necesitará publicar en el sitio Power BI. Para más información, consulte [Publicar conjuntos de datos e informes desde Power BI Desktop](desktop-upload-desktop-files.md).

## <a name="copy-and-paste-between-reports"></a>Copiar y pegar entre informes

Puede tomar fácilmente un objeto visual de un informe de Power BI Desktop y pegarlo en otro informe. Basta con usar el método abreviado de teclado Ctrl+C para copiar el objeto visual del informe. En el otro informe de Power BI Desktop, use Ctrl+V para pegar el objeto visual en el otro informe. Puede seleccionar un objeto visual cada vez o todos los objetos visuales de una página para copiarlos y pegarlos en el informe de Power BI Desktop de destino.

La capacidad de copiar y pegar objetos visuales es útil para personas que con frecuencia compilan y actualizan varios informes. Al copiar entre archivos, la configuración y el formato que se han establecido explícitamente en el panel de formato continúan, mientras que los elementos visuales que dependen de un tema o la configuración predeterminada se actualizan automáticamente para coincidir con el tema del informe de destino. De modo que, cuando obtenga un objeto visual formateado y con la apariencia deseada, puede copiarlo y pegarlo en nuevos informes y conservar todo ese buen trabajo de formato.

Si los campos del modelo son diferentes, verá un error en el objeto visual y una advertencia sobre qué campos no existen. El error es similar a la experiencia que ve cuando se elimina un campo en el modelo que usa un objeto visual.

![Error al copiar o pegar el objeto visual: no hay campos de datos](media/desktop-report-view/report-view_07.png)

Para corregirlo, simplemente reemplace los campos rotos por los campos que desea usar del modelo en el informe en el que pegó el objeto visual. Si usa un objeto visual personalizado, también debe importar ese objeto visual personalizado en el informe de destino.

## <a name="hide-report-pages"></a>Ocultación de páginas de informes

Al crear un informe, también puede ocultar algunas de sus páginas. Este enfoque puede ser útil si necesita crear objetos visuales o datos subyacentes en un informe, pero no desea que dichas páginas sean visibles para otros usuarios, como cuando se crean tablas u objetos visuales auxiliares que se utilizan en otras páginas del informe. Hay muchas otras razones creativas que pueden llevarle a crear una página de informe y, después, ocultarla de un informe que desea publicar.

La ocultación de una página del informe es fácil. Simplemente haga clic con el botón derecha en la pestaña de la página del informe y seleccione **Ocultar** en el menú que aparece.

![Opción Ocultar página](media/desktop-report-view/report-view_05.png)

Hay algunas consideraciones que debe tener en cuenta al ocultar una página del informe:

* Puede seguir viendo una vista de informe oculta en Power BI Desktop, incuso si su título está atenuado. En la siguiente imagen, la página 4 está oculta.

    ![Página atenuada que está oculta](media/desktop-report-view/report-view_06.png)

* *No* puede ver una página oculta si visualiza el informe en el servicio Power BI.

* Ocultar una página del informe *no* es una medida de seguridad. Los usuarios aún pueden tener acceso a la página, y su contenido se puede ver explorando en profundidad o con otros métodos.

* Si una página está oculta, no aparecerá ninguna flecha de navegación en el modo Ver.
