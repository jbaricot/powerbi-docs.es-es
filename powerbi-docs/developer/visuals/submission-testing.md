---
title: Prueba de envío de un objeto visual de Power BI
description: En este artículo se describen los casos de prueba que el objeto visual debe superar antes de publicarse en AppSource. También hay casos de prueba opcionales.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131135"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Prueba de envío de un objeto visual de Power BI

Antes de publicar el objeto visual en [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), debe superar estos casos de prueba. Pruebe el objeto visual antes de enviarlo. Si el visual no supera los casos de prueba necesarios, se rechazará.

Para obtener más información sobre el proceso de publicación, consulte [Publicación de objetos visuales de Power BI en el Centro de partners](./office-store.md).

## <a name="general-test-cases"></a>Casos de prueba generales

| Caso de prueba | Resultados esperados
| --------- | ----------------
| Cree un **gráfico de columnas apiladas** con **categoría** y **valor**. Conviértalo en el objeto visual y vuelva al gráfico de columnas. | No aparece ningún error después de estas conversiones. |
| Cree un **medidor** con tres medidas. Conviértalo en el objeto visual y vuelva al **medidor**. | No aparece ningún error después de estas conversiones. |
| Realice selecciones en el objeto visual. | Otros objetos visuales reflejan las selecciones. |
| Seleccione elementos en otros objetos visuales. | El objeto visual muestra datos filtrados de acuerdo con la selección en otros objetos visuales. |
| Compruebe las condiciones **dataViewMapping** mín./máx. | Los cubos de campo pueden aceptar varios campos, un solo campo o los pueden determinar otros cubos. Las condiciones **dataViewMapping** mín./máx. deben estar configuradas correctamente en las funcionalidades del objeto visual. |
| Quite todos los campos en órdenes diferentes. | El objeto visual se limpia correctamente a medida que los campos se quitan en orden arbitrario. No hay ningún error en la consola o en el explorador. |
| Abra el panel **Formato** con cada configuración de cubo posible. | Esta prueba no desencadena excepciones de referencia nula. |
| Filtre los datos mediante el panel **Filtro** en el nivel de objeto visual, página e informe. | Las informaciones sobre herramientas son correctas después de aplicar filtros. Las informaciones sobre herramientas muestran el valor filtrado. |
| Filtre los datos mediante una **segmentación**. | Las informaciones sobre herramientas son correctas después de aplicar filtros. Las informaciones sobre herramientas muestran el valor filtrado. |
| Filtre los datos mediante un objeto visual publicado. Por ejemplo, seleccione un segmento de gráfico circular o una columna. | Las informaciones sobre herramientas son correctas después de aplicar filtros. Las informaciones sobre herramientas muestran el valor filtrado. |
| Si se admite el filtrado cruzado, compruebe que los filtros funcionan correctamente. | La selección aplicada filtra otros objetos visuales en esta página del informe. |
| Seleccione con las teclas Ctrl, Alt y Mayús. | No aparece ningún comportamiento inesperado. |
| Cambie **Modo de vista** a **Tamaño real**, **Ajustar a página** y **Ajustar al ancho**. | Las coordenadas del mouse son precisas. |
| Cambie el tamaño del objeto visual. | El objeto visual reacciona correctamente al cambio de tamaño. |
| Establezca el tamaño del informe en el mínimo. | No hay ningún error de presentación. |
| Asegúrese de que las barras de desplazamiento funcionan correctamente. | Las barras de desplazamiento deberían existir, si es necesario. Compruebe los tamaños de las barras de desplazamiento. Las barras de desplazamiento no deben ser demasiado anchas ni demasiado altas. La posición y el tamaño de las barras de desplazamiento deben ser acordes con otros elementos del objeto visual. Compruebe que las barras de desplazamiento son necesarias para distintos tamaños del objeto visual. |
| Ancle el objeto visual a un **panel**. | El objeto visual se debe mostrar correctamente. |
| Agregue varias versiones del objeto visual a una sola página del informe. | Todas las versiones del objeto visual se muestran y funcionan correctamente. |
| Agregue varias versiones del objeto visual a varias páginas del informe. | Todas las versiones del objeto visual se muestran y funcionan correctamente. |
| Cambie entre las páginas del informe. | El objeto visual se muestra correctamente. |
| Pruebe la vista de lectura y la vista de edición para el objeto visual. | Todas las funciones realizan su trabajo correctamente. |
| Si el objeto visual usa animaciones, agregue, cambie y elimine elementos de dicho objeto. | La animación de elementos del objeto visual funciona correctamente. |
| Abra el panel **Propiedades**. Active y desactive las propiedades, escriba texto personalizado, ponga a prueba las opciones disponibles e introduzca datos incorrectos. | El objeto visual responde correctamente. |
| Guarde el informe y vuelva a abrirlo. | Todas las configuraciones de propiedades se conservan. |
| Cambie a otras páginas del informe y vuelva atrás. | Todas las configuraciones de propiedades se conservan. |
| Pruebe todas las funcionalidades del objeto visual, incluidas las distintas opciones que proporciona dicho objeto. | Todas las pantallas y características funcionan correctamente. |
| Pruebe todos los tipos de datos numéricos, de fecha y de caracteres, como en las siguientes pruebas. | Todos los datos tienen el formato correcto. |
| Revisar el formato de los valores de la información sobre herramientas, las etiquetas de ejes, las etiquetas de datos y otros elementos del objeto visual con formato. | Todos los elementos tienen el formato correcto. |
| Compruebe que las etiquetas de datos usan la cadena de formato. | Todas las etiquetas de datos tienen el formato correcto. |
| Active y desactive el formato automático para valores numéricos en las informaciones sobre herramientas. | Las informaciones sobre herramientas muestran los valores correctamente. |
| Compruebe las entradas de datos con diferentes tipos de datos, incluidos los numéricos, de texto, de fecha y hora, y las cadenas de formato diferente del modelo. Pruebe diferentes volúmenes de datos, como miles de filas, una fila y dos filas. | Todas las pantallas y características funcionan correctamente. |
| Proporcione datos incorrectos para el objeto visual, como valores nulos, infinito, valores negativos y tipos de valor incorrectos. | Todas las pantallas y características funcionan correctamente. |

## <a name="optional-browser-testing"></a>Pruebas opcionales del explorador

El equipo de AppSource valida el objeto visual en las versiones de Windows más recientes de los exploradores Google Chrome, Microsoft Edge y Mozilla Firefox.
Opcionalmente, pruebe el objeto visual en los siguientes exploradores.

| Caso de prueba | Resultados esperados
| --------- | ----------------
| **Windows** |
| Google Chrome (versión anterior) | Todas las pantallas y características funcionan correctamente. |
| Mozilla Firefox (versión anterior) | Todas las pantallas y características funcionan correctamente. |
| Microsoft Edge (versión anterior) | Todas las pantallas y características funcionan correctamente. |
| Microsoft Internet Explorer 11 (opcional) | Todas las pantallas y características funcionan correctamente. |
| **macOS** |
| Chrome (versión anterior) | Todas las pantallas y características funcionan correctamente. |
| Firefox (versión anterior) | Todas las pantallas y características funcionan correctamente. |
| Safari (versión anterior) | Todas las pantallas y características funcionan correctamente. |
| **Linux** |
| Firefox (versiones última y anterior) | Todas las pantallas y características funcionan correctamente. |
| **Mobile iOS** |
| Apple Safari iPad (versión anterior de Safari) | Todas las pantallas y características funcionan correctamente. |
| Chrome iPad (última versión de Safari) | Todas las pantallas y características funcionan correctamente. |
| **Mobile Android** |
| Chrome (versiones última y anterior) | Todas las pantallas y características funcionan correctamente. |

## <a name="desktop-testing"></a>Pruebas de escritorio

Pruebe el objeto visual en la versión actual de [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Caso de prueba | Resultados esperados
| --------- | ----------------
| Pruebe todas las características del objeto visual. | Todas las pantallas y características funcionan correctamente. |
| Importe, guarde, abra un archivo y publique en el servicio web de Power BI mediante el botón **Publicar** de Power BI Desktop. | Todas las pantallas y características funcionan correctamente. |
| Cambie la cadena de formato numérico para que tenga cero posiciones decimales o tres posiciones decimales aumentando o reduciendo la precisión. | El objeto visual se muestra correctamente. |

## <a name="performance-testing"></a>Pruebas de rendimiento

El objeto visual debe funcionar en un nivel aceptable. Use las herramientas de desarrollo para validar el rendimiento. No se base en las indicaciones visuales y los registros de tiempo de la consola.

| Caso de prueba | Resultados esperados
| --------- | ----------------
| Cree un objeto visual con muchos elementos visuales. | El objeto visual debe funcionar bien y no congelar la aplicación. No debería haber ningún problema de rendimiento con elementos como la velocidad de la animación, el cambio de tamaño, el filtrado y la selección.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre el proceso de publicación, consulte [Publicación de objetos visuales de Power BI en el Centro de partners](./office-store.md).

¿Tiene más preguntas? [Pregunte a la Comunidad de Power BI](https://community.powerbi.com/).
