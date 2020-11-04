---
title: Sugerencias para el diseño de informes en el Generador de informes de Power BI
description: Use las siguientes sugerencias para diseñar sus informes paginados en el Generador de informes de Power BI.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: dc8400361ca8d7bdd3713efa7bdf180578a597a2
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297911"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Sugerencias para el diseño de informes en el Generador de informes de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Use las siguientes sugerencias para diseñar sus informes paginados en el Generador de informes de Power BI.  
  
##  <a name="designing-reports"></a><a name="DesigningReports"></a> Diseñar informes  
  
-   Un informe bien diseñado transmite información que lleva a emprender acciones. Identifique las preguntas que el informe ayuda a responder. Téngalas en cuenta al diseñar el informe.  
  
-   Para diseñar visualizaciones de datos efectivas, imagine una forma de mostrar información que sea fácil de entender para el usuario del informe. Elija una región de datos que sea apropiada para los datos que desea visualizar. Por ejemplo, un gráfico transmite de forma eficaz información de resumen y de conjunto mejor que una tabla que abarca muchas páginas de información detallada. Puede visualizar los datos de un conjunto de datos en cualquier región de datos, incluidos gráficos, mapas, indicadores, minigráficos, barras de datos y datos tabulares, con diversos diseños de cuadrícula basados en una tablix. 
  
-   Si piensa proporcionar el informe en un formato de exportación concreto, pruebe el formato en una fase temprana del diseño. La compatibilidad con las características varía en función del representador elegido.  
  
-   Al crear diseños complejos, puede generar el diseño en etapas. Puede utilizar rectángulos como contenedores para organizar los elementos de informe. Puede crear regiones de datos directamente en la superficie de diseño para maximizar el área de trabajo y, al finalizar cada una de ellas, arrastrarla a un contenedor de rectángulo. Si utiliza rectángulos como contenedores, puede ubicar todo su contenido en un solo paso. Los rectángulos también ayudan a controlar cómo se representan los elementos de informe en cada página.  
  
-   Para que el informe esté más despejado, puede utilizar visibilidad condicional para elementos concretos del informe y permitir que el usuario decida si mostrarlos o no. Puede establecer la visibilidad en función de un parámetro o un comando de alternancia de cuadro de texto. Puede agregar cuadros de texto condicionales para mostrar los resultados provisionales de las expresiones. Si en un informe aparecen datos inesperados, puede mostrar estos resultados provisionales para facilitar la depuración de las expresiones.  
  
-   Cuando trabaje con elementos anidados en celdas o rectángulos de Tablix, puede establecer diferentes colores de fondo para el contenedor y los elementos contenidos. El color de fondo predeterminado es **Ningún color**. Los elementos con un color de fondo concreto se ven a través de los elementos que tienen el color de fondo establecido en **Ningún color**. Esta técnica puede ayudarle a seleccionar el elemento correcto para establecer propiedades de presentación, como la visibilidad de bordes en las celdas de Tablix.  
  
 Para más información acerca de lo que hay que tener en cuenta al diseñar el informe, consulte [Planeamiento de un informe en el Generador de informes](report-builder-planning-report.md)).  
  
##  <a name="naming-conventions-for-reports-data-sources-and-datasets"></a><a name="NamingConventions"></a> Convenciones de nomenclatura para informes, orígenes de datos y conjuntos de datos  
  
-   Utilice convenciones de nomenclatura para los orígenes de datos y conjuntos de datos que documenten el origen de datos.  
  
    1.  **Orígenes de datos.** Si no desea utilizar un servidor real o la base de datos debido a motivos de seguridad, utilice un alias que indique al usuario cuál es el origen de datos.  
  
    2.  **Conjuntos de datos.** Utilice un nombre que indique en qué origen de datos se basa.  
  
##  <a name="working-with-data"></a><a name="Data"></a> Trabajar con datos  
  
-   Como primer paso, haga que aparezcan en el panel Datos de informe todos los datos con los que desea trabajar. Cuando ajuste las preguntas que el informe va a responder, piense cómo limitar los datos de los conjuntos de datos del informe a solo los necesarios.  
  
-   En general, incluya solo los datos que se vayan a mostrar en un informe. Utilice variables de consulta en las consultas de conjunto de datos para que el usuario pueda elegir los datos que desea ver en el informe. Si crea conjuntos de datos compartidos, proporcione filtros basados en parámetros de informe para proporcionar la misma funcionalidad.  
  
-   Si tiene experiencia en la creación de consultas, debe entender que para cantidades de datos intermedias podría interesarle agrupar los datos en el informe y no en la consulta. Si hace todos los grupos en la consulta, el informe suele ser una presentación del conjunto de resultados de la consulta. Por otro lado, para que se muestren valores de agregado de grandes cantidades de datos en un gráfico o una matriz, no es necesario incluir datos detallados.  
  
-   Dependiendo de los requisitos, puede mostrar en el informe nombres y ubicaciones de orígenes de datos de informe, texto de comandos de consulta del conjunto de datos y valores de parámetro. La primera pregunta que muchos nuevos usuarios se plantean es acerca del lugar de procedencia de los datos. Para que el informe esté más despejado, puede ocultar condicionalmente los cuadros de texto con este tipo de información y permitir que los usuarios elijan la posibilidad de verlos. Intente agregar esta información en la última página del informe. Establezca la visibilidad de los cuadros de texto en función de un parámetro que el usuario pueda cambiar.  
  
##  <a name="interacting-with-the-report-design-surface"></a><a name="DesignSurface"></a> Interactuar con la superficie de diseño del informe  
 La superficie de diseño de informes no es WYSIWIG. Al colocar los elementos de informe en la superficie de diseño, su ubicación relativa afecta a cómo aparecen los elementos en la página del informe representado. Se conserva el espacio en blanco.  
  
-   Utilice líneas de ajuste y botones de diseño para alinear y organizar los elementos en la superficie de diseño del informe. Por ejemplo, puede alinear las partes superiores o los bordes de los elementos seleccionados, expandir un elemento para que su tamaño sea igual que el de otro elemento o ajustar el espaciado entre los elementos.  
  
-   Utilice las teclas de dirección para ajustar la posición y el tamaño de los elementos seleccionados en la superficie de diseño. Por ejemplo, las siguientes combinaciones de teclas son muy útiles:  
  
    -   **Teclas de flecha** Mueven el elemento de informe seleccionado.  
  
    -   **CTRL+teclas de flecha** Desplazan el elemento de informe seleccionado.  
  
    -   **CTRL+SHIFT+teclas de flecha** Aumentan o reducen el tamaño del elemento de informe seleccionado.  
  
-   Para agregar un elemento a un rectángulo, utilice la punta superior izquierda del mouse para señalar la ubicación inicial del elemento en el contenedor de rectángulo. Utilice los métodos abreviados de teclado para ayudar a colocar los objetos seleccionados. El rectángulo se expande automáticamente para que quepan los elementos que contiene.  
  
-   Si desea agregar varios elementos de informe a una celda del Tablix, primero agregue un rectángulo y, después, agregue los elementos.  
  
     De forma predeterminada, cada celda de Tablix contiene un cuadro de texto. Al agregar un rectángulo a una celda, el rectángulo reemplaza al cuadro de texto. Por ejemplo, coloque indicadores anidados en un rectángulo en una celda de Tablix para contribuir a controlar cómo aumenta el tamaño de un gráfico o indicador cuando cambia el alto de la fila en que está la celda.  
  
-   Utilice el control **Zoom** para ajustar la vista de la superficie de diseño. Puede trabajar con la página entera o con secciones más pequeñas de la página.  
  
-   Para arrastrar campos del panel Datos de informe al panel de agrupación, no lo haga por otros elementos de informe de la superficie de diseño, porque así se seleccionan los otros elementos y se anula la selección la región de datos Tablix. Arrastre el campo hacia abajo el panel Datos de informe y, a continuación, al panel de agrupación.  
  
###  <a name="selecting-items"></a><a name="Selecting"></a> Seleccionar elementos  
 Para seleccionar el objeto deseado en la superficie de diseño del informe, utilice la tecla ESC, el menú contextual del botón secundario, el panel Propiedades y el panel Agrupación.  
  
-   -   Presione ESC para recorrer la pila de elementos de informe que ocupan el mismo espacio en la superficie de diseño.  
  
    -   En algunos elementos de informe, puede utilizar el menú contextual del botón secundario para seleccionar el elemento de informe o parte del elemento de informe que desee.  
  
    -   Las propiedades de la selección actual aparecen en el panel de propiedades.  
  
    -   Para trabajar con los grupos de filas y grupos de columnas de una región de datos Tablix, seleccione el grupo en el panel Agrupación.  

  
##  <a name="working-with-specific-types-of-report-items"></a><a name="ReportItems"></a> Trabajar con tipos específicos de elementos de informe  
  
###  <a name="working-with-parameters"></a><a name="Parameters"></a> Trabajar con parámetros  
  
-   El propósito principal de los parámetros de informe consiste en filtrar los datos en el origen de datos y recuperar solo los necesarios para el propósito del informe.  
  
-   En el caso de los parámetros de informe, busque un equilibrio entre permitir la interactividad y ayudar a un usuario a obtener los resultados que desea. Por ejemplo, puede establecer los valores predeterminado de un parámetro en valores que sabe que son habituales.  
  
###  <a name="working-with-text"></a><a name="Text"></a> Trabajar con texto  
  
-   Si pega varias líneas en un cuadro de texto, el texto se agrega como una unidad de texto. Las unidades de texto solo pueden recibir formato como una unidad. Para dar formato independientemente a cada línea, inserte una nueva línea presionando RETORNO en la unidad de texto según sea necesario. A continuación, puede aplicar formato y estilos a cada línea de texto independiente del cuadro de texto.  
  
-   Puede establecer propiedades de y acciones de formato en un cuadro de texto o en texto de marcador de posición del cuadro de texto. Si hay solo una línea de texto, resulta más eficiente establecer las propiedades en el cuadro de texto que en el texto.  
  
###  <a name="working-with-expressions"></a><a name="Expressions"></a> Trabajar con expresiones  
  
-   Descripción de los formatos de expresiones simples y complejas. Puede escribir directamente el formato de expresión simple en los cuadros de texto, las propiedades en el panel de propiedades, o en los lugares de los cuadros de diálogo que acepten una expresión.
  
-   Al crear una expresión, ayuda a crear cada parte de forma independiente y a comprobar su valor. A continuación, puede combinar todas las partes en una expresión final. Una técnica útil es agregar un cuadro de texto en una celda de la matriz, mostrar cada parte de la expresión y establecer la visibilidad condicional en el cuadro de texto. Para controlar el estilo de borde y el color cuando se oculta el cuadro de texto, coloque primero el cuadro de texto en un rectángulo y, a continuación, establezca el estilo de borde y el color del rectángulo de modo que coincidan con la matriz.  
  
###  <a name="working-with-indicators"></a><a name="Indicators"></a> Trabajar con indicadores  
  
-   De forma predeterminada, un indicador muestra tres estados por lo menos. Después de agregar un indicador a un informe, puede configurarlo agregando o quitando estados. Para facilitar la visualización por parte de los usuarios, elija un indicador que varíe el color y la forma.  
  
##  <a name="controlling-the-rendering-of-report-items-on-the-report-page"></a><a name="Rendering"></a> Controlar la representación de elementos de informe en la página del informe  
  
-   En la superficie de diseño de informe, los elementos de informe aumentan de tamaño para alojar el contenido del conjunto de datos, expresión, subinforme o texto asociados.  
  
    -   Al colocar un elemento en la página del informe, la distancia entre el elemento y todos los elementos que comienzan a su derecha se convierte en la distancia mínima que se debe mantener cuando un elemento de informe crece horizontalmente. De igual forma, la distancia entre un elemento y el elemento que encima se convierte en la distancia mínima que se debe mantener cuando el elemento superior aumenta de tamaño verticalmente.  
  
    -   Un elemento de informe aumenta de tamaño para dar cabida a sus datos y empuja a los elementos del mismo nivel (elementos dentro del mismo contenedor primario), para que no estorben, utilizando las siguientes reglas:  
  
    -   Cada elemento se desplaza hacia abajo para mantener el espacio mínimo entre él y los elementos que acaban por encima.  
  
    -   Cada elemento se desplaza hacia la derecha para mantener el espacio mínimo entre él y los que acaban a su izquierda. En el caso de sistemas con diseños de derecha a izquierda, cada elemento se desplaza hacia la izquierda para mantener el espacio mínimo entre él y los que acaban a su derecha.  
  
    -   Los contenedores aumenta de tamaño si los elementos secundarios aumentan de tamaño. En el caso de un elemento seleccionado, en el panel Propiedades, la propiedad primaria identifica el contenedor para el elemento. También puede utilizar el panel del esquema del documento para ver la jerarquía de contención de los elementos del informe.  
  
    -   La barra de herramientas **Diseño** proporciona varios botones que ayudan a alinear bordes, centros y el espaciado de los elementos de informe. Para habilitar la barra de herramientas **Diseño** , en el menú **Ver** , seleccione **Barras de herramientas** y, a continuación, haga clic en **Diseño**.  
  
-   Si planea guardar el informe como archivo .PDF, el ancho del informe debe establecerse explícitamente en un valor que proporcione los resultados que se deseen en el formato de archivo de exportación. Por ejemplo, establezca el ancho de la página del informe en 20,16 cm exactamente, y los márgenes izquierdo y derecho en 1,27 cm.  
  
-   Use **Diseño de impresión** y **Configurar página** en la barra de herramientas del visor de informes para representar un informe en una vista compatible con la impresión. Para ayudar a quitar páginas en blanco innecesarias, haga lo siguiente:  
  
    1.  Quite todo el espacio en blanco adicional entre las regiones de datos y de los bordes del informe.  
  
    2.  Reduzca los márgenes de página en el cuadro de diálogo **Propiedades del informe** .  
  
    3.  Utilice **Rectángulos** como contenedores para ayudar a controlar el medio de representación de los elementos de informe.  
  
    4.  En encabezados de columna, cambie la propiedad de cuadro de texto WritingMode de forma que se use texto vertical.  

 Para obtener más instrucciones, consulte [Eliminación de páginas en blanco al imprimir informes paginados](../guidance/report-paginated-blank-page.md).

 La combinación de este comportamiento, las propiedades de alto y ancho de los elementos de informe, el tamaño del cuerpo del informe, la definición del alto y el ancho de página, la configuración de los márgenes del informe primario, y la compatibilidad específica del representador con la paginación, en conjunto, determinan qué elementos de informe pueden estar juntos en una página representada.
 
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
