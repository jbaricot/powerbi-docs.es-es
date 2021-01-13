---
title: Creación de un trazado de embudo a partir de un script de R para un objeto visual de R en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se describe cómo crear un trazado de embudo a partir de un script de R para un objeto visual de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: f3d22a4143287588ad9290d000402a10a4cef227
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889280"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Tutorial: Creación de un trazado de embudo a partir de un script de R para un elemento visual de R
En este artículo se describe paso a paso cómo crear un trazado de embudo a partir de un script de R en un objeto visual de R.

En este artículo aprenderá a crear lo siguiente:

> [!div class="checklist"]
>
> * Un script de R para RStudio
> * Un objeto visual de R en Power BI
> * Un objeto visual con tecnología de R *basado en PNG* en Power BI
> * Un objeto visual con tecnología de R *basado en HTML* en Power BI

El trazado de embudo proporciona una manera fácil de consumir, interpretar y mostrar la cantidad de variación esperada. Para crear el **embudo** se usan los límites de confianza y los valores atípicos que se muestran como puntos fuera del embudo.

En este ejemplo, el trazado de embudo se usa para comparar y analizar diversos datos de conjuntos.  

> [!NOTE]
> Los archivos de origen están disponibles para descargar en cada conjunto de pasos.

## <a name="build-an-r-script-with-dataset"></a>Compilación de un script de R con un conjunto de datos

1. Descargue un [script de R mínimo](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) y su tabla de datos, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Después, edite el script para reflejar [este script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r). Esto agrega control de errores de entrada y parámetros de usuario para controlar la apariencia del trazado.

## <a name="build-a-report"></a>Generación de un informe

Después, edite el script para reflejar [este script](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r). Esto carga *dataset.csv* en lugar de *read.csv* en el área de trabajo de Power BI Desktop y crea una tabla **Cancer Mortality** (Mortalidad del cáncer). Vea los resultados en el siguiente [archivo PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix).

> [!NOTE]
> `dataset` es un nombre codificado de forma rígida para el elemento `data.frame` de entrada de cualquier objeto visual de R. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Creación de un objeto visual con tecnología de R y un paquete en código de R

1. Antes de empezar, asegúrese de [instalar las herramientas de PBIVIZ](./environment-setup.md#install-pbiviz).

1. Ejecute el comando siguiente para crear un objeto visual con tecnología de R:

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Este comando crea la carpeta *funnel-visual* con el objeto visual de plantilla inicial (`-t` para **plantilla**). PBIVIZ se puede encontrar en la carpeta *dist* y el código de R en el archivo *script.r*. Intente importarlo en Power BI y vea lo que sucede.

1. Edite el archivo *script.r* y reemplace el contenido por el script anterior.

1. Edite *capabilities.json* y reemplace la cadena `Values` por `dataset`. Esto reemplaza el nombre de "Role" en la plantilla para que sea similar al código de R.

   ![En la captura de pantalla se muestra una comparación de diferencias del cambio en el archivo json.](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(opcional)* Edite *dependencies.json* y agregue una sección para cada paquete de R necesario para el script de R. Esto indica a Power BI que importe de forma automática estos paquetes cuando se carga por primera vez el objeto visual.

   ![En la captura de pantalla se muestra una comparación de diferencias en la que se ha agregado contenido a los elementos cranPackages.](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Vuelva a empaquetar el objeto visual con el comando `pbiviz package` e intente importarlo en Power BI.

> [!NOTE]
> Vea [PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) y [código fuente](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/) para la descarga.

## <a name="make-r-based-visual-improvements"></a>Mejoras de objetos visuales basados en R

El objeto visual todavía no es descriptivo porque el usuario tiene que conocer el orden de las columnas de la tabla de entrada.

1. Divida el campo de entrada `dataset` en tres campos (roles): `Population`, `Number` y `Tooltips`.

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Edite *capabilities.json* y reemplace el rol `dataset` por los tres roles nuevos, o bien descargue [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   Tendrá que actualizar las secciones: en `dataRoles` y `dataViewMappings`, se definen los nombres, los tipos, la información sobre herramientas y el número máximo de columnas para cada campo de entrada.

   ![antes y después](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Para obtener más información, vea [funcionalidades](./capabilities.md).

1. Edite *script.r* para admitir `Population`, `Number` y `Tooltips` como tramas de datos de entrada en lugar de `dataset`, o bien descargue [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![script](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Para seguir los cambios en el script de R, busque bloques de comentarios: 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Vuelva a empaquetar el objeto visual con el comando `pbiviz package` e intente importarlo en Power BI.

> [!NOTE]
> Vea [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) y [código fuente](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02) para la descarga.

## <a name="add-user-parameters"></a>Adición de parámetros de usuario

1. Agregue funciones para que el usuario controle los colores y tamaños de los objetos visuales, incluidos los parámetros internos de la interfaz de usuario.

   ![En la captura de pantalla se muestran dos versiones del panel de herramientas con las opciones agregadas a la versión de la derecha.](./media/funnel-plot/diagram-two.PNG)

1. Edite *capabilities.json* y actualice la sección `objects`. Aquí se definen los nombres, las informaciones sobre herramientas y los tipos de cada parámetro, y también se decide la partición de los parámetros en grupos (en este caso, tres).

   Descargue [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json) y vea [propiedades de objeto](./objects-properties.md) para obtener más información.

   ![capabilities](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Edite *src/settings.ts* para reflejar [este archivo settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts). Este archivo está escrito en TypeScript.  

   Aquí encontrará dos bloques del código agregado a:
   - Declaración de una interfaz nueva para que contenga el valor de propiedad
   - Definición de una propiedad miembro y valores predeterminados

   ![configuración](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Edite *script.r* para reflejar [este archivo script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r). Esto agrega compatibilidad con los parámetros en la interfaz de usuario mediante la adición de llamadas a `if.exists` por cada parámetro de usuario.

   > [!TIP]
   > Para seguir los cambios en el script de R, busque comentarios:
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![script antes y después](https://raw.githubusercontent.com/microsoft/PowerBI-visuals/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   Puede decidir no exponer los parámetros en la interfaz de usuario, como se ha hecho.  

1. Vuelva a empaquetar el objeto visual con el comando `pbiviz package` e intente importarlo en Power BI.

> [!NOTE]
> Vea [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) y [código fuente](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/) para la descarga.

> [!TIP]
> Aquí se han agregado parámetros de varios tipos (booleanos, numéricos, de cadena y de color) a la vez. Para obtener un caso sencillo, vea [este ejemplo](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md) sobre cómo agregar un solo parámetro. 

## <a name="convert-visual-to-rhtml-based-visual"></a>Conversión del objeto visual en un objeto visual basado en RHTML

Como el objeto visual resultante está basado en PNG, no responde al desplazamiento del mouse, no se puede acercar el zoom, etc., por lo que es necesario convertirlo en un objeto visual basado en HTML. Ahora se creará una plantilla de objeto visual basado en HTML con tecnología de R y, después, se copiarán algunos scripts del proyecto basado en PNG.

1. Ejecute el comando:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Abra *capabilities.json* y anote la línea `"scriptOutputType":"html"`.

1. Abra *dependencies.json* y anote los nombres de los paquetes de R que se enumeran.

1. Abra *script.r* y anote la estructura. Puede abrirlo y ejecutarlo en RStudio, ya que no usa la entrada externa. 

   Esto crea y guarda *out.html*. Este archivo es independiente (sin dependencias externas) y define los gráficos dentro del widget HTML. 

   > [!IMPORTANT]
   > Para los usuarios de `htmlWidgets`, se proporcionan utilidades de R en la [carpeta r_files](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) a fin de facilitar la conversión de objetos `plotly` o `widget` en HTML independiente. 
   > 
   > Esta versión del objeto visual con tecnología de R también admite el comando `source` (a diferencia de los tipos de objetos visuales anteriores), para que el código sea más legible.   
 
1. Reemplace *capabilities.json* por el archivo *capabilities.json* del paso anterior, o bien descargue [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Asegúrese de mantener lo siguiente:

   `"scriptOutputType": "html"`

1. Combine la versión más reciente de *script.r* con el archivo *script.r* de la plantilla, o bien descargue [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   El nuevo script usa el paquete `plotly` para convertir el objeto **ggplot** en un objeto **plotly** y, después, el paquete `htmlWidgets` para guardarlo en un archivo HTML. 

   La mayoría de las funciones de utilidad se mueven a [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) y se agrega la función `generateNiceTooltips` para la apariencia del objeto **plotly**.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Para seguir los cambios en el script de R, busque comentarios:
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Combine la versión más reciente de *dependencies.json* con el archivo *dependencies.json* de la plantilla, para incluir nuevas dependencias de paquete de R, o bien descargue [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Edite *src/settings.ts* de la misma manera que en los pasos anteriores.

1. Vuelva a empaquetar el objeto visual con el comando `pbiviz package` e intente importarlo en Power BI.

> [!NOTE]
> Vea [PBIX y código fuente](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01) para la descarga.

## <a name="build-additional-examples"></a>Compilación de ejemplos adicionales

1. Ejecute el comando siguiente para crear un proyecto vacío: 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Tome el código de esta [presentación](http://www.htmlwidgets.org/showcase_networkD3.html) y realice los cambios resaltados:

   ![Cambios resaltados](./media/funnel-plot/diagram-three.PNG)

1. Reemplace el archivo *script.r* de la plantilla y vuelva a ejecutar `pbiviz package`. Ahora el objeto visual se incluye en el informe de Power BI.

## <a name="tips-and-tricks"></a>Trucos y sugerencias

* Se recomienda que los desarrolladores editen *pbiviz.json* para almacenar los metadatos correctos, como **versión**, **correo electrónico**, **nombre**, **tipo de licencia**, etc.

   > [!IMPORTANT]
   > El campo **guid** es el identificador único de un objeto visual. Si crea un proyecto para cada objeto visual, el GUID también será diferente. Solo será el mismo cuando se usa un proyecto anterior y se copia en un objeto visual nuevo, algo que no se debe hacer.

* Edite [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) para crear iconos únicos para el objeto visual. 

* Para depurar código de R en RStudio con los mismos datos que en el informe de Power BI, agregue lo siguiente al principio del script de R (edite la variable `fileRda`):

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Esto guarda el entorno de un informe de Power BI y lo carga en RStudio. 

* No es necesario desarrollar objetos visuales con tecnología de R desde cero con código disponible en [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). Puede seleccionar el objeto visual que se va a usar como plantilla y copiar el código en un proyecto nuevo.

   Por ejemplo, pruebe a usar el [objeto visual personalizado de spline](https://github.com/Microsoft/PowerBI-visuals-spline).

* Todos los objetos visuales de R aplican el operador `unique` a su tabla de entrada. Para evitar que se quiten filas idénticas, considere la posibilidad de agregar un campo de entrada adicional con un identificador único y omitirlo en el código de R.   

* Si tiene una cuenta de Power BI, use el servicio Power BI para desarrollar un objeto visual [sobre la marcha](./develop-circle-card.md) en lugar de volver a empaquetarlos con el comando `pbiviz package`.

### <a name="html-widgets-gallery"></a>Galería de widgets HTML
Explore los objetos visuales en la [galería de widgets HTML](http://gallery.htmlwidgets.org/) para usarlos en el siguiente objeto visual. Para facilitar el proceso, se ha creado un [repositorio de proyectos de objetos visuales](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) con más de 20 objetos visuales HTML interactivos entre los que elegir.

> [!TIP]
> Para cambiar entre los widgets HTML, use **Formato** > **Configuración** > **Tipo**. Pruébelo con [este archivo PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Para usar una muestra para el objeto visual

1. Descargue la carpeta completa.
1. Edite *script.r* y *dependencies.json* para mantener un solo widget.
1. Edite *capabilities.json* y *settings.ts* para quitar el selector de `Type`.
1. Cambie `const updateHTMLHead: boolean = true;` por `false` en *visual.ts*. *(para mejorar el rendimiento)*
1. Cambie los metadatos de *pbiviz.json*, en especial, el campo `guid`.
1. Vuelva a empaquetar y continúe con la personalización del objeto visual como de la forma prevista. 

![En la captura de pantalla se muestran seis widgets descritos anteriormente en este artículo.](./media/funnel-plot/diagram-four.PNG)

![En la captura de pantalla se muestran seis widgets más descritos anteriormente en este artículo.](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> No todos los widgets de este proyecto son compatibles con el servicio.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información, vea tutoriales de Power BI adicionales, [Desarrollo de un objeto visual Circle Card de Power BI](./develop-circle-card.md) y [Objetos visuales de R](../../visuals/service-r-visuals.md).

Obtenga información sobre cómo [desarrollar y enviar objetos visuales](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) a la [Tienda Office (galería)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI), o para obtener más ejemplos, vea la [presentación de scripts de R](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals).