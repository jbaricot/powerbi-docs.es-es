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
ms.openlocfilehash: 5f4067e77631f22951844c0d4d64b06e5e2e30cc
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079586"
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
  
## <a name="see-also"></a>Vea también

* [Restricciones y límites del servicio Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
* [Información general sobre la API de REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/)