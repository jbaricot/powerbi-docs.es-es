---
title: Uso de un dirección de correo electrónico alternativa
description: Uso de un dirección de correo electrónico alternativa
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: b03ecff1bcb74789adfea640c0279b568a09ffc7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409088"
---
# <a name="use-an-alternate-email-address"></a>Uso de un dirección de correo electrónico alternativa

Al suscribirse a Power BI, proporciona una dirección de correo electrónico. De forma predeterminada, Power BI usa esta dirección para enviar actualizaciones acerca de la actividad en el servicio. Por ejemplo, cuando alguien le envía una invitación de uso compartido, se remite a esta dirección.

A veces, puede que desee que estos correos electrónicos se entreguen a una dirección de correo electrónico alternativa en lugar de a la que usó para registrarse. En este artículo se explica cómo especificar una dirección alternativa en Microsoft 365 y en PowerShell. En el artículo también se explica cómo se resuelve una dirección de correo electrónico en Azure Active Directory (Azure AD).

> [!NOTE]
> La especificación de una dirección alternativa no afecta a la dirección de correo electrónico que Power BI usa para las suscripciones de correo electrónico, las actualizaciones del servicio, los boletines y otras comunicaciones promocionales. Esas comunicaciones siempre se envían a la dirección de correo electrónico que usó al suscribirse a Power BI.

## <a name="use-microsoft-365"></a>Uso de Microsoft 365

Para especificar una dirección alternativa en Microsoft 365, siga estos pasos.

1. Abra la página [Información personal](https://portal.office.com/account/#personalinfo) de su cuenta. Si la aplicación se lo solicita, inicie sesión con la dirección de correo electrónico y la contraseña que se usa para Power BI.

1. En el menú izquierdo, seleccione **Información personal**.

1. En la sección **Detalles de contacto**, seleccione **Editar**.

    Si no puede editar los detalles, significa que el administrador administra la dirección de correo electrónico. Póngase en contacto con el administrador para actualizar su dirección de correo electrónico.

    ![Captura de pantalla del cuadro de diálogo Detalles de contacto en el que se muestra cómo especificar un correo electrónico alternativo.](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. En el campo **Correo electrónico alternativo**, escriba la dirección de correo electrónico a la que quiere que Microsoft 365 envíe las actualizaciones de Power BI.

## <a name="use-powershell"></a>Uso de PowerShell

Para especificar una dirección alternativa en PowerShell, use el comando [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Resolución de direcciones de correo electrónico en Azure AD

Para capturar un token de inserción de Azure AD para Power BI, puede usar tres tipos distintos de dirección de correo electrónico:

* La dirección de correo electrónico principal asociada a una cuenta de Azure AD de un usuario

* La dirección de correo electrónico de UserPrincipalName (UPN)

* El atributo de matriz *Otra dirección de correo electrónico*

Power BI selecciona la dirección de correo electrónico que se va según la siguiente secuencia:

1. Si el atributo de correo electrónico del objeto de usuario de Azure AD está presente, Power BI usará ese atributo para la dirección de correo electrónico.

1. Si la dirección de correo electrónico UPN *no* es una dirección de correo electrónico con el dominio **\*.onmicrosoft.com** (la información que aparece detrás del símbolo "\@"), Power BI usa ese atributo de correo para la dirección de correo electrónico.

1. Si el atributo de matriz *Otra dirección de correo electrónico* del objeto de usuario de Azure AD está presente, Power BI usa la primera dirección de correo electrónico de esa lista (dado que puede haber una lista de direcciones de correo electrónico en este atributo).

1. Si no está presente ninguna de las condiciones anteriores, Power Bi usa la dirección UPN.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
