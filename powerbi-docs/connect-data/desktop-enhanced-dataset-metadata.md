---
title: Uso de metadatos de conjuntos de datos mejorados en Power BI Desktop
description: En este artículo se describe cómo usar metadatos de conjunto de datos mejorado en Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/22/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 67141f67be85f5c292118d4e88cfe3c5a949ce4f
ms.sourcegitcommit: ff981839e805f523748b7e71474acccf7bdcb04f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "91019869"
---
# <a name="using-enhanced-dataset-metadata"></a>Uso de los metadatos de conjuntos de datos mejorados

Cuando Power BI Desktop crea informes, también crea metadatos de conjunto de datos en los archivos PBIX y PBIT correspondientes. Anteriormente, los metadatos se almacenaban en un formato específico de Power BI Desktop. Se usaban expresiones de M codificadas con Base 64 y orígenes de datos, y se formulaban suposiciones sobre cómo se almacenaban los metadatos.

Con el lanzamiento de la característica **Metadatos del conjunto de datos mejorado**, se quitan muchas de estas limitaciones. Los archivos PBIX se actualizan automáticamente a los metadatos mejorados al abrir el archivo. Con los **metadatos del conjunto de datos mejorado**, los metadatos creados por Power BI Desktop usan un formato similar al de los tabulares de Analysis Services, que se basa en el [Modelo de objetos tabulares](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La característica **Metadatos del conjunto de datos mejorado** es estratégica y fundamental, ya que la futura funcionalidad de Power BI se generará en función de sus metadatos. Algunas de las funcionalidades adicionales que se benefician de la característica Metadatos del conjunto de datos mejorado incluyen la [lectura y escritura de XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para la administración de conjuntos de datos de Power BI y la migración de cargas de trabajo de Analysis Services a Power BI para aprovechar las características de próxima generación.


## <a name="next-steps"></a>Pasos siguientes

Puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Novedades de Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Información general sobre consultas con Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](../transform-model/desktop-common-query-tasks.md)