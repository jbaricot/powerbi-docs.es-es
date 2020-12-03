---
title: Vista previa de los informes en el Generador de informes de Power BI
description: Mientras se crea un informe paginado del Generador de informes, puede resultar útil obtener una vista previa del informe con frecuencia para comprobar que muestra lo que desea.
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
ms.openlocfilehash: d982174d814b3f1042e02dc9beda762848c48086
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416218"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Vista previa de los informes en el Generador de informes de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Mientras se crea un informe paginado del Generador de informes, puede resultar útil obtener una vista previa del informe con frecuencia para comprobar que muestra lo que desea. Para obtener una vista previa de un informe, haga clic en **Ejecutar**. El informe se representa en el modo de vista previa.  
  
 El Generador de informes mejora la experiencia de vista previa utilizando sesiones de edición cuando se conecta a un servidor de informes. La sesión de edición crea una memoria caché de datos y hace que los conjuntos de datos de la memoria caché estén disponibles para las diferentes vistas previas del informe. Una sesión de edición no es una característica con la que se interactúe directamente, pero saber cuándo se actualiza el conjunto de datos almacenado en memoria caché le ayudará a mejorar el rendimiento al obtener una vista previa de un informe y saber por qué el informe se representa con más rapidez o lentitud.  

  
> [!NOTE]  
> Hay algunas diferencias entre una vista previa en el Generador de informes y la vista en un explorador. Por ejemplo, un control de calendario, que se agrega a un informe cuando se especifica un parámetro de tipo Fecha y hora, es diferente en el Generador de informes y en un explorador. 
  
## <a name="improving-preview-performance"></a>Mejora del rendimiento de la vista previa  
 El modo en que se crean y actualizan los informes afecta a la rapidez con que se representan en la vista previa. La primera vez que se obtiene una vista previa de un informe que se basa en una referencia de servidor, se crea automáticamente una sesión de edición y los datos que se utilizaron al ejecutar el informe se agregan a una memoria caché de datos que se almacena. Al efectuar cambios en el informe que no afectan a los datos, el informe utiliza la copia de los datos que está en la memoria caché. Esto significa que no verá el cambio de los datos cada vez que obtenga una vista previa del informe. Si desea los nuevos datos, haga clic en el botón **Actualizar** en la cinta de opciones.  
  
 Las acciones siguientes hacen que la memoria caché se actualice y ralentizan la representación del informe la próxima vez que se obtenga una vista previa del mismo:  
  
-   Agregar, cambiar o eliminar un conjunto de datos. El conjunto de datos almacenado en memoria caché contiene todos los conjuntos de datos que un informe utiliza y la modificación de cualquier conjunto de datos invalida el conjunto de datos almacenado en memoria caché. Esto incluye cambiar el nombre, la consulta o los campos en el conjunto de datos.  
  
    > [!NOTE]  
    >  Si el conjunto de datos tiene un gran número de campos que no espera utilizar, considere la posibilidad de actualizar el conjunto de datos para omitirlos. Aunque esto crea una nueva sesión de edición y la primera vista previa del informe es más lenta, el menor conjunto de datos almacenado en memoria caché resulta beneficioso en conjunto para el rendimiento del servidor de informes.  
  
-   Agregar, cambiar o eliminar un origen de datos. Esto incluye cambiar el nombre o las propiedades del origen de datos, la extensión de datos del origen de datos o las propiedades de la conexión con el origen de datos.  
  
-   Cambiar el origen de datos que utiliza el informe a un origen de datos diferente.  
  
-   Cambiar el idioma del informe.  
  
-   Cambiar los ensamblados o el código personalizado que el informe utiliza.  
  
-   Agregar, cambiar o eliminar los parámetros de la consulta en los valores de parámetros o informes.  
  
 Los cambios realizados en el diseño del informe y el formato de los datos no afectan al conjunto de datos de la memoria caché. Puede efectuar las acciones siguientes sin actualizar el conjunto de datos almacenado en memoria caché:  
  
-   Agregar o quitar regiones de datos como tablas, matrices o gráficos.  
  
-   Agregar o eliminar columnas del informe. Todos los campos del conjunto de datos están disponibles para utilizarlos en el informe. Agregar o quitar campos en el informe no tiene ningún efecto en el conjunto de datos.  
  
-   Cambiar el orden de los campos en las tablas y matrices.  
  
-   Agregar, cambiar o eliminar grupos de filas y columnas.  
  
-   Agregar, cambiar o eliminar el formato de los valores de datos en los campos.  
  
-   Agregar, cambiar o eliminar imágenes, líneas o cuadros de texto.  
  
-   Cambiar los saltos de página.  
  
La sesión de edición se crea la primera vez que se obtiene una vista previa de un informe. De forma predeterminada, una sesión de edición dura 7.200 segundos (2 horas). La sesión se restablece en dos horas cada vez que se ejecuta el informe. Cuando la sesión de edición expira, se elimina la memoria caché de datos. Si la sesión de edición expira, se vuelve a crear una automáticamente la próxima vez que se obtiene una vista previa del informe.
  
De forma predeterminada, la memoria caché de datos puede contener hasta cinco conjuntos de datos. Si utiliza muchas combinaciones diferentes de valores de parámetros, el informe podría necesitar más datos. Esto requiere que la memoria caché se actualice y el informe se represente más lentamente la próxima vez que se obtenga una vista previa del mismo. 
  
## <a name="concurrency-of-report-updates"></a>Simultaneidad de actualizaciones de informes  
Con frecuencia, se obtiene una vista previa de un informe como un paso de su actualización para, a continuación, guardar el informe en el servicio Power BI. Cuando se actualiza un informe, es posible que otra persona esté actualizando y guardando el informe al mismo tiempo. El informe que se guarda en último lugar es la versión del informe que está disponible para su posterior consulta y actualización. Podría darse el caso de que la versión del informe de la que obtuvo una vista previa no sea la versión que vuelve a abrir posteriormente. Tiene la opción de guardar el informe con un nombre nuevo utilizando la opción **Guardar como** en el menú del Generador de informes.  
  
## <a name="external-report-items"></a>Elementos externos del informe  
 El informe puede incluir elementos como imágenes externas que se almacenan por separado del informe. Dado que los elementos se almacenan por separado, es posible que se puedan mover a otra ubicación o ser eliminados. Si ocurre esto, podría no obtenerse una vista previa del informe. Puede actualizar el informe para indicar la ubicación actualizada del elemento o si el elemento se eliminó, reemplazarlo por un elemento existente o quitar la referencia al mismo desde el informe.  
  
## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
