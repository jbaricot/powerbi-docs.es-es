---
title: Cambio del modo de ordenar un gráfico en un informe
description: Cambio del modo de ordenar un gráfico en un informe de Power BI
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 08/25/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 6147bc0ee725eb7adc7e1edb637a22bb7dc66558
ms.sourcegitcommit: 1aaa742c239a3119cdaad698be5a7553b68801fa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2020
ms.locfileid: "89040353"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Cambio del modo de ordenar un gráfico en un informe de Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]


> [!IMPORTANT]
> **Este artículo está destinado a usuarios de Power BI que no tienen permisos de edición para el informe o el conjunto de datos y que solo trabajan en la versión en línea de Power BI (el servicio Power BI). Si es *diseñador*, *administrador* o *propietario* de un informe, puede que este artículo no contenga toda la información que necesita. Así que lea mejor [Ordenar por columnas en Power BI Desktop](../create-reports/desktop-sort-by-column.md)** .

En el servicio Power BI, puede cambiar el aspecto de un objeto visual al ordenar por campos de datos diferentes. Al cambiar cómo se ordena un objeto visual, puede resaltar la información que quiere transmitir. Independientemente de si usa datos numéricos (como cifras de ventas) o datos de texto (como nombres de estado), puede ordenar sus objetos visuales de la forma que quiera. Power BI proporciona mucha flexibilidad para la ordenación y menús rápidos para su uso. 

Los objetos visuales de un panel no se pueden ordenar, pero en un informe de Power BI, sí puede ordenar la mayoría de los objetos visuales por un campo, y a veces dos, a la vez. En algunos tipos de objetos visuales, la ordenación no está disponible en absoluto: gráficos de rectángulos, medidores, mapas, etc. 

## <a name="get-started"></a>Comenzar

Para empezar, abra un informe que haya creado o que se haya compartido con usted. Seleccione un objeto visual (que se pueda ordenar) y elija **Más acciones** (...).  Hay tres opciones para ordenar: **Orden descendente**, **Orden ascendente** y **Ordenar por**. 
    

![gráfico de barras ordenado alfabéticamente por el eje X](media/end-user-change-sort/power-bi-actions.png)

### <a name="sort-alphabetically-or-numerically"></a>Ordenar alfabéticamente o numéricamente

Los objetos visuales se pueden ordenar alfabéticamente por los nombres de las categorías del objeto visual o por los valores numéricos de cada categoría. Por ejemplo, este gráfico está ordenado alfabéticamente por la categoría del eje X **Nombre** de tienda.

![gráfico de barras ordenado alfabéticamente por eje X](media/end-user-change-sort/powerbi-sort-category.png)

Para cambiar el orden de una categoría (nombre de almacén) a un valor (ventas por metro cuadrado), seleccione **Más acciones** (...) y elija **Ordenar por**. Seleccione un valor numérico usado en el objeto visual.  En este ejemplo, hemos seleccionado **Ventas por metro cuadrado**.

![Captura de pantalla en la que se muestra la selección de "Ordenar por" y la selección de un valor](media/end-user-change-sort/power-bi-sort-value.png)

Si es necesario, cambie el criterio de ordenación a ascendente o descendente.  Vuelva a seleccionar **Más acciones** (...) y seleccione **Orden descendente** u **Orden ascendente**. El campo que se usa para ordenar está en negrita y tiene una barra amarilla.

   ![vídeo que muestra la selección de ordenar por y, a continuación, ascendente, descendente](media/end-user-change-sort/sort.gif)

> [!NOTE]
> No todos los objetos visuales se pueden ordenar. Por ejemplo, los siguientes objetos visuales no se pueden ordenar: gráfico de rectángulos, mapa, mapa coroplético, dispersión, medidor, tarjeta y cascada.

## <a name="sorting-by-multiple-columns"></a>Ordenación por varias columnas
Los datos de esta tabla se ordenan por **número de clientes**.  Sabemos que es así por la flecha pequeña que se encuentra debajo de la palabra *Número*. La flecha apunta hacia abajo, lo que significa que la columna está en orden *descendente*.

![captura de pantalla que muestra la primera columna que se usa para la ordenación](media/end-user-change-sort/power-bi-sort-column.png)


Para agregar más columnas al criterio de ordenación, presione Mayús + clic en el encabezado de la columna que quiere agregar a continuación en el criterio de ordenación. Por ejemplo, si hace clic en **Número de clientes** y, después, presiona Mayús + clic en **Ingresos totales**, la tabla se ordena primero por clientes y después por ingresos. El contorno rojo muestra las áreas en las que cambió el criterio de ordenación.

![captura de pantalla que muestra la segunda columna que se usa para la ordenación](media/end-user-change-sort/power-bi-sort-second.png)

Si presiona Mayús y hace clic por segunda vez en la misma columna, se cambiará la dirección de ordenación (ascendente, descendente) de dicha columna. Además, si presiona Mayús + clic en una columna que ha agregado anteriormente al criterio de ordenación, esa columna se moverá a la parte posterior del criterio de ordenación.


## <a name="saving-changes-you-make-to-sort-order"></a>Guardar los cambios realizados en el criterio de ordenación
Los informes de Power BI conservan los filtros, las segmentaciones de datos, la ordenación y otros cambios de la vista de datos que realice, aunque esté trabajando en [vista de lectura](end-user-reading-view.md). De modo que, si sale de un informe y vuelve más tarde, se guardan los cambios de ordenación.  Si quiere revertir los cambios a la configuración del *diseñador* del informe, seleccione **Restablecer valores predeterminados** en la barra de menús superior. 

![ordenación persistente](media/end-user-change-sort/power-bi-reset.png)

Pero, si el botón **Restablecer valores predeterminados** está atenuado, significa que el *diseñador* del informe ha deshabilitado la capacidad de guardar (conservar) los cambios.

<a name="other"></a>
## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

### <a name="sorting-using-other-criteria"></a>Ordenación siguiendo otros criterios
Es posible que, a veces, quiera ordenar el objeto visual mediante un campo diferente (que no está incluido en el objeto visual) o siguiendo otros criterios.  Por ejemplo, quizás quiera ordenarlo por mes en orden secuencial (y no en orden alfabético) o por números enteros en lugar de dígitos (ejemplo, 0, 1, 9, 20 y no 0, 1, 20, 9).  

Solo la persona que diseñó el informe puede hacer estos cambios. Para encontrar la información de contacto del *diseñador*, seleccione el nombre del informe en la barra de encabezado.

![Elemento desplegable que muestra la información de contacto](media/end-user-change-sort/power-bi-header.png)

Si es *diseñador* y tiene permisos de edición para el contenido, lea [Ordenar por columnas en Power BI Desktop](../create-reports/desktop-sort-by-column.md) para saber cómo actualizar el conjunto de datos y habilitar este tipo de ordenación.

## <a name="next-steps"></a>Pasos siguientes
Más información sobre [Visualizaciones en Power BI](end-user-visualizations.md).

[Power BI: Conceptos básicos](end-user-basic-concepts.md)
