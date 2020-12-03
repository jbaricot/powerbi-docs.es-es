---
title: Uso del panel Análisis en Power BI Desktop
description: Crear líneas de referencia dinámicas para objetos visuales de Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 1437e680ac7dc4114d68bd534ba8ec93dd8ae508
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416057"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>Uso del panel Análisis en Power BI Desktop

Con el panel **Análisis** en *Power BI Desktop*, puede agregar líneas de referencia dinámicas en objetos visuales y destacar las tendencias o detalles importantes. El panel e icono **Análisis** se encuentran en el área **Visualizaciones** de Power BI Desktop.

![Panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> El panel **Analytics** solo se muestra cuando se selecciona un objeto visual en el lienzo de Power BI Desktop.

## <a name="search-within-the-analytics-pane"></a>Búsqueda en el panel Análisis

Desde la versión de febrero de 2018 de Power BI Desktop (versión 2.55.5010.201 o posterior), puede buscar en el panel **Análisis**, que es una subsección del panel **Visualizaciones**. El cuadro de búsqueda aparece cuando se selecciona el icono **Análisis**.

![Cuadro de búsqueda, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>Uso del panel Analytics

Con el panel **Análisis**, puede crear estos tipos de líneas de referencias dinámicas:

* Línea constante del eje X
* Línea constante del eje Y
* Línea mínima
* Línea máxima
* Línea promedio
* Línea mediana
* Línea de percentil
* Sombreado de simetría

> [!NOTE]
> No todas las líneas están disponibles para todos los tipos de objetos visuales.

Las secciones siguientes muestran cómo se puede usar el panel **Analytics** y las líneas de referencia dinámicas en las visualizaciones.

Para ver las líneas de referencia dinámicas disponibles para un objeto visual, siga estos pasos:

1. Seleccione o cree un objeto visual y, a continuación, seleccione el icono **Analytics** desde la sección **Visualizaciones**.

    ![Vista del análisis de un objeto visual, panel Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. Seleccione el tipo de línea que desea crear para expandir sus opciones. En este caso, seleccionaremos **Línea promedio**.

    ![Línea promedio, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. Para crear una línea, seleccione **+&nbsp;Agregar**. Luego, puede asignarle un nombre a la línea. Haga doble clic en el cuadro de texto y escriba su nombre.

    Ahora tiene todo tipo de opciones para la línea. Puede especificar su **Color**, el porcentaje de **Transparencia**, el **Estilo de línea** y la **Posición** (en comparación con los elementos de datos del objeto visual). También puede elegir si quiere incluir la **Etiqueta de datos**. Para especificar la medida visual en la que se basará la línea, seleccione la lista desplegable **Medida**, que se rellena automáticamente con los elementos de datos del objeto visual. Aquí seleccionaremos **Referencia cultural** como medida, la etiquetaremos como *Promedio de referencia cultural* y personalizaremos algunas de las otras opciones.

    ![Línea promedio de referencia cultural, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. Si quiere que aparezca una etiqueta de datos, cambie **Etiqueta de datos** de **Desactivada** a **Activada**. Al hacerlo, obtendrá una gran variedad de opciones adicionales para la etiqueta de datos.

    ![Configuración de Etiqueta de datos, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. Observe el número que aparece junto al elemento **Línea promedio** en el panel **Analytics**. Eso le indica cuántas líneas dinámicas tiene actualmente en el objeto visual y de qué tipo son. Si agregamos una **Línea máxima** para **Affordability** (Asequibilidad), el panel **Análisis** muestra que ahora también tenemos una línea de referencia dinámica de **Línea máxima** aplicada a este objeto visual.

    ![Línea máxima y totales de línea promedio, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

Si el objeto visual seleccionado no puede tener líneas de referencia dinámica aplicadas (en este caso, un objeto visual de **Mapa**), verá el mensaje siguiente al seleccionar el panel **Análisis**.

![Análisis no disponible para un objeto visual de Mapa, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

Puede resaltar distintos tipos de información interesante mediante la creación de líneas de referencia dinámicas con el panel **Análisis**.

Estamos planeando más características y funcionalidades, como la ampliación de los objetos visuales que pueden tener líneas de referencia dinámicas aplicadas. Vuelva periódicamente para ver las novedades.

## <a name="apply-forecasting"></a>Aplicación de Previsión

Si tiene datos de tiempo en el origen, puede usar la característica de *previsión*. Simplemente debe seleccionar un objeto visual y, luego, expandir la sección **Previsión** del panel **Análisis**. Puede especificar muchas entradas para modificar la previsión, como **Predecir duración** o el **Intervalo de confianza**. En la imagen siguiente se muestra un objeto visual de línea básica con la previsión aplicada. Use su imaginación (y juegue con la previsión) para ver cómo se puede aplicar a los modelos.

![Característica Previsión, panel Análisis, Visualizaciones, Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> La característica de previsión solo está disponible para los objetos visuales de gráfico de líneas.

## <a name="limitations"></a>Limitaciones

La capacidad de usar líneas de referencia dinámicas se basa en el tipo de objeto visual que se está usando. En las listas siguientes se describen estas limitaciones de manera más específica.

Puede usar la *línea constante del eje x*, la *línea constante del eje y* y el *sombreado de simetría* en el objeto visual siguiente:

* Gráfico de dispersión

El uso de *línea constante*, *línea mínima*, *línea máxima*, *línea promedio*, *línea mediana* y *línea de percentil* solo está disponible en estos objetos visuales:

* Gráfico de áreas
* Gráfico de barras agrupadas
* Gráfico de columnas agrupadas
* Gráfico de líneas
* Gráfico de dispersión

Los siguientes objetos visuales solo pueden usar una *línea constante* del panel **Analytics**:

* Gráfico de áreas apiladas
* Gráfico de barras apiladas
* Gráfico de columnas apiladas
* Gráfico de cascada
* Gráfico de barras 100 % apiladas
* Gráfico de columnas 100 % apiladas

Los objetos visuales siguientes pueden usar una *línea de tendencia* si hay datos de tiempo:

* Gráfico de áreas
* Gráfico de columnas agrupadas
* Gráfico de líneas
* Gráfico de líneas y columnas agrupadas

Por último, actualmente no se pueden aplicar líneas dinámicas a muchos objetos visuales, incluidos, entre otros, los siguientes:

* Embudo
* Gráfico de líneas y columnas agrupadas
* Gráfico de líneas y columnas apiladas
* Gráfico de la barra de herramientas
* Objetos visuales no cartesianos, como gráficos de anillos, medidores, matrices, gráficos circulares y tablas

La *línea de percentil* solo está disponible cuando se usan datos importados en Power BI Desktop o cuando se establece una conexión dinámica con un modelo en un servidor que ejecuta **Analysis Service 2016** o posterior, **Azure Analysis Services** o un conjunto de datos en el servicio Power BI.

## <a name="next-steps"></a>Pasos siguientes

Puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [Novedades de Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Obtener Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)
* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](../connect-data/desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Realización de tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)
