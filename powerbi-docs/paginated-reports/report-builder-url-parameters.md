---
title: 'Parámetros de dirección URL en informes paginados: Generador de informes de Power BI'
description: En este tema se describen los usos comunes de los parámetros de informe de Power BI Report Builder, las propiedades que puede establecer y mucho más.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 09/09/2020
ms.openlocfilehash: f81cf6625f02f71b1ccf8bcd2c442ded3329083d
ms.sourcegitcommit: 002c140d0eae3137a137e9a855486af6c55ad957
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89642389"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Parámetros de dirección URL en informes paginados en Power BI

Puede enviar comandos a informes paginados en Power BI agregando un parámetro a una dirección URL. Por ejemplo, es posible que haya visto el informe con un conjunto específico de valores de parámetro de informe. Para encapsular esta información en la dirección URL, use los parámetros de acceso URL predefinidos. Puede personalizar aún más el modo en que Power BI procesa el informe mediante la inserción de parámetros para representar formatos o para la apariencia de la barra de herramientas de informe. Después, pegue esta dirección URL directamente en un correo o una página web para que otros usuarios puedan ver el informe de la misma manera en el explorador. 

Estas son las acciones que puede realizar a través de los parámetros de acceso URL: 

- Enviar parámetros de informe a un informe. 
- Iniciar la exportación del contenido del informe en un formato de archivo compatible. 
- Ocultar o ver el panel de parámetros. 
- Especificar la configuración DeviceInfo. 

Para obtener una lista completa de los comandos y las configuraciones disponibles a través del acceso URL, vea  [Referencia de parámetros de acceso URL](#url-access-parameter-reference) más adelante en este artículo. 

## <a name="url-access-concepts"></a>Conceptos de acceso URL 

Las solicitudes URL a Power BI contienen parámetros que el servicio se encarga de procesar. La forma en que el servicio controla las solicitudes URL depende de los parámetros, los prefijos de parámetro y los tipos de elementos que se incluyen en la dirección URL. La función URL de informe paginado es compatible con la mayoría de los exploradores y las aplicaciones que admiten el direccionamiento de direcciones URL estándar. 

## <a name="url-access-syntax"></a>Sintaxis de acceso URL 

Las solicitudes URL pueden contener varios parámetros, que se enumeran en cualquier orden. Los parámetros están separados por una Y comercial (&). Los pares de nombre y valor están separados por un signo de igual (=). Por ejemplo:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>Descripción de la sintaxis 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

La URL del servicio web del inquilino de Power BI. Por ejemplo: 

**&** Se usa para separar los pares de nombre y valor de los parámetros de acceso URL.

**prefix** Prefijo para el parámetro de URL (por ejemplo, rp: or rdl:) que especifica una acción en el servicio Power BI. 

> [!NOTE]
> Los parámetros de informe necesitan un prefijo de parámetro y distinguen entre mayúsculas y minúsculas. 

**parameter** Nombre del parámetro. 

### <a name="value"></a>value 

Texto de la URL que corresponde al valor del parámetro que se está usando. 

Para obtener ejemplos de cómo pasar parámetros de informe en la URL, vea  [Pasar un parámetro de informe en una URL](report-builder-url-pass-parameters.md).

## <a name="url-access-parameter-reference"></a>Referencia de parámetros de acceso URL

Puede usar los siguientes parámetros como parte de una URL para configurar la apariencia de los informes paginados en Power BI. En esta sección se enumeran los parámetros más comunes. Los parámetros no distinguen entre mayúsculas y minúsculas y empiezan con el prefijo de parámetro  `rdl:`  si están relacionados con el formato de salida.  

### <a name="report-commands-rdl"></a>Comandos de informe (`rdl:`) 

**Formato de exportación** Especifica el formato en el que se va a representar y exportar un informe.

Ejemplo: rdl:format=PDF

Valores disponibles:
 
- PPTX (PowerPoint)
- MHTML 
- IMAGEN 
- EXCELOPENXML (EXCEL) 
- WORDOPENXML (WORD) 
- CSV 
- PDF 
- ACCESSIBLEPDF (PDF)
- XML 

**Vista de informe** Especifica el tipo de vista que se usa para mostrar el informe.

-   rdl:reportView

    - "interactive" (valor predeterminado): carga el informe en modo interactivo.
    - "pageView": carga el informe en el modo de vista de página.

**Panel de parámetros**: especifica si el panel de parámetros está cerrado o abierto cuando se carga el informe, o si está oculto por completo.

-   rdl:parameterPanel

    - "contraído": carga el informe con el panel de parámetros cerrado. El botón de parámetros está habilitado para que los usuarios puedan hacer clic en el botón y expandirlo;
    - "oculto": carga el informe con el panel de parámetros cerrado y el botón de parámetros deshabilitado;
    - "expandido" (valor predeterminado): carga el informe con el panel de parámetros abierto y el botón de parámetros habilitado;

**Información del dispositivo**: puede especificar parámetros de salida adicionales para los siguientes formatos de exportación. 

PDF / ACCESSIBLEPDF:

- rdl:AccessiblePDF=true/false
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:HumanReadablePDF=true/false
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
    - rdl:StartPage=integer
    
CSV:

- rdl:Encoding=string
- rdl:ExcelMode=true/false
- rdl:FieldDelimiter=string
- rdl:NoHeader=true/false
- rdl:Qualifier=string
- rdl:RecordDelimiter=string
- rdl:SuppressLineBreaks=true/false
    - rdl:UseFormattedValues=true/false
    
WORDOPENXML (WORD):

- rdl:AutoFit=string -> True/False/Never/Default
- rdl:ExpandToggles=true/false
- rdl:FixedPageWidth=true/false
- rdl:OmitHyperlinks=true/false
- rdl:OmitDrillthroughs=true/false

EXCELOPENXML (EXCEL):

- rdl:OmitDocumentMap=true/false
- rdl:OmitFormulas=true/false
    - rdl:SimplePageHeaders=true/false
    
PPTX (PowerPoint):
 
- rdl:Columns=integer
- rdl:ColumnSpacing=decimal(in)
- rdl:DpiX=integer
- rdl:DpiY=integer
- rdl:EndPage=integer
- rdl:MarginBottom=decimal(in)
- rdl:MarginLeft=decimal(in)
- rdl:MarginRight=decimal(in)
- rdl:MarginTop=decimal(in)
- rdl:PageHeight=decimal(in)
- rdl:PageWidth=decimal(in)
- rdl:StartPage=integer
    - rdl:UseReportPageSize=true/false

XML:

- rdl:XSLT=string
- rdl:MIMEType=string
- rdl:UseFormattedValues=true/false
- rdl:Indented=true/false
- rdl:OmitNamespace=true/false
- rdl:OmitSchema=true/false
- rdl:Encoding=string
- rdl:Schema=true/false

**Abra hipervínculo en la misma ventana del explorador** Puede anexar "rdl:targetSameWindow=true" a la dirección URL del hipervínculo en el informe para que Power BI lo abra en la misma ventana del explorador. Para obtener información sobre cómo agregar hipervínculos a un informe, vea [Adición de un hipervínculo a una dirección URL](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-hyperlink-to-a-url-report-builder-and-ssrs) en la documentación de SQL Server Reporting Services.

## <a name="next-steps"></a>Pasos siguientes

- [Pasar un parámetro de informe en una URL para un informe paginado en Power BI](report-builder-url-pass-parameters.md)
- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)
