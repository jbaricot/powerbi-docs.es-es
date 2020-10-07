---
title: Limitaciones de la API de REST de Power BI
description: La API REST de Power BI tiene las siguientes limitaciones
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: de9fd241959b679a0da7926cd6b2254689afbfd2
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2020
ms.locfileid: "91747284"
---
# <a name="power-bi-rest-api-limitations"></a>Limitaciones de la API de REST de Power BI  
  
**Para filas POST**
  
* 75 columnas como máximo
* 75 tablas como máximo
* Un máximo de 10.000 filas para cada solicitud POST de filas  
* 1\.000.000 de filas agregadas por hora por cada conjunto de datos  
* Un máximo de 5 solicitudes POST de filas pendientes por cada conjunto de datos  
* 120 solicitudes POST de filas por minuto por cada conjunto de datos
* Si la tabla tiene 250 000 o más filas, 120 solicitudes de filas POST por hora por conjunto de datos
* Un máximo de 200.000 filas almacenadas por tabla en el conjunto de datos FIFO
* Un máximo de 5 millones de filas almacenadas por tabla en el conjunto de datos "none retention policy"  
* 4\.000 caracteres por valor para las columnas de cadena en la operación POST de filas
  
## <a name="see-also"></a>Consulte también

* [Restricciones y límites del servicio Azure AD](/azure/active-directory/active-directory-service-limits-restrictions)   
* [Información general sobre la API de REST de Power BI](/rest/api/power-bi/)