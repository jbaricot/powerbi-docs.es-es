---
title: Incorporación de bibliotecas externas a objetos visuales de Power BI
description: En este artículo se describe cómo usar bibliotecas externas en objetos visuales de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: 9df111e7545c43fe9b75784b1a95df4f37fd01e7
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114138"
---
# <a name="adding-external-libraries"></a>Adición de bibliotecas externas

En este artículo se describe cómo usar bibliotecas externas en objetos visuales de Power BI. Incluye información sobre cómo instalar, importar y llamar a bibliotecas externas desde el código del objeto visual de Power BI.

## <a name="javascript-libraries"></a>Bibliotecas de JavaScript

1. Instale una biblioteca de JavaScript externa con cualquier administrador de paquetes, como *npm* o *yarn*.
2. Importe los módulos necesarios en los archivos de origen mediante la biblioteca externa.

>[!NOTE]
>Si quiere agregar escrituras a la biblioteca de JavaScript y obtener IntelliSense y seguridad en tiempo de compilación, asegúrese de instalar el paquete adecuado.

### <a name="installing-the-d3-library"></a>Instalación de la biblioteca d3

Este es un ejemplo de instalación de la [biblioteca d3](https://www.npmjs.com/package/d3) y el [@types/d3paquete ](https://www.npmjs.com/package/@types/d3), con [npm](https://www.npmjs.com/).

Para ver un ejemplo completo, consulte el código de [visualizaciones de Power BI](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Instale el paquete *d3* y el paquete de *tipos de d3*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importe la biblioteca *d3* en los archivos que la usan, como `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>Marco de CSS

1. Instale un marco de CSS externo con cualquier administrador de paquetes, como *npm* o *yarn*.
2. En el archivo `.less` del objeto visual, incluya la instrucción `import`.

### <a name="installing-bootstrap"></a>Instalación de bootstrap

Este es un ejemplo de instalación de [bootstrap](https://www.npmjs.com/package/bootstrap) mediante [npm](https://www.npmjs.com/).

Para ver un ejemplo completo, consulte el código de [visualizaciones de Power BI](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Instale el paquete *bootstrap*.

    ```powershell
    npm install bootstrap --save
    ```

2. Incluya la instrucción `import` en `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
