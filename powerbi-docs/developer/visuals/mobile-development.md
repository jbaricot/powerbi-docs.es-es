---
title: Desarrollo para dispositivos móviles
description: Cómo crear objetos visuales de Power BI preparados para dispositivos móviles
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 38e6ac3be143381304f1fdfc8e1427b91f398a9a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82196638"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>Cómo crear objetos visuales de Power BI preparados para dispositivos móviles
El consumo móvil desempeña un papel importante en Power BI. Una de sus ventajas es que permite permanecer conectado a los datos en cualquier momento y lugar.

Como desarrollador encargado de la creación de objetos visuales de Power BI, debe abordar las restricciones únicas de cada dispositivo móvil para llegar a tantos usuarios como sea posible y proporcionar la mejor experiencia móvil.

Use la [aplicación de Power BI para Windows, iOS y Android](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices) para poner al alcance de la mano de los usuarios empresariales una vista completa de sus datos en cualquier lugar.

## <a name="requirements"></a>Requisitos

Los siguientes requisitos son esenciales para el desarrollo de objetos visuales preparados para dispositivos móviles:

- Representación

  Los objetos visuales de Power BI deben representarse en todos los dispositivos móviles compatibles, incluidos los exploradores y aplicaciones admitidos, sin errores en los informes o los paneles ni cuando se ejecutan en modo de **enfoque**. 

- Interactive

  La funcionalidad interactiva debe proporcionarse de la misma manera que para los dispositivos de escritorio. Es necesario admitir todos los eventos que se controlan en exploradores de escritorio o disponer de controladores de eventos comparables para dispositivos móviles.
  
  Por ejemplo, la navegación básica y la selección de puntos de datos deben tener las mismas funcionalidades que en los exploradores de escritorio. Si un objeto visual admite la selección múltiple mediante **CTRL**, el desarrollador debe considerar la posibilidad de agregar un controlador de eventos similar para dispositivos móviles.

  En la tabla siguiente se proporciona una lista de los eventos correspondientes en los dispositivos móviles.

  | Nombre del evento de mouse | Nombre del evento táctil |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | Usar una biblioteca externa |
  | `contextmenu` | Usar una biblioteca externa |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (o biblioteca externa) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > No todos los dispositivos móviles o de pantalla táctil admiten eventos de mouse (o con el prefijo *mouse*). En tales casos, controle los eventos de *mouse* y *táctiles* al mismo tiempo.

## <a name="optional"></a>Opcional
Lo que se incluye a continuación se considera opcional y se usa para crear una mejor experiencia del usuario final.

- Representación

  Si quiere admitir tamaños más pequeños para los objetos visuales, pruebe a agregar opciones de formato que el usuario pueda cambiar para ajustar el tamaño de cada elemento. Por ejemplo, agregue opciones de formato a las etiquetas, para su uso en informes y paneles. Esto permite a los usuarios personalizar un objeto visual específicamente para su dispositivo móvil.
  
  La misma configuración se puede aplicar también a los objetos visuales de los exploradores de escritorio y, si es necesario, invalidarse para adaptar el objeto visual a pantallas más pequeñas.

  > [!NOTE]
  > Para optimizar un objeto visual en el modo de **enfoque**, deben tenerse en cuenta las orientaciones de tamaño de pantalla vertical y horizontal. Consulte [Mostrar el contenido en modo de enfoque](/power-bi/consumer/end-user-focus).

- Interactive

  Considere la posibilidad de agregar controladores de eventos específicos para dispositivos móviles, como arrastrar y desplazarse.

- Conmutación por error

  Un objeto visual debería mostrar un error descriptivo si no se puede representar en el dispositivo móvil.

## <a name="supported-browsers-and-devices"></a>Exploradores y dispositivos compatibles
El objeto visual de Power BI debe representarse en todos los dispositivos que admiten aplicaciones de Power BI. Para obtener más información, consulte [Exploradores compatibles con Power BI](/power-bi/power-bi-browsers) y [Aplicaciones móviles de Power BI](/power-bi/consumer/mobile/mobile-apps-for-mobile-devices).

Al realizar pruebas en los modelos más recientes de dispositivos Windows, iOS y Android, el desarrollador debe tener en cuenta la mayoría de estas cuestiones relacionadas con la calidad.

## <a name="next-steps"></a>Pasos siguientes
Para empezar, consulte [Tutorial: Desarrollar un objeto visual de Power BI](/power-bi/developer/visuals/custom-visual-develop-tutorial).
