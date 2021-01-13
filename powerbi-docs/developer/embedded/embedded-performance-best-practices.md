---
title: Procedimientos recomendados del rendimiento de análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se proporcionan instrucciones sobre los procedimientos recomendados de análisis integrados de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: f8bf41ae9a4b6f2e16aae2c05df8fa4448a0457c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888797"
---
# <a name="power-bi-embedded-analytics-performance-best-practices"></a>Procedimientos recomendados de rendimiento de análisis integrados de Power BI

En este artículo se proporcionan recomendaciones para un procesamiento más rápido de los informes, paneles e iconos de la aplicación.

> [!Note]
> Recuerde que el tiempo de carga depende principalmente de los elementos relevantes para el informe y los datos mismos, incluidos los objetos visuales, el tamaño de los datos y la complejidad de las consultas y medidas. Para más información, vea [Guía de optimización para Power BI](../../guidance/power-bi-optimization.md).

## <a name="update-tools-and-sdk-packages"></a>Actualizar herramientas y paquetes SDK

Mantenga actualizadas las herramientas y los paquetes SDK.

* Use siempre la versión más reciente de [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Instale la versión más reciente del [SDK de cliente de Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Seguimos publicando más mejoras, así que asegúrese de hacer un seguimiento de vez en cuando.

## <a name="embed-parameters"></a>Insertar parámetros

El método `powerbi.embed(element, config)` recibe un elemento y una configuración. El parámetro config incluye campos que tienen implicaciones en el rendimiento.

### <a name="embed-url"></a>Insertar URL

Evite generar usted mismo la dirección URL que se va a insertar. En su lugar, asegúrese de obtener la dirección URL de inserción mediante una llamada a las API [Obtener informes](/rest/api/power-bi/reports/getreportsingroup), [Obtener paneles](/rest/api/power-bi/dashboards/getdashboardsingroup) u [Obtener iconos](/rest/api/power-bi/dashboards/gettilesingroup). Hemos agregado un parámetro nuevo a la dirección URL denominado **_config_**, que se usa para mejorar el rendimiento.

### <a name="permissions"></a>Permisos

Proporcione permisos de **visualización** si no tiene previsto insertar un informe en el modo de edición. De este modo, el código para insertar no inicializa los componentes que se usan en el modo de edición.

### <a name="filters-bookmarks-and-slicers"></a>Filtros, marcadores y segmentaciones

Por lo general, los objetos visuales de los informes se guardan con los datos almacenados en caché. Los datos en caché se usan para dar la percepción de rendimiento. Los informes representan los datos en caché mientras se ejecutan las consultas. Si se proporcionan filtros, marcadores o segmentaciones, los datos en caché no son relevantes y los objetos visuales se representan solo después de que finalice la consulta del objeto visual.

Si inserta informes con los mismos filtros, marcadores y segmentaciones, para mejorar el rendimiento, guarde el informe con los filtros, marcadores y segmentaciones ya aplicados. Esto representa el informe con los datos en caché, lo que incluye los filtros, marcadores y segmentaciones.

## <a name="switching-between-reports"></a>Cambio entre informes

Al insertar varios informes en el mismo IFrame, no genere un IFrame nuevo para cada informe. En su lugar, use `powerbi.embed(element, config)` con una configuración distinta para insertar el informe nuevo.

> [!NOTE]
> El cambio entre informes cuando se insertan para sus clientes (también conocido como escenario de "la aplicación posee los datos") requiere el uso de un token de inserción con permisos para todos los informes y conjuntos de datos. Para más información, consulte [Generación de API de token](/rest/api/power-bi/embedtoken/generatetoken).

## <a name="query-caching"></a>Almacenamiento en caché de consultas

Las organizaciones con capacidad de Power BI Premium o capacidad de Power BI Embedded pueden aprovechar el almacenamiento en caché de consultas para acelerar los informes asociados a un conjunto de datos.

[Más información sobre el almacenamiento en caché de consultas en Power BI](../../connect-data/power-bi-query-caching.md).

## <a name="preload"></a>Carga previa

Use `powerbi.preload()` para mejorar el rendimiento del usuario final. El método `powerbi.preload()` descarga JavaScript, archivos CSS y otros artefactos que se usan posteriormente para insertar un informe.

Llame a `powerbi.preload()` si no va a insertar el informe de inmediato. Por ejemplo, si el contenido de Power BI insertado no aparece en la página principal, use `powerbi.preload()` para descargar y almacenar en caché los artefactos que se usan para insertar el contenido.

## <a name="bootstrapping-the-iframe"></a>Arranque del IFrame

> [!NOTE]
> Se requiere la versión 2.9 del [SDK de cliente de Power BI](https://github.com/Microsoft/PowerBI-JavaScript) para arrancar el iFrame.

`powerbi.bootstrap(element, config)` permite iniciar la inserción antes de que estén disponibles todos los parámetros necesarios. La API de arranque prepara e inicializa el iframe.
Cuando se usa la API de arranque, también es necesario llamar a `powerbi.embed(element, config)` en el mismo elemento HTML.

Por ejemplo, uno de los casos de uso de esta característica consiste en ejecutar el arranque de iframe y las llamadas de back-end para la inserción, en paralelo.
> [!TIP]
> Use la API de arranque cuando sea posible generar el iframe antes de que sea visible para el usuario final.

[Más información sobre el arranque de IFrame](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Medir el rendimiento

### <a name="performance-events"></a>Eventos de rendimiento

Para medir el rendimiento insertado, puede usar dos eventos:

1. Evento cargado: el tiempo hasta que se inicializa el informe (el logotipo de Power BI desaparecerá cuando se complete la carga).
2. Evento representado: el tiempo hasta que el informe se representa completamente, mediante los datos actuales. El evento representado se desencadena cada vez que se vuelve a representar el informe (por ejemplo, después aplicar filtros). Para medir un informe, asegúrese de que realiza los cálculos en el primer evento generado.

Los datos en caché se representan cuando están disponibles pero no se genera ningún evento adicional.

[Más información sobre el control de eventos](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Analizador de rendimiento

Para examinar el rendimiento de los elementos del informe, puede usar el Analizador de rendimiento de Power BI Desktop.
El Analizador de rendimiento le permitirá ver y registrar los registros que midan el rendimiento de cada uno de los elementos del informe.

[Más información sobre el Analizador de rendimiento](../../create-reports/desktop-performance-analyzer.md).

> [!NOTE]
> Recuerde siempre comparar el rendimiento de los informes insertados con el rendimiento en powerbi.com. Esto puede ayudarlo a comprender el origen de los problemas de rendimiento.

## <a name="next-steps"></a>Pasos siguientes

* [Guía de optimización para Power BI](../../guidance/power-bi-optimization.md)
* [Cómo solucionar problemas de análisis integrados de Power BI](embedded-troubleshoot.md)
* [Preguntas más frecuentes sobre análisis integrados de Power BI](embedded-faq.md)