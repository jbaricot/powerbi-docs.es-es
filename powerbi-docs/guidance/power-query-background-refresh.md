---
title: Deshabilitación de la actualización en segundo plano de Power Query
description: Instrucciones sobre cuándo deshabilitar la actualización en segundo plano de Power Query.
author: peter-myers
ms.author: v-pemyer
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: 54e8524d2997e086b218e7d5b569e58ace21c48e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418656"
---
# <a name="disable-power-query-background-refresh"></a>Deshabilitación de la actualización en segundo plano de Power Query

Este artículo está dirigido a modeladores de datos de importación que trabajan con Power BI Desktop.

De forma predeterminada, cuando Power Query importa datos, también almacena en caché hasta 1000 filas de datos de vista previa para cada consulta. Los datos de vista previa facilitan la presentación de una vista previa rápida de los datos de origen y los resultados de transformación de cada paso de las consultas. Se almacenan por separado en el disco y no dentro del archivo de Power BI Desktop.

Pero cuando el archivo de Power BI Desktop contiene muchas consultas, la recuperación y el almacenamiento de datos de vista previa pueden ampliar el tiempo necesario para completar una actualización.

## <a name="recommendation"></a>Recomendación

Para lograr una actualización más rápida, establezca el archivo de Power BI Desktop para actualizar la caché de vista previa _en segundo plano_. Para habilitarlo En Power BI Desktop, seleccione _Archivo > Opciones y configuración > Opciones_ y, después, seleccione la página _Carga de datos_. Después, puede activar la opción **Permitir que se descargue la vista previa de datos en segundo plano**. Tenga en cuenta que esta opción solo se puede establecer para el archivo actual.

![Captura de pantalla de Power BI Desktop con las opciones de Datos en segundo plano.](media/power-query-background-refresh/power-query-options-background-data.png)

La habilitación de la actualización en segundo plano puede dar lugar a que los datos de vista previa estén desactualizados. En ese caso, el Editor de Power Query le notificará la siguiente advertencia:

![Captura de pantalla de Power BI Desktop en la que se muestra la Advertencia del Editor de Power Query sobre datos de vista previa antiguos.](media/power-query-background-refresh/power-query-preview-data-old.png)

Siempre se puede actualizar la caché de vista previa. Puede actualizarla para una sola consulta o para todas mediante el comando **Actualizar vista previa**. Lo encontrará en la cinta **Inicio** de la ventana del Editor de Power Query.

![Captura de pantalla de Power BI Desktop en la que se muestran Comandos del Editor de Power Query para actualizar los datos de vista previa.](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Documentación de Power Query](/power-query/)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
