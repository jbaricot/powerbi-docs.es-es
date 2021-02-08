---
title: Activación o desactivación del registro y la compra de autoservicio
description: Información sobre cómo los administradores pueden desactivar la posibilidad de que los usuarios se registren en el servicio Power BI y compren o actualicen una licencia.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/31/2021
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 80e263cc6e67c28b7593fcf10aea4c81c9f4af86
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494314"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>Activación o desactivación del registro y la compra de autoservicio

## <a name="what-is-self-service"></a>¿Qué significa "autoservicio"?

El término "autoservicio" se refiere a la capacidad de los usuarios de una organización (profesional o educativa) de registrarse para usar servicios gratuitos o de pago mediante la suscripción de la organización, sin pedir a dicha organización que realice acciones en su nombre. Por ejemplo, una persona se dirige a un sitio web de Microsoft, encuentra un servicio en la nube que ofrece su organización y usa su dirección de correo electrónico corporativa para registrarse en ese servicio. 

En muchos casos, la organización ha pagado una cuota para suscribirse a ese servicio. En otros, esa persona es el primer usuario y se convierte en el administrador del servicio. Para obtener una prueba o una licencia gratuita no se requiere realizar ninguna compra. Sin embargo, en el caso de Power BI Pro, la organización es responsable de pagar la cuota mensual. 

Como administrador de Microsoft 365, puede ver quién se registra para obtener pruebas, licencias y suscripciones.

> [!NOTE]
> El registro de autoservicio solo está disponible para los clientes de la nube comercial, y no para los clientes de la Administración pública ni de nubes nacionales.

## <a name="when-to-use-self-service-sign-up-and-purchase"></a>Cuándo usar las compras y el registro de autoservicio

### <a name="self-service-is-a-good-idea"></a>El autoservicio se recomienda en los siguientes casos: 

- Para organizaciones más grandes y descentralizadas (profesionales o educativas) a las que se les suele ofrecer la flexibilidad de adquirir licencias de SaaS (software como servicio) para uso propio. 
- Para organizaciones pequeñas o unipersonales que necesiten comprar solo una licencia de Power BI Pro (o unas pocas).
- Para personas interesadas en probar Power BI y familiarizarse con el producto antes de adquirir una suscripción para toda la organización.
- Para los usuarios actuales con una licencia gratuita de Power BI que ahora quieran crear y compartir contenido, y obtener una prueba de Power BI Pro. 

### <a name="you-may-want-to-disable-self-service-when"></a>Casos en los que recomendamos deshabilitar el autoservicio:

- Su organización tiene procesos de adquisición para satisfacer necesidades reglamentarias y de cumplimiento, seguridad y gobernanza. Debe asegurarse de que todas las licencias de Power BI Pro se aprueben y administren de acuerdo con los procesos definidos. 
- Su organización tiene requisitos para los nuevos usuarios de Power BI Pro, como el aprendizaje obligatorio o la confirmación por parte de los usuarios de que aceptan las directivas de protección de datos.
- Su organización prohíbe el uso del servicio Power BI debido a la privacidad de los datos o a otros problemas, y tiene que controlar de forma muy exhaustiva la asignación de licencias gratuitas de Power BI.
- Necesita asegurarse de que todas las licencias de Power BI Pro entren en el ámbito del contrato Enterprise con el fin de aprovechar las tarifas de licencia negociadas o con descuento.
- Para los usuarios actuales con una licencia gratuita de Power BI, a los que se les pide que prueben o compren directamente una licencia de Power BI Pro. Es posible que su organización no quiera que estos usuarios se pasen a Power BI Pro por motivos de seguridad, privacidad o gastos.


## <a name="enable-and-disable-self-service"></a>Habilitación y deshabilitación del autoservicio

Como administrador, puede determinar si quiere habilitar o deshabilitar el registro de autoservicio. También puede determinar si los usuarios de su organización pueden realizar compras de autoservicio para obtener su propia licencia. 

Al desactivar el registro de autoservicio, los usuarios no pueden explorar Power BI para la visualización y el análisis de datos. Si bloquea el registro individual, puede que desee obtener licencias de Power BI (gratis) para su organización y asignarlas a todos los usuarios. 

> [!NOTE]
>Si adquirió Power BI a través de un proveedor de soluciones en la nube de Microsoft (CSP), la configuración podría estar deshabilitada para impedir que los usuarios se registren individualmente. El CSP también puede actuar como administrador global de su organización, lo que requiere que se ponga en contacto con ellos para ayudarle a cambiar esta configuración.
>


 Usará los comandos de PowerShell para cambiar la configuración que controla las compras y el registro de autoservicio. 

- Si quiere deshabilitar todos los inicios de sesión de autoservicio, cambie la configuración en Azure Active Directory denominada **AllowAdHocSubscriptions** mediante los comandos de Azure AD PowerShell. Siga los pasos de este artículo para [habilitar o deshabilitar la suscripción de autoservicio](#enable-or-disable-self-service-sign-up-for-your-organization). Esta opción desactiva el registro de autoservicio para *todos* los servicios y aplicaciones basados en la nube de Microsoft.

- Si quiere impedir que los usuarios compren su propia licencia Pro, cambie el valor **AllowSelfServicePurchase** mediante los comandos de PowerShell de MSCommerce. Esta configuración permite desactivar la compra de autoservicio para productos específicos. Siga los pasos de este artículo para [habilitar o deshabilitar la compra de autoservicio de licencias de Power BI Pro](#enable-or-disable-self-service-purchase-in-your-organization).

## <a name="enable-or-disable-self-service-sign-up-for-your-organization"></a>Habilitación o deshabilitación del registro de autoservicio en su organización

Si el registro de autoservicio está habilitado, el valor de **AllowAdHocSubscriptions** es *true*. Echemos un vistazo a lo que sucede cuando se cambia esta configuración a *false*:

- No se permite que los nuevos usuarios de la organización se registren individualmente. Los usuarios que se hubieran registrado en Power BI antes de que cambiara la configuración conservarán sus licencias.

- Los usuarios con una licencia de Power BI (gratis) todavía pueden registrarse para obtener una prueba de Power BI Pro para usuarios individuales.

- Un administrador tendrá que asignar todas las licencias de Power BI a los nuevos usuarios que las necesiten.

### <a name="before-you-begin"></a>Antes de empezar

En estos pasos se usan los comandos de Azure Active Directory PowerShell para cambiar el valor de la configuración **AllowAdHocSubscriptions**. Debe tener el módulo de Azure AD PowerShell instalado para que estos comandos estén disponibles. Para obtener más información sobre el uso de PowerShell, consulte [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

Para instalar el módulo de Azure AD, inicie Windows PowerShell como administrador. Asegúrese de que la directiva de ejecución local le permita ejecutar scripts. Si tiene problemas, consulte las [directivas de ejecución de PowerShell](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) para obtener información sobre cómo cambiar la directiva local.

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

## <a name="enable-or-disable-self-service-purchase-in-your-organization"></a>Habilitación o deshabilitación de las compras de autoservicio en su organización

Si la compra de autoservicio está habilitada, el valor de **AllowSelfServicePurchase** es *true*. Echemos un vistazo a lo que sucede cuando se cambia esta configuración a *false*:

- No se permite que los usuarios de la organización compren su propia licencia de Power BI Pro. Los usuarios que hubieran comprado una licencia antes de que cambiara la configuración conservarán sus licencias.

- Los usuarios con una licencia de Power BI (gratis) no podrán obtener una licencia de Power BI Pro para usuarios individuales. 

- Un administrador debe asignar una licencia Pro a todos los usuarios que la necesiten.

### <a name="before-you-begin"></a>Antes de empezar

En estos pasos se usan los comandos de PowerShell de MSCommerce para cambiar el valor de la configuración **AllowSelfServicePurchase**. Debe tener el módulo de PowerShell de MSCommerce instalado para que estos comandos estén disponibles. Para obtener más información sobre el uso de PowerShell, consulte [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

Para instalar el módulo de MSCommerce, inicie Windows PowerShell como administrador. Asegúrese de que la directiva de ejecución local le permita ejecutar scripts. Si tiene problemas, consulte las [directivas de ejecución de PowerShell](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies) para obtener información sobre cómo cambiar la directiva local.

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

## <a name="what-to-do-if-individuals-have-already-used-self-service"></a>Qué hacer si los usuarios ya han usado el autoservicio

Las compras y el registro de autoservicio están habilitados de forma predeterminada. Gracias a esto, los usuarios de la organización ya tienen suscripciones y licencias de Power BI. Independientemente de que intervenga o no, necesita tener una idea clara de lo que ya existe en la organización.

A los usuarios que se han unido al inquilino mediante la suscripción autoservicio se les asigna una licencia única por la que se puede filtrar dentro el panel de usuarios activos en el panel de administración. Para crear esta vista, siga estos pasos.

1. Vaya al Centro de administración de Microsoft 365.

1. En el panel de navegación, seleccione **usuarios** > **Usuarios activos**.

1. En el menú Vistas, seleccione **Agregar vista personalizada**.

1. Asigne un nombre a la nueva vista y, en Licencia de producto asignada, seleccione Power BI (gratis) o Power BI Pro.

    Solo puede tener una licencia seleccionada por vista. Si tiene tanto la licencia Power BI (gratis) como la licencia Power BI Pro en su organización, puede crear dos vistas.

1. Escriba cualquier otra condición que desee y después seleccione **Agregar**.

    Después de crear la vista, estará disponible en el menú Vistas.


    > [!NOTE]
    > Si la organización no tiene un entorno de Microsoft 365 conectado a su dominio de correo electrónico, significa que los usuarios de autoservicio se agregaron a un nuevo directorio de usuario solo en la nube. Es posible que necesite buscar, reclamar y [tomar el control de los inquilinos que ya se crearon](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover). 

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre la compra de autoservicio en Power BI y el resto de Power Platform, consulte estos artículos:

- [Preguntas más frecuentes sobre compras de autoservicio](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities)
- [Uso de AllowSelfServicePurchase para el módulo de PowerShell de MSCommerce](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell)