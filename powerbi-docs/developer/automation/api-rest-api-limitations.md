---
title: Limitaciones de la API REST de Power BI en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: La API de REST de Power BI tiene las siguientes limitaciones. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 1196917f0223ccde012d203d75c4e96fbc3b9dcf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887670"
---
# <a name="power-bi-rest-api-limitations"></a>Limitaciones de la API de REST de Power BI  
  
**Para filas POST**
  
* 75 columnas como máximo
* 75 tablas como máximo
* Un máximo de 10.000 filas para cada solicitud POST de filas  
* 1.000.000 de filas agregadas por hora por cada conjunto de datos  
* Un máximo de 5 solicitudes POST de filas pendientes por cada conjunto de datos  
* 120 solicitudes POST de filas por minuto por cada conjunto de datos
* Si la tabla tiene 250 000 o más filas, 120 solicitudes de filas POST por hora por conjunto de datos
* Un máximo de 200.000 filas almacenadas por tabla en el conjunto de datos FIFO
* Un máximo de 5 millones de filas almacenadas por tabla en el conjunto de datos "none retention policy"  
* 4.000 caracteres por valor para las columnas de cadena en la operación POST de filas
  
## <a name="see-also"></a>Consulte también

* [Restricciones y límites del servicio Azure AD](/azure/active-directory/active-directory-service-limits-restrictions)   
* [Información general sobre la API de REST de Power BI](/rest/api/power-bi/)