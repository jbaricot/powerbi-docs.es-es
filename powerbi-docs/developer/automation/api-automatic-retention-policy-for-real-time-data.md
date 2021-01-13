---
title: API de análisis integrados de Power BI que usan la directiva de retención automática en datos en tiempo real para procurar una mejor información de BI insertada
description: Información sobre la directiva de retención automática en el servicio Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 81c975332abc4cb599a7172f1697c1b06ea34eba
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887739"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Directiva de retención automática para datos en tiempo real

La directiva de retención automática del servicio Power BI es un parámetro de cadena de consulta que habilita una directiva de retención predeterminada para limpiar de forma automática los datos antiguos y, al mismo tiempo, mantiene un flujo constante de datos nuevos en el panel. La primera directiva de retención se denomina *Primero en entrar, primero en salir (FIFO)*. Cuando se habilita, se recopilan los datos en una tabla hasta que se alcancen las 200.000 filas. Una vez que los datos superan las 200.000 filas, las filas más antiguas se eliminan del conjunto de datos. Esto mantiene entre 200.000 y 210.000 filas que contendrán solo los datos más recientes.  
  
<center>

![Directiva de retención](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Las directivas de retención se habilitan cuando se crean los conjuntos de datos. Lo único que debe hacer es agregar el parámetro de consulta de "directiva de retención predeterminada" a la llamada de los conjuntos de datos POST y establecer su valor en *basicFIFO*.  

```console
POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
```
