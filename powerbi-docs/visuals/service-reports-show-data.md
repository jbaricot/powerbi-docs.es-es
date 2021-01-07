---
title: Mostrar los datos que se utilizaron para crear la visualización de Power BI
description: En este documento se explica cómo mostrar los datos que se usaron para crear un objeto visual en Power BI y cómo exportar esos datos a un archivo .csv.
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 12/4/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 7aa15bae7ab94619a9f652aa20da9222e3d4af41
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721648"
---
# <a name="display-a-visualizations-underlying-data"></a>Visualización de los datos subyacentes de una visualización

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-nyyn.md)]    

## <a name="show-data"></a>Mostrar datos
Una visualización de Power BI se construye con datos provenientes de los conjuntos de datos. Si quiere ver lo que sucede en segundo plano, Power BI le permite *mostrar* los datos que se usan para crear el objeto visual. Cuando se selecciona **Mostrar datos**, Power BI muestra los datos que están situados debajo (o cerca) de la visualización.

También puede exportar los datos que se usan para crear la visualización como un archivo .xlsx o .csv y verlos en Excel. Para obtener más información, consulte [Exportar datos de visualizaciones de Power BI](power-bi-visualization-export-data.md).

> [!NOTE]
> Las opciones *Mostrar datos* y *Exportar datos* están disponibles en el servicio Power BI y Power BI Desktop. Pero Power BI Desktop proporciona un nivel adicional de detalle. Mediante [*Mostrar registros*, se muestran las filas reales del conjunto de datos](../create-reports/desktop-see-data-see-records.md).
> 
> 

## <a name="using-show-data"></a>Uso de *Mostrar datos* 
1. En Power BI Desktop, seleccione una visualización para activarla.

2. Seleccione **Más opciones** (...) y, después, **Mostrar datos**. 
    ![Mostrar opción para mostrar datos](media/service-reports-show-data/power-bi-more-action.png)


3. De manera predeterminada, los datos aparecen debajo del objeto visual.
   
   ![Presentación vertical de objeto visual y datos](media/service-reports-show-data/power-bi-show-data-below.png)

4. Para cambiar la orientación, seleccione el diseño vertical ![Captura de pantalla pequeña del icono que se usa para cambiar el diseño vertical](media/service-reports-show-data/power-bi-vertical-icon-new.png) en la esquina superior derecha de la visualización.
   
   ![Presentación horizontal de objeto visual y datos](media/service-reports-show-data/power-bi-show-data-side.png)
5. Para exportar los datos a un archivo .csv, seleccione los puntos suspensivos y elija **Exportar datos**.
   
    ![Selección de Exportar datos](media/service-reports-show-data/power-bi-export-data-new.png)
   
    Para obtener más información sobre cómo exportar los datos a Excel, consulte [Exportar datos de visualizaciones de Power BI](power-bi-visualization-export-data.md).
6. Para ocultar los datos, anule la selección de **Explorar** > **Mostrar datos**.

## <a name="using-show-records"></a>Uso de Mostrar registros
También puede centrarse en un registro de datos de una visualización y profundizar en los detalles que contiene. 

1. Para usar **Ver registros**, seleccione una visualización para activarla. 

2. En la cinta de opciones Escritorio, seleccione la pestaña de **Herramientas de objetos visuales**  > **Datos y detalles**  > **Ver registros**. 

    ![Captura de pantalla con la opción Ver registros seleccionada.](media/service-reports-show-data/power-bi-see-record.png)

3. Seleccione un punto de datos o una fila en la visualización. En este ejemplo hemos seleccionado la cuarta columna desde la izquierda. Power BI nos muestra el registro del conjunto de datos de este punto de datos.

    ![Captura de pantalla de un registro individual de un conjunto.](media/service-reports-show-data/power-bi-row.png)

4. Seleccione **Volver al informe** para volver al lienzo de informe del Escritorio. 

## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

- Si el botón **Ver registros** de la cinta está deshabilitado y en gris, significa que la visualización seleccionada no admite Ver registros.
- No puede cambiar los datos de la vista Ver registros y guardarlos de nuevo en el informe.
- No se puede usar Ver registros cuando el objeto visual utilice una medida calculada en un modelo multidimensional.
- No se puede usar Ver registros al conectarse a un modelo multidimensional (MD) activo.  

## <a name="next-steps"></a>Pasos siguientes
[Exportación de datos de visualizaciones de Power BI](power-bi-visualization-export-data.md)    

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)


