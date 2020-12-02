---
title: Exportación de informes a PDF
description: Obtenga información sobre cómo exportar un informe de Power BI a PDF.
author: mihart
ms.author: mihart
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: de9265112d587418345c2eadb8d33acdddf900d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96399704"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>Exportación de informes de Power BI a PDF

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Con Power BI, puede publicar el informe en formato PDF y crear fácilmente un documento basado en el informe de Power BI. Al exportar a PDF, cada página del informe de Power BI se convierte en una página individual en el documento PDF.

## <a name="export-your-power-bi-report-to-pdf"></a>Exportación del informe de Power BI a PDF
En el servicio Power BI, seleccione un informe para mostrarlo en el lienzo. También puede seleccionar un informe en la página **Inicio**, **Aplicaciones** o en cualquier otro contenedor del panel de navegación.

1. Seleccione **Exportar** > **PDF** en la barra de menús.

    ![Selección de Exportar en la barra de menús](media/end-user-pdf/power-bi-export-pdfs.png)

    Aparece una ventana emergente en la que tiene la opción de seleccionar los **Valores actuales** o los **Valores predeterminados**. Los **valores actuales** exportan el informe en el estado actual, lo que incluye los cambios activos que haya realizado en los valores de filtro o segmentación. La mayoría de los usuarios seleccionan esta opción. Como alternativa, al seleccionar **Valores predeterminados** se exporta el informe en su estado original, como lo haya compartido el *diseñador*, y no se reflejan los cambios que haya realizado en ese estado original.
    
    Además, hay una casilla para seleccionar si se quieren exportar o no las pestañas ocultas de un informe. Seleccione esta casilla si solo quiere exportar las pestañas del informe que son visibles para usted en el explorador. Si prefiere incluir todas las pestañas ocultas como parte de la exportación, puede dejar desactivada esta casilla. Si la casilla aparece atenuada, significa que no hay ninguna pestaña oculta en el informe. Seleccione **Exportar** para continuar cuando haya realizado las selecciones.
    
    También puede optar por exportar solo la página que esté viendo de un informe activando la opción **Exportar solo la página actual**.  De forma predeterminada, esta opción está desactivada y se exportarán todas las páginas del informe.
    
    En la esquina superior derecha se muestra una barra de progreso. La exportación puede tardar unos minutos. Puede continuar trabajando en Power BI mientras se exporta el informe.

    ![Mensaje de progreso de la exportación](media/end-user-pdf/power-bi-export-progress.png)

    Cuando el servicio Power BI termina el proceso de exportación, el banner de notificación cambiará para informarle.

2. El archivo está disponible donde el explorador muestra los archivos descargados. En la siguiente imagen, se muestra como un banner de descarga en la parte inferior de la ventana del explorador.

    ![Ubicación del archivo descargado](media/end-user-pdf/power-bi-export-done.png)

Y eso es todo. Puede descargar el archivo y abrirlo con cualquier visor de PDF, como el disponible en Microsoft Edge.


## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones
Hay algunas consideraciones y limitaciones que se deben tener en cuenta cuando se trabaja con la característica **Exportar a PDF**.

* El PDF incluirá los datos y las visualizaciones visibles en el lienzo de Power BI. Si el objeto visual incluye barras de desplazamiento, el PDF incluirá el objeto visual en su estado predeterminado no desplazado.  
* En la actualidad, no se admiten objetos visuales de R y Python. En el archivo PDF, estos objetos visuales están en blanco y muestran un mensaje de error. 
* Se admiten los objetos visuales de Power BI que se han certificado. Para obtener más información sobre los objetos visuales de Power BI certificados, incluido cómo obtener un objeto visual de Power BI certificado, vea [Obtención de un objeto visual de Power BI certificado](../developer/visuals/power-bi-custom-visuals-certified.md). No se admiten los objetos visuales de Power BI que no se hayan certificado. En el archivo PDF, se muestran con un mensaje de error.
* Este objeto visual de ESRI no se admite.
* Actualmente no se pueden exportar informes de más de 50 páginas.
* El proceso de exportación del informe a PDF puede tardar unos minutos en completarse, por lo que debe tener paciencia. Entre los factores que pueden afectar al tiempo requerido está la estructura del informe y la carga actual del servicio Power BI.
* Si el elemento de menú **Exportar a PDF** no está disponible en el servicio Power BI, probablemente se deba a que el administrador de Power BI haya deshabilitado la característica. Póngase en contacto con el administrador para obtener información detallada.
* Las imágenes de fondo se recortan con el área de límite del gráfico. Se recomienda quitar las imágenes de fondo antes de realizar la exportación a PDF.
* Los informes que pertenecen a un usuario situado fuera del dominio del inquilino de Power BI como, por ejemplo, un informe de alguien de fuera de la organización y que han compartido con usted, no pueden publicarse en PDF.
* Si se comparte un panel con alguien de fuera de su organización y, por lo tanto, con un usuario que no está en su inquilino de Power BI, ese usuario no podrá exportar a PDF los informes asociados del panel compartido. Por ejemplo, si es aaron@contoso.com, puede compartir con cassie@northwinds.com. Pero cassie@northwinds.com no puede exportar los informes asociados a PDF.
* Al exportar a PDF con informes que contienen una imagen de fondo, puede que vea una imagen distorsionada en la exportación si usa las opciones **Normal** o **Rellenar** para el **Fondo de página**. Para obtener mejores resultados, use la opción **Ajustar** para evitar incidencias con el documento exportado.
* El servicio Power BI usa su propia configuración de idioma como idioma para la exportación de PDF. Para ver o configurar las preferencias de idioma, seleccione el icono de engranaje ![Icono de engranaje](media/end-user-powerpoint/power-bi-settings-icon.png) > **Configuración** > **General** > **Idioma**.
* Actualmente no se respetan los filtros de las direcciones URL al elegir **Valores actuales** para la exportación.
* Los informes con tamaños de página personalizados inusuales pueden experimentar problemas en escenarios de exportación. Para obtener los mejores resultados, considere la posibilidad de cambiar a un tamaño de página estándar para el informe.
* Al exportar a PDF, en los informes que usen temas con fuentes personalizadas se reemplazará la fuente personalizada por una fuente predeterminada.
* Aunque el objetivo es proporcionar una experiencia coherente, no se puede garantizar que el PDF exportado desde el servicio Power BI siempre coincidirá con el PDF exportado desde un archivo de Power BI Desktop local.
* Al exportar a PDF, no se puede garantizar una fidelidad hasta el más mínimo detalle para los informes de PBIX.

## <a name="next-steps"></a>Pasos siguientes
[Imprimir un informe](end-user-print.md)
