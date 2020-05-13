---
title: Usar un filtro o una segmentación de tiempo relativo en Power BI
description: Obtenga información sobre cómo usar un filtro o una segmentación para restringir intervalos tiempo relativos en Power BI.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 31563e5bb5b91468b8913c3204e9d27607716c77
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83279213"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>Usar un filtro y una segmentación de tiempo relativo en Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Con los escenarios de actualización rápida que están surgiendo, la capacidad de filtrar por un período de tiempo más pequeño puede resultar útil. Con la segmentación de tiempo relativo o el filtro de tiempo relativo, puede aplicar filtros basados en el tiempo a cualquier columna de fecha o de hora del modelo de datos. Por ejemplo, puede usar la segmentación de tiempo relativa para mostrar solo las vistas de vídeo de la última hora o el último minuto. 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="Ejemplo de tiempo relativo":::

No es necesario usar esta característica junto con la característica de [actualización automática de páginas](../create-reports/desktop-automatic-page-refresh.md), pero muchos escenarios de tiempo relativo se emparejan bien con la característica de actualización automática de páginas.  

> [!NOTE]
> Al aplicar un filtro de tiempo relativo o una segmentación de página o de informe, todos los objetos visuales de esa página o informe se filtran hasta el mismo intervalo de tiempo, mediante un tiempo *delimitador* compartido. Dado que los objetos visuales pueden tener tiempos de ejecución ligeramente diferentes, este tiempo delimitador compartido garantiza que los objetos visuales se sincronizan en la página o en el informe. En este artículo podrá leer más sobre el [tiempo delimitador](#understanding-anchor-time).

## <a name="turn-on-relative-time-preview"></a>Activar la vista previa de tiempo relativo

El filtro de tiempo relativo está en vista previa, por lo que se debe activar la modificación de característica. Vaya a **Archivo** > **Opciones y configuración** > **Opciones**. En **Configuración global** > **Características en vista previa**, asegúrese de que está seleccionado **Filtro de tiempo relativo**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-preview.png" alt-text="Establecer la opción de vista previa de tiempo relativo":::

## <a name="create-a-relative-time-slicer-or-filter"></a>Crear un filtro o segmentación de tiempo relativo

Después de habilitar la característica, puede arrastrar y colocar el campo de fecha u hora en el campo de una segmentación de datos o en la zona de colocación en el panel Filtros. 

### <a name="create-a-slicer"></a>Crear una segmentación

1. Arrastre un campo de fecha u hora al lienzo.

2. Seleccione el tipo de visualización **Segmentación de datos**.

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="Crear una segmentación de tiempo":::

### <a name="create-a-filter"></a>Crear un filtro
 
- Arrastre un campo de fecha u hora al panel Filtros, para **este objeto visual**, **esta página** o **todas las páginas**.

### <a name="set-relative-time"></a>Definir tiempo relativo 

Después, cambie el tipo de filtro a **Tiempo relativo**.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="Cambiar a tiempo relativo":::
 
Este es el aspecto que tiene en una segmentación:

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="Tiempo relativo en una segmentación":::

Este es el aspecto que tiene en una tarjeta de filtro: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="Tiempo relativo en un filtro":::
 
Con este nuevo tipo de filtro, tiene la opción de filtrar según **Último**, **Siguiente** o **Este período de tiempo**: 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="Elegir Último, Siguiente o Este período de tiempo":::
 
La ventana de tiempo se especifica con un número entero y una unidad de tiempo: **Minutos** u **Horas**.
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="Elegir minutos u horas":::

Si necesita ahorrar espacio en el lienzo, también puede crear el filtro de tiempo relativo como una tarjeta de filtro en el panel Filtros.

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="Establecer tiempo relativo en un filtro":::
 
## <a name="understanding-anchor-time"></a>Descripción del tiempo delimitador

Cuando se aplica un filtro al nivel de página o de informe, todos los objetos visuales de esa página o informe se sincronizan con el mismo intervalo de tiempo exacto. Todas estas consultas se emiten en relación con una hora llamada *tiempo delimitador*. El tiempo delimitador se actualiza automáticamente en las siguientes condiciones:

- Carga de página inicial.
- Actualización manual.
- Actualización de página automática o de detección de cambios.
- Cambio en el modelo.

### <a name="anchor-time-exceptions"></a>Excepciones de tiempo delimitador

- El filtrado de tiempo relativo mediante un objeto visual de Preguntas y respuestas no será relativo a este tiempo delimitador hasta que convierta el objeto visual de Preguntas y respuestas en un objeto visual estándar. Pero los otros objetos visuales de IA, como influenciadores clave y el árbol de descomposición, se sincronizan con el tiempo delimitador. 
- Además, las segmentaciones o los filtros de fecha relativa no son relativos al tiempo delimitador, a menos que haya filtros de hora relativos. Si una fecha relativa y un filtro de tiempo relativo están en la misma página, el filtro de fecha relativa respeta el tiempo delimitador.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Actualmente se aplican estas limitaciones y consideraciones al filtro y la segmentación de fecha relativa.

- **Consideraciones de zona horaria**: Los modelos de datos de Power BI no incluyen información de zona horaria. Los modelos pueden almacenar horas, pero no hay ninguna indicación de la zona horaria en la que se encuentran. La segmentación y el filtro se basan siempre en la hora UTC. Si configura un filtro en un informe y lo envía a un compañero de trabajo que está en otra zona horaria, los dos verán los mismos datos. A menos que su compañero o usted estén en la zona horaria UTC, los dos deben tener en cuenta el desfase horario que experimentarán. Use el Editor de consultas para convertir los datos capturados en una zona horaria local a UTC.
- Este nuevo tipo de filtro se admite en Power BI Desktop, en el servicio Power BI, Power BI Embedded y en las aplicaciones móviles de Power BI. Pero hay algunas limitaciones de compatibilidad conocidas:

    - No se admite a través de la API de inserción.
    - No se admite para publicar en la web.

- **Almacenamiento en caché de consultas**: Usamos la memoria caché del cliente. Por lo tanto, supongamos que especifica "último minuto", luego "últimos 5 minutos" y después vuelve a "último minuto". En ese momento, verá los mismos resultados que cuando se ejecutó por primera vez, a menos que actualice la página o la página se actualice automáticamente.

## <a name="next-steps"></a>Pasos siguientes

- [Uso de un filtro y una segmentación de fecha relativa en Power BI](../visuals/desktop-slicer-filter-date-range.md)
- [Segmentaciones en Power BI](../visuals/power-bi-visualization-slicers.md)
