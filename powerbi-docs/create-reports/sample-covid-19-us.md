---
title: Ejemplo de seguimiento de la COVID-19 para gobiernos locales y estatales de EE. UU.
description: Descargue y modifique el informe de ejemplo con los datos locales y estatales de EE. UU. para la pandemia de la COVID-19.
author: LukaszPawlowski-MS
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: 66e76c21e7d5171d24ff1518745a35947aa7ca42
ms.sourcegitcommit: e7fda395b47e404c61e961a60816b7a1b0182759
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80979785"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>Ejemplo de seguimiento de la COVID-19 para gobiernos locales y estatales de EE. UU.

El equipo de Power BI ha creado un ejemplo de seguimiento de la COVID-19 que permite a los gobiernos estatales y locales de EE. UU. publicar o personalizar un informe interactivo sobre la COVID-19. Con Power BI Desktop, estos pueden analizar y visualizar los datos de la COVID-19 para mantener a sus comunidades informadas a nivel de ciudad, condado, estado y país. A continuación, con Publicar en Web de Power BI, pueden compartir el informe públicamente para informar a los ciudadanos. En el artículo se ofrecen opciones diferentes para el uso de visualizaciones interactivas de Power BI en su propia historia, blog o sitio web de carácter público.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="Ejemplo de COVID-19 con datos de EE. UU.":::

En este artículo se describe cómo hacer lo siguiente:

- Copiar código para insertar y colocarlo en su propio sitio. 
- Realizar personalizaciones, como la aplicación de formato de un estado específico.
- Publicar en el servicio Power BI.
- Publicar en Web. 
- Combinar estos datos con datos de otro origen. 

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar a usar Power BI para contar su historia, necesita estos requisitos previos:

- Descargar gratis la aplicación [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Suscríbase al [servicio Power BI](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Opción 1: Compilar previamente el código para insertar

Microsoft ha publicado el informe de ejemplo y ha creado un código para insertar de Publicar en Web. Puede usar el código para insertar para insertar el ejemplo completo, incluida la vista nacional, y explorar en profundidad hasta el nivel de estado y de condado en su propio sitio web. Antes de publicar estos datos, se recomienda revisar las [declinaciones de responsabilidades](#disclaimers) de este artículo.

Para incluir el gráfico interactivo en el sitio, copie y pegue el siguiente código para insertar en el lugar en el que desea que aparezca el gráfico en la página web.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

El código para insertar es un elemento iFrame de HTML que puede insertar en cualquier página HTML. Ajuste el ancho y el alto del iFrame proporcionado para que quepa en el sitio. El informe de ejemplo se ha creado en la proporción 16:9, por lo que debe elegir un tamaño que conserve esta dimensión. Cuando se implementa correctamente, el gráfico aparece sin ningún borde gris adicional. Resulta útil [revisar las sugerencias y trucos para el tamaño de iFrame](../service-publish-to-web.md#tips-and-tricks-for-iframe-height-and-width) al realizar estos cambios.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Opción 2: Personalizar el archivo de Power BI de ejemplo

El archivo de Power BI contiene los datos y los gráficos interactivos en un formato de archivo. pbix que se puede editar en Power BI Desktop.  

Una personalización típica es filtrar el informe por un estado específico y, a continuación, crear su propio código para insertar de Publicar en Web para el informe personalizado.

Los datos de USAFacts se proporcionan en una licencia de Creative Commons que requiere atribución. Antes de publicar estos datos, revise las [declinaciones de responsabilidades](#disclaimers).

Para empezar, [descargue el archivo .pbix (aquí)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Actualización del informe 

1. Descargue la versión más reciente de la aplicación gratuita, [Power BI Desktop](https://powerbi.microsoft.com/desktop/), si no lo ha hecho todavía. 

2. Descargue el [archivo .pbix](https://go.microsoft.com/fwlink/?linkid=2125058) si no lo ha hecho aún y ábralo en Power BI Desktop.

3. Para filtrar el informe por un estado específico, seleccione la flecha para expandir el panel de filtros.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Expansión del panel Filtros":::

4. Seleccione el estado que le interese. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Selección de un estado":::

5. Para guardar el archivo, seleccione **Archivo** > **Guardar**. 

### <a name="refresh-your-report"></a>Actualización del informe 

1. Seleccione el botón **Actualizar**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Botón Actualizar":::

2. Seleccione **Anónimo** > **Conectar**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Selección de anónimo":::

 
3. Seleccione **Ignorar los niveles de privacidad**, si se muestra > **Guardar**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Selección de los niveles de privacidad":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Publicación del informe en el servicio Power BI

Una vez que haya personalizado el informe a su gusto, [siga los pasos que se describen aquí para publicarlo](../desktop-upload-desktop-files.md) en el servicio Power BI.

### <a name="configure-scheduled-refresh"></a>Configuración de actualización programada

Para mantener actualizados los datos del informe, puede [configurar la actualización programada](../refresh-scheduled-refresh.md) después de publicar el informe.

Cuando siga los pasos, elija las opciones siguientes:

1. Método de autenticación de credenciales de origen de datos: Anónimo
2. Nivel de privacidad para este origen de datos: Público

Para probar la configuración de la actualización, seleccione la opción [Actualizar ahora](../refresh-data.md#data-refresh), disponible en el elemento del conjunto de datos.

Los datos actualizados se cargan cada vez que se ejecuta la programación. Los datos subyacentes los proporciona USAFacts y puede que no se actualicen con tanta frecuencia como la programación de la actualización. Consulte el [sitio web de USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) para saber cuándo se actualizaron por última vez los datos subyacentes. 

Si tiene previsto publicar el informe personalizado en su sitio web, es mejor configurar la actualización programada para que se ejecute al menos con tanta frecuencia como se actualicen los datos de USAFacts. Dado que USAFacts puede actualizar sus datos en momentos diferentes cada día, es posible que desee configurar varias actualizaciones al día. 

### <a name="create-a-publish-to-web-embed-code"></a>Creación de un código para insertar de Publicar en Web 

Para insertar el informe personalizado en su propio sitio web, siga las instrucciones para [crear su propio código para insertar de Publicar en Web](../service-publish-to-web.md#how-to-use-publish-to-web).

Una vez que publique el código para insertar, use el iFrame del cuadro de diálogo de confirmación para insertarlo en el sitio web.

Si realiza cambios en el informe en Power BI Desktop, puede publicar y reemplazar el informe existente en el servicio Power BI. El código para insertar no cambia. Los cambios en el informe o los datos actualizados tardan aproximadamente una hora en aparecer en el sitio web. 

## <a name="option-3-mash-up-data-from-another-source"></a>Opción 3: Combinar datos de otro origen 

También puede combinar los datos de este informe con datos de otro origen. El ejemplo siguiente se basa en los datos de la [Universidad Johns Hopkins](https://github.com/CSSEGISandData/COVID-19). Antes de publicar estos datos, se recomienda revisar las [declinaciones de responsabilidades](#disclaimers) de este artículo.

1. Seleccione **Obtener datos** > **Web**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Botón Obtener datos":::

2. Escriba la siguiente dirección URL:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Selección de datos de una Web":::

3. Seleccione **Aceptar**. 

    > [!NOTE]
    > El vínculo publicado por la Universidad Johns Hopkins puede cambiar. Consulte la [página de GitHub de Johns Hopkins](https://github.com/CSSEGISandData/COVID-19) para obtener la información más reciente.

4. Seleccione **Cargar** para cargar el conjunto de los casos totales confirmados en todo el mundo.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Carga de datos desde la Web":::

    En el artículo [Conexión a páginas web desde Power BI Desktop](../desktop-connect-to-web.md) se proporciona más información acerca de la carga de datos desde la Web.
    
A continuación, puede usar Power BI Desktop para visualizar los datos. Por último, siga los pasos descritos en la **Opción 2:** [Publicación del informe en el servicio Power BI](#publish-your-report-to-the-power-bi-service) para publicar el informe y crear un código para insertar personalizado. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Opción 4: Uso de la plantilla de aplicación del Seguimiento de la COVID-19 en EE. UU.

A fin de contar con una opción más, el equipo de Power BI ha creado la *aplicación de plantilla* del Seguimiento de la COVID-19 en EE. UU. para que pueda empezar de inmediato. Las aplicaciones de plantilla son agrupaciones de informes, paneles y conjuntos de datos para un origen de datos específico. Puede descargarlos desde AppSource, usarlos o modificarlos para adaptarlos a sus necesidades y distribuirlos a sus compañeros. 

Esta aplicación de plantilla del Seguimiento de la COVID-19 en EE. UU. contiene un informe predefinido de métricas de la COVID-19 que se puede usar tal cual, personalizar directamente en el servicio Power BI o descargar para agregar otros orígenes de datos si lo desea. Obtenga información sobre cómo instalar la [aplicación de plantilla del Seguimiento de la COVID-19 en EE. UU.](../connect-data/service-connect-to-covid-19-tracking.md) y empezar inmediatamente.

## <a name="about-the-data-source-for-this-report"></a>Acerca del origen de datos para este informe
Este informe interactivo agrega datos de los centros de control y prevención de enfermedades (CDC) de Estados Unidos y organismos de salud pública a nivel estatal y local. Los datos a nivel de condado se confirman mediante referencia directa a los organismos estatales y locales (vínculo).

Los datos son proporcionados por USAFacts. Debido a la frecuencia de las actualizaciones de datos, puede que estos no reflejen los números exactos que notifican las organizaciones gubernamentales o los medios de noticias. Para obtener más información o para descargar los datos, visite el sitio web de [USAFacts](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/). 

## <a name="disclaimers"></a>Declinación de responsabilidades

Este informe y los datos se proporcionan "tal cual", "con todos los defectos" y sin ninguna garantía de ningún tipo. Microsoft no ofrece garantías expresas y renuncia expresamente a todas las garantías implícitas, incluidas las de comerciabilidad, idoneidad para un propósito genérico y ausencia de infracción.

Los datos de USAFacts están disponibles bajo una licencia de Creative Commons. Para usarlos, cite a USAFacts como proveedor de datos y vincule a USAFacts. Para conocer los pasos de atribución exactos, vea la sección **#MadewithUSAFacts** de la página USAFacts [Coronavirus en Estados Unidos: cartografía del brote de COVID-19 en estados y condados](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

Los datos de la Universidad Johns Hopkins están protegidos con el copyright 2020 Johns Hopkins University, reservados todos los derechos. Se proporcionan al público estrictamente para fines de investigación académica y educativa. Aquí están los [términos de uso](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) completos de los datos que se muestran en el ejemplo de combinación. Hay más información disponible en el [sitio web de la Universidad Johns Hopkins](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Pasos siguientes

[Obtención de ejemplos para Power BI](../sample-datasets.md)