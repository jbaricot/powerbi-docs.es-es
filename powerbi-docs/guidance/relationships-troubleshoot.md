---
title: Instrucciones para solución de problemas de relaciones
description: Instrucciones para solucionar problemas relacionados con la relación de modelos.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "78263654"
---
# <a name="relationship-troubleshooting-guidance"></a>Instrucciones para solución de problemas de relaciones

Este artículo está dirigido a modeladores de datos como usted que trabajan con Power BI Desktop. Proporciona instrucciones sobre cómo solucionar problemas específicos que pueden surgir al desarrollar modelos e informes.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Lista de comprobación de solución de problemas

Cuando un objeto visual de informe está configurado para usar campos de dos (o más) tablas y no presenta el resultado correcto (o ningún resultado), es posible que el problema esté relacionado con las relaciones de modelo.

En este caso, se muestra una lista de comprobación de solución de problemas general que se debe seguir. Puede avanzar por los pasos propuestos en la lista de comprobación hasta que identifique los problemas.

1. Cambie el objeto visual a una tabla o matriz, o abra el panel "Ver datos" —es más fácil solucionar problemas cuando puede ver el resultado de la consulta—.
1. Si hay un resultado de consulta vacío, cambie a la vista de datos: compruebe que las tablas se han cargado con filas de datos.
1. Cambie a la vista de modelo: es fácil ver las relaciones y determinar rápidamente sus propiedades.
1. Compruebe que existen relaciones entre las tablas.
1. Compruebe que las propiedades de cardinalidad están configuradas correctamente: podrían ser incorrectas si una columna de "varios" contiene en este momento valores únicos y se ha configurado incorrectamente como de "uno".
1. Compruebe que las relaciones están activas (línea continua).
1. Compruebe que las direcciones de los filtros admiten la propagación (interprete los cabezales de las flechas).
1. Compruebe que las columnas correctas están relacionadas: seleccione la relación o mantenga el cursor sobre ella para mostrar las columnas relacionadas.
1. Compruebe que los tipos de datos de columna relacionados son los mismos, o al menos compatibles; es posible relacionar una columna de texto con una columna de número entero, pero los filtros no encontrarán ninguna coincidencia para propagarse.
1. Cambie a la vista de datos y compruebe que los valores coincidentes se pueden encontrar en columnas relacionadas.

## <a name="troubleshooting-guide"></a>Guía de solución de problemas

Esta es una lista de problemas junto con las posibles soluciones.

|Problema|Posible motivo:|
|---------|---------|
|El objeto visual no muestra resultados.|- El modelo todavía debe cargarse con datos.<br />- No existe ningún dato en el contexto de filtro.<br />- Se aplica la seguridad de nivel de fila.<br />- Las relaciones no se propagan entre tablas, _siga la lista de comprobación anterior_.<br />- Se aplica la seguridad de nivel de fila, pero no se habilita la propagación de una relación bidireccional; consulte [Seguridad de nivel de fila (RLS) con Power BI Desktop](../desktop-rls.md)|
|El objeto visual muestra el mismo valor para cada agrupación. |- Las relaciones no existen.<br />- Las relaciones no se propagan entre tablas, _siga la lista de comprobación anterior_.|
|El objeto visual muestra los resultados, pero no son correctos.|- El objeto visual no está configurado correctamente.<br />- La lógica de medida es incorrecta.<br />- Los datos del modelo deben actualizarse.<br />- Los datos del informe son incorrectos.<br />- Las columnas de relación están incorrectamente relacionadas (por ejemplo, la columna **ProductID** se asigna a **CustomerID**).<br />- Es una relación entre dos tablas de DirectQuery y la columna "uno" de una relación contiene valores duplicados.|
|Aparecen agrupaciones o elementos de filtro o segmentación en blanco y las columnas de origen no contienen espacios en blanco.|- Se trata de una relación fuerte y la columna "varios" contiene valores que no se almacenan en la columna "uno"; vea [Creación de relaciones de modelos en Power BI Desktop (Relaciones fuertes)](../desktop-relationships-understand.md#strong-relationships).<br />- Se trata de una relación de uno a uno sólida y las columnas relacionadas contienen espacios en blanco; vea [Creación de relaciones de modelos en Power BI Desktop (Relaciones fuertes)](../desktop-relationships-understand.md#strong-relationships).<br />- La columna "varios" de la relación inactiva almacena espacios en blanco o tiene valores que no están almacenados en el lado "uno".|
|Faltan datos en el objeto visual.|- Se aplican filtros incorrectos o inesperados.<br />- Se aplica la seguridad de nivel de fila.<br />- Se trata de una relación débil y hay espacios en blanco en las columnas relacionadas, o problemas de integridad de datos; vea [Creación de relaciones de modelos en Power BI Desktop (Relaciones débiles)](../desktop-relationships-understand.md#weak-relationships).<br />- Se trata de una relación entre dos tablas DirectQuery, la relación se configura para [asumir la integridad referencial](../desktop-relationships-understand.md#assume-referential-integrity), pero hay problemas de integridad de datos (valores no coincidentes en las columnas relacionadas).|
|La seguridad de nivel de fila no se aplica correctamente.|- Las relaciones no se propagan entre tablas, _siga la lista de comprobación anterior_.<br />- Se aplica la seguridad de nivel de fila, pero no se habilita la propagación de una relación bidireccional; consulte [Seguridad de nivel de fila (RLS) con Power BI Desktop](../desktop-rls.md)|
|||

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Relaciones de modelos en Power BI Desktop](../desktop-relationships-understand.md)
- ¿Preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
