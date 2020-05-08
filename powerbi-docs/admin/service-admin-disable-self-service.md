---
title: Activación o desactivación del registro y la compra de autoservicio
description: Información sobre cómo los administradores pueden desactivar la posibilidad de que los usuarios se registren en Power BI y compren una licencia.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 561d8b6cd0e17e885ced984315a04376400a2a58
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "81447519"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Activación o desactivación del registro y la compra de autoservicio

En la mayoría de las organizaciones, el registro de autoservicio está habilitado de forma predeterminada. Los usuarios individuales de su organización pueden registrarse para obtener Power BI con su cuenta profesional o educativa. También se puede ofrecer a los usuarios la opción de adquirir directamente una licencia de Power BI Pro si intentan usar una característica que requiere Pro. Como administrador, puede determinar si quiere habilitar o deshabilitar el registro de autoservicio. También puede controlar si los usuarios de su organización pueden realizar compras de autoservicio para obtener su propia licencia.

> [!NOTE]
>Si adquirió Power BI a través de un proveedor de soluciones Microsoft Cloud (CSP), la configuración podría estar deshabilitada para impedir que los usuarios se registren individualmente. El CSP también puede actuar como administrador global de su organización, lo que requiere que se ponga en contacto con ellos para ayudarle a cambiar esta configuración.
>
>

Los comandos de PowerShell se usan para cambiar la configuración que controla la compra y el registro de autoservicio. Hay dos configuraciones que controlan si los usuarios de su organización pueden realizar el registro de autoservicio o efectuar compras de autoservicio.

- Si quiere deshabilitar todos los inicios de sesión de autoservicio, cambie la configuración en Azure Active Directory denominada **AllowAdHocSubscriptions** mediante los comandos de Azure AD PowerShell. Siga los pasos de este artículo para [habilitar o deshabilitar la suscripción de autoservicio](#enable-or-disable-self-service-signup). Esta opción desactiva el registro de autoservicio para *todos* los servicios y aplicaciones basados en la nube de Microsoft.

- Si quiere impedir que los usuarios compren su propia licencia Pro, cambie el valor **AllowSelfServicePurchase** mediante los comandos de PowerShell de MSCommerce. Esta configuración permite desactivar la compra de autoservicio para productos específicos. Siga los pasos de este artículo para [habilitar o deshabilitar la compra de autoservicio de licencias de Power BI Pro](#enable-or-disable-self-service-purchase).

## <a name="enable-or-disable-self-service-signup"></a>Habilitación o deshabilitación del registro de autoservicio

Si el registro de autoservicio está habilitado, el valor de **AllowAdHocSubscriptions** es *true*. Echemos un vistazo a lo que sucede cuando se cambia esta configuración a *false*:

- Si cambia la configuración de "true" a "false", no se permitirá que los usuarios nuevos de la organización se registren individualmente. Los usuarios que se hayan registrado en Power BI antes del cambio de configuración conservan sus licencias.

- Si cambia el valor a "false", los usuarios con una licencia de Power BI (gratis) todavía podrán registrarse para obtener una versión de prueba de Power BI Pro para usuarios individuales.

- Un administrador debe asignar todas las licencias de Power BI a los nuevos usuarios que las necesiten.

### <a name="before-you-begin"></a>Antes de empezar

En estos pasos se usan los comandos de Azure Active Directory PowerShell para cambiar el valor de la configuración **AllowAdHocSubscriptions**. Debe tener el módulo de Azure AD PowerShell instalado para que estos comandos estén disponibles. Para obtener más información sobre el uso de PowerShell, consulte [Introducción a Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Para instalar el módulo de Azure AD, inicie Windows PowerShell como administrador. Asegúrese de que la directiva de ejecución local le permita ejecutar scripts. Si tiene problemas, consulte las [directivas de ejecución de PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) para obtener información sobre cómo cambiar la directiva local.

Ejecute el siguiente comando para instalar el módulo de Azure AD:

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>Cambio de la directiva de registro de autoservicio

Ejecute el siguiente comando en PowerShell para conectarse a Azure AD:

```powershell
Connect-MsolService
```

Escriba sus credenciales de administrador en el cuadro de diálogo de inicio de sesión y complete cualquier autenticación en dos fases que se le pueda requerir. Después de la comprobación, volverá a la ventana de PowerShell.

Para ver la configuración actual, ejecute el siguiente comando. La salida se canaliza a una lista con formato mediante el modificador "fl".

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

Para cambiar la configuración actual, ejecute este comando:

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

Después de ejecutar este comando, la suscripción de autoservicio está deshabilitada para todos los usuarios. Para volver a activarla, vuelva a ejecutar este comando y establezca el valor en $true.

## <a name="enable-or-disable-self-service-purchase"></a>Habilitación o deshabilitación de la compra de autoservicio

Si la compra de autoservicio está habilitada, el valor de **AllowSelfServicePurchase** es *true*. Echemos un vistazo a lo que sucede cuando se cambia esta configuración a *false*:

- Si cambia la configuración de "true" a "false", no se permitirá que los usuarios de la organización compren su propia licencia de Power BI Pro. Los usuarios que hayan comprado una licencia antes del cambio de configuración conservarán sus licencias.

- Si cambia el valor a "false", los usuarios con una licencia de Power BI (gratis) no podrán obtener una licencia de Power BI Pro para usuarios individuales. 

- Un administrador debe asignar una licencia Pro a todos los usuarios que la necesiten.

### <a name="before-you-begin"></a>Antes de empezar

En estos pasos se usan los comandos de PowerShell de MSCommerce para cambiar el valor de la configuración **AllowSelfServicePurchase**. Debe tener el módulo de PowerShell de MSCommerce instalado para que estos comandos estén disponibles. Para obtener más información sobre el uso de PowerShell, consulte [Introducción a Windows PowerShell](https://docs.microsoft.com/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7).

Para instalar el módulo de MSCommerce, inicie Windows PowerShell como administrador. Asegúrese de que la directiva de ejecución local le permita ejecutar scripts. Si tiene problemas, consulte las [directivas de ejecución de PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies) para obtener información sobre cómo cambiar la directiva local.

Ejecute el siguiente comando para instalar el módulo de MSCommerce:

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>Cambio de la directiva de registro de autoservicio

Ejecute el siguiente comando en PowerShell para conectarse:

```powershell
Connect-MSCommerce
```

Escriba sus credenciales de administrador en el cuadro de diálogo de inicio de sesión y complete cualquier autenticación en dos fases que se le pueda requerir. Después de la comprobación, la ventana de PowerShell muestra una conexión correcta.

Para ver la configuración actual, ejecute el siguiente comando. La salida se canaliza a una lista con formato mediante el modificador "fl" para evitar que se trunque el texto.

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

Puede deshabilitar la configuración que permite la compra de autoservicio para un producto individual proporcionando su **ProductId**. Para cambiar la configuración actual del servicio Power BI, ejecute este comando:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

Después de ejecutar este comando, la compra de autoservicio de Power BI está deshabilitada para todos los usuarios. Para volver a activarla, vuelva a ejecutar este comando y establezca el valor en $true.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre la compra de autoservicio en Power BI y el resto de Power Platform, consulte estos artículos:

- [Preguntas más frecuentes sobre compras de autoservicio](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities)
- [Uso de AllowSelfServicePurchase para el módulo de PowerShell de MSCommerce](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide)
