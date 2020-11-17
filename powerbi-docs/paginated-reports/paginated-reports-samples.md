---
title: Informes paginados de Power BI de ejemplo
description: En este artículo, obtendrá información sobre cómo descargar y usar informes paginados de Power BI de ejemplo.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/10/2020
ms.openlocfilehash: cfa4b46e521079802ec87b63d6323e01213625c3
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483928"
---
# <a name="sample-power-bi-paginated-reports"></a>Informes paginados de Power BI de ejemplo


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

En este artículo se proporcionan información y vínculos a varios ejemplos de informes paginados de Power BI para descargar y explorar. Ilustran las maneras habituales de usar los informes paginados.

## <a name="prerequisites"></a>Requisitos previos

- Puede compartir estos informes en línea, tal como están, sin necesidad de hacer cambios. Para ello, necesita una licencia de Power BI Pro. Regístrese para obtener una [evaluación gratuita de una licencia de Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro).
- También necesita acceso a un área de trabajo de Power BI en una [capacidad Premium](../admin/service-premium-what-is.md).
- Para editar estos informes tendrá que [instalar Power BI Report Builder](https://aka.ms/pbireportbuilder) desde el Centro de descarga de Microsoft.
- Bien, está a punto para descargar estos informes paginados de ejemplo de GitHub. No necesita una cuenta de GitHub. 

## <a name="download-the-reports"></a>Descargar los informes

Para descargar los informes correctamente, debe descargar el repositorio como archivo .zip y, luego, extraer el contenido. Los informes paginados son archivos .rdl.

1. Abra el [repositorio Reporting Services de GitHub](https://github.com/microsoft/Reporting-Services).
1. Seleccione la flecha del botón verde **Code** (Código) > **Download ZIP** (Descargar archivo .zip).

    :::image type="content" source="media/paginated-reports-samples/paginated-report-download-zip.png" alt-text="Captura de pantalla del repositorio de GitHub que contiene los informes paginados de Power BI de ejemplo.":::
    
1. Abra el archivo, seleccione **Extraer todo** y elija una ubicación para los archivos. De forma predeterminada, el nombre de la carpeta es **Reporting-Services-master**.
1. Abra la carpeta **Reporting-Services-master** y, luego, la carpeta **PaginatedReportSamples**.

    >[!NOTE]
    >Puede eliminar todas las demás carpetas de la carpeta **Reporting-Services-master**, ya que contienen otros ejemplos que no necesita.

1. Seleccione uno de los archivos .rdl para abrirlo en Power BI Report Builder.
1. Ahora ya puede [publicar el informe paginado en el servicio Power BI](paginated-reports-save-to-power-bi-service.md).

## <a name="invoice"></a>Factura

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="Captura de pantalla del ejemplo de informe paginado de Power BI relativo a una factura.":::


Este informe paginado es una factura independiente. El escenario de este informe es que quiere una factura que se pueda imprimir con una calidad de píxeles perfecta. Debe mostrar el total de ventas con detalles de las descripciones de los elementos, las cantidades, los descuentos y el costo.

En este ejemplo se resaltan características únicas para crear facturas reales, como las siguientes:  

- Región de datos Tablix (la región de datos subyacente a tablas y matrices). Muestra el contenido específico del usuario generado de forma dinámica, así como el tema.
- Región de datos rectangular que se coloca en cada fila de la región de datos Tablix del cuerpo del informe.
- Elementos de informe como cuadros de texto y líneas.
- Parámetro del informe para seleccionar el contenido dinámicamente. El contenido que se muestra se aplica a un tema específico mediante marcadores de posición de expresión. 

Origen de datos: incluido en el archivo .rdl

## <a name="labels"></a>Etiquetas

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="Captura de pantalla de las etiquetas del informe paginado.":::

Este es un ejemplo de un informe paginado independiente. Se trata de un informe de varias columnas que tiene un tamaño perfecto para ajustarse al diseño de impresión de la plantilla de la etiqueta de correo. 

Los informes de etiquetas son sencillos, pero tienen algunas características únicas para crear una etiqueta paginada:

- Región de datos Tablix con un recuento fijo de tres columnas, con el espaciado de columnas definido.
- Región de datos rectangular que se repite en las filas y columnas de la página impresa.
- Parámetro del informe para seleccionar el contenido que se va a mostrar en cada región de datos rectangular.

Origen de datos: incluido en el archivo .rdl

## <a name="mailing-letter"></a>Carta de correo

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="Captura de pantalla del ejemplo de informe paginado de Power BI relativo a una carta.":::

Este ejemplo de informe paginado independiente está diseñado para crear cartas de correo reales. El escenario de este informe es que quiere una carta que se pueda imprimir con una calidad de píxeles perfecta y con contenido dinámico.

Este ejemplo tiene características únicas, como las siguientes: 

- Región de datos rectangular que se coloca en diferentes secciones del cuerpo del informe. 
- Imágenes para personalizar la carta. 
- Región de datos Tablix (la subyacente a tablas y matrices). La región de datos Tablix muestra el contenido específico del usuario generado de forma dinámica.
- Elementos de informe como cuadros de texto y líneas.
- Parámetro del informe para seleccionar el contenido dinámicamente. El contenido que se muestra se aplica a un tema específico mediante marcadores de posición de expresión. 

Origen de datos: incluido en el archivo .rdl

## <a name="transcript"></a>Transcripción

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="Captura de pantalla del ejemplo de informe paginado de Power BI relativo a una transcripción.":::

El escenario de este informe es que quiere una transcripción que se pueda imprimir con una calidad de píxeles perfecta. Debe incluir contenido dinámico que muestre los detalles y las fechas de la descripción del programa de cada alumno.

Este ejemplo de informe paginado independiente tiene características únicas, como las siguientes: 

- Región de datos Tablix (la subyacente a tablas y matrices). La región de datos Tablix muestra el contenido específico del usuario generado de forma dinámica mediante grupos de filas anidadas.
- Regiones de datos rectangulares que se colocan en diferentes secciones del cuerpo del informe.
- Elementos de informe como cuadros de texto y líneas.

Origen de datos: incluido en el archivo .rdl

## <a name="sales-performance"></a>Rendimiento de ventas

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="Captura de pantalla del ejemplo de informe paginado de Power BI relativo al rendimiento de las ventas.":::

Rendimiento de las ventas por países es un ejemplo de informe paginado independiente. El escenario de este informe es que quiere una factura que se pueda imprimir con una calidad de píxeles perfecta para ver los totales de las ventas y los detalles. Muestra estas características:

- Uso de un parámetro para expandir los detalles de la tabla.
- Encabezados y pies de página.
- Elementos del informe como cuadros de texto, líneas y rectángulos con marcadores de posición de expresiones.
- Barras de datos.
- Líneas de tendencia.
- Paneles de medidores.

Origen de datos: incluido en el archivo .rdl
  
## <a name="next-steps"></a>Pasos siguientes

[Visualización de un informe paginado en el servicio Power BI](../consumer/paginated-reports-view-power-bi-service.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
