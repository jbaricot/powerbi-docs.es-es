---
title: 'Project Online: conexión a los datos a través de Power BI Desktop'
description: 'Project Online: conexión a los datos a través de Power BI Desktop'
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/01/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: b6078a2122a77682af328f9935b23da0d0d0d945
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404948"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Conexión a datos de Project Online a través de Power BI Desktop
Puede conectarse a los datos en Project Online a través de Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Paso 1: Descargar Power BI Desktop
1. [Descargue Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662) y, después, ejecute el instalador para obtener **Power BI Desktop** en el equipo.

## <a name="step-2-connect-to-project-online-with-odata"></a>Paso 2: Conexión a Project Online con OData
1. Abra **Power BI Desktop**.
2. En la pantalla de *bienvenida*, seleccione **Obtener datos**.
3. Elija **Fuente de OData** y seleccione **Conectar**.
4. Escriba la dirección de su fuente de OData en el cuadro de la dirección URL y, a continuación, haga clic en Aceptar.
   
   Si la dirección del sitio de Project Web App se parece a *https://\<tenantname\>.sharepoint.com/sites/pwa*, la dirección que especificará para la fuente de OData será *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata*.
   
   En nuestro ejemplo, estamos usando:

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop le solicitará que realice la autenticación con su cuenta profesional o educativa. Seleccione la cuenta de la organización y, a continuación, escriba sus credenciales.
   
   ![Captura de pantalla de Power BI Desktop, donde se muestra la solicitud de credenciales para conectarse.](media/desktop-project-online-connect-to-data/image.png)

La cuenta usada para conectarse a la fuente de OData debe tener como mínimo acceso de Visor de carteras al sitio de Project Web App. 

Desde aquí, puede elegir a qué tablas le gustaría conectarse y crear una consulta.  ¿Desea una idea de cómo comenzar?  La siguiente entrada de blog muestra cómo crear un gráfico de evolución a partir de los datos de Project Online.  La entrada de blog se refiere al uso de Power Query para conectarse a Project Online, pero esto se aplica también a Power BI Desktop.

[Creación de gráficos de evolución para Project con PowerPivot y Power Query](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

