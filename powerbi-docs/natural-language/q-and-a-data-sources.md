---
title: Uso de lenguaje natural con el modo de importación, de conexión dinámica y DirectQuery
description: En este artículo se ve cómo funciona la característica Preguntas y respuestas con los diferentes tipos de orígenes de datos disponibles en Power BI. También se examinan los conceptos de indexación y almacenamiento en caché.
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2020
ms.author: mohaali
ms.openlocfilehash: 85ecc5adc55daee86922c39e417db1cac5ba4a52
ms.sourcegitcommit: 0f807d3c74e5202b6e6a95fad49f2787928b9613
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706220"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>Uso de lenguaje natural con el modo de importación, de conexión dinámica y DirectQuery

La característica Preguntas y respuestas de Power BI permite obtener respuestas rápidamente mediante el empleo de lenguaje natural para formular preguntas sobre los datos. En este artículo se explica cómo se usan la indexación y el almacenamiento en caché para mejorar el rendimiento de cada configuración admitida.

## <a name="what-data-sources-are-supported-in-qa"></a>Orígenes de datos admitidos en Preguntas y respuestas

Preguntas y respuestas se admite en las siguientes configuraciones:

- Modo Importar
- Modo de conexión dinámica: uso de conjuntos de datos locales de SQL Server Analysis Services, Azure Analysis Services o Power BI
- DirectQuery: Azure Synapse, Azure SQL y SQL Server 2019. Aunque hay otros orígenes que pueden funcionar en el modo DirectQuery, no se admiten oficialmente.

De forma predeterminada, Preguntas y respuestas está habilitado dentro de un informe si se usa el objeto visual de Preguntas y respuestas. Si usa el modo DirectQuery o de conexión dinámica aparece un mensaje. Puede activar o desactivar las capacidades de lenguaje natural de un informe de forma explícita; para ello, vaya a las opciones.

![Opciones de escritorio de Preguntas y respuestas](media/qna-desktop-options.png)

Para obtener más información, vea [Limitaciones de Preguntas y respuestas de Power BI](q-and-a-limitations.md).

## <a name="how-does-indexing-work-with-qa"></a>Funcionamiento de la indexación con Preguntas y respuestas

Al habilitar Preguntas y respuestas, se compila un índice para proporcionar rápidamente comentarios en tiempo real al usuario y para ayudar a interpretar las preguntas del usuario. El índice puede tardar algún tiempo en compilarse y tiene los siguientes elementos y limitaciones.

- Todos los nombres de columna y las tablas se insertan en el índice, a menos que se haya desactivado de forma explícita desde las herramientas de Preguntas y respuestas.
- Se indexan todos los valores de texto con menos de 100 caracteres. No se indexan los valores de texto con más de 100 caracteres. 
- Preguntas y respuestas almacena un máximo de 5 millones de valores únicos en su índice. Si se supera este umbral, el índice no va a incluir todos los valores potenciales, lo que puede reducir la precisión de los resultados que se reciben de Preguntas y respuestas.
- Si se produce un error durante la indexación, el índice permanece en un estado parcial y se vuelve a crear en la siguiente actualización, como se explica en la sección siguiente.

## <a name="how-often-is-the-index-refreshed-and-cached"></a>Frecuencia de actualización y almacenamiento en caché del índice

En Power BI Desktop, el índice se crea en el momento en que se usa Preguntas y respuestas. Aparece un icono pequeño que permite saber que el índice se está compilando. Durante este tiempo, el objeto visual de Preguntas y respuestas, incluidas las sugerencias, puede tardar algún tiempo en cargarse.

En el servicio Power BI, el índice se vuelve a crear al publicar, volver a publicar y actualizar. El índice de Preguntas y respuestas no siempre se crea automáticamente y, a veces, se hace a petición a fin de optimizar las actualizaciones del conjunto de datos. En el modo DirectQuery, los datos se indexan como máximo una vez al día para reducir el impacto en el origen de DirectQuery.

## <a name="next-steps"></a>Pasos siguientes

Puede integrar el lenguaje natural en los informes de varias maneras. Para más información, consulte estos artículos:

* [Objeto visual Preguntas y respuestas](../visuals/power-bi-visualization-q-and-a.md)
* [Procedimientos recomendados de Preguntas y respuestas](q-and-a-best-practices.md)
