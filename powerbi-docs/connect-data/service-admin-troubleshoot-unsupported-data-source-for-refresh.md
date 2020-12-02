---
title: Solución de problemas de origen de datos no admitido para la actualización
description: Solución de problemas de origen de datos no admitido para la actualización
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 05/08/2020
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4ab84a4f40acff894416fe2e5b33788c413ad4f5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410767"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Solución de problemas de origen de datos no admitido para la actualización
Puede ver un error al intentar configurar un conjunto de datos para la actualización programada.

```output
You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.
```

Esto sucede cuando no se admite el origen de datos que usa, en Power BI Desktop, para la actualización. Tendrá que buscar el origen de datos que está usando y compararlo con la lista de orígenes de datos compatibles en [Actualizar datos en Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Búsqueda del origen de datos
Si no está seguro de qué origen de datos se utilizó, puede encontrarlo siguiendo los siguientes pasos en Power BI Desktop.  

1. En Power BI Desktop, asegúrese de que se encuentra en el panel **Informe** .  
   ![Panel de informes de Desktop](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Seleccione **Editar consultas** en la barra de cinta.  
   ![Editar consultas](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Seleccione **Editor avanzado**.  
   ![Editor avanzado](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Tome nota del proveedor que aparece para el origen.  En este ejemplo, el proveedor es Active Directory.  
   ![Proveedor del origen de datos](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Compare el proveedor con la lista de orígenes de datos admitidos que se encuentra en los [orígenes de datos de Power BI](power-bi-data-sources.md).

> [!NOTE]
> En el caso de problemas de actualización relacionados con orígenes de datos dinámicos, como aquellos que contienen consultas creadas manualmente, consulte [Actualización y orígenes de datos dinámicos](refresh-data.md#refresh-and-dynamic-data-sources).


## <a name="next-steps"></a>Pasos siguientes
[Actualización de datos](refresh-data.md)  
[Power BI Gateway - Personal](service-gateway-personal-mode.md)  
[Puerta de enlace de datos local](service-gateway-onprem.md)  
[Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md)  
[Solución de problemas de Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
