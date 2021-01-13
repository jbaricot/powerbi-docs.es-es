---
title: Consejos de rendimiento en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: Procedimiento para crear un objeto visual de Power BI de alto rendimiento. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: c8bcf5e13ba769b976ab123adb3ba37f46b0359e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885945"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Cómo crear un objeto visual de Power BI de alto rendimiento
En este artículo se tratan las técnicas que permiten a los desarrolladores obtener un alto rendimiento al representar objetos visuales. 

Nadie quiere que un objeto visual tarde en representarse, por lo que es fundamental aprovechar al máximo el rendimiento del código durante la representación. 

> [!NOTE]
> A medida que mejoremos la plataforma, se irán lanzando nuevas versiones de la API. Para sacar el máximo partido del conjunto de características y la plataforma de objetos visuales de Power BI, se recomienda mantenerse actualizado a la versión más reciente.
>
> Desde la **versión 2.1** (la más reciente), los tiempos de carga de los objetos visuales de Power BI han mejorado de media un 20 %.

## <a name="power-bi-visual-performance-tips"></a>Sugerencias de rendimiento para los objetos visuales de Power BI
A continuación se indican algunas recomendaciones sobre cómo conseguir un rendimiento óptimo de los objetos visuales. 

### <a name="use-user-timing-api"></a>Uso de User Timing API
El uso de **User Timing API** para medir el rendimiento de JavaScript de la aplicación puede ayudarle a decidir qué partes del script deben optimizarse.

Para obtener más información, consulte [User Timing API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Revisión de los bucles de animación
¿Vuelve el bucle de animación a dibujar elementos que no se han modificado? 

 - Problema: pierde tiempo dibujando elementos que no cambian de fotograma a fotograma.

 - Solución: actualice los fotogramas de forma selectiva. 
 
Cuando llega el momento de animar visualizaciones estáticas, es tentador dibujar el total del código en una función de actualización y llamarlo repetidamente con nuevos datos para cada iteración del bucle de animación.

En su lugar, considere el siguiente patrón de actualización y use un método de constructor de objeto visual para dibujar todos los elementos estáticos. Después, la función de actualización solo tendrá que dibujar los elementos de visualización que cambien. 

   > [!TIP]
   > Suelen encontrarse bucles de animación ineficaces en ejes y leyendas.

### <a name="cache-dom-nodes"></a>Almacenamiento en caché de nodos DOM 
Cuando se recupera un nodo o una lista de nodos de DOM, debe pensar si puede reutilizarlos en cálculos posteriores (en ocasiones, incluso en la siguiente iteración del bucle). Siempre y cuando no necesite agregar o eliminar nodos adicionales en el área correspondiente, el almacenamiento en caché puede mejorar la eficacia global de la aplicación.

Para asegurarse de que el código sea rápido y no ralentice el explorador, mantenga el acceso a DOM al mínimo. 

- Antes: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Después: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Evitación de la manipulación de DOM 
Limite la manipulación de DOM en la medida de lo posible.  Las operaciones de inserción como `prepend()`, `append()` y `after()` requieren mucho tiempo y no deben usarse a menos que sea necesario.

Por ejemplo:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

El ejemplo anterior podría agilizarse si se usa `html()` y se crea la lista de antemano: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Reconsideración de JQuery

La limitación de los marcos de JS y el uso de JS nativo siempre que sea posible puede aumentar el ancho de banda disponible y reducir la sobrecarga de procesamiento. Esto también puede limitar los problemas de compatibilidad con exploradores antiguos. 

Para obtener más información, consulte en [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) ejemplos alternativos de funciones de JQuery, como `show`, `hide`, `addClass`, etc.  

### <a name="use-canvas-or-webgl"></a>Uso de Canvas o WebGL 
Para el uso repetido de animaciones, considere la posibilidad de usar **Canvas** o **WebGL**, en lugar de SVG. A diferencia de lo que sucede con SVG, con estas opciones, el rendimiento viene determinado por el tamaño, no por el contenido. 

Puede obtener más información sobre las diferencias en [SVG frente a Canvas: cómo elegir](/previous-versions/windows/internet-explorer/ie-developer/samples/gg193983(v=vs.85)). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Uso de requestAnimationFrame en lugar de setTimeout 
Si usa [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) para actualizar las animaciones en pantalla, se llamará a las funciones de animación **antes** de que el explorador llame a otro método Repaint.

Para obtener más información, vea este [ejemplo](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) de animación suavizada con `requestAnimationFrame`.

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre las técnicas de optimización en la [Guía de optimización para Power BI](../../guidance/power-bi-optimization.md).