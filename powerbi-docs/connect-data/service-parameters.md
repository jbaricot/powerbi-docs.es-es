---
title: Edición de la configuración de los parámetros en el servicio Power BI
description: Los parámetros de consulta se crean en Power BI Desktop, pero se pueden revisar y actualizar en el servicio Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/04/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 29468ea50625b1d354bd431f77c5e89edf5a889d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402096"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Edición de la configuración de los parámetros en el servicio Power BI
Los creadores de informes agregan parámetros de consulta a los informes en Power BI Desktop. Estos parámetros les permiten establecer elementos de los informes como dependientes de uno o varios *valores* de parámetro. Por ejemplo, un creador de informes puede crear un parámetro que restrinja los datos a una única región o país, o bien un parámetro que defina qué formatos son aceptables en campos como los relativos a fechas, hora y texto.

![Pestaña Inicio con la opción Administrar parámetros en Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Revisión y edición de parámetros en el servicio Power BI

Como creador del informe, define los parámetros en Power BI Desktop. Al [publicar ese informe en el servicio Power BI](../create-reports/desktop-upload-desktop-files.md), la configuración de los parámetros y las selecciones se transfieren con él. Puede revisar y editar la configuración de los parámetros en el servicio Power BI, pero no crearlos.

1. En el servicio Power BI, seleccione el icono de engranaje ![Icono de engranaje](media/service-parameters/power-bi-cog.png) para abrir **Configuración**.

2. Seleccione la pestaña **Conjuntos de datos** y resalte un conjunto de datos de la lista. 
    
    ![Ventana Configuración con la pestaña Conjuntos de datos seleccionada](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda **Parámetros**.  Si el conjunto de datos seleccionado no tiene parámetros, verá un mensaje con un vínculo que lleva a Más información sobre los parámetros de consulta. Si el conjunto de datos sí tiene parámetros, podrá verlos expandiendo el encabezado **Parámetros**. 

    ![Ventana Configuración con Parámetros expandido](media/service-parameters/power-bi-settings.png)

    Revise la configuración de los parámetros y realice los cambios que considere necesarios. Los campos atenuados no se pueden editar. 


## <a name="next-steps"></a>Pasos siguientes
Una manera directa de agregar parámetros simples es [modificar la dirección URL](../collaborate-share/service-url-filters.md).
