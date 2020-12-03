---
title: Aspectos básicos de DAX en Power BI Desktop
description: Aspectos básicos de DAX en Power BI Desktop
author: Minewiskan
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 10/21/2019
LocalizationGroup: Model your data
ms.openlocfilehash: 522dccb6f4e6e3cf3422bc85ba9727c9160d9d80
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413849"
---
# <a name="apply-dax-basics-in-power-bi-desktop"></a>Aplicación de los aspectos básicos de DAX en Power BI Desktop
Este artículo está destinado a usuarios sin experiencia en Power BI Desktop. Le proporciona una introducción rápida y fácil al uso de expresiones de análisis de datos (DAX) para solucionar una variedad de problemas de análisis de datos y cálculo básico. Abordaremos información conceptual, una serie de tareas que puede completar y una prueba de conocimientos para probar lo que ha aprendido. Al finalizar este artículo, debe tener una buena comprensión de los conceptos fundamentales más importantes en DAX.

## <a name="what-is-dax"></a>¿Qué es DAX?
DAX es una colección de funciones, operadores y constantes que se pueden usar en una fórmula o expresión, para calcular y devolver uno o más valores. En pocas palabras, DAX le ayuda a crear información nueva a partir de datos ya incluidos en un modelo.

## <a name="why-is-dax-so-important"></a>¿Por qué es tan importante DAX?
Crear un archivo de Power BI Desktop nuevo e importar algunos datos en él es fácil. Incluso puede crear informes que muestren información valiosa sin usar las fórmulas DAX en absoluto. Pero, ¿qué ocurre si necesita analizar el porcentaje de crecimiento por categorías de producto y para intervalos de fechas diferentes? ¿O bien, si debe calcular el crecimiento interanual en comparación con las tendencias del mercado? Las fórmulas DAX proporcionan esta y muchas otras capacidades igual de importantes. Obtener información sobre cómo crear fórmulas DAX eficaces le ayudará a aprovechar los datos al máximo. Cuando obtiene la información que necesita, puede empezar a resolver problemas empresariales reales que afectan los resultados finales. Ese es el potencial de Power BI y DAX le ayuda a alcanzarlo.

## <a name="prerequisites"></a>Requisitos previos
Posiblemente ya esté familiarizado con la creación de fórmulas en Microsoft Excel. Esa información será útil para comprender DAX, pero incluso si no tiene ninguna experiencia con las fórmulas de Excel, los conceptos descritos aquí le ayudarán a empezar a crear fórmulas de DAX y solucionar problemas de inteligencia empresarial del mundo real inmediatamente.

Nos centraremos en comprender las fórmulas DAX que se usan en los cálculos, más específicamente, en columnas calculadas y medidas. Debe estar familiarizado con el uso de Power BI Desktop para importar datos y agregar campos a un informe. También debe estar familiarizado con los conceptos fundamentales de [medidas](desktop-measures.md) y [columnas calculadas](desktop-calculated-columns.md).

### <a name="example-workbook"></a>Libro de Excel

La mejor manera de aprender a usar DAX es crear algunas fórmulas básicas, usarlas con datos reales y comprobar los resultados con sus propios ojos. Los ejemplos y tareas que se exponen aquí utilizan el [archivo de ventas de muestra de Contoso para Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip). Este es el mismo archivo de ejemplo que se utilizó en el artículo [Tutorial: Crear medidas propias en Power BI Desktop](desktop-tutorial-create-measures.md). 

## <a name="lets-begin"></a>¡Comencemos!
Centraremos nuestro estudio de DAX en torno a tres conceptos fundamentales: *sintaxis*, *funciones* y *contexto*. Hay otros conceptos importantes en DAX, pero la comprensión de estos tres conceptos le proporcionará una base óptima para desarrollar sus habilidades de DAX.

### <a name="syntax"></a>Sintaxis
Antes de crear sus propias fórmulas, echemos un vistazo a la sintaxis de las fórmulas DAX. La sintaxis incluye los distintos elementos que componen una fórmula, o en términos más simples, cómo se escribe la fórmula. Por ejemplo, aquí tiene una fórmula DAX simple para una medida:

![Sintaxis de fórmulas DAX](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Esta fórmula incluye los siguientes elementos de sintaxis:

**A.** El nombre de medida **Total Sales**.

**B.** El operador signo igual ( **=** ) que indica el principio de la fórmula. Al calcular, devolverá un resultado.

**C.** La función DAX **SUM** que suma todos los números en la columna **Sales[SalesAmount]** . Aprenderá más acerca de las funciones más adelante.

**D.** Los paréntesis **()** que rodean una expresión que contiene uno o varios argumentos. Todas las funciones requieren al menos un argumento. Un argumento pasa un valor a una función.

**E.** La tabla de referencia **Sales**.

**F.** La columna de referencia **[SalesAmount]** en la tabla Sales. Con este argumento, la función SUM detecta en qué columna se agrega una suma.

Al tratar de comprender una fórmula DAX, a menudo resulta útil descomponer cada uno de los elementos en un lenguaje común. Por ejemplo, puede leer esta fórmula como:

> *Para la medida denominada Total Sales, calcular (=) la SUMA de los valores de la columna [SalesAmount] en la tabla Sales.*
> 
> 

Cuando se agrega a un informe, esta medida calcula y devuelve valores que resulten de sumar los importes de las ventas de cada uno de los demás campos que se incluyen, por ejemplo, el de teléfonos móviles de Estados Unidos.

Quizás se pregunte "¿Esta medida no hace lo mismo que si simplemente agregara el campo SalesAmount a mi informe?" Bueno, sí. Pero hay una buena razón para crear nuestra propia medida que suma los valores del campo SalesAmount: podemos usarla como argumento en otras fórmulas. Esto puede parecer un poco confuso ahora, pero a medida que desarrolle sus habilidades con las fórmulas DAX, conocer esta medida hará sus fórmulas y modelos más eficientes. De hecho, verá que la medida Ventas totales aparece como argumento en otras fórmulas más adelante.

Veamos algunos otros aspectos de esta fórmula. En concreto, introdujimos una función, [SUM](/dax/sum-function-dax). Las funciones son fórmulas previamente escritas que facilitan el realizar cálculos complejos y manipulaciones con números, fechas, horas, texto y mucho más. Aprenderá más acerca de las funciones más adelante.

También puede ver que el nombre de la columna [SalesAmount] estaba precedido de la tabla Sales a la que pertenece la columna. Este nombre se conoce como un nombre de columna completo porque incluye el nombre de la columna precedido por el nombre de la tabla. Las columnas a las que se hace referencia en la misma tabla no requieren que el nombre de la tabla se incluya en la fórmula, lo que puede hacer que las fórmulas largas que hacen referencia a muchas columnas sean más cortas y fáciles de leer. Sin embargo, es recomendable incluir el nombre de la tabla en las fórmulas de medida, incluso cuando estén en la misma tabla.

> [!NOTE]
> Si un nombre de tabla contiene espacios, palabras clave reservadas o caracteres no permitidos, deberá incluir el nombre de la tabla entre comillas simples. También deberá escribir los nombres de tabla entre comillas si el nombre contiene algún carácter fuera del rango de caracteres alfanuméricos ANSI, independientemente de si la configuración regional es compatible con el conjunto de caracteres o no.
> 
> 

Es importante que las fórmulas tengan la sintaxis correcta. En la mayoría de los casos, si la sintaxis no es correcta, se devolverá un error de sintaxis. En otros casos, la sintaxis puede ser correcta, pero los valores devueltos podrían no ser los que esperaba. El editor de DAX en Power BI Desktop incluye una característica de sugerencias que lo ayuda a seleccionar los elementos correctos para crear fórmulas sintácticamente correctas.

Vamos a crear una fórmula simple. Esta tarea le ayudará a entender mejor la sintaxis de fórmulas y la utilidad de la característica de sugerencias en la barra de fórmulas.

### <a name="task-create-a-measure-formula"></a>Tarea: Crear una fórmula de medida

1. [Descargue](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) y abra el archivo de muestra de ventas de Contoso de Power BI Desktop. 
    
2. En la vista Informes, en la lista de campos, haga clic con el botón derecho en la tabla **Sales** y, a continuación, seleccione **Nueva medida**.
    
3. En la barra de fórmulas, reemplace **Medida** con un nuevo nombre de medida: *Ventas del trimestre anterior*.
    
4. Después del signo igual, escriba las primeras letras *CAL* y luego haga doble clic en la función que quiere usar. En esta fórmula, se quiere usar la función **CALCULATE**.

   Usará la función CALCULATE para filtrar los importes que deseamos sumar mediante un argumento que pasamos a la función CALCULATE. Esto es lo que se conoce como funciones anidadas. La función CALCULATE tiene al menos dos argumentos. El primero es la expresión que se evalúa; el segundo, un filtro.
   
5. Después del paréntesis de apertura *(* para la función **CALCULATE**, escriba *SUM* seguido por otro paréntesis de apertura *(* . 

   A continuación, vamos a pasar un argumento a la función SUM.

6. Comience a escribir *Sal* y luego seleccione **Sales[SalesAmount]** , seguido de un paréntesis de cierre *)* . 

   Este es el primer argumento de expresión de nuestra función CALCULATE.
    
7. Escriba una coma ( *,* ) seguida de un espacio para especificar el primer filtro y luego escriba *PREVIOUSQUARTER*. 
    
   Se usará la función de inteligencia de tiempo PREVIOUSQUARTER para filtrar los resultados de SUM por el trimestre anterior.
    
8. Después del paréntesis de apertura *(* para la función PREVIOUSQUARTER, escriba *Calendar[DateKey]* .
    
   La función PREVIOUSQUARTER tiene un argumento, una columna que contiene un intervalo de fechas contiguas. En este caso, es la columna DateKey de la tabla Calendar.
    
9. Cierre los dos argumentos que se pasan a la función PREVIOUSQUARTER y la función CALCULATE mediante dos paréntesis de cierre *))* .
    
   La fórmula debe tener el siguiente aspecto:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. Seleccione la marca de verificación ![Icono de marca de verificación](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) en la barra de fórmulas o presione Entrar para validar la fórmula y agregarla al modelo.

¡Lo logró! Acaba de crear una medida compleja mediante DAX (¡y no una de las fáciles!). Lo que hará esta fórmula es calcular el total de ventas del trimestre anterior, según los filtros aplicados en un informe. Por ejemplo, si incluimos SalesAmount y nuestra nueva medida de ventas del trimestre anterior en un gráfico y, a continuación, agregamos Year y QuarterOfYear como segmentaciones de datos, obtendríamos algo parecido a esto:

![Gráfico Ventas del trimestre anterior y SalesAmount](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Le acabamos de presentar varios aspectos importantes de las fórmulas DAX: 

- Esta fórmula incluye dos funciones. [PREVIOUSQUARTER](/dax/previousquarter-function-dax), una función de inteligencia de tiempo, se anida como un argumento pasado a la función de filtro [CALCULATE](/dax/calculate-function-dax). 

   Las fórmulas DAX pueden contener hasta 64 funciones anidadas. Es poco probable que una fórmula llegue a contener tantas funciones anidadas. De hecho, una fórmula así sería difícil de crear y depurar, y probablemente tampoco sería muy rápida.

- En esta fórmula, también usó filtros. Los filtros limitan lo que se calculará. En este caso, se seleccionó un filtro como argumento, que es, de hecho, el resultado de otra función. Aprenderá más acerca de los filtros más adelante.

- Usó la función CALCULATE. Esta función es una de las funciones más potentes de DAX. A medida que cree modelos y fórmulas más complejas, seguramente volverá a usar esta función muchas veces. Aunque un análisis más detallado de la función CALCULATE está fuera del ámbito de este artículo, le recomendamos prestar especial atención a esta función conforme aumente sus conocimientos de DAX.

### <a name="syntax-quickquiz"></a>Cuestionario rápido sobre sintaxis
1. ¿Qué hace este botón de la barra de fórmulas?
   
   > ![Selección de botón](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. ¿Qué rodea siempre a un nombre de columna en una fórmula DAX?

Encontrará las respuestas al final de este artículo.

### <a name="functions"></a>Funciones
Las funciones son fórmulas predefinidas que realizan cálculos por medio de valores específicos, denominados argumentos, en un orden o estructura determinados. Los argumentos pueden ser otras funciones, otra fórmula, una expresión, referencias de columna, números, texto, valores lógicos como TRUE o FALSE, o constantes.

DAX incluye las siguientes funciones de funciones: [Fecha y hora](/dax/date-and-time-functions-dax), [Inteligencia de tiempo](/dax/time-intelligence-functions-dax), [Información](/dax/information-functions-dax), [Lógicas](/dax/logical-functions-dax), [Matemáticas](/dax/math-and-trig-functions-dax), [Estadísticas](/dax/statistical-functions-dax), [Texto](/dax/text-functions-dax), [Primarias/Secundarias](/dax/parent-and-child-functions-dax) y [Otras](/dax/other-functions-dax). Si está familiarizado con las funciones en las fórmulas de Excel, muchas de las funciones DAX le parecerán semejantes; sin embargo, las funciones DAX son únicas de las maneras siguientes:

* Una función DAX siempre hace referencia a una columna o tabla completa. Si desea usar solo determinados valores de una tabla o columna, puede agregar filtros a la fórmula.
* Si necesita personalizar los cálculos fila por fila, DAX ofrece funciones para usar el valor de la fila actual o un valor relacionado como un tipo de argumento, lo que permite realizar cálculos que varían según el contexto. Aprenderá más acerca del contexto más adelante.
* DAX incluye muchas funciones que devuelven una tabla en lugar de un valor. La tabla no se muestra, pero se usa para proporcionar datos para otras funciones. Por ejemplo, puede recuperar una tabla y después contar los diferentes valores que contenga o calcular sumas dinámicas en tablas o columnas filtradas.
* DAX incluye una variedad de funciones de inteligencia de tiempo. Estas funciones permiten definir o seleccionar intervalos de fechas y realizar cálculos dinámicos con base en ellos. Por ejemplo, puede comparar sumas de períodos paralelos.
* Excel tiene una función popular, BUSCARV. Las funciones DAX no toman una celda o rango de celdas como una referencia como BUSCARV en Excel. Las funciones DAX toman una columna o una tabla como referencia. Tenga en cuenta que, en Power BI Desktop, está trabajando con un modelo de datos relacionales. Buscar valores en otra tabla es fácil y en la mayoría de los casos no es necesario crear ninguna fórmula.
  
  Como puede ver, las funciones de DAX pueden ayudarle a crear fórmulas eficaces. En realidad, solo hemos tratado los conceptos básicos de las funciones. A medida que desarrolle sus habilidades de DAX, podrá crear fórmulas con muchas funciones diferentes. Uno de los mejores lugares para obtener información detallada sobre cada una de las funciones de DAX es la [referencia de funciones de DAX](/dax/).

### <a name="functions-quickquiz"></a>Cuestionario rápido sobre funciones
1. Una función siempre hace referencia a...
2. ¿Puede una fórmula contener más de una función?
3. ¿Qué categoría de funciones usaría para concatenar dos cadenas de texto en una sola cadena?

Encontrará las respuestas al final de este artículo.

### <a name="context"></a>Contexto
El contexto es uno de los conceptos de DAX más importantes. Hay dos tipos de contexto en DAX: contexto de fila y contexto de filtro. En primer lugar, examinaremos el contexto de fila.

**Contexto de fila**

Es más fácil pensar en el contexto de fila como la fila actual. Se aplica siempre que una fórmula tiene una función use filtros para identificar una fila individual en una tabla. De manera inherente, la función aplicará un contexto de fila para cada fila de la tabla que está filtrando. Este tipo de contexto de fila se aplica con mayor frecuencia en medidas.

**Contexto de filtro**

El contexto de filtro es un poco más difícil de entender que el contexto de fila. Para simplificarlo, piense en el contexto de filtro como uno o varios filtros aplicados en un cálculo que determina un resultado o valor.

El contexto de filtro no existe en lugar del contexto de fila; más bien, se aplica además del contexto de fila. Por ejemplo, para restringir aún más los valores que quiera incluir en un cálculo, puede aplicar un contexto de filtro que no solo especifique el contexto de fila, sino que también especifique un valor determinado (filtro) en ese contexto de fila.

El contexto de filtro se puede identificar fácilmente en los informes. Por ejemplo, cuando agrega el costo total a una visualización y, a continuación, el año y región, define un contexto de filtro que selecciona un subconjunto de datos basándose en un año y región determinados.

¿Por qué es tan importante para DAX el contexto de filtro? Porque aunque el contexto de filtro se puede aplicar más fácilmente agregando campos a una visualización, también puede aplicarse en una fórmula DAX al definir un filtro mediante funciones como ALL, RELATED, FILTER, CALCULATE, por relaciones, así como por otras medidas y columnas. Por ejemplo, echemos un vistazo a la siguiente fórmula en una medida denominada Store Sales:

![Medida Store Sales](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

Para entender mejor esta fórmula, podemos desglosarla, similar a como podemos hacerlo otras fórmulas.

Esta fórmula incluye los siguientes elementos de sintaxis:

**A.** El nombre de medida, **Store Sales**.

**B.** El operador signo igual ( **=** ) que indica el principio de la fórmula.

**C.** La función **CALCULATE**, que evalúa una expresión, como argumento, en un contexto modificado por los filtros especificados.

**D.** Los paréntesis **()** que envuelven una expresión que contiene uno o más argumentos.

**E.** Una medida **[Total Sales]** en la misma tabla como una expresión. La medida Total Sales tiene la fórmula: =SUM(Sales[SalesAmount]).

**F.** Una coma ( **,** ), que separa el primer argumento de expresión del argumento de filtro.

**G.** La columna completa a la que se hace referencia, **Channel[ChannelName]** . Se trata de nuestro contexto de fila. Cada fila de esta columna especifica un canal como Store, Online, etc.

**H.** El valor concreto **Store** como filtro. Este es el contexto de filtro.

Esta fórmula garantiza que únicamente se calculen los valores de ventas definidos por la medida Total Sales y solamente para las filas de la columna Channel[ChannelName] con el valor *Store* utilizado como filtro.

Como puede imaginar, la posibilidad de definir el contexto de filtro dentro de una fórmula ofrece grandes y potentes capacidades. La capacidad de hacer referencia solamente a un valor determinado en una tabla relacionada es solo un ejemplo. No se preocupe si no comprende por completo el concepto de contexto inmediatamente. A medida que cree sus propias fórmulas, comprenderá mejor el contexto y por qué es tan importante en DAX.

### <a name="context-quickquiz"></a>Cuestionario rápido sobre el contexto
1. ¿Cuáles son los dos tipos de contexto?
2. ¿Qué es el contexto de filtro?
3. ¿Qué es el contexto de fila?

Encontrará las respuestas al final de este artículo.

## <a name="summary"></a>Resumen
Ahora que tiene conocimientos básicos de los conceptos más importantes en DAX, puede empezar a crear fórmulas DAX para medidas por su cuenta. En efecto, las expresiones DAX pueden ser un poco complicadas de aprender, pero hay muchos recursos a su disposición. Después de leer este artículo y experimentar con algunas de fórmulas propias, puede obtener más información acerca de otros conceptos y fórmulas de DAX que le ayudarán a solucionar sus problemas de negocios. Existen muchos recursos de DAX disponibles; el más importante es la [Referencia de expresiones de análisis de datos (DAX)](/dax/).

DAX se usa desde hace varios años en otras herramientas de Microsoft BI, como los modelos tabulares de Power Pivot y Analysis Services, por lo que hay una gran cantidad de información disponible. Puede encontrar más información en libros, notas de producto y blogs tanto de Microsoft como de profesionales líderes de BI. El [Wiki del Centro de recursos de DAX de TechNet](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) también es un excelente punto de partida.

### <a name="quickquiz-answers"></a>Respuestas de los cuestionarios rápidos
Sintaxis:

1. Valida e introduce la medida en el modelo.
2. Corchetes [].

Funciones:

1. Una tabla y una columna.
2. Sí. Una fórmula puede contener hasta 64 funciones anidadas.
3. [Funciones de texto](/dax/text-functions-dax).

Contexto:

1. Contexto de fila y contexto de filtro.
2. Uno o más filtros en un cálculo que determina un valor único.
3. La fila actual.
