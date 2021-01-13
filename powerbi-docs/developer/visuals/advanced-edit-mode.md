---
title: Modo de edición avanzada en objetos visuales de Power BI en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: En este artículo se describe cómo establecer controles de interfaz de usuario avanzados en objetos visuales de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 02f02f23d3dfd7ec514e17d1bab17be715e9cd7d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889142"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Modo de edición avanzada en objetos visuales de Power BI

Si necesita controles de interfaz de usuario avanzados en el objeto visual de Power BI, puede aprovechar el modo de edición avanzada. Cuando esté en el modo de edición de informes, seleccione el botón **Editar** para establecer el modo de edición en **Avanzado**. El objeto visual puede usar la marca `EditMode` para determinar si debe mostrar este control de interfaz de usuario.

De forma predeterminada, el objeto visual no admite el modo de edición avanzada. Si se requiere otro comportamiento, puede indicarlo de forma explícita en el archivo *capabilities.json* del objeto visual, al establecer la propiedad `advancedEditModeSupport`.

Los valores posibles son:

- `0`: NotSupported

- `1`: SupportedNoAction

- `2`: SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Acceso al modo de edición avanzada

Se muestra el botón **Editar** si:

* La propiedad `advancedEditModeSupport` está establecida en el archivo *capabilities.json* en `SupportedNoAction` o `SupportedInFocus`.

* El objeto visual se ve en el modo de edición de informes.

Si falta la propiedad `advancedEditModeSupport` en el archivo *capabilities.json* o está establecida en `NotSupported`, no se muestra el botón **Editar**.

![Acceso al modo de edición](media/advanced-edit-mode/edit-mode.png)

Al seleccionar **Editar**, el objeto visual recibe una llamada de update() con EditMode establecido en `Advanced`. Según el valor que se haya establecido en el archivo *capabilities.json*, se producen las siguientes acciones:

* `SupportedNoAction`: el host no requiere más acciones.
* `SupportedInFocus`: el host muestra el objeto visual en el modo de enfoque.

## <a name="exit-advanced-edit-mode"></a>Salida del modo de edición avanzada

Se muestra el botón **Volver al informe** si:

* La propiedad `advancedEditModeSupport` está establecida en el archivo *capabilities.json* en `SupportedInFocus`.
