---
title: Uso de metadatos de conjuntos de datos mejorados en Power BI Desktop
description: En este artículo se describe cómo usar metadatos de conjunto de datos mejorado en Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906985"
---
# <a name="using-enhanced-dataset-metadata"></a>Uso de los metadatos de conjuntos de datos mejorados

Cuando Power BI Desktop crea informes, también crea metadatos de conjunto de datos en los archivos PBIX y PBIT correspondientes. Anteriormente, los metadatos se almacenaban en un formato específico de Power BI Desktop. Los metadatos usaban orígenes de datos y expresiones M codificados en Base64. Power BI realizaba conjeturas para saber cómo se almacenaban esos metadatos.

Con el lanzamiento de la característica **Metadatos del conjunto de datos mejorado**, se quitan muchas de estas limitaciones. Los archivos PBIX se actualizan automáticamente a los metadatos mejorados al abrir el archivo. Con los **metadatos del conjunto de datos mejorado**, los metadatos creados por Power BI Desktop usan un formato similar al de los tabulares de Analysis Services, que se basa en el [Modelo de objetos tabulares](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La característica de **metadatos de conjunto de datos mejorado** es estratégica y fundamental. La funcionalidad futura de Power BI se basará sus metadatos. Estas otras funcionalidades se benefician de los metadatos de conjunto de datos mejorados:

- [Lectura y escritura de XMLA](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para la administración de conjuntos de datos de Power BI
- Migración de cargas de trabajo de Analysis Services a Power BI para beneficiarse de las características de última generación

## <a name="limitations"></a>Limitaciones
Antes de la compatibilidad con los metadatos mejorados, en SQL Server, Oracle, Teradata y las conexiones HANA heredadas, Power BI Desktop agregaba una consulta nativa al modelo de datos. Esa consulta la usan los modelos de datos del servicio Power BI. Gracias a la compatibilidad con los metadatos mejorados, el modelo de datos del servicio Power BI regenera la consulta nativa en tiempo de ejecución. No usa la consulta que Power BI Desktop creó. En la mayoría de los casos, esta recuperación se resuelve sola correctamente, pero algunas transformaciones no funcionarán sin leer los datos subyacentes. Posiblemente aparezcan algunos errores en los informes que antes iban bien. Por ejemplo, el error indicará: 

"No se puede convertir una consulta M en la tabla 'Dimension City' en una consulta de origen nativa. Vuelva a intentarlo más tarde o póngase en contacto con soporte técnico. Si se pone en contacto con soporte técnico, proporcione estos detalles." 

Puede corregir las consultas en tres lugares distintos de Power BI Desktop:

- Al aplicar cambios o realizar una actualización.
- En una barra de advertencia del editor de Power Query, que informa de que la expresión no se pudo plegar en el origen de datos.
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="Captura de pantalla del mensaje de aplicación de cambios de consulta que indica que no ha sido posible plegar la expresión en el origen de datos":::
- Al ejecutar evaluaciones cuando abre un informe para comprobar si tiene consultas no admitidas. Ejecutar estas evaluaciones puede repercutir en el rendimiento.


## <a name="next-steps"></a>Pasos siguientes

Puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Novedades de Power BI Desktop](../fundamentals/desktop-latest-update.md)
* [Información general sobre consultas con Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](../transform-model/desktop-common-query-tasks.md)
