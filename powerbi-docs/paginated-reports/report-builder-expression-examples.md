---
title: Ejemplos de expresiones en el Generador de informes de Power BI
description: A menudo se usan expresiones en los informes paginados de Power BI Report Builder para controlar el aspecto y el contenido de estos.
author: maggiesMSFT
ms.author: maggies
ms.date: 11/08/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
ms.openlocfilehash: a919efad0b9656327a766986456c533242d40c2e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416333"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Ejemplos de expresiones en el Generador de informes de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

A menudo se usan expresiones en los informes paginados de Power BI Report Builder para controlar el aspecto y el contenido de estos. Las expresiones se escriben en Microsoft Visual Basic y pueden usar funciones integradas, código personalizado, variables de informe y grupo, y variables definidas por el usuario. Las expresiones comienzan con un signo igual (=).   

En este tema se incluyen ejemplos de expresiones que se pueden usar en los informes para realizar tareas comunes.  
  
-   [Funciones de Visual Basic](#VisualBasicFunctions): ejemplos de funciones de fecha, cadena, conversión y condicionales de Visual Basic.  
  
-   [Funciones de informe](#ReportFunctions) Ejemplos de agregados y otras funciones de informe integradas.  
  
-   [Apariencia de los datos del informe](#AppearanceofReportData) : ejemplos relacionados con el cambio de apariencia de un informe.  
  
-   [Propiedades](#Properties) : ejemplos para establecer las propiedades de elementos de informe a fin de controlar el formato o la visibilidad.  
  
-   [Parámetros](#Parameters) : ejemplos relacionados con el uso de parámetros en una expresión.  
  
-   [Código personalizado](#CustomCode) : ejemplos de código personalizado incrustado.  
  
Para más información sobre las expresiones simples y complejas, dónde se pueden usar las expresiones y los tipos de referencias que se pueden incluir en una expresión, consulte los temas incluidos en [Expressions in Power BI Report Builder](report-builder-expressions.md) (Expresiones en el Generador de informes de Power BI). 
  
## <a name="functions"></a>Functions  
 Muchas expresiones de un informe contienen funciones. Con estas funciones, se puede dar formato a los datos, aplicar lógica y obtener acceso a los metadatos del informe. Puede escribir expresiones que usen funciones de la biblioteca en tiempo de ejecución de Microsoft Visual Basic y de los espacios de nombres `xref:System.Convert` y `xref:System.Math`. Puede agregar referencias a funciones en el código personalizado. También puede usar las clases de Microsoft .NET Framework, incluida `xref:System.Text.RegularExpressions`.  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Funciones de Visual Basic  
 Puede usar funciones de Visual Basic para manipular los datos que se muestran en los cuadros de texto o que se utilizan para los parámetros, las propiedades u otras áreas del informe. En esta sección se ofrecen ejemplos de algunas de estas funciones. Para obtener más información, vea [Miembros de la biblioteca en tiempo de ejecución de Visual Basic](/dotnet/visual-basic/language-reference/runtime-library-members) en MSDN.  
  
 .NET Framework proporciona muchas opciones de formato personalizado, por ejemplo, formatos de fecha específicos. Para obtener más información, consulte [Aplicar formato a tipos](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Funciones matemáticas  
  
-   La función **Round** es útil para redondear números al entero más cercano. La siguiente expresión redondea el valor1,3 a 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     También puede escribir una expresión para redondear un valor al múltiplo que usted especifique, de forma similar a la función **MRound** de Excel. Multiplique el valor por un factor que crea un entero, redondee el número y, a continuación, divida por el mismo factor. Por ejemplo, para redondear 1,3 al múltiplo más cercano de 0,2 (1,4), utilice la siguiente expresión:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> Funciones de fecha  
  
-   La función **Today** proporciona la fecha actual. Esta expresión puede utilizarse en un cuadro de texto para mostrar la fecha en el informe o puede utilizarse en un parámetro para filtrar los datos por la fecha actual.  
  
    ```  
    =Today()  
    ```  
  
-   Use la función **DateInterval** para extraer una parte específica de una fecha. Estos son algunos parámetros válidos de **DateInterval**:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Por ejemplo, esta expresión muestra el número de la semana del año actual del día de hoy:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   La función **DateAdd** es útil para suministrar un rango de fechas basado en un solo parámetro. La expresión siguiente proporciona una fecha que es seis meses posterior a la fecha de un parámetro denominado *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   La función **Year** muestra el año correspondiente a una fecha determinada. Puede utilizarse para agrupar las fechas o para mostrar el año como etiqueta para un conjunto de fechas. Esta expresión proporciona el año correspondiente a un determinado grupo de fechas de pedidos de venta. También es posible utilizar la función **Month** y otras funciones para manipular las fechas. Para más información, consulte la documentación sobre Visual Basic.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Puede combinar las funciones en una expresión para personalizar el formato. La siguiente expresión cambia el formato día/mes/año de una fecha a número de la semana/semana/mes. Por ejemplo, 23/12/2009 a tercera semana de diciembre:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     Cuando se utiliza como un campo calculado en un conjunto de datos, puede utilizar esta expresión en un gráfico para agregar los valores por semana dentro de cada mes.  
  
-   La siguiente expresión da formato al valor SellStartDate como MMM-AA. El campo SellStartDate es un tipo de datos de fecha y hora.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   La siguiente expresión da formato al valor SellStartDate como dd/MM/aaaa. El campo SellStartDate es un tipo de datos de fecha y hora.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   La función **CDate** convierte el valor en una fecha. La función **Now** devuelve un valor de fecha que contiene la fecha y la hora actuales del sistema. **DateDiff** devuelve un valor de tipo Long que especifica el número de intervalos de tiempo entre dos valores de fecha.  
  
     El ejemplo siguiente muestra la fecha de inicio del año en curso  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   El ejemplo siguiente muestra la fecha de inicio del mes anterior en función del mes actual.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   La siguiente expresión genera los años de intervalo entre SellStartDate y LastReceiptDate. Estos campos están en dos conjuntos de datos distintos, DataSet1 y DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   La función **DatePart** devuelve un valor entero que contiene el componente especificado de un valor de fecha determinado. La siguiente expresión devuelve el año del primer valor de SellStartDate en DataSet1. Se especifica el ámbito del conjunto de datos porque hay varios conjuntos de datos en el informe.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   La función **DateSerial** devuelve un valor de fecha que representa un año, un mes y un día especificados, con la información de hora establecida en medianoche. El ejemplo siguiente muestra la fecha final del mes anterior en función del mes actual.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Las siguientes expresiones muestran varias fechas según un valor de parámetro de fecha seleccionado por el usuario.  
  
|Descripción de ejemplo|Ejemplo|  
|-------------------------|-------------|  
|Ayer|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Hace dos días|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|Hace un mes|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Hace dos meses|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Hace un año|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Hace dos años|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> Funciones de cadena  
  
-   Combine más de un campo mediante el uso de operadores de concatenación y constantes de Visual Basic. La expresión siguiente devuelve dos campos, cada uno de ellos en una línea diferente del mismo cuadro de texto:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Aplique formato a las fechas y los números de una cadena con la función **Format** . La expresión siguiente muestra los valores de los parámetros *StartDate* y *EndDate* en formato de fecha larga:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Si el cuadro de texto solo contiene una fecha o un número, necesitará usar la propiedad Format del cuadro de texto para aplicar formato, en lugar de usar la función **Format** dentro del cuadro de texto.  
  
-   Las funciones **Right**, **Len** e **InStr** son útiles para devolver una subcadena (por ejemplo, para reducir *DOMINIO*\\*nombre_de_usuario* a solo el nombre de usuario). La siguiente expresión devuelve la parte de la cadena situada a la derecha de un carácter de barra diagonal inversa (\\) de un parámetro denominado *User*:  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     La siguiente expresión da como resultado el mismo valor que el anterior, usando los miembros de la clase `xref:System.String` de .NET Framework en lugar de funciones de Visual Basic:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Muestre los valores seleccionados en un parámetro de varios valores. En el ejemplo siguiente, se usa la función **Join** para concatenar los valores seleccionados del parámetro *MySelection* en una sola cadena que se podrá establecer como una expresión para el valor de un cuadro de texto en un elemento de informe:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     El ejemplo siguiente hace lo mismo que el ejemplo anterior, además de mostrar una cadena de texto antes de la lista de valores seleccionados.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   Las funciones **Regex** de la clase `xref:System.Text.RegularExpressions` de .NET Framework son útiles para cambiar el formato de cadenas existentes, por ejemplo, para dar formato a un número de teléfono. La expresión siguiente usa la función **Replace** para cambiar el formato de un número de teléfono de diez dígitos de un campo de "*nnn*-*nnn*-*nnnn*" a "(*nnn*) *nnn*-*nnnn*":  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Compruebe que el valor de Fields!Phone.Value no tiene espacios adicionales y es del tipo `xref:System.String`.  
  
### <a name="lookup"></a>Búsqueda  
  
-   Al especificar un campo clave, puede usar la función **Lookup** para recuperar un valor de un conjunto de datos para una relación uno a uno (por ejemplo, un par clave-valor). En la expresión siguiente se muestra el nombre de producto de un conjunto de datos ("Producto"), según el identificador de producto con el que se va a realizar la coincidencia:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Al especificar un campo clave, puede usar la función **LookupSet** para recuperar un conjunto de valores de un conjunto de datos para una relación uno a varios. Por ejemplo, una persona puede tener varios números de teléfono. En el siguiente ejemplo, suponga que el conjunto de datos PhoneList contiene un identificador de persona y un número de teléfono en cada fila. **LookupSet** devuelve una matriz de valores. La siguiente expresión combina los valores devueltos en una sola cadena y muestra la lista de números de teléfono para la persona especificada por ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> Funciones de conversión  
 Puede usar funciones de Visual Basic para convertir un campo de un tipo de datos a otro. Las funciones de conversión pueden usarse para convertir el tipo de datos predeterminado de un campo en el tipo de datos necesario para realizar cálculos o para combinar texto.  
  
-   La expresión siguiente convierte la constante 500 al tipo Decimal con el fin de compararla con un tipo de datos monetario de Transact-SQL en el campo Value de una expresión de filtro.  
  
    ```  
    =CDec(500)  
    ```  
  
-   La expresión siguiente muestra el número de valores seleccionados para el parámetro de varios valores *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> Funciones de decisión  
  
-   La función **Iif** devuelve un valor u otro en función de si la expresión es TRUE o no. En la expresión siguiente, se usa la función **Iif** para devolver el valor booleano **True** si el valor de `LineTotal` es mayor que 100. En caso contrario, devuelve **False**:  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Use varias funciones **IIF** (que también se conocen como "funciones IIF anidadas") para devolver un valor (de tres posibles) según el valor de `PctComplete`. La expresión siguiente puede situarse en el color de relleno de un cuadro de texto para cambiar el color de fondo en función del valor existente en dicho cuadro de texto.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Los valores mayores o iguales que 10 se muestran con un fondo verde, los valores entre 1 y 9 se muestran con un fondo azul, y los valores menores que 1 se muestran con un fondo rojo.  
  
-   Otra forma de obtener la misma funcionalidad es con la función **Switch** . La función **Switch** resulta de gran utilidad cuando se necesita probar tres condiciones o más. La función **Switch** devuelve el valor asociado a la primera expresión en una serie que se evalúa como TRUE:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Los valores mayores o iguales que 10 se muestran con un fondo verde, los valores entre 1 y 9 se muestran con un fondo azul, los valores iguales que 1 se muestran con un fondo amarillo, y los valores iguales o menores que 0 se muestran con un fondo rojo.  
  
-   Prueba el valor del campo `ImportantDate` y devuelve "Red" si tiene más de una semana de antigüedad o "Blue" en caso contrario. Esta expresión puede utilizarse para controlar la propiedad Color de un cuadro de texto en un elemento de informe:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Prueba el valor del campo `PhoneNumber` y devuelve "No Value" si es **null** (**Nothing** en Visual Basic); en caso contrario, devuelve un valor de número de teléfono. Esta expresión puede utilizarse para controlar el valor de un cuadro de texto en un elemento de informe.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Prueba el valor del campo `Department` y devuelve un nombre de subinforme o **null** (**Nothing** en Visual Basic). Esta expresión puede utilizarse con subinformes detallados condicionales.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Comprueba si el valor de un campo es NULL. Esta expresión puede usarse para controlar la propiedad **Hidden** de un elemento de informe de imagen. En el ejemplo siguiente, la imagen especificada por el campo [LargePhoto] solamente se muestra si el valor del campo es distinto de NULL.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   La función **MonthName** devuelve un valor de cadena que contiene el nombre del mes especificado. El ejemplo siguiente muestra NA en el campo Month si el campo contiene el valor 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> Funciones de informe  
 En una expresión, puede agregar una referencia a las funciones de informe adicionales que manipulan datos de un informe. En esta sección, se ofrecen ejemplos de dos de estas funciones. 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   La función **Sum** puede calcular el total de los valores de un grupo o de una región de datos. Esta función puede resultar útil en el encabezado o en el pie de página de un grupo. La expresión siguiente muestra la suma de los datos del grupo o de la región de datos Order:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   También puede usar la función **Sum** para calcular agregados condicionales. Por ejemplo, si un conjunto de datos tiene un campo denominado State cuyos valores posibles son Not Started, Started y Finished, la expresión siguiente, situada en un encabezado de grupo, calcula la suma de agregados solamente para el valor Finished:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   La función **RowNumber** , cuando se utiliza en un cuadro de texto de una región de datos, muestra el número de fila de cada instancia del cuadro de texto en que aparece la expresión. Esta función puede ser de utilidad para numerar las filas de una tabla. También puede resultar útil para tareas más complejas, como proporcionar saltos de página según el número de filas. Para obtener más información, vea [Saltos de página](#PageBreaks) más adelante en este tema.  
  
     El ámbito que especifique para **RowNumber** controlará cuándo comienza la nueva numeración. La palabra clave **Nothing** indica que la función empezará a contar desde la primera fila de la región de datos más externa. Para empezar a contar en regiones de datos anidadas, utilice el nombre de la región de datos. Para empezar a contar en un grupo, utilice el nombre del grupo.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> Apariencia de los datos del informe  
 Pueden utilizarse expresiones para manipular la apariencia de los datos en el informe. Por ejemplo, se pueden mostrar los valores de dos campos en un solo cuadro de texto, se puede mostrar información acerca del informe o se puede influir en el modo en que se insertan los saltos de página en el informe.  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> Encabezados y pies de página  
 Cuando se diseña un informe, existe la posibilidad de mostrar el nombre del informe y el número de página en el pie del informe. Para ello, se utilizan las siguientes expresiones:  
  
-   La siguiente expresión proporciona el nombre del informe y la hora a la que se ejecutó. Puede colocarse en un cuadro de texto en el pie de página o en el cuerpo del informe. La fecha y hora se presenta con el formato de fecha corta de .NET Framework:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   La siguiente expresión, situada en un cuadro de texto en el pie de página de un informe, devuelve el número de página y el total de páginas del informe:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 En los ejemplos siguientes, se indica cómo mostrar el primer y el último valor de una página en el encabezado de página, de manera similar a lo que aparece en una lista de directorios. En el ejemplo se supone que existe una región de datos que contiene un cuadro de texto denominado `LastName`.  
  
-   La siguiente expresión, situada en un cuadro de texto a la izquierda del encabezado de página, proporciona el primer valor del cuadro de texto `LastName` en la página:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   La expresión siguiente, situada en un cuadro de texto a la derecha del encabezado de página, proporciona el último valor del cuadro de texto `LastName` de la página:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 En el ejemplo siguiente, se indica cómo incluir un total para la página. En el ejemplo se supone que existe una región de datos que contiene un cuadro de texto denominado `Cost`.  
  
-   La siguiente expresión, situada en el encabezado o pie de página, proporciona la suma de los valores del cuadro de texto `Cost` para la página:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Solamente puede hacerse referencia a un elemento de informe por expresión en un encabezado o pie de página. Asimismo, puede hacer referencia al nombre del cuadro de texto, pero no a la expresión de datos real del cuadro de texto, en expresiones de encabezado y de pie de página.  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> Saltos de página  
 Es posible que en algunos informes se desee insertar un salto de página al final de un número de filas determinado, en lugar de (o además de) en los grupos o elementos de informe. Para ello, cree un grupo que contenga los grupos o registros de detalle que desee, agregue un salto de página al grupo y, a continuación, agregue una expresión de grupo para agrupar por un número concreto de filas.  
  
-   Si se coloca la expresión siguiente en la expresión de grupo, se asigna un número a cada conjunto de 25 filas. Cuando se define un salto de página para el grupo, el resultado de la expresión es un salto de página cada 25 filas.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Para permitir al usuario establecer un valor para el número de filas por página, cree un parámetro denominado `RowsPerPage` y base la expresión de grupo en dicho parámetro, tal y como se muestra en la expresión siguiente:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> Propiedades  
 Las expresiones no se utilizan únicamente para mostrar datos en cuadros de texto. También se pueden utilizar para cambiar el modo en que se aplican las propiedades a los elementos de informe. Es posible cambiar la información de estilo de un elemento de informe o modificar su visibilidad.  
  
###  <a name="formatting"></a><a name="Formatting"></a> Formato  
  
-   La expresión siguiente, cuando se usa en la propiedad Color de un cuadro de texto, cambia el color del texto según el valor del campo `Profit` :  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     También puede usar la variable de objeto de Visual Basic `Me`. Esta variable es otra manera de hacer referencia al valor de un cuadro de texto.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   La siguiente expresión, cuando se usa en la propiedad BackgroundColor de un elemento de informe en una región de datos, cambia el color de fondo de cada fila entre verde pálido y blanco:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Si se utiliza una expresión para un ámbito determinado, puede que sea necesario indicar el conjunto de datos para la función de agregado:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Los colores disponibles son los de la enumeración KnownColor de .NET Framework.  
  
### <a name="chart-colors"></a>Colores de gráfico  
 Para especificar los colores de un gráfico de formas, puede usar código personalizado que le permita controlar el orden en que los colores se asignan a los valores de los puntos de datos. Esto le permitirá usar colores coherentes para varios gráficos que tienen los mismos grupos de categorías. 
  
###  <a name="visibility"></a><a name="Visibility"></a> Visibilidad  
 Es posible mostrar y ocultar los elementos de un informe mediante las propiedades de visibilidad del elemento de informe. En una región de datos, como una tabla, se pueden ocultar inicialmente las filas de detalles basándose en el valor de una expresión.  
  
-   La expresión siguiente, cuando se utiliza para la visibilidad inicial de las filas de detalles de un grupo, muestra las filas de detalles de todas las ventas que superen el 90 por ciento en el campo `PctQuota` :  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   La expresión siguiente, cuando se establece en la propiedad Hidden de una tabla, muestra la tabla solo si tiene más de 12 filas:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   La expresión siguiente, cuando se establece en la propiedad **Hidden** de una columna, muestra la columna solo si el campo existe en el conjunto de datos de informe después de haber recuperado los datos del origen de datos:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> direcciones URL  
 Puede personalizar direcciones URL con los datos de informe y, además, controlar de manera condicional si las dichas direcciones URL se agregan como acciones para un cuadro de texto.  
  
-   La expresión siguiente, cuando se usa como acción en un cuadro de texto, genera una dirección URL personalizada que especifica el campo `EmployeeID` del conjunto de datos como parámetro de URL.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   La expresión siguiente controla de forma condicional si debe agregarse una dirección URL a un cuadro de texto. Esta expresión depende de un parámetro denominado `IncludeURLs` que permite a un usuario decidir si deben incluirse direcciones URL activas en un informe. Esta expresión se establece como acción en un cuadro de texto. Si se establece el parámetro en FALSE y, a continuación, se visualiza el informe, puede exportar el informe a Microsoft Excel sin hipervínculos.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
> [!NOTE]
>  Los informes paginados de Power BI no admiten el uso de JavaScript en una expresión **Ir a dirección URL**.  
  
##  <a name="report-data"></a><a name="ReportData"></a> Datos del informe  
 Pueden utilizarse expresiones para manipular los datos que se usan en el informe. Se puede hacer referencia a parámetros y a otra información del informe. Incluso se puede modificar la consulta que se usa para recuperar datos para el informe.  
  
###  <a name="parameters"></a><a name="Parameters"></a> Parámetros  
 Pueden utilizarse expresiones en un parámetro para modificar su valor predeterminado. Por ejemplo, puede usar un parámetro que filtre datos para un usuario determinado basándose en el identificador de usuario con el que se ejecuta el informe.  
  
-   La siguiente expresión, cuando se usa como valor predeterminado para un parámetro, obtiene el identificador de usuario de la persona que ejecuta el informe:  
  
    ```  
    =User!UserID  
    ```  
  
-   Para hacer referencia a un parámetro en un parámetro de consulta, una expresión de filtro, un cuadro de texto u otras áreas del informe, use la colección global **Parameters** . En este ejemplo se da por supuesto que el parámetro se denomina *Department*:  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Pueden crearse parámetros en un informe y establecerse como ocultos. Cuando se ejecuta el informe en el servidor de informes, el parámetro no aparece en la barra de herramientas y el lector del informe no puede cambiar el valor predeterminado. Puede usar un parámetro oculto establecido en un valor predeterminado como constante personalizada. Puede usar este valor en cualquier expresión, incluida una expresión de campo. La expresión siguiente identifica el campo especificado por el valor de parámetro predeterminado para el parámetro denominado *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> Código personalizado  
 Puede usar código personalizado insertado en un informe. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Uso de variables de grupo para la agregación personalizada  
 Puede inicializar el valor de una variable de grupo local en un ámbito de grupo determinado y, a continuación, incluir una referencia a esa variable en expresiones. Una forma de usar una variable de grupo con código personalizado es implementar un agregado personalizado. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Supresión de valores null o cero en tiempo de ejecución  
 Algunos valores de una expresión pueden evaluarse como NULL o como indefinidos durante el procesamiento del informe. Esto puede provocar errores en tiempo de ejecución que hacen que en el cuadro de texto se muestre **#Error** en lugar de la expresión evaluada. La función **IIF** es especialmente sensible a este comportamiento porque, a diferencia de lo que ocurre en una instrucción If-Then-Else, se evalúa cada una de las partes de la instrucción **IIF** (incluidas las llamadas a función) antes de que se pasen a la rutina que comprueba si es **verdadera** o **falsa**. La instrucción `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` genera **#Error** en el informe representado si el valor de `Fields!Sales.Value` es NOTHING.  
  
 Para evitar esta condición, use una de las estrategias siguientes:  
  
-   Establezca el numerador en 0 y el denominador en 1 si el valor del campo B es 0 o un valor no definido; en caso contrario, establezca el numerador en el valor del campo A y el denominador en el valor del campo B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Use una función de código personalizado para devolver el valor de la expresión. En el ejemplo siguiente, se devuelve la diferencia porcentual entre un valor actual y un valor anterior. Esto puede usarse para calcular la diferencia entre dos valores consecutivos cualesquiera y controla el caso límite de la primera comparación (cuando no hay ningún valor anterior) y los casos en los que el valor anterior o el valor actual es **null** (**Nothing** en Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     En la expresión siguiente se muestra cómo llamar a este código personalizado desde un cuadro de texto, para el contenedor "ColumnGroupByYear" (grupo o región de datos).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Esto ayuda a evitar excepciones en tiempo de ejecución. Ahora puede usar una expresión como `=IIF(Me.Value < 0, "red", "black")` en la propiedad **Color** del cuadro de texto para mostrar de forma condicional el texto según si los valores son mayores o menores que 0.  
  
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
