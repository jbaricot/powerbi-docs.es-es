---
title: Paginación en informes paginados de Power BI
description: Obtenga información sobre los informes paginados en el servicio Power BI. Obtenga información sobre las reglas que se usan para controlar la paginación con el fin de diseñar un informe optimizado para el representador que tiene previsto usar.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: 591caf8aaefa1b71576a014c5e74cce6ae79acac
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297872"
---
# <a name="pagination-in-power-bi-paginated-reports"></a>Paginación en informes paginados de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

 La *paginación* hace referencia al número de páginas de un informe y a la organización de los elementos del informe en esas páginas. La paginación de los informes paginados de Power BI varía en función de la extensión de representación que use para ver y entregar el informe. Al ejecutar un informe en el servidor de informes, el informe usa el representador de HTML. HTML sigue un conjunto concreto de reglas de paginación. Si exporta el mismo informe a PDF, por ejemplo, estará usando el representador de PDF, que usa otro conjunto de reglas. Por lo tanto, el informe se paginará de manera diferente. Debe comprender las reglas que se usan para controlar la paginación en los informes paginados de Power BI. Después, podrá diseñar correctamente un informe fácil de leer que optimice para el representador que va a usar para enviar el informe.  
  
 En este tema se describe el impacto del tamaño de página físico y el diseño del informe sobre el modo en que los representadores de saltos de página manuales representan el informe. Puede establecer propiedades para modificar el tamaño de página físico y los márgenes, y dividir el informe en columnas mediante el panel **Propiedades del informe** , el panel **Propiedades** o el cuadro de diálogo **Configurar página**. Para acceder al panel **Propiedades del informe** , haga clic en el área azul fuera del cuerpo del informe. Para acceder al cuadro de diálogo **Configurar página** , haga clic en **Ejecutar** en la pestaña Inicio y, a continuación, haga clic en **Configurar página** en la pestaña Ejecutar.  
  
> [!NOTE]  
>  Si ha diseñado un informe para que tenga el ancho de una página, pero se representa en varias páginas, compruebe que el ancho del cuerpo del informe, incluidos los márgenes, no sea superior al ancho del tamaño de página físico. Para evitar que se agreguen páginas vacías al informe, puede reducir el tamaño del contenedor arrastrando la esquina del contenedor hacia la izquierda.  

## <a name="the-report-body"></a>Cuerpo del informe  
 El cuerpo del informe es un contenedor rectangular que se muestra como un espacio en blanco en la superficie de diseño. Puede aumentar o reducir su tamaño para dar cabida a los elementos de informe que contiene. El cuerpo del informe no refleja el tamaño de página físico y, de hecho, puede crecer por encima de límites del tamaño de página físico para abarcar varias páginas del informe. Algunos representadores representan informes que aumentan o reducen su tamaño en función del contenido de la página. Los informes representados en estos formatos se optimizan para la visualización basada en pantalla, como en un explorador web. Estos representadores, como Microsoft Excel, Word, HTML y MHTML, agregan saltos de página verticales cuando es necesario.  
  
 Puede dar formato al cuerpo del informe con el color, el estilo y el ancho del borde. También puede agregar un color de fondo y una imagen de fondo.  
  
## <a name="the-physical-page"></a>Página física  
 El tamaño físico de la página es el tamaño del papel. El tamaño de papel que especifica para el informe controla cómo se representa el informe. Los informes representados en formatos de saltos de página manuales insertan saltos de página horizontal y verticalmente en función del tamaño físico de la página. Estos saltos de página proporcionan una experiencia de lectura optimizada cuando se imprimen o se visualizan en un formato de archivo de salto de página manual. Los informes representados en formatos de saltos de página automáticos insertan saltos de página horizontalmente en función del tamaño físico. De nuevo, los saltos de página proporcionan una experiencia de lectura optimizada cuando se ven en un explorador web.  
  
 De forma predeterminada, el tamaño de página es de 8,5 x 11 pulgadas. Puede cambiarlo en el panel **Propiedades del informe** o el cuadro de diálogo **Configurar página** , o bien cambiar las propiedades PageHeight y PageWidth en el panel **Propiedades**. El tamaño de página no aumenta ni se reduce para ajustarse al contenido del cuerpo del informe. Si desea que el informe aparezca en una única página, todo el contenido del cuerpo del informe debe ajustarse a la página física. Si no cabe y usa el formato de salto de página manual, el informe requerirá páginas adicionales. Si el cuerpo del informe crece más allá del borde derecho de la página física, se inserta un salto de página horizontal. Si el cuerpo del informe crece más allá del borde inferior de la página física, se inserta un salto de página vertical.  
  
 Puede invalidar el tamaño físico de la página definido en el informe. Especifique el tamaño de página físico mediante la configuración Información del dispositivo del representador que use para exportar el informe. Para obtener una lista completa, consulte [Device Information Settings for Rendering Extensions](/sql/reporting-services/device-information-settings-for-rendering-extensions-reporting-services) (Configuración de la información del dispositivo para las extensiones de representación) en la documentación de SQL Server Reporting Services.  
  
### <a name="margins"></a>Márgenes

Report Builder dibuja los márgenes desde el borde de las dimensiones de la página física hacia el interior, hasta el valor de margen especificado. Si un elemento de informe se extiende hasta el área de margen, se recorta para que el área superpuesta no se represente. Si especifica tamaños de márgenes que provocan que el ancho horizontal o vertical de la página sea igual a cero, la configuración de margen predeterminada es cero. Los márgenes se especifican en el panel **Propiedades del informe** o el cuadro de diálogo **Configurar página** , o bien puede modificar las propiedades TopMargin, BottomMargin, LeftMargin y RightMargin del panel **Propiedades**. Para invalidar el tamaño de margen definido en el informe, especifique el tamaño de margen mediante la configuración Información del dispositivo para el representador específico que use para exportar el informe.  
  
 El *área de página utilizable* es el área de la página física que queda después de asignar espacio para los márgenes, el espaciado de las columnas, y el encabezado y pie de página de la página. Los márgenes solo se aplican cuando se representan e imprimen informes en formatos de representador de saltos de página manuales. La imagen siguiente indica el margen y el área de página utilizable de una página física.  
  
![Página física con márgenes y área utilizable](media/paginated-reports-pagination/power-bi-paginated-rs-page-margins.png) 
  
### <a name="newsletter-style-columns"></a>Columnas de estilo boletín  

 El informe se puede dividir en columnas, como las columnas de un periódico. Las columnas se tratan como páginas *lógicas* representadas en la misma página *física*. Están organizadas de izquierda a derecha y de arriba abajo, y están separadas por espacios en blanco entre las columnas. Si el informe se divide en más de una columna, cada página física se divide verticalmente en columnas. Cada columna se considera una página lógica. Por ejemplo, supongamos que tiene dos columnas en una página física. El contenido del informe rellena la primera columna y, a continuación, la segunda. Si el informe no cabe por completo en las dos primeras columnas, el informe rellenará la primera y la segunda columna de la página siguiente. Las columnas se continúan rellenando, de izquierda a derecha y de arriba abajo hasta que se representan todos los elementos del informe. Si especifica tamaños de columna que provocan que el ancho horizontal o vertical sea igual a cero, el espaciado entre columnas predeterminado es cero.  
  
 Las columnas se especifican en el panel **Propiedades del informe** o el cuadro de diálogo **Configurar página**. También se pueden especificar modificando las propiedades TopMargin, BottomMargin, LeftMargin y RightMargin del panel **Propiedades**. Para usar un tamaño del margen que no esté definido, especifique el tamaño del margen mediante la configuración Información del dispositivo para el representador específico al que vaya a exportar el informe. Las columnas solo se aplican cuando se representan y se imprimen informes en formatos PDF o Imagen. La imagen siguiente indica el área de página utilizable de una página que contiene columnas.  
  
![Página física con columnas](media/paginated-reports-pagination/power-bi-paginated-rs-page-columns.png)
  
## <a name="page-breaks-and-page-names"></a>Saltos de página y nombres de página

 Un informe puede ser más legible y sus datos más fáciles de auditar y exportar si el informe tiene nombres de página. Report Builder proporciona propiedades para estos elementos:

- reports
- regiones de datos de tablas, matrices y listas
- groups
- rectángulos del informe para controlar la paginación, restablecer los números de página y proporcionar nuevos nombres de página de informe en los saltos de página. 
 
Estas características pueden mejorar los informes, con independencia del formato en el que se representen. Son especialmente útiles al exportar informes a libros de Excel.

> [!NOTE]
> Las regiones de datos de tabla, matriz y lista son, en realidad, el mismo tipo de región de datos en segundo plano: *tablix*. Por lo que es posible que aparezca este nombre. 

 La propiedad InitialPageName proporciona el nombre de página inicial del informe. Si el informe no incluye los nombres de página para los saltos de página, se usa el nombre de página inicial para todas las páginas nuevas que crean los saltos de página. No es necesario usar un nombre de página inicial.  
  
 Un informe representado puede proporcionar un nuevo nombre de página para la nueva página que crea un salto de página. Para proporcionar el nombre de página, debe establecer la propiedad PageName de una tabla, matriz, lista, grupo o rectángulo. No es necesario especificar los nombres de página en los saltos. Si no lo hace, se usa el valor de InitialPageName en su lugar. Si InitialPageName también está en blanco, la nueva página no tiene nombre.  
  
 Las regiones de datos de tabla, matriz y lista, los grupos y los rectángulos admiten saltos de página.  
  
 El salto de página incluye las siguientes propiedades:  
  
- **BreakLocation** proporciona la ubicación del salto para el elemento de informe con saltos de página habilitados: al principio, al final, o al principio y al final. En los grupos, BreakLocation se puede situar entre grupos.  
  
- **Deshabilitado** indica si se aplica un salto de página al elemento de informe. Si esta propiedad se evalúa como true, se omite el salto de página. Esta propiedad se utiliza para deshabilitar dinámicamente los saltos de página basados en expresiones cuando se ejecuta el informe.  
  
- **ResetPageNumber** indica si el número de página se debe restablecer a 1 cuando se inserta un salto de página. Si esta propiedad se evalúa como true, se restablece el número de página.  
  
 Puede definir la propiedad BreakLocation en los cuadros de diálogo **Propiedades de Tablix** , **Propiedades del rectángulo** o **Propiedades del grupo** , pero debe definir las propiedades Disabled, ResetPageNumber y PageName en el panel Propiedades del Generador de informes. Si las propiedades del panel Propiedades están organizadas por categoría, las propiedades estarán disponibles en la categoría **PageBreak**. Para los grupos, la categoría **PageBreak** se encuentra dentro de la categoría **Grupo**.  
  
 Puede usar constantes y expresiones simples o complejas para establecer el valor de las propiedades Disabled y ResetPageNumber. Sin embargo, no puede utilizar la expresión con la propiedad BreakLocation. Para obtener más información sobre cómo escribir y usar expresiones, consulte [Expresiones en el Generador de informes de Power BI](report-builder-expressions.md).  
  
 En el informe, puede escribir expresiones que hagan referencia a los nombres o números de página actuales mediante la colección **Globales**. Para obtener más información, consulte [Built-in Globals and Users References](/sql/reporting-services/report-design/built-in-collections-built-in-globals-and-users-references-report-builder) (Referencias de variables globales y de usuarios integradas) en la documentación del Generador de informes y Reporting Services.
  
### <a name="naming-excel-worksheet-tabs"></a>Asignar nombres a las pestañas de libros de Excel

 Estas propiedades son útiles a la hora de exportar informes a libros de Excel. Use la propiedad InitialPage para especificar un nombre predeterminado para el nombre de la pestaña de la hoja de cálculo cuando exporte el informe, y use saltos de página y la propiedad PageName para proporcionar nombres diferentes para cada hoja de cálculo. Cada nueva página del informe, definida por un salto de página, se exporta a una hoja de cálculo diferente designada por el valor de la propiedad PageName. Si PageName está en blanco, pero el informe tiene un nombre de página inicial, todas las hojas de cálculo del libro de Excel usan el mismo nombre: el nombre de página inicial.  
  
 Para obtener más información sobre cómo funcionan estas propiedades cuando se exportan informes a Excel, consulte [Exporting to Microsoft Excel](/sql/reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs) (Exportar a Microsoft Excel) en la documentación del Generador de informes y Reporting Services.  
  
## <a name="next-steps"></a>Pasos siguientes

- [Visualización de un informe paginado en el servicio Power BI](../consumer/paginated-reports-view-power-bi-service.md)
- [Eliminación de páginas en blanco al imprimir informes paginados](../guidance/report-paginated-blank-page.md)
- ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
