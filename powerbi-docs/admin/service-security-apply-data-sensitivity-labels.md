---
title: Aplicación de etiquetas de confidencialidad en Power BI
description: Más información sobre cómo aplicar etiquetas de confidencialidad de datos en Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 12/09/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 14b3329ea2b8636c1e5cf2412ca9843bc777bed1
ms.sourcegitcommit: b472236df99b490db30f0168bd7284ae6e6095fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/16/2020
ms.locfileid: "97600470"
---
# <a name="how-to-apply-sensitivity-labels-in-power-bi"></a>Aplicación de etiquetas de confidencialidad en Power BI

Las etiquetas de confidencialidad de Microsoft Information Protection para informes, paneles, conjuntos de datos, flujos de datos y archivos .pbix pueden proteger el contenido confidencial contra pérdidas y el acceso no autorizado a los datos. El etiquetado correcto de los datos con etiquetas de confidencialidad garantiza que solo las personas autorizadas puedan acceder a los datos. En este artículo se muestra cómo aplicar etiquetas de confidencialidad en el servicio Power BI y en Power BI Desktop.

Para obtener más información sobre las etiquetas de confidencialidad en Power BI, consulte [Etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md).

## <a name="apply-sensitivity-labels-in-the-power-bi-service"></a>Aplicación de etiquetas de confidencialidad en el servicio Power BI

En el servicio Power BI, puede aplicar las etiquetas de confidencialidad a informes, paneles, conjuntos de datos y flujos de datos.

Para poder aplicar las etiquetas de confidencialidad en el servicio Power BI:
* Debe tener una [licencia de Power BI Pro](./service-admin-purchasing-power-bi-pro.md) y permisos de edición en el contenido que desea etiquetar.
* Las etiquetas de confidencialidad deben estar habilitadas para su organización. Si no está seguro al respecto, póngase en contacto con su administrador de Power BI.
* Debe pertenecer a un grupo de seguridad que tenga permisos para aplicar etiquetas de confidencialidad, tal como se describe en [Habilitación de etiquetas de confidencialidad en Power BI](./service-security-enable-data-sensitivity-labels.md).
* Se deben haber cumplido todos los [requisitos de licencia y otros](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements).

Cuando la protección de datos está habilitada en el inquilino, las etiquetas de confidencialidad aparecen en la columna Confidencialidad de la vista de lista de paneles, informes, conjuntos de datos y flujos de datos.

![Habilitación de etiquetas de confidencialidad](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**Para aplicar o cambiar una etiqueta de confidencialidad en un informe o un panel**
1. Haga clic en **Más opciones (...)** .
1. Haga clic en **Configuración**.
1. En el panel de configuración, elija la etiqueta de confidencialidad adecuada.
1. Guarde la configuración

En la imagen siguiente se muestran estos pasos en un informe

![Establecimiento de etiquetas de confidencialidad](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**Para aplicar o cambiar una etiqueta de confidencialidad en un conjunto de datos o un flujo de datos**

1. Haga clic en **Más opciones (...)** .
1. Haga clic en **Configuración**.
1. Seleccione la pestaña de conjuntos de valores o de flujos de entrada, según corresponda.
1. Expanda la sección de etiquetas de confidencialidad y elija la etiqueta de confidencialidad adecuada.
1. Aplique la configuración.

En las dos imágenes siguientes se muestran estos pasos en un conjunto de datos.

Elija **Más opciones (...)** y, después, **Configuración**.

![Abrir configuración del conjunto de datos](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

En la pestaña de configuración de conjuntos de datos, abra la sección de etiquetas de confidencialidad, elija la etiqueta de confidencialidad que quiera y haga clic en **Aplicar**.

![Elegir etiqueta de confidencialidad](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="apply-sensitivity-labels-in-power-bi-desktop-preview"></a>Aplicación de etiquetas de confidencialidad en Power BI Desktop (versión preliminar)

>[!NOTE]
>Durante las primeras 48 horas después de empezar a usar la característica en vista previa (GB) de Information Protection de Power BI Desktop, **puede experimentar problemas con los archivos .pbix que tienen etiquetas de confidencialidad aplicadas (por ejemplo, publicar el archivo .pbix en el servicio, descargar el archivo. pbix desde el servicio)** . Estos problemas son esperables y se resolverán automáticamente dentro de un plazo de 48 horas.

Para usar las etiquetas de confidencialidad en Power BI Desktop:
* Debe tener una [licencia de Power BI Pro](./service-admin-purchasing-power-bi-pro.md).
* Las etiquetas de confidencialidad deben estar habilitadas para su organización. Si no está seguro al respecto, póngase en contacto con su administrador de Power BI.
* Debe pertenecer a un grupo de seguridad que tenga permisos para aplicar etiquetas de confidencialidad, tal como se describe en [Habilitación de etiquetas de confidencialidad en Power BI](./service-security-enable-data-sensitivity-labels.md).
* Se deben haber cumplido todos los [requisitos de licencia y otros](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements).
* El cambio de característica en vista previa (GB) de protección de la información en Power BI Desktop debe estar activado. Si ve el botón de confidencialidad en la pestaña Inicio, la característica en vista previa (GB) está activada. Si no ve el botón, vaya a **Archivo > Opciones y configuración > Opciones > Características en vista previa (GB)** y active la casilla junto a **Protección de la información**.

    ![Captura de pantalla de la página de características en vista previa (GB) de Desktop.](media/service-security-apply-data-sensitivity-labels/desktop-preview-features-page.png)

    Si no ve la opción de versión preliminar de protección de la información, es posible que la característica en vista previa (GB) de protección de la información esté bloqueada para su organización. En este caso, póngase en contacto con el administrador de Power BI.

    >[!NOTE]
    >Después de activar la característica en vista previa (GB) de protección de la información, debe reiniciar Desktop para poder empezar a usar etiquetas de confidencialidad.
* Debe haber iniciado sesión.

Para aplicar una etiqueta de confidencialidad en el archivo en el que está trabajando, haga clic en el botón de confidencialidad en la pestaña Inicio y elija la etiqueta que quiera en el menú que aparece.

![Captura de pantalla que muestra el menú de etiqueta de confidencialidad en Desktop.](media/service-security-apply-data-sensitivity-labels/sensitivity-label-menu-desktop.png)

>[!NOTE]
> Si ha activado la característica de etiquetas de confidencialidad en las características en vista previa (GB), pero sigue sin ver el botón de confidencialidad, puede indicar que no tiene una licencia adecuada o que no pertenece al grupo de seguridad que tiene permisos para aplicar las etiquetas de confidencialidad, tal como se describe en [Habilitación de etiquetas de confidencialidad en Power BI](./service-security-enable-data-sensitivity-labels.md).

Una vez aplicada la etiqueta, estará visible en la barra de estado.

![Captura de pantalla que muestra la etiqueta de confidencialidad en la barra de estado de Desktop.](media/service-security-apply-data-sensitivity-labels/sensitivity-label-in-desktop-status-bar.png)

### <a name="sensitivity-labels-when-uploading-or-downloading-pbix-files-tofrom-the-service"></a>Etiquetas de confidencialidad al cargar o descargar archivos .pbix en el servicio
* Al publicar un archivo .pbix en el servicio Power BI desde Desktop, o al cargar un archivo .pbix en el servicio Power BI directamente a través de **Obtener datos**, la etiqueta del archivo .pbix se aplica tanto al informe como al conjunto de datos que se crean en el servicio. Si el archivo .pbix que está publicando o cargando reemplaza los recursos existentes (es decir, los recursos que tienen el mismo nombre que el archivo .pbix), la etiqueta del archivo .pbix sobrescribirá cualquier etiqueta de esos recursos.
* Cuando se usa "Descargar al archivo .pbix" en el servicio Power BI, si el informe y el conjunto de datos que se está descargando tienen etiquetas y esas etiquetas son diferentes, la etiqueta que se aplicará al archivo .pbix es la más restrictiva de las dos.

## <a name="remove-sensitivity-labels"></a>Etiquetas de confidencialidad remotas

### <a name="service"></a>Servicio
Para quitar una etiqueta de confidencialidad de un informe, panel, conjunto de datos o flujo de datos, siga el [mismo procedimiento que se usa para aplicar las etiquetas en el servicio Power BI](#apply-sensitivity-labels-in-the-power-bi-service), pero elija **(Ninguna)** cuando se le pida que clasifique la confidencialidad de los datos.

### <a name="desktop"></a>Escritorio
Actualmente, en Desktop no se puede quitar la etiqueta de confidencialidad de un archivo .pbix una vez guardado con la etiqueta. En tales casos, se recomienda publicar el archivo en el servicio Power BI y luego en el servicio para quitar la etiqueta del informe y del conjunto de datos siguientes.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Consulte [Etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md#limitations) para ver la lista de las limitaciones de la etiqueta de confidencialidad en Power BI.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se describe cómo aplicar etiquetas de confidencialidad en Power BI. En los artículos siguientes se proporcionan más detalles acerca de la protección de datos en Power BI. 

* [Información general sobre las etiquetas de confidencialidad en Power BI](./service-security-sensitivity-label-overview.md)
* [Habilitación de etiquetas de confidencialidad en Power BI](./service-security-enable-data-sensitivity-labels.md)
* [Uso de controles de Microsoft Cloud App Security en Power BI](./service-security-using-microsoft-cloud-app-security-controls.md)