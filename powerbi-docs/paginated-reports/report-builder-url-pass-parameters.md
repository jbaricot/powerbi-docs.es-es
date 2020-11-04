---
title: 'Pasar un parámetro de informe en una URL para un informe paginado: Generador de informes de Power BI'
description: En este tema se describe cómo pasar parámetros de informe a un informe incluyéndolos en una URL de informe paginado.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: f103f29c61d1a4e4a5340d97598d80a86c708701
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298046"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Pasar un parámetro de informe en una URL para un informe paginado en Power BI 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Puede pasar parámetros de informe a un informe incluyéndolos en una URL de informe paginado. Todos los parámetros de consulta pueden tener parámetros de informe correspondientes. Por lo tanto, para pasar un parámetro de consulta a un informe, se pasa el parámetro de informe correspondiente. Debe agregar un prefijo al nombre del parámetro con `rp:` para que Power BI lo reconozca en la dirección URL. 

Los parámetros de informe distinguen entre mayúsculas y minúsculas y usan estos caracteres especiales: 

- Un espacio en la parte del parámetro de la dirección URL se reemplaza por un signo más (+).  Por ejemplo: 

    ```rp:Holiday=Christmas+Day```

- Un punto y coma en cualquier parte de la cadena se reemplaza con los caracteres `%3A`.

Los exploradores deberían realizar de forma automática la codificación de dirección URL apropiada. No tiene que codificar ninguno de los caracteres manualmente. 

Para establecer un parámetro de informe dentro de una dirección URL, use la siguiente sintaxis: 

```
rp:parameter=value
```

Por ejemplo, para especificar dos parámetros, "Salesperson" y "State", definidos en un informe de Mi área de trabajo, usaría esta URL: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Para especificar los mismos dos parámetros definidos en un informe en una aplicación, usaría esta URL: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&rp:State=Utah 
```

Para pasar un valor NULL para un parámetro, use la siguiente sintaxis: 

```
parameter:isnull=true
```

Por ejemplo:

```
rp:SalesOrderNumber:isnull=true
```

Para pasar un valor booleano, use 0 para false y 1 para true. Para pasar un valor Float, incluya el separador decimal de la configuración regional del servidor.

> [!NOTE]
> Si el informe contiene un parámetro de informe con un valor predeterminado y el valor de la propiedad **Prompt** es **false** (es decir, la propiedad **Prompt User** no está seleccionada en el Administrador de informes), no se puede pasar un valor para ese parámetro de informe dentro de una dirección URL. Esto proporciona a los administradores la opción de impedir que los usuarios finales agreguen o modifiquen los valores de determinados parámetros de informe.
> 
> Power BI no admite una cadena de consulta de más de 2000 caracteres.  Este valor se puede superar si se usan parámetros URL para ver el informe paginado,  especialmente si se emplean parámetros con varios valores.

## <a name="additional-examples"></a>Ejemplos adicionales 

En el siguiente ejemplo de URL se incluye un parámetro de varios valores "Salesperson". El formato para un parámetro multivalor es repetir el nombre del parámetro para cada valor. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

En el siguiente ejemplo de URL se pasa un único parámetro de SellStartDate con un valor de "7/1/2005" para un servidor de informes en modo nativo.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Pasos siguientes

- [Parámetros de dirección URL en informes paginados en Power BI](report-builder-url-parameters.md)
- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
