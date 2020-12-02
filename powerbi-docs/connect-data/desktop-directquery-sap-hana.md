---
title: DirectQuery para SAP HANA en Power BI
description: Consideraciones importantes al utilizar DirectQuery con SAP HANA
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/10/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: f6cb4fa1ee35754d8ffe468ddb845089f26045a9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411181"
---
# <a name="connect-to-sap-hana-data-sources-by-using-directquery-in-power-bi"></a>Conexión a orígenes de datos SAP HANA mediante DirectQuery en Power BI
Puede conectarse a los orígenes de datos de **SAP HANA** directamente mediante **DirectQuery**. Hay dos opciones para conectarse a SAP HANA:

* **Tratar SAP HANA como un origen multidimensional (opción predeterminada):**  En este caso, el comportamiento es similar a cuando Power BI se conecta a otros orígenes multidimensionales, como SAP Business Warehouse o Analysis Services. Al conectarse a SAP HANA con esta configuración, se selecciona una única vista de análisis o cálculo, y todas las medidas, jerarquías y atributos de esa vista estarán disponibles en la lista de campos. A medida que se creen objetos visuales, los datos agregados se recuperarán siempre de SAP HANA. Este método, que es el recomendado, es el método predeterminado para los informes nuevos de DirectQuery en SAP HANA.

* **Tratar SAP HANA como origen relacional:** en este caso, Power BI trata SAP HANA como un origen relacional. Este escenario ofrece una mayor flexibilidad. Sin embargo, es necesario tener cuidado con este enfoque para garantizar que las medidas se agregan del modo esperado y para evitar problemas de rendimiento.

El enfoque de conexión viene determinado por una opción de herramienta global, que se configura al seleccionar **Archivo > Opciones y configuración** y **Opciones > DirectQuery**, y luego la opción **Tratar SAP HANA como origen relacional**, como se ve en la imagen siguiente. 

![Captura de pantalla del cuadro de diálogo Opciones, en el que se muestran las opciones de DirectQuery.](media/desktop-directquery-sap-hana/directquery-sap-hana_01a.png)

La opción para tratar SAP HANA como un origen relacional controla el método usado para todos los informes *nuevos* que usen DirectQuery en SAP HANA. No surte efecto en las conexiones de SAP HANA existentes en el informe actual ni en las conexiones de otros informes que estén abiertas. Por tanto, si la opción está actualmente desactivada, al agregar una nueva conexión a SAP HANA mediante la opción **Obtener datos**, esta se establecerá tratando SAP HANA como origen multidimensional. Sin embargo, si se abre un informe diferente que también se conecta a SAP HANA, ese informe seguirá comportándose de acuerdo con la opción que se estableció *en el momento de creación*, lo que significa que los informes que se conectan a SAP HANA creados antes de febrero de 2018 seguirá tratando a SAP HANA como un origen relacional. 

Los dos enfoques tienen comportamientos muy diferentes, y no es posible cambiar un informe ya creado de un enfoque a otro. 

Fijémonos con más detalle en cada uno de estos enfoques (primero uno y luego el otro).

## <a name="treat-sap-hana-as-a-multi-dimensional-source-default"></a>Tratar SAP HANA como un origen multidimensional (opción predeterminada)

Todas las conexiones nuevas establecidas con SAP HANA usan este método de conexión de forma predeterminada, tratando SAP HANA como un origen multidimensional. Si quiere tratar una conexión con SAP HANA como origen relacional, debe seleccionar **Archivo > Opciones y configuración > Opciones** y, después, activar la casilla situada debajo de **DirectQuery > Tratar SAP HANA como origen relacional**. Mientras esta característica esté en **versión preliminar**, los informes creados con el enfoque multidimensional *no* se podrán publicar en el servicio Power BI. Si lo hace, se producirán errores al abrir el informe dentro del servicio Power BI.  

Al conectarse a SAP HANA como origen multidimensional, es necesario considerar lo siguiente:

* En **Get Data Navigator** (Obtener navegador de datos), se puede seleccionar una sola vista de SAP HANA. No es posible seleccionar medidas o atributos individuales. No hay ninguna consulta definida en el momento de la conexión, lo cual es diferente de la importación de datos o el uso de DirectQuery cuando se trata SAP HANA como origen relacional. Esto también significa que no es posible usar directamente una consulta SQL de SAP HANA al seleccionar este método de conexión.

* Todas las medidas, jerarquías y atributos de la vista seleccionada se mostrarán en la lista de campos. 

* Siempre que se use una medida en un elemento visual, se consultará a SAP HANA para recuperar el valor de medida al nivel de agregación necesario para el objeto visual. Así pues, cuando trate con medidas que no sean de adición (contadores, relaciones etc.), SAP HANA se ocupará de todas las agregaciones, y Power BI ya no realizará ninguna. 

* Para garantizar que siempre puedan obtenerse de SAP HANA los valores de agregado correctos, deben imponerse ciertas restricciones. Por ejemplo, no es posible agregar columnas calculadas ni combinar datos de varias vistas de SAP HANA dentro del mismo informe. 

El tratamiento de SAP HANA como un origen multidimensional no ofrece la mayor flexibilidad proporcionada por el enfoque *relacional* alternativo, pero es más sencillo y garantiza los valores agregados correctos cuando se trata con medidas SAP HANA más complejas, y por lo general ofrece un mejor rendimiento. 

La lista **Campo** incluirá todas las medidas, atributos y jerarquías de la vista de SAP HANA. Tenga en cuenta que se encontrará con los siguientes comportamientos al usar este método de conexión:

* De forma predeterminada, se ocultará cualquier atributo incluido en al menos una jerarquía. Sin embargo, se pueden ver si fuera necesario seleccionando **Ver ocultos** en el menú contextual de la lista de campos. Es posible hacerlos visibles en el mismo menú contextual, en caso de que fuera necesario.

* En SAP HANA se puede definir un atributo para que use otro atributo como etiqueta. Por ejemplo, **Producto** (con valores 1, 2, 3, etc.) podría usar **ProductName** (con los valores Bicicleta, Camisa, Guantes, etc.) como etiqueta. En este caso, aparecería un solo campo **Producto** en la lista de campos, cuyos valores serán las etiquetas Bicicleta, Camisa, Guantes, etc., pero aparecerán ordenados por los valores clave 1, 2, 3, que determinarán también su carácter único. Se creará también una columna oculta **Clave.Producto**, que permite el acceso a los valores de clave subyacentes si fuera necesario. 

Las variables definidas en la vista de SAP HANA subyacente se mostrarán en el momento de la conexión y se podrán introducir los valores necesarios. Dichos valores se pueden cambiar posteriormente seleccionando **Editar consultas** en la cinta de opciones y, luego, **Administrar parámetros** en el menú desplegable que aparece. 

Las operaciones de modelado permitidas son más restrictivas que en el caso general al usar DirectQuery, dada la necesidad de comprobar que siempre pueden obtenerse los datos agregados correctos de SAP HANA. Sin embargo, resulta todavía posible realizar muchas adiciones y cambios, como definir medidas, cambiar el nombre y ocultar campos, así como definir los formatos de presentación. Todos esos cambios se conservarán en la actualización y se aplicarán los cambios que no planteen conflictos realizados en la vista de SAP HANA. 

### <a name="additional-modeling-restrictions"></a>Restricciones de modelado adicionales

Las restricciones de modelado adicionales principales al conectarse a SAP HANA mediante DirectQuery (tratado como origen multidimensional) son las siguientes: 

* **No se admiten las columnas calculadas:** la capacidad para crear columnas calculadas está deshabilitada. Esto también significa que tanto la agrupación como la agrupación en clústeres, que crean columnas calculadas, no están disponibles.
* **Limitaciones adicionales para las medidas:** se han impuesto limitaciones adicionales en las expresiones de DAX que pueden usarse en las medidas, para reflejar el nivel de compatibilidad que ofrece SAP HANA.
* **No se admite la definición de relaciones:** solo puede consultarse una vista única dentro de un informe y, por lo tanto, no se admite la definición de relaciones.
* **Sin vista de datos:** la **vista de datos** normalmente muestra los datos del nivel de detalle en las tablas. Dada la naturaleza de los orígenes de OLAP como SAP HANA, esta vista no está disponible a través de SAP HANA.
* **Los detalles de las columnas y medidas son fijos:** la lista de columnas y medidas que se ve en la lista de campos la fija el origen subyacente y no se puede modificar. Por ejemplo, no se puede eliminar una columna, ni cambiar su tipo de datos (sin embargo, se puede cambiar su nombre).
* **Limitaciones adicionales en DAX:** hay limitaciones adicionales sobre la DAX que se pueden usar en las definiciones de las medidas para reflejar las limitaciones en el origen. Por ejemplo, no es posible utilizar una función de agregado en una tabla.

### <a name="additional-visualization-restrictions"></a>Restricciones de visualización adicionales

Hay una serie de restricciones en los objetos visuales a la hora de conectarse a SAP HANA mediante DirectQuery (tratado como origen multidimensional): 
* **No se permite la agregación de columnas:** no es posible cambiar la agregación de una columna en un objeto visual; es siempre *No resumir*.

## <a name="treat-sap-hana-as-a-relational-source"></a>Tratar SAP HANA como origen relacional 

Al elegir la opción de conectarse a SAP HANA como un origen relacional, hay disponible cierta flexibilidad adicional. Por ejemplo, puede crear columnas calculadas, incluir datos de varias vistas de SAP HANA y crear relaciones entre las tablas resultantes. Sin embargo, al usar SAP HANA de esta manera, es importante entender ciertos aspectos de cómo se tratan las conexiones, para asegurarse de lo siguiente: 

* Los resultados son los previstos, si la vista de SAP HANA contiene medidas que no son de adición (por ejemplo, recuentos distintivos o promedios, en lugar de simples sumas).
* Las consultas resultantes son eficaces.

Resulta útil comenzar aclarar el comportamiento de un origen relacional como SQL Server, cuando la consulta definida en **Obtener datos** o en el **Editor de consultas** realiza una agregación. En el ejemplo siguiente, una consulta definida en el **Editor de consultas** devuelve el precio medio por *ProductID*.  

![Diagrama en el que se muestra una consulta definida en el Editor de consultas que devuelve el precio medio por id. de producto.](media/desktop-directquery-sap-hana/directquery-sap-hana_01.png)

Si se va a importar los datos en Power BI (frente al uso de DirectQuery), el resultado sería el siguiente:

* Los datos se importan en el nivel de agregación definido por la consulta creada en el **Editor de consultas**. Por ejemplo, el precio medio por producto. Esto da como resultado una tabla con dos columnas *ProductID* y *AveragePrice* que se pueden utilizar en los objetos visuales.
* En un objeto visual, cualquier agregación posterior (como *Suma*, *Promedio*, *Mínimo*, etc.) se realiza con los datos importados. Por ejemplo, al incluir *AveragePrice* en un objeto visual, se usará el agregado *Suma* de forma predeterminada, cuyo resultado sería la suma de *AveragePrice* de cada *ProductID*, que en este caso de ejemplo sería 13,67. Lo mismo se aplica a cualquier función de agregado alternativa (como *Mínimo*, *Promedio*, etc.) usada en el objeto visual. Por ejemplo, el *promedio* de *AveragePrice* devuelve la media de 6,66, 4 y 3, que equivale a 4,56, y no la media del *precio* de los seis registros de la tabla subyacente, que es 5,17.
  
Si se usa **DirectQuery** (sobre el mismo origen relacional) en lugar de la importación, se aplica la misma semántica y los resultados serían exactamente los mismos:  

* Si la consulta es la misma, lógicamente se presentan exactamente los mismos datos en el nivel de informes, aunque los datos no se importen realmente.

* En un objeto visual, cualquier agregación posterior (*Suma*, *Promedio*, *Mínimo*, etc.) vuelve a realizarse según la tabla lógica de la consulta. Y, una vez más, un objeto visual que contiene el *promedio* de *AveragePrice* devuelve el mismo resultado de 4,56.
  
Ahora veamos SAP HANA cuando la conexión se trata como un origen relacional. Power BI puede trabajar con las *vistas analíticas* y las *vistas de cálculo* en SAP HANA, ya que ambas opciones pueden contener medidas. Sin embargo, el enfoque en el caso de SAP HANA sigue los mismos principios descritos anteriormente en esta sección: la consulta definida en **Obtener datos** o en el **Editor de consultas** determinará los datos disponibles y, después, cualquier agregación posterior aplicada a un objeto visual se calcula con respecto a dichos datos; y lo mismo se aplica para la importación y para DirectQuery.  
No obstante, por la naturaleza de SAP HANA, la consulta definida en el cuadro de diálogo inicial **Obtener datos** o en el **Editor de consultas** siempre es una consulta de agregado y, por norma general, incluirá medidas en las que la vista de SAP HANA define la agregación real que se va a usar.

El equivalente del ejemplo de SQL Server anterior es que hay una vista de SAP HANA que contiene las medidas *ID*, *ProductID* y *DepotID*, además de medidas que incluyen *AveragePrice*, que se define en la vista como *precio promedio*.  
    
Si, en el caso de la experiencia con **Obtener datos**, las selecciones realizadas fueron **ProductID** y la medida de **AveragePrice**, entonces eso supone definir una consulta sobre la vista, en la que se solicitan dichos datos agregados (en el ejemplo anterior, a efectos de simplificación, se usa un seudocódigo de SQL que no coincide exactamente con la sintaxis de SQL para SAP HANA). Después, todas las agregaciones adicionales definidas en un objeto visual se agregan a los resultados de dicha consulta. Una vez más, como se ha descrito anteriormente para SQL Server, esto se aplica a los casos de importación y DirectQuery. En el caso de DirectQuery, la consulta de **Obtener datos** o del **Editor de consultas** se usará en una subselección dentro de una consulta única enviada a SAP HANA y, por tanto, no se da el caso realmente de que se lean todos los datos antes de realizar más agregaciones.  

Al utilizar DirectQuery sobre SAP HANA, es necesario tener en cuenta las siguientes consideraciones importantes derivadas de lo anterior:  

* Es necesario prestar atención a todas las agregaciones adicionales realizadas en objetos visuales, siempre que la medida de SAP HANA no se corresponda con una adición (por ejemplo, que no sea una simple función de *Suma*, *Mínimo* o *Máximo*).

* En **Obtener datos** o en el **Editor de consultas**, solo se deben incluir las columnas necesarias para recuperar los datos requeridos, lo que refleja que el resultado será una consulta, que debe tratarse de una consulta razonable que se pueda enviar a SAP HANA. Por ejemplo, si se seleccionaron decenas de columnas, con la idea de que podrían ser necesarias en objetos visuales posteriores, incluso en DirectQuery un simple objeto visual reflejará que la consulta de funciones agregadas usada en la subselección contendrá esas decenas de columnas, cuyo rendimiento será muy bajo por norma general.
  
Veamos un ejemplo. En el ejemplo siguiente, la selección de cinco columnas (**CalendarQuarter**, **Color**, **LastName**, **ProductLine**, **SalesOrderNumber**) en el cuadro de diálogo **Obtener datos**, junto con la medida *OrderQuantity*, supondrá que la posterior creación de un objeto visual sencillo que contiene la medida mínima de OrderQuantity dé como resultado la siguiente consulta de SQL a SAP HANA. La parte sombreada es la subselección, que contiene la consulta de **Obtener datos** / **Editor de consultas**. Si esta subselección ofrece un resultado de cardinalidad alto, entonces es probable que el rendimiento resultante de SAP HANA sea bajo.  

![Captura de pantalla de un ejemplo de consulta, en la que se muestra la consulta SQL a SAP HANA.](media/desktop-directquery-sap-hana/directquery-sap-hana_03.png)

   
Debido a este comportamiento, se recomienda limitar los elementos seleccionados en **Obtener datos** o en el **Editor de consultas** a aquellos elementos que sean necesarios, pero siempre que el resultado sea una consulta razonable para SAP HANA.  

## <a name="best-practices"></a>Procedimientos recomendados 

En ambos enfoques para conectarse a SAP HANA, las recomendaciones para utilizar DirectQuery se aplican también a SAP HANA, en particular las relacionadas con la garantía del buen rendimiento. Estas recomendaciones se describen en detalle en el artículo [Uso de DirectQuery en Power BI](desktop-directquery-about.md).
   
## <a name="limitations"></a>Limitaciones

En la lista siguiente se enumeran todas las características de SAP HANA que no son totalmente compatibles, o que se comportan de forma diferente cuando se usa Power BI. 

* **Jerarquías de elementos primarios-secundarios**: las jerarquías de elementos primarios-secundarios no serán visible en Power BI.
Esto se debe a que Power BI accede a SAP HANA por medio de la interfaz SQL, y no es posible acceder totalmente a las jerarquías de elementos primarios-secundarios a través de SQL.
* **Otros metadatos de la jerarquía**: en Power BI se muestra la estructura básica de jerarquías; sin embargo, algunos metadatos de la jerarquía (por ejemplo, el control del comportamiento de las jerarquías desiguales) no surten ningún efecto.
De nuevo, esto se debe a las limitaciones impuestas por la interfaz SQL.
* **Conexión mediante SSL**: puede conectarse mediante importación y como origen multidimensional con SSL, pero no se puede conectar a instancias de SAP HANA configuradas para usar SSL con el conector relacional.
* **Compatibilidad con vistas de atributo**: Power BI puede conectar con las vistas de análisis y cálculo, pero no puede conectar directamente con las vistas de atributo.
* **Compatibilidad con los objetos de catálogo**: Power BI no puede conectar con los objetos de catálogo.
* **Cambio en las variables después de publicar**: no se pueden cambiar los valores de las variables de SAP HANA directamente en el servicio Power BI una vez publicado el informe. 
 
## <a name="known-issues"></a>Problemas conocidos 
En la lista siguiente se describen todos los problemas conocidos al conectarse a SAP HANA (DirectQuery) con Power BI. 

* **Problema de SAP HANA al consultar los contadores y otras medidas**: se devuelven datos incorrectos de SAP HANA si se conecta a una vista de análisis y hay una medida de contador, y alguna otra medida de la relación, en el mismo objeto visual. Este tema se trata en la nota de SAP 2128928 (resultados inesperados cuando se consulta una columna calculada y un contador). En este caso, la medida de la relación será incorrecta. 

* **Varias columnas de Power BI a partir de una columna única de SAP HANA**: en algunas vistas de cálculo en las que se usa una columna de SAP HANA en más de una jerarquía, SAP HANA las expone como dos atributos separados. Esto da como resultado la creación de dos columnas en Power BI.  Estas columnas están ocultas de manera predeterminada; sin embargo, todas las consultas que implican a las jerarquías, o a las columnas directamente, se comportan según lo esperado. 
 
## <a name="next-steps"></a>Pasos siguientes

Para más información acerca de DirectQuery, revise los siguientes recursos:

* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](power-bi-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [Puerta de enlace de datos local](service-gateway-onprem.md)
