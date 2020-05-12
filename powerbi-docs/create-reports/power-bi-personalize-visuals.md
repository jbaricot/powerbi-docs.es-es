---
title: Permitir a los usuarios personalizar los objetos visuales en un informe
description: Permita que los lectores del informe creen su propia vista de un informe, sin modificarlo.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867125"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permitir a los usuarios personalizar los objetos visuales en un informe

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Al compartir un informe con un público amplio, es posible que algunos de los usuarios prefieran tener una vista diferente de determinados objetos visuales. Es posible que quieran cambiar lo que hay en el eje, cambiar el tipo de objeto visual o agregar algo a la información sobre herramientas. Es difícil crear un solo objeto visual que satisfaga los requisitos de todos. Con esta nueva capacidad, puede permitir a los consumidores explorar y personalizar objetos visuales, todo ello en la vista de lectura del informe. Pueden ajustar el objeto visual como quieran y guardarlo como un marcador para volver a él. No necesitan tener permiso para editar el informe ni ponerse en contacto con el autor del informe para hacer cambios.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalizar un objeto visual":::
 
## <a name="what-report-consumers-can-change"></a>Qué pueden cambiar los consumidores del informe

Esta característica permite a los consumidores obtener información adicional a través de la exploración ad hoc de objetos visuales en un informe de Power BI. La característica es ideal para los creadores de informes que quieran habilitar escenarios de exploración básicos para los lectores de informes. Estas son las modificaciones que pueden realizar los lectores de informes:

- Cambiar el tipo de visualización
- Intercambiar una medida o una dimensión
- Agregar o quitar una leyenda
- Comparar dos o más medidas
- Cambiar agregaciones, etc.

Esta característica no solo permite nuevas capacidades de exploración, sino que también incluye otras maneras de que los consumidores capturen y compartan sus cambios:

- Capturar los cambios
- Compartir los cambios
- Restablecer todos los cambios para un informe
- Restablecer todos los cambios para un objeto visual
- Borrar los cambios recientes

## <a name="turn-on-the-preview-feature"></a>Habilitar la característica en vista previa

Puesto que esta característica está en vista previa, primero debe activar el cambio de características. Vaya a **Archivo** > **Opciones y configuración** > **Opciones**. En **Configuración global** > **Características en vista previa**, asegúrese de que **Personalizar objetos visuales** está seleccionado.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="Activar la personalización de objetos visuales":::

Es posible que tenga que reiniciar Power BI Desktop para verlo en la configuración del archivo actual.

## <a name="enable-personalization-in-a-report"></a>Habilitar la personalización en un informe

Después de activar la modificación de vista previa, deberá habilitarla específicamente para los informes para los que quiere que los consumidores puedan personalizar objetos visuales.

Puede habilitar la característica en Power BI Desktop o en el servicio Power BI.

### <a name="in-power-bi-desktop"></a>En Power BI Desktop

Para habilitar la característica en Power BI Desktop, vaya a **Archivo** > **Opciones y configuración** > **Opciones** > **Archivo actual** > **Configuración del informe**. Asegúrese de que **Personalizar objetos visuales (vista previa)** está activada.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="Habilitar la personalización en un informe":::

### <a name="in-the-power-bi-service"></a>En el servicio Power BI

Para habilitar la característica en el servicio Power BI en su lugar, vaya a **Configuración** en el informe.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Configuración del informe en el servicio Power BI":::

Active **Personalizar objetos visuales (vista previa)**  > **Guardar**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="Activar la personalización de objetos visuales en el servicio":::

## <a name="select-visuals-that-can-be-personalized"></a>Seleccionar objetos visuales que se puedan personalizar

Cuando se habilita esta opción para un informe determinado, todos los objetos visuales del informe se pueden personalizar de forma predeterminada. Si no quiere que se personalicen todos los objetos visuales, puede activar o desactivar la configuración según el objeto visual.

Seleccione el objeto visual, seleccione **Formato** en el panel **Visualizaciones** y expanda **Encabezado de objeto visual**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="Seleccionar el encabezado el objeto visual":::
 
Deslice **Personalizar objeto visual** >  **Activar** o **Desactivar**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="Activar o desactivar personalización del objeto visual":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Personalizar objetos visuales en el servicio Power BI

Al personalizar un objeto visual, los consumidores pueden explorar los datos de muchas maneras, sin tener que salir de la vista de lectura del informe. En estos ejemplos se muestran distintas formas en que los usuarios pueden modificar una visualización para satisfacer sus necesidades. 

1. Abra un informe en la vista de lectura en el servicio Power BI.

2. En la esquina superior derecha del objeto visual, seleccione el icono **Personalizar este objeto visual** ![icono Personalizar este objeto visual](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png). 

### <a name="change-the-visualization-type"></a>Cambiar el tipo de visualización

Puede ver la visualización en una representación diferente cambiando el **Tipo de visualización**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="Cambiar el tipo de visualización":::
 
### <a name="swap-out-a-measure-or-dimension"></a>Intercambiar una medida o una dimensión
Para reemplazar una medida o una dimensión en el eje X, seleccione el campo que quiere reemplazar y, después, seleccione otra medida o dimensión.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="Cambiar el eje":::
 
### <a name="add-or-remove-a-legend"></a>Agregar o quitar una leyenda
Al agregar una leyenda, puede codificar por colores un objeto visual según una categoría. Puede eliminar la codificación por colores de categorías si desactiva el cuadro **Leyenda** en el panel **Personalizar**. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="Agregar o quitar la leyenda":::

### <a name="compare-two-or-more-different-measures"></a>Comparar dos o más medidas diferentes
Puede comparar y contrastar los valores de distintas medidas mediante el icono + para agregar varias medidas para un objeto visual.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="Comparar medidas":::

### <a name="change-aggregations"></a>Cambiar agregaciones
Puede cambiar el modo en que se calcula una medida si cambia la agregación en el panel **Personalizar**.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="Cambiar agregaciones":::

### <a name="capture-changes"></a>Capturar cambios 
Use marcadores personales para capturar los cambios, para que pueda volver a la vista personalizada. 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="Crear un marcador":::
 
También puede convertir el marcador en la vista predeterminada.

### <a name="share-changes"></a>Compartir cambios 
Si tiene permisos para leer y volver a compartir, cuando comparta el informe podrá elegir incluir los cambios.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="Compartir cambios":::
 
### <a name="reset-all-your-changes-to-a-report"></a>Restablecer todos los cambios en un informe

Seleccione **Restablecer valores predeterminados** para quitar todos los cambios del informe y volver a establecerlo en la última vista guardada del informe.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="Restablecer todos los cambios":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>Restablecer todos los cambios en un objeto visual

Seleccione **Restablecer este objeto visual** para quitar todos los cambios de un determinado objeto visual y volver a establecerlo en la última vista guardada de ese objeto visual.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="Restablecer todos los cambios del objeto visual":::
 
### <a name="clear-recent-changes"></a>Borrar cambios recientes

Seleccione el icono de borrador para borrar todos los cambios recientes realizados desde que abrió el panel **Personalizar**.  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="Revertir cambios recientes":::

## <a name="limitations-and-known-issues"></a>Limitaciones y problemas conocidos

Actualmente, la característica tiene algunas limitaciones que se deben tener en cuenta.

- Esta característica no es compatible con escenarios de inserción, incluido publicar en la web.
- Las exploraciones de los usuarios no se conservan automáticamente. Debe guardar la vista como un marcador personal para capturar los cambios.
- No se pueden cambiar los objetos visuales mientras se está en Power BI para aplicaciones móviles. Pero todos los cambios visuales que guarde en un marcador personal mientras está en el servicio Power BI se respetan en las aplicaciones móviles.

También hay algunos problemas conocidos que estamos tratando:

- no se admite la adición de jerarquías; debe agregar los elementos secundarios individuales.
- No se puede cambiar una jerarquía de fecha a una fecha, o viceversa. 
- Con los marcadores personales, podría obtener resultados ligeramente diferentes en función de la secuencia que seleccione. Las discrepancias son posibles porque no capturamos el estado completo del informe, sino solo las modificaciones realizadas. La solución consiste en seleccionar **Restablecer valores predeterminados** y luego seleccionar el marcador que quiere ver. 

## <a name="next-steps"></a>Pasos siguientes

Pruebe la nueva experiencia de personalización visual. Proporciónenos sus comentarios sobre esta característica y cómo podemos seguir mejorándola en el [sitio Ideas sobre Power BI](https://ideas.powerbi.com/forums/265200-power-bi). 

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

