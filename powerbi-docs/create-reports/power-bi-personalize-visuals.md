---
title: Permitir a los usuarios personalizar los objetos visuales en un informe
description: Permita que los lectores del informe creen su propia vista de un informe, sin modificarlo.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: ab232d4e5b6d17e7f20ed8a41875ca47693eb285
ms.sourcegitcommit: 21b06e49056c2f69a363d3a19337374baa84c83f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2020
ms.locfileid: "83407584"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>Permitir a los usuarios personalizar los objetos visuales en un informe

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Al compartir un informe con un público amplio, es posible que algunos de los usuarios prefieran tener una vista diferente de determinados objetos visuales. Es posible que quieran cambiar lo que hay en el eje, cambiar el tipo de objeto visual o agregar algo a la información sobre herramientas. Es difícil crear un solo objeto visual que satisfaga los requisitos de todos. Con esta nueva capacidad, puede permitir a los consumidores explorar y personalizar objetos visuales, todo ello en la vista de lectura del informe. Pueden ajustar el objeto visual como quieran y guardarlo como un marcador para volver a él. No necesitan tener permiso para editar el informe ni ponerse en contacto con el autor del informe para hacer cambios.

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="Personalizar un objeto visual":::
 
## <a name="what-report-consumers-can-change"></a>Qué pueden cambiar los consumidores del informe

Esta característica permite a los consumidores obtener información adicional a través de la exploración ad hoc de objetos visuales en un informe de Power BI. Para aprender a usar esta característica como consumidor, consulte [Personalización de objetos visuales en un informe](../consumer/end-user-personalize-visuals.md). La característica es ideal para los creadores de informes que quieran habilitar escenarios de exploración básicos para los lectores de informes. Estas son las modificaciones que pueden realizar los lectores de informes:

- Cambiar el tipo de visualización
- Intercambiar una medida o una dimensión
- Agregar o quitar una leyenda
- Comparar dos o más medidas
- Cambiar agregaciones, etc.

Esta característica no solo incorpora nuevas funcionalidades de exploración, sino que también permite que los consumidores capturen y compartan sus cambios:

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

[Personalice objetos visuales en los informes](../consumer/end-user-personalize-visuals.md).     

Pruebe la nueva experiencia de personalización visual. Proporciónenos sus comentarios sobre esta característica y cómo podemos seguir mejorándola en el [sitio Ideas sobre Power BI](https://ideas.powerbi.com/forums/265200-power-bi). 

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
