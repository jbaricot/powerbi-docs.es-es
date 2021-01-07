---
title: Habilitación de etiquetas de confidencialidad en Power BI
description: Más información sobre cómo habilitar etiquetas de confidencialidad de datos en Power BI
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 12/09/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 1732c1b6b8b748c4f3a820b31c4e4fe050a66fcd
ms.sourcegitcommit: b472236df99b490db30f0168bd7284ae6e6095fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/16/2020
ms.locfileid: "97600332"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Habilitación de etiquetas de confidencialidad en Power BI

Para poder usar las [etiquetas de confidencialidad de Microsoft Information Protection](/microsoft-365/compliance/sensitivity-labels) en Power BI, deben estar habilitadas en el inquilino. Este artículo muestra a los administradores de Power BI cómo hacerlo. Para obtener información general sobre las etiquetas de confidencialidad en Power BI, consulte [Etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md). Para obtener información sobre cómo aplicar etiquetas de confidencialidad en Power BI, vea [Aplicación de etiquetas de confidencialidad](./service-security-apply-data-sensitivity-labels.md) 

Cuando las etiquetas de confidencialidad están habilitadas:

* Usuarios y grupos de seguridad concretos de la organización pueden clasificar y [aplicar etiquetas de confidencialidad](./service-security-apply-data-sensitivity-labels.md) a su contenido de Power BI. En el servicio Power BI, esto se refiere a sus informes, paneles, conjuntos de datos y flujos de datos. En Power BI Desktop, se refiere a los archivos .pbix.
* En el servicio, todos los miembros de la organización podrán ver esas etiquetas. En Desktop, solo los miembros de la organización que tienen las etiquetas publicadas podrán verlas.

La habilitación de etiquetas de confidencialidad requiere una licencia de Azure Information Protection. Para más información, consulte [Licencia y requisitos](#licensing-and-requirements).

>[!NOTE]
>Durante las primeras 48 horas después de empezar a usar la característica en vista previa (GB) de Information Protection, **los usuarios pueden experimentar problemas con los archivos .pbix que tienen etiquetas de confidencialidad aplicadas (por ejemplo, publicar el archivo .pbix en el servicio, descargar el archivo. pbix desde el servicio)** . Estos problemas son esperables y se resolverán automáticamente dentro de un plazo de 48 horas.

## <a name="licensing-and-requirements"></a>Licencia y requisitos

* Para ver o aplicar etiquetas de confidencialidad de Microsoft Information Protection en Power BI, se necesita una licencia de Azure Information Protection Premium P1 o Premium P2. Azure Information Protection se puede adquirir de forma independiente o mediante uno de los conjuntos de licencias de Microsoft. Consulte [Precios de Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) para más detalles.

    >[!NOTE]
    > Si su organización usa etiquetas de confidencialidad de Azure Information Protection, se deben migrar a la plataforma de etiquetado unificado de Microsoft Information Protection para usarlas en Power BI. [Más información sobre la migración de etiquetas de confidencialidad](/azure/information-protection/configure-policy-migrate-labels).

* Para aplicar etiquetas a contenido y archivos de Power BI, un usuario debe tener una licencia de Power BI Pro además de una de las licencias de Azure Information Protection mencionadas anteriormente.

* Las aplicaciones de Office tienen sus propios [requisitos de licencia para ver y aplicar etiquetas de confidencialidad]( https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels ).

* Antes de habilitar etiquetas de confidencialidad en el inquilino, asegúrese de que se hayan definido y publicado para los usuarios y grupos pertinentes. Para más información, consulte [Crear y configurar etiquetas de confidencialidad y sus directivas](/microsoft-365/compliance/create-sensitivity-labels).

* El uso de etiquetas de confidencialidad en Desktop requiere la versión de Desktop de diciembre de 2020 y versiones posteriores.

    >[!NOTE]
    > Si intenta abrir un archivo .pbix protegido con una versión de Desktop anterior a la de diciembre de 2020, se producirá un error y se le pedirá que actualice la versión de Desktop.

## <a name="enable-sensitivity-labels"></a>Habilitación de etiquetas de confidencialidad

Las etiquetas de confidencialidad deben estar habilitadas en el inquilino para poder usarlas tanto en el servicio como en Desktop. En esta sección se describe cómo habilitarlas en la configuración del inquilino. Para otras consideraciones relacionadas con Desktop, consulte [Deshabilitación de las etiquetas de confidencialidad en Desktop en toda la organización](#disable-sensitivity-labels-in-desktop-across-your-org). 

Para habilitar las etiquetas de confidencialidad en el inquilino, vaya al **Portal de administración** de Power BI, abra el panel **Configuración de inquilinos** y busque la sección **Protección de la información**.

![Búsqueda de la sección Information Protection](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

En la sección **Information Protection**, realice los pasos siguientes:
1. Abra **Permitir a los usuarios aplicar etiquetas de confidencialidad al contenido de Power BI**.
1. Habilite el control de alternancia.
1. Defina quién puede aplicar y cambiar las etiquetas de confidencialidad en los recursos de Power BI. De forma predeterminada, todos los usuarios de su organización podrán aplicar etiquetas de confidencialidad. Sin embargo, puede optar por habilitar la configuración de las etiquetas de confidencialidad solo para usuarios o grupos de seguridad específicos. Con toda la organización o bien con grupos de seguridad específicos seleccionados, puede excluir subconjuntos específicos de usuarios o grupos de seguridad.
   
   * Cuando las etiquetas de confidencialidad están habilitadas para toda la organización, las excepciones suelen ser grupos de seguridad.
   * Cuando las etiquetas de confidencialidad están habilitadas solo para usuarios o grupos de seguridad específicos, las excepciones suelen ser usuarios específicos.  
    Este enfoque permite impedir que determinados usuarios apliquen etiquetas de confidencialidad en Power BI, aunque pertenezcan a un grupo que tenga permisos para hacerlo.

1. Presione **Aplicar**.

![Habilitación de etiquetas de confidencialidad](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Solo los usuarios de Power BI Pro que tengan permisos para *crear* y *editar* en el recurso y que formen parte del grupo de seguridad pertinente que se estableció en esta sección, podrán establecer y editar las etiquetas de confidencialidad. Los usuarios que no forman parte de este grupo no podrán establecer ni editar las etiquetas.  

## <a name="disable-sensitivity-labels-in-desktop-across-your-org"></a>Deshabilitación de las etiquetas de confidencialidad en Desktop en toda la organización

En el caso de las organizaciones que quieran asegurarse de que los archivos .pbix **no** funcionen con etiquetas de confidencialidad, el administrador de Power BI puede crear una directiva de grupo que haga que Power BI impida que los usuarios clasifiquen y protejan los archivos .pbix o abran archivos que ya tienen aplicada la protección. Para crear este tipo de directiva:

1. Abra el [Editor del Registro](https://support.microsoft.com/windows/how-to-open-registry-editor-in-windows-10-deab38e6-91d6-e0aa-4b7c-8878d9e07b11).

1. Busque la clave **HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop**.

1. Busque el valueName **EnableInformationProtection** y establézcalo en **false**.

Consulte la [información general sobre las etiquetas de confidencialidad](./service-security-sensitivity-label-overview.md#limitations) para ver limitaciones y consideraciones adicionales relacionadas con el uso de las etiquetas de confidencialidad en Power BI Desktop.

## <a name="troubleshooting"></a>Solución de problemas

Power BI usa las etiquetas de confidencialidad de Microsoft Information Protection. Por lo tanto, si encuentra un mensaje de error al intentar habilitar las etiquetas de confidencialidad, puede deberse a uno de los siguientes motivos:

* No tiene una [licencia](#licensing-and-requirements) de Azure Information Protection.
* Las etiquetas de confidencialidad no se han [migrado](#enable-sensitivity-labels) a la versión de Microsoft Information Protection compatible con Power BI.
* No se ha definido ninguna etiqueta de confidencialidad de Microsoft Information Protection [en la organización](#enable-sensitivity-labels).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Consulte [Etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md#limitations) para ver la lista de las limitaciones de la etiqueta de confidencialidad en Power BI.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se describe cómo habilitar las etiquetas de confidencialidad en Power BI. En los artículos siguientes se proporcionan más detalles acerca de la protección de datos en Power BI. 

* [Información general sobre las etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md)
* [Aplicación de etiquetas de confidencialidad en Power BI](./service-security-apply-data-sensitivity-labels.md)
* [Uso de controles de Microsoft Cloud App Security en Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Informe de métricas de protección](service-security-data-protection-metrics-report.md)