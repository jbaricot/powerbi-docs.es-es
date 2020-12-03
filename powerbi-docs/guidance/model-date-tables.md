---
title: Creación de tablas de fechas en Power BI Desktop
description: Técnicas e instrucciones para crear tablas de fechas en Power BI Desktop.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: 9040fb54e51dfeecad853e5ba980f423ab48e908
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417851"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Creación de tablas de fechas en Power BI Desktop

Este artículo está dirigido a modeladores de datos como usted que trabajan con Power BI Desktop. Se describen prácticas recomendadas de diseño para crear tablas de fechas en los modelos de datos.

Para trabajar con las [funciones de inteligencia de tiempo](/dax/time-intelligence-functions-dax) de las expresiones de análisis de datos (DAX), hay un requisito previo para el modelo: Debe tener al menos una _tabla de fechas_ en el modelo. Una tabla de fechas es una tabla que cumple los siguientes requisitos:

> [!div class="checklist"]
> - Debe contener una columna de tipo de datos **fecha**, o **fecha y hora**, conocida como la _columna de fecha_.
> - La columna de fecha debe contener valores únicos.
> - La columna de fecha no debe contener ESPACIOS EN BLANCO.
> - En la columna de fecha no debe faltar ninguna fecha.
> - La columna de fecha debe abarcar años completos. Un año no es necesariamente un año natural (de enero a diciembre).
> - La tabla de fechas debe estar [marcada como una tabla de fechas](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

Puede utilizar cualquiera de las distintas técnicas para agregar una tabla de fechas al modelo:

- Opción de fecha y hora automáticas
- Power Query para conectarse a una tabla de dimensiones de fecha
- Power Query para generar una tabla de fechas
- DAX para generar una tabla de fechas
- DAX para clonar una tabla de fechas existente

> [!TIP]
> Una tabla de fechas es quizás la característica más coherente que agregará a cualquiera de sus modelos. Además, dentro de una organización, una tabla de fechas debe definirse de forma coherente. Por lo tanto, independientemente de la técnica que decida usar, se recomienda crear una [plantilla de Power BI Desktop](../create-reports/desktop-templates.md) que contenga una tabla de fechas totalmente configurada. Comparta la plantilla con todos los modeladores de su organización. Por lo tanto, cada vez que alguien desarrolla un nuevo modelo, puede comenzar con una tabla de fechas definida de forma coherente.

## <a name="use-auto-datetime"></a>Uso de la fecha y hora automáticas

La opción [Fecha y hora automáticas](../transform-model/desktop-auto-date-time.md) ofrece inteligencia de tiempo cómoda, rápida y fácil de usar. Los autores de informes pueden trabajar con la inteligencia de tiempo al filtrar, agrupar y explorar los períodos de tiempo de calendario.

Se recomienda mantener habilitada la opción Fecha y hora automáticas solo al trabajar con períodos de tiempo de calendario y cuando tenga requisitos de modelo sencillos con respecto al tiempo. Usar esta opción también puede ser útil cuando se crean modelos ad hoc o se realiza la generación de perfiles o la exploración de datos. Sin embargo, este enfoque no es compatible con un diseño de tabla de fechas único que puede propagar filtros a varias tablas. Para más información, vea [Guía sobre la fecha y hora automáticas en Power BI Desktop](auto-date-time.md).

## <a name="connect-with-power-query"></a>Conexión con Power Query

Cuando el origen de datos ya tiene una tabla de fechas, se recomienda utilizarlo como origen de la tabla de fechas del modelo. Este caso suele darse cuando se conecta a un almacenamiento de datos, ya que tendrá una tabla de dimensiones de fecha. De este modo, el modelo utiliza una única fuente de confianza para los aspectos temporales de su organización.

Si va a desarrollar un modelo de DirectQuery y el origen de datos no incluye una tabla de fechas, le recomendamos encarecidamente que agregue una tabla de fechas al origen de datos. Debe cumplir todos los requisitos de modelado de una tabla de fechas. A continuación, puede usar Power Query para conectarse a la tabla de fechas. De esta manera, los cálculos del modelo pueden utilizar las funcionalidades de inteligencia de tiempo de DAX.

## <a name="generate-with-power-query"></a>Generación con Power Query

Puede generar una tabla de fechas mediante Power Query. A continuación, se presentan dos entradas de blog que muestran cómo:

- [Crear una dimensión de fecha con un script de Power Query](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/), de Matt Masson
- [Generar una tabla de dimensiones de fecha en Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/), de Chris Webb

> [!TIP]
> Si no dispone de un almacenamiento de datos u otra definición coherente para los aspectos temporales de su organización, considere la posibilidad de usar Power Query para publicar un [flujo de datos](../transform-model/dataflows/dataflows-introduction-self-service.md). A continuación, haga que todos los modeladores de datos se conecten al flujo de datos para agregar tablas de fechas a sus modelos. El flujo de datos se convierte en la única fuente de confianza para los aspectos temporales de su organización.

Si necesita generar una tabla de fechas, considere la posibilidad de hacerlo con DAX. Es posible que le resulte más fácil. Además, puede resultar más conveniente, ya que DAX integra alguna inteligencia para simplificar la creación y administración de tablas de fechas.

## <a name="generate-with-dax"></a>Generación con DAX

Puede generar una tabla de fechas en el modelo mediante la creación de una tabla calculada con las funciones [CALENDAR](/dax/calendar-function-dax) o [CALENDARAUTO](/dax/calendarauto-function-dax) de DAX. Cada función devuelve una tabla de fechas de una sola columna. A continuación, puede extender la tabla calculada con columnas calculadas para admitir los requisitos de agrupación y filtrado de intervalos de fechas.

- Utilice la función **CALENDAR** cuando desee definir un intervalo de fechas. Se pasan dos valores: la fecha de inicio y la fecha de finalización. Estos valores pueden definirse con otras funciones de DAX, como `MIN(Sales[OrderDate])` o `MAX(Sales[OrderDate])`.
- Utilice la función **CALENDARAUTO** cuando desee que el intervalo de fechas abarque automáticamente todas las fechas almacenadas en el modelo. Puede pasar un solo parámetro opcional que sea el mes en que finaliza el año (si se trata de un año natural, que finaliza en diciembre, no es necesario pasar ningún valor). Es una función útil, ya que garantiza que se devuelvan años de fechas completos; es un requisito para una tabla de fechas marcada. Además, no es necesario administrar la extensión de la tabla a los próximos años: cuando se completa una actualización de datos, desencadena el recálculo de la tabla. Un recálculo extenderá automáticamente el intervalo de fechas de la tabla cuando se carguen fechas de un año nuevo en el modelo.

## <a name="clone-with-dax"></a>Clonación con DAX

Cuando el modelo ya tiene una tabla de fechas y necesita otra adicional, puede clonar fácilmente la tabla de fechas existente. Esto sucede cuando la fecha es una [dimensión realizadora de roles](star-schema.md#role-playing-dimensions). Puede clonar una tabla mediante la creación de una tabla calculada. La expresión de tabla calculada es simplemente el nombre de la tabla de fechas existente.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Fecha y hora automáticas en Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Guía sobre la fecha y hora automáticas en Power BI Desktop](auto-date-time.md)
- [Configuración y uso de tablas de fechas en Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Autoservicio de preparación de los datos en Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [Función CALENDAR (DAX)](/dax/calendar-function-dax)
- [Función CALENDARAUTO (DAX)](/dax/calendarauto-function-dax)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)