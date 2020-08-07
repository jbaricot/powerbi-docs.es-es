---
title: Modelo de ejemplo de DAX
description: Modelo de ejemplo de DAX para admitir artículos de referencia.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2020
ms.author: v-pemyer
ms.openlocfilehash: 6e2fe331fa274305447266321893204dddcc3148
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537467"
---
# <a name="dax-sample-model"></a>Modelo de ejemplo de DAX

El modelo de ejemplo **Adventure Works DW 2020** de Power BI Desktop está diseñado para admitir el aprendizaje de DAX. El modelo se basa en el [ejemplo de almacenamiento de datos de Adventure Works](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) para AdventureWorksDW2017, pero los datos se modificaron para satisfacer los objetivos del modelo de ejemplo.

## <a name="scenario"></a>Escenario

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="Se muestra una imagen del logotipo de la empresa Adventure Works.":::

La empresa Adventure Works representa a un fabricante de bicicletas que vende bicicletas y accesorios en mercados globales. La empresa tiene sus datos de almacenamiento de datos almacenados en una instancia de Azure SQL Database.

## <a name="model-structure"></a>Estructura del modelo

El modelo tiene siete tablas:

|Tabla|Descripción|
|-----|-------|
|**Customer**|Describe los clientes y su ubicación geográfica. Los clientes compran productos en línea (ventas por Internet).|
|**Date**|Hay tres relaciones entre las tablas **Date** y **Sales**, para la fecha del pedido, la fecha de envío y la fecha de vencimiento. La relación de fecha de pedido está activa. Los informes de ventas de la empresa usan un año fiscal que comienza el 1 de julio de cada año. La tabla se marca como una tabla de fechas con la columna **Date**.|
|**Producto**|Almacena solo los productos terminados.|
|**Reseller**|Describe los revendedores y su ubicación geográfica. Revendedor en la venta de productos a sus clientes.|
|**Sales**|Almacena filas en la línea de pedido de ventas. Todos los valores financieros están en dólares estadounidenses (USD). La fecha de pedido más temprana es el 1 de julio de 2017 y la fecha del último pedido es el 15 de junio de 2020.|
|**Sales Order**|Describe los números de pedido de ventas y los números de línea de pedido, además del canal de ventas, que es **Revendedor** o **Internet**. Esta tabla tiene una relación uno a uno con la tabla **Sales**.|
|**Sales Territory**|Los territorios de ventas están organizados en grupos (Norteamérica, Europa y Pacífico), países y regiones. Solo el grupo de Estados Unidos vende productos en el nivel de región.|

El modelo no contiene ningún cálculo de DAX.

## <a name="download-sample"></a>Descarga de un ejemplo

Puede descargar el archivo de modelo de ejemplo de Power BI Desktop [aquí](https://aka.ms/dax-docs-sample-file).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre este artículo, consulte los recursos siguientes:

- [Referencia de expresiones de análisis de datos (DAX)](/dax/)
- Ruta de aprendizaje: [Uso de DAX en Power BI Desktop](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com)
