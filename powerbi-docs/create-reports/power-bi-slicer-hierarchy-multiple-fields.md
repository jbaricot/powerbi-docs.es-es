---
title: Adición de varios campos a una segmentación de jerarquía
description: Obtenga información sobre cómo crear una segmentación de jerarquía que contenga varios campos en una jerarquía.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 5fbaeaafb14fc935e26b4a2d13acf9dc09ea188f
ms.sourcegitcommit: 11deeccf596e9bb8f22615276a152614f7579f35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2020
ms.locfileid: "86409587"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Adición de varios campos a una segmentación de jerarquía

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Si quiere filtrar por varios campos relacionados en una sola segmentación, puede crear lo que se denomina una segmentación de *jerarquía*. Puede crear estas segmentaciones en Power BI Desktop o en el servicio Power BI.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Captura de pantalla de la segmentación de jerarquía en Power BI.":::

Al agregar varios campos a la segmentación, se muestra de manera predeterminada una flecha (o *botón de contenido adicional*) junto a los elementos que se pueden expandir para mostrar los elementos en el siguiente nivel.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Captura de pantalla de la lista desplegable de la segmentación de jerarquía en Power BI.":::
 
 
Al seleccionar uno o varios elementos secundarios para un elemento, verá un círculo seleccionado parcialmente en el elemento de nivel superior.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Captura de pantalla de la segmentación de jerarquía de selección única en Power BI.":::

## <a name="format-the-slicer"></a>Dar formato a la segmentación

El comportamiento de la segmentación no ha cambiado. También puede diseñar la segmentación de la forma que desee. Por ejemplo, puede establecerla en modo de selección única. O bien, puede intercambiar entre una lista y un menú desplegable. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Captura de pantalla de la segmentación de jerarquía con formato de segmentación desplegable.":::

También puede realizar los cambios de formato siguientes.

### <a name="change-the-title"></a>Cambiar el título

Puede editar el título de cualquier segmentación, pero es especialmente útil para las segmentaciones de la jerarquía. De forma predeterminada, el nombre de una segmentación de jerarquía es una lista de los nombres de campo de la jerarquía.

En este ejemplo, el título de la segmentación muestra los tres campos de la jerarquía: tipo, plataforma y nombre.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="Captura de pantalla de la segmentación de jerarquía con los campos de tipo, plataforma y nombre.":::

Para cambiar el nombre, seleccione la segmentación y, a continuación, seleccione el panel **Formato**. En **Encabezado de segmentación**, verá el nombre actual de la segmentación en el cuadro **Texto del título**.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="Captura de pantalla del panel Formato con el título actual.":::

Seleccione el texto y agregue un nuevo nombre.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="Captura de pantalla del nuevo título para la segmentación de jerarquía.":::


### <a name="change-the-expandcollapse-icon"></a>Cambio del icono de expandir o contraer

Las segmentaciones de la jerarquía tienen algunas otras opciones de formato. Puede cambiar el icono de expandir/contraer de la flecha predeterminada a un signo más/menos o un símbolo de intercalación.

1. Seleccione la segmentación y, a continuación, seleccione **Formato**.
1. Expanda **Elementos** y seleccione **icono de expandir/contraer**.
1. Elija entre **Botón de contenido adicional**, **Más/menos** o **Símbolo de intercalación**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Captura de pantalla de selección de un icono de expandir/contraer para la segmentación de jerarquía.":::
 
### <a name="change-the-indentation"></a>Cambio de la sangría

Si hay poco espacio en el informe, puede que desee reducir la sangría de los elementos secundarios. De forma predeterminada, la sangría es de 15 píxeles, pero puede aumentarla o reducirla. 

1. Seleccione la segmentación y, a continuación, seleccione **Formato**.
1. Expanda **Elementos** y arrastre **Sangría de diseño escalonado** a un tamaño menor o mayor. También puede escribir un número en el cuadro.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Captura de pantalla del establecimiento de la sangría de la segmentación de la jerarquía.":::

## <a name="next-steps"></a>Pasos siguientes

- [Segmentaciones en Power BI](../visuals/power-bi-visualization-slicers.md)
- ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)