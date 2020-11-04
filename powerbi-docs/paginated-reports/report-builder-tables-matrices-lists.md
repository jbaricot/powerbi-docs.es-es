---
title: Tablas, matrices y listas en el Generador de informes de Power BI
description: En Power BI Report Builder, las tablas, las matrices y las listas son las regiones de datos que muestran los datos del informe paginado en celdas organizadas en filas y columnas.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3d22696168d8ae550238fab243110db357b39c22
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297681"
---
# <a name="tables-matrixes-and-lists-in-power-bi-report-builder"></a>Tablas, matrices y listas en el Generador de informes de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

En el Generador de informes, las tablas, matrices y listas son las *regiones de datos* que muestran los datos del informe paginado en celdas organizadas en filas y columnas. Normalmente, las celdas contienen datos como texto, fechas y números, pero también pueden contener medidores, gráficos o elementos de informe como imágenes. En conjunto, las tablas, matrices y listas suelen aparecer como regiones de datos *tablix*.  
  
 La plantillas de tabla, matriz y lista se generan en la región de datos Tablix, que es una cuadrícula flexible que puede mostrar datos en celdas. En las plantillas para matrices y tablas, las celdas se organizan en filas y columnas. Como las plantillas son variaciones de la región de datos Tablix genérica subyacente, los datos se pueden mostrar en combinaciones de formatos de plantilla; la tabla, matriz o lista se pueden cambiar al diseñar el informe, de forma que contengan características de otra región de datos. Por ejemplo, si agrega una tabla y se da cuenta de que no le resulta útil, puede agregar grupos de columnas para convertir la tabla en una matriz.  
  
 Las regiones de datos de tabla y matriz pueden mostrar relaciones complejas de datos mediante la inclusión de medidores, matrices, listas, gráficos y tablas anidadas. Las tablas y matrices tienen un diseño tabular y sus datos proceden de un único conjunto de datos basado en un único origen de datos. La principal diferencia entre las tablas y matrices es que las tablas pueden incluir solo grupos de filas, mientras que las matrices tienen grupos de filas y grupos de columnas.  
  
 Las listas son un poco diferentes. Admiten un diseño libre que puede incluir varias tablas del mismo nivel o matrices, cada una con los datos de otro conjunto de datos. Las listas también se pueden utilizar para los formularios, como facturas.  
  
 Las siguientes imágenes ilustran informes sencillos con una tabla, matriz o lista.  

![Tabla, matriz y lista en el Generador de informes](media/report-builder-tables-matrices-lists/report-builder-table-matrix-list.png)
  
##  <a name="tables"></a><a name="Table"></a> Tablas  
 use una tabla para mostrar datos detallados, para organizar los datos en grupos de filas, o para ambas cosas. La plantilla Tabla contiene tres columnas con una fila de encabezado de tabla y una fila de detalles para los datos. En la ilustración siguiente, se muestra la plantilla de tabla inicial, seleccionada en la superficie de diseño:  

![Plantilla de tabla del Generador de informes en la superficie de diseño, seleccionada](media/report-builder-tables-matrices-lists/report-builder-new-table.png)
  
 Puede agrupar los datos por un solo campo, por varios campos o escribiendo su propia expresión. Puede crear grupos anidados o independientes, grupos adyacentes y presentar valores para datos agrupados, o agregar totales a los grupos. Por ejemplo, si la tabla tiene un grupo de filas llamado **Categoría** , puede agregar un subtotal para cada grupo, así como un total general para el informe. Para mejorar la apariencia de tabla y resaltar los datos a los que desee dar énfasis, puede combinar celdas y aplicar formato a los datos y encabezados de tabla.  
  
 Puede ocultar inicialmente los datos detallados o agrupados, e incluir controles de alternancia de obtención de detalles para permitir a los usuarios elegir interactivamente cuántos datos se van a mostrar.  
  
##  <a name="matrixes"></a><a name="Matrix"></a> Matrices  
 use una matriz para mostrar resúmenes de los datos agregados agrupados en filas y en columnas; algo similar a una tabla dinámica o a una tabla de referencias cruzadas. El número de valores únicos por cada grupo de filas y columnas determina el número de filas y de columnas de los grupos. En la ilustración siguiente, se muestra la plantilla de matriz inicial, seleccionada en la superficie de diseño:  

![Nueva matriz del Generador de informes agregada desde el cuadro de herramientas, seleccionada](media/report-builder-tables-matrices-lists/report-builder-new-matrix.png)
 
 Puede agrupar datos por varios campos o expresiones en grupos de filas y de columnas. En tiempo de ejecución, cuando se combinan las regiones de datos y los datos del informe, una matriz crece en horizontal y vertical en la página al irse agregando columnas a los grupos de columnas y filas a los grupos de filas. Las celdas de la matriz muestran valores agregados cuyo ámbito es la intersección de los grupos de filas y de columnas a los que pertenece la celda. Por ejemplo, si la matriz tiene un grupo de filas (Categoría) y dos grupos de columnas (Territorio y Año) que muestran la suma de las ventas, el informe muestra dos celdas con las sumas de ventas de cada valor del grupo de categorías. El ámbito de las celdas son las dos intersecciones: Category y Territory, y Category y Year. La matriz puede tener grupos anidados y adyacentes. Los grupos anidados tienen una relación primario-secundario y los adyacentes una relación del mismo nivel. Puede agregar los subtotales a cualquiera de los niveles de grupos anidados de filas y columnas de la matriz.  
  
 Para que los datos de la matriz sean más legibles y resaltar los datos a los que desea dar énfasis, puede combinar celdas, dividir los datos en horizontal y en vertical, o aplicar formato a los datos y encabezados de grupo.  
  
 También puede incluir controles de alternancia de obtención de detalles que ocultan inicialmente los datos detallados; de esta forma, el usuario podrá hacer clic en dichos controles para mostrar más o menos detalles, según sea necesario.  
  
##  <a name="lists"></a><a name="List"></a> Listas  
 use una lista para crear un diseño de forma libre. Con una lista, no está limitado a un diseño de cuadrícula, sino que puede colocar libremente los campos dentro de la lista. Use una lista para diseñar un formulario que permita mostrar muchos campos de conjunto de datos, o como contenedor para mostrar en paralelo varias regiones de datos para los datos agrupados. Por ejemplo, puede definir un grupo para una lista; agregar una tabla, un gráfico y una imagen; y mostrar los valores en forma de tabla y de gráfico para cada valor del grupo, tal y como lo haría con un registro de un empleado o de un paciente.  

![Nueva lista del Generador de informes agregada desde el cuadro de herramientas, seleccionada](media/report-builder-tables-matrices-lists/report-builder-new-list.png)
  
##  <a name="preparing-data"></a><a name="PreparingData"></a> Preparación de los datos  
 Una región de datos de tabla, matriz y lista muestra datos de un conjunto de datos. Puede preparar los datos en la consulta que recupera los datos para el conjunto de datos, o establecer las propiedades en la tabla, matriz o lista.  
  
 Para preparar los datos, los lenguajes de consulta, como Transact-SQL, que se usan para recuperar los datos para los conjuntos de datos de informe pueden filtros para incluir solo un subconjunto de los datos, reemplazar los valores null o en blanco por constantes que hagan el informe más legible, y ordenar y agrupar los datos.  
  
 Si decide preparar los datos de la región de datos de tabla, matriz o lista de un informe, debe establecer las propiedades en la región de datos o las celdas de la región de datos. Si desea filtrar u ordenar los datos, debe establecer las propiedades en la región de datos. Por ejemplo, para ordenar los datos debe especificar las columnas por las que se va a ordenar y el sentido de la ordenación. Si desea proporcionar un valor alternativo para un campo, debe establecer los valores del texto de la celda en que se muestra el campo. Por ejemplo, para mostrar En blanco cuando un campo esté vacío o tenga un valor nulo, debe usar una expresión para establecer el valor.  
  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a> Creación y configuración de una tabla, matriz o lista  
 Al agregar tablas o matrices a un informe, puede usar el asistente para tablas y matrices, o puede generarlas manualmente con las plantillas que proporciona el Generador de informes. Las listas se generan manualmente a partir de la plantilla de lista.  
  
 El asistente indica todos los pasos para generar y configurar rápidamente una tabla o una matriz. Después de completar el asistente o generar las regiones de datos Tablix desde cero, puede configurarlas y refinarlas. Los cuadros de diálogo, disponible en los menús contextuales en las regiones de datos, facilitan el establecimiento de las propiedades más utilizadas para los saltos de página, repeticiones y visibilidad de encabezados y pies de página, opciones de pantalla, filtros y orden. La región de datos Tablix ofrece muchas otras propiedades, que solo puede establecer en el panel Propiedades de Generador de informes. Por ejemplo, si quiere mostrar un mensaje cuando el conjunto de datos de una tabla, matriz o lista esté vacío, debe especificar el texto del mensaje en la propiedad de Tablix NoRowsMessage en el panel Propiedades.  
  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a> Cambiar entre las plantillas de tablix  
 La plantilla inicial de Tablix que elija no es necesariamente definitiva. Mientras agrega grupos, totales y etiquetas, es posible que decida modificar el diseño de Tablix. Por ejemplo, puede comenzar con una tabla y, a continuación, eliminar la fila de detalles y agregar grupos de columnas.  
  
 Para continuar el desarrollo de una tabla, matriz o lista, puede agregar cualquier característica de Tablix. Entre las características de Tablix se incluye la visualización de datos detallados o agregados para los datos agrupados en filas y columnas. Puede crear grupos anidados, grupos adyacentes independientes o grupos recursivos. Puede filtrar y ordenar datos agrupados, y combinar grupos fácilmente mediante la inclusión de varias expresiones de grupo en una definición de grupo.  
  
 También puede agregar totales para un grupo o totales generales para la región de datos. Puede ocultar filas o columnas para simplificar un informe y permitir al usuario alternar entre mostrar u ocultar los datos, como en un informe detallado. 

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
