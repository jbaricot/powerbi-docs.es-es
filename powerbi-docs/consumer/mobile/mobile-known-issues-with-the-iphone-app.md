---
title: 'Solución de "errores de comunicación" en aplicaciones móviles de iOS: Power BI'
description: 'En este artículo puede se de ayuda si ve este mensaje: "Encontramos errores de comunicación. Es posible que estos errores estén relacionados con la configuración del proxy de la conexión Wi-Fi.'
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.openlocfilehash: 1af46edad96ce191798502a1887c6c402a0e7319
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415344"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>Solución de "errores de comunicación" en aplicaciones móviles de iOS: Power BI

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhones |iPad |

## <a name="we-encountered-communication-failures"></a>"Encontramos errores de comunicación"
"Encontramos errores de comunicación. Estos errores pueden estar relacionados con la configuración del proxy de la conexión Wi-Fi. Es posible que cambiar a otra conexión Wi-Fi resuelva el problema".

Este mensaje podría aparecer si la conexión a Internet del iPhone o iPad requiere configurar un proxy HTTP explícito obligatorio, ya sea manual o automático. En este caso, la aplicación de Power BI no funcionará en el dispositivo iOS.

### <a name="workaround"></a>Solución alternativa
Cambie el iPhone o el iPad a otra conexión que no requiera una configuración de proxy HTTP explícita (es decir, una donde la configuración de proxy HTTP esté desactivada).

## <a name="other-issues"></a>¿Otros problemas?
Pruebe a preguntar a la [Comunidad de Power BI](https://community.powerbi.com/).

