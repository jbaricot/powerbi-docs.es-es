---
title: Funcionamiento correcto de los datos de Excel con Preguntas y respuestas en Power BI
description: Cómo hacer que los datos funcionen correctamente con Preguntas y respuestas en Power BI
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 41672fa809544198a053ae41f935e890d83cfa72
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388112"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Funcionamiento correcto de los datos de Excel con Preguntas y respuestas en Power BI
Si es la persona que crea modelos de datos o compila libros de Excel que se usarán con Power BI, siga leyendo...

En Power BI, Preguntas y respuestas pueden buscar datos estructurados y elegir la visualización correcta para la pregunta; esto es lo que lo convierte en una herramienta atractiva.   

Preguntas y respuestas puede trabajar en cualquier archivo de Excel cargado que tenga tablas, intervalos o que contenga un modelo de PowerPivot, pero cuantas más optimizaciones y limpieza de datos realice, más sólido será el rendimiento de Preguntas y respuestas.  Si tiene pensado compartir informes y paneles basados en el conjunto de datos, querrá que sea fácil para sus compañeros formular preguntas y obtener respuestas de calidad.

## <a name="how-qa-works-with-excel"></a>Funcionamiento de Preguntas y respuestas con Excel
Preguntas y respuestas tiene un conjunto de capacidades de descripción de lenguaje natural básicas que funcionan en todos los datos. Cuenta con la búsqueda de palabras claves dependientes del contexto para tablas, columnas y nombres de los campos calculados de Excel. También sabe cómo filtrar, ordenar, agregar, agrupar y mostrar datos. 

Por ejemplo, en una tabla de Excel denominada "Ventas", con columnas "Producto", "Mes", "Unidades vendidas", "Ventas brutas" y "Beneficios", podría formular preguntas sobre cualquiera de esas entidades.  Podría pedir que se mostraran las ventas, el total de beneficios por mes, ordenar los productos por unidades vendidas y muchas otras combinaciones. Más información sobre el [uso de preguntas y respuestas en los paneles y los informes](power-bi-tutorial-q-and-a.md) y los [tipos de visualización que puede especificar en una consulta de Preguntas y respuestas](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Preparación de un conjunto de datos de Excel para Preguntas y respuestas
Preguntas y respuestas se basa en los nombres de tablas, columnas y campos calculados para responder a preguntas específicas de datos, lo que significa que lo que llama entidades en su libro es muy importante.

Estas son algunas sugerencias para sacar el máximo partido de Preguntas y respuestas en el libro.

* Asegúrese de que los datos están en una tabla de Excel. Aquí se explica [cómo crear una tabla de Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Asegúrese de que los nombres de las tablas, las columnas y los campos calculados son significativos en lenguaje natural.
  
  Por ejemplo, si tiene una tabla con datos de ventas, llame a la tabla "Ventas". Nombres de columna como "Año", "Producto", "Representante de ventas" y "Cantidad" funcionarán bien con Preguntas y respuestas.

* Si el libro tiene un modelo de datos de PowerPivot, puede hacer más optimizaciones todavía. Lea más sobre [Desmitificación de Preguntas y respuestas de Power BI parte 2](https://powerbi.microsoft.com/blog/demystifying-power-bi-q-amp-a-part-2/), redactado por nuestro equipo interno de expertos en lenguaje natural.

* Abra el conjunto de datos en Power BI Desktop y podrá crear nuevas columnas, crear medidas, concatenar campos para crear valores únicos, clasificar los datos por tipo (por ejemplo, fechas, cadenas, datos geográficos, imágenes, direcciones URL) y mucho más.

## <a name="next-steps"></a>Pasos siguientes

- [Preguntas y respuestas para consumidores](../consumer/end-user-q-and-a.md)  
- [Uso de Preguntas y respuestas en paneles e informes](power-bi-tutorial-q-and-a.md)
- [Preparación de conjuntos de datos locales para Preguntas y respuestas](service-q-and-a-direct-query.md)   
- [Obtener datos (para Power BI)](../connect-data/service-get-data.md)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
