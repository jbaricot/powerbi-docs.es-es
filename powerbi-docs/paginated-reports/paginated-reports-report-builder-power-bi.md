---
title: ¿Qué son los informes paginados en Power BI Premium?
description: Los informes paginados ahora están disponibles en el servicio Power BI. Durante mucho tiempo, han sido el formato de informe estándar en SQL Server Reporting Services. Estos informes se pueden imprimir o compartir. Puede controlar el diseño del informe totalmente. Muestran todos los datos en una tabla, por ejemplo, incluso si la tabla abarca varias páginas.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: jXTiYJKw1Rs
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 10/16/2020
ms.openlocfilehash: 2c136f4d81a9cb1c1904c3a06b58271391c76c23
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297767"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>¿Qué son los informes paginados en Power BI Premium?

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Los *informes paginados* están diseñados para imprimirse o compartirse. Se denominan *paginados* porque presentan un formato apto para encajar en una página. Muestran todos los datos en una tabla, incluso si esta abarca varias páginas. A veces se denominan *perfectos hasta el último detalle* , porque se puede controlar exactamente el diseño de página del informe. Power BI Report Builder es la herramienta independiente para crear informes paginados para el servicio Power BI. 

Estos son algunos vínculos rápidos si está a punto para empezar:

- [Instalación del Generador de informes de Power BI desde el Centro de descarga de Microsoft](https://aka.ms/pbireportbuilder)
- [Tutorial: Crear un informe paginado](paginated-reports-quickstart-aw.md)
- [Informes paginados de Power BI de ejemplo](paginated-reports-samples.md)
- ¿Busca información sobre Report Builder para Power BI Report Server o SQL Server Reporting Services? Vea [Instalación de Report Builder: Power BI Report Server](../report-server/install-report-builder.md) en su lugar.

Los informes paginados suelen tener muchas páginas. Por ejemplo, este informe tiene 563 páginas. Cada una de ellas está diseñada con precisión, con una página por factura y encabezados y pies de página que se repiten.

![Paginado](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Puede obtener una vista previa del informe en el Generador de informes y luego publicarlo en el servicio Power BI, app.powerbi.com. Necesita una licencia de Power BI Pro para publicar un informe en el servicio. Puede publicar y compartir informes paginados en Mi área de trabajo o en las áreas de trabajo de la aplicación, siempre que el área de trabajo tenga la capacidad Premium de Power BI. Además, un administrador de Power BI debe habilitar los informes paginados en la [sección de capacidades Premium](../admin/service-admin-premium-workloads.md#paginated-reports) del portal de administración de Power BI. 

## <a name="compare-power-bi-reports-and-paginated-reports"></a>Comparación entre los informes de Power BI y los informes paginados

Una ventaja importante de los informes paginados es la posibilidad de imprimir todos los datos de una tabla, sin importar lo largos que sean. Imagine que coloca una tabla en un informe de Power BI. Verá algunas de sus filas en la página y tendrá una barra de desplazamiento para ver el resto. Si imprime esa página o la exporta a PDF, las únicas filas que imprime son las que vio en la página. 

Ahora, supongamos que coloca la misma tabla en un informe paginado. Al imprimirlo o exportarlo a PDF, el informe paginado tiene tantas páginas como sea necesario para imprimir cada fila de esa tabla. 

En el siguiente vídeo, Peter Myers, uno de los profesionales más valiosos de Microsoft de plataforma de datos, y Chris Finlan, jefe de programación principal, demuestran la impresión de una tabla similar en los dos formatos de informe. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXTiYJKw1Rs?list=PL1N57mwBHtN1icIhpjQOaRL8r9G-wytpT" frameborder="0" allowfullscreen></iframe>

Este vídeo forma parte de un curso en vídeo de ocho módulos, [Informes paginados de Power BI en un día](../learning-catalog/paginated-reports-online-course.md). Este curso está concebido para proporcionarle, como autor de informes, los conocimientos técnicos necesarios para crear, publicar y distribuir informes paginados de Power BI.

## <a name="create-reports-in-power-bi-report-builder"></a>Creación de informes en el Generador de informes de Power BI

Los informes paginados tienen su propia herramienta de diseño, el Generador de informes de Power BI. Se trata de una herramienta nueva que comparte la misma base que las herramientas que había utilizado previamente para crear informes paginados para Power BI Report Server o SQL Server Reporting Services (SSRS). De hecho, los informes paginados que cree para SSRS 2016 y 2017 o para Power BI Report Server en el entorno local son compatibles con el servicio Power BI. El servicio Power BI mantiene la compatibilidad con versiones anteriores, para poder avanzar con los informes, y puede actualizar cualquier informe paginado de una versión anterior. No todas las características de informes están disponibles durante el lanzamiento. Vea [Limitaciones y consideraciones](#limitations-and-considerations) en este artículo para obtener más información.
     
## <a name="report-from-a-variety-of-data-sources"></a>Informes a partir de una variedad de orígenes de datos

Un único informe paginado puede tener un número de orígenes de datos distintos. No tiene un modelo de datos subyacente, a diferencia de los informes de Power BI. Para la versión inicial de los informes paginados del servicio Power BI, los conjuntos de datos y los orígenes de datos insertados se crean en el propio informe. Por ahora, no puede usar orígenes de datos compartidos ni conjuntos de datos compartidos. Cree informes en el generador de informes en el equipo local. Si un informe se conecta a datos locales, después de cargar el informe en el servicio Power BI, debe crear una puerta de enlace y redirigir la conexión de datos. Estos son los orígenes de datos a los que puede conectarse en este momento:

- Azure SQL Database y Data Warehouse (mediante Basic y oAuth)
- Azure Analysis Services (mediante SSO)
- SQL Server a través de una puerta de enlace
- SQL Server Analysis Services a través de una puerta de enlace
- Conjuntos de datos de Power BI
- Oracle
- Teradatos

## <a name="design-your-report"></a>Diseño del informe  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Creación de informes paginados con diseños de forma libre, gráfico y matriz

Los informes de tabla funcionan bien con datos basados en columnas. Los informes de matriz, como los informes de tabla dinámica e informes de tabla cruzada, son buenos para datos resumidos. Los informes de gráfico presentan los datos en formato gráfico y los informes de *lista* de formato libre pueden presentar casi cualquier cosa, como facturas. 
  
Puede empezar con uno de los asistentes del generador de informes. Los asistentes de tabla, matriz y gráfico le ayudarán a crear el conjunto de datos insertado y la conexión del origen de datos insertada. Después, arrastre y coloque los campos para crear una consulta de conjunto de datos, seleccionar un diseño y estilo y personalizar el informe.  
  
Con el asistente para mapas, puede crear informes que muestren datos agregados con un fondo geométrico o geográfico. Los datos de mapas pueden ser datos espaciales de una consulta Transact-SQL o un archivo de forma de Environmental Systems Research Institute, Inc. (ESRI). También puede agregar un fondo de mosaico de mapa de Microsoft Bing.  

### <a name="add-more-to-your-report"></a>Agregar más al informe

Modifique los datos mediante el filtrado, la agrupación y la ordenación de los datos o con la adición de fórmulas o expresiones. Agregue gráficos, medidores, minigráficos e indicadores para resumir los datos en un formato visual.  Use parámetros y filtros para filtrar datos en vistas personalizadas. Inserte imágenes y otros recursos o haga referencia a ellos, incluido contenido externo.  

Todo el contenido de un informe paginado, desde el propio informe hasta cada cuadro de texto, imagen, tabla y gráfico, tiene una matriz de propiedades que puede configurar para que el informe tenga exactamente el mismo aspecto que desea.

## <a name="creating-a-report-definition"></a>Creación de una definición de informe

Al diseñar un informe paginado, realmente crea una *definición de informe*. No contiene los datos. Especifica de dónde se obtienen los datos, qué datos se obtienen y cómo mostrar los datos. Al ejecutar el informe, el procesador de informes toma la definición de informe que ha especificado, recupera los datos y los combina con el diseño del informe para generar el informe. Cargue la definición de informe en el servicio Power BI, `https://app.powerbi.com`, en Mi área de trabajo o en un área de trabajo compartida con sus compañeros. Si el origen de datos del informe es local, después de cargar el informe, redirija la conexión del origen de datos para que pase por una puerta de enlace. 

## <a name="view-your-paginated-report"></a>Visualización del informe paginado
Verá el informe paginado en el servicio Power BI en un explorador y también en las aplicaciones móviles de Power BI. En el servicio Power BI, puede exportar el informe a varios formatos, como HTML, MHTML, PDF, XML, CSV, TIFF, Word y Excel. También puede compartirlo con otros usuarios.  

## <a name="create-a-subscription-to-your-report"></a>Creación de una suscripción al informe

Ahora puede configurar suscripciones de correo electrónico para usted y otros usuarios para los informes paginados en el servicio Power BI. En general, el proceso es el mismo que para la suscripción a informes y paneles en el servicio Power BI. En la configuración de las suscripciones, elija la frecuencia con la que desea recibir los correos electrónicos: diaria, semanal o cada hora. La suscripción contiene un archivo PDF adjunto con la salida completa del informe.

Para más información, consulte el artículo [Suscripción personal y de otros usuarios a informes paginados en el servicio Power BI](../consumer/paginated-reports-subscriptions.md). 

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Estas son algunas otras características que no son compatibles con la versión inicial:

- Anclar páginas de informes u objetos visuales a los paneles de Power BI. Aún puede anclar visualizaciones a un panel de Power BI desde un informe paginado local en un servidor de informes de Power BI o un servidor de informes de Reporting Services. Para más información, consulte [Anclar elementos de Reporting Services en paneles de Power BI](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards).
- Mapas del documento.
- Informes detallados.  Plantéese el uso de parámetros de dirección URL con informes paginados en escenarios de obtención de detalles.
- Orígenes de datos compartidos y conjuntos de datos compartidos.

 
## <a name="next-steps"></a>Pasos siguientes

- [Instalación del Generador de informes de Power BI desde el Centro de descarga de Microsoft](https://aka.ms/pbireportbuilder)
- [Tutorial: Crear un informe paginado](paginated-reports-quickstart-aw.md)
- [Curso en línea: Informes paginados de Power BI en un día](../learning-catalog/paginated-reports-online-course.md)
- [Informes paginados de Power BI de ejemplo](paginated-reports-samples.md)
- [Escritura directa de datos en un informe paginado](paginated-reports-enter-data.md)
- [Tutorial: Inserción de informes paginados de Power BI en una aplicación para los clientes](../developer/embedded/embed-paginated-reports-customers.md)