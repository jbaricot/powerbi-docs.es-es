---
title: Automatización de la configuración de la instalación de aplicaciones de plantilla para los clientes
description: Obtenga información sobre la automatización de la configuración de la instalación de aplicaciones de plantilla.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 0852fcb2c932680f6c20aeee94a89c68f473e46d
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565730"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Configuración automatizada de la instalación de una aplicación de plantilla

Las aplicaciones de plantilla son una excelente manera de que los clientes empiecen a obtener conclusiones de sus datos. Esto se debe a que con estas aplicaciones de plantilla se pueden poner manos a la obra rápidamente conectándose a sus datos. Las aplicaciones de plantilla les proporcionan informes generados previamente que pueden personalizar si así lo desean.

Los clientes no siempre están al tanto de todos los detalles sobre cómo conectarse a sus datos, de modo que tener que proporcionar estos detalles al instalar una aplicación de plantilla puede ser un problema para ellos.

Si es un proveedor de servicios de datos y ha creado una aplicación de plantilla para ayudar a los clientes a empezar a trabajar con sus datos en el servicio, puede facilitarles la instalación de la aplicación de plantilla, automatizando para ello la configuración de los parámetros de la aplicación de plantilla. Cuando un cliente inicia sesión en el portal, selecciona un vínculo especial que usted ha preparado. Este vínculo:

- Inicia la automatización, que recopila la información que necesita.
- Preconfigura los parámetros de la aplicación de plantilla.
- Redirige al cliente a su cuenta de Power BI, donde puede instalar la aplicación.

Solo tiene que seleccionar **Instalar**, autenticarse en su origen de datos y listo.

Aquí se ilustra esta experiencia del cliente.

![Ilustración de la experiencia de usuario con la aplicación de instalación automática](media/template-apps-auto-install/high-level-flow.png)

En este artículo se describe el flujo básico, los requisitos previos y los pasos principales y las API que necesita para automatizar la configuración de la instalación de una aplicación de plantilla. Si quiere entrar de lleno para empezar, puede ir directamente al [tutorial](template-apps-auto-install-tutorial.md) en el que se automatiza la configuración de la instalación de la aplicación de plantilla con una aplicación de ejemplo sencilla que se ha preparado y en la que se usa una función de Azure.

## <a name="basic-flow"></a>Flujo básico

El flujo básico de automatización de la configuración de la instalación de una aplicación de plantilla es el siguiente:

1. El usuario inicia sesión en el portal del ISV y selecciona el vínculo proporcionado. Esta acción inicia el flujo automatizado. En esta fase, el portal del ISV prepara la configuración específica del usuario.

1. El ISV adquiere un token *de solo aplicación* basado en una [entidad de servicio (token de solo aplicación)](../embedded/embed-service-principal.md), que está registrada en el inquilino del ISV.

1. Mediante las [API REST de Power BI](/rest/api/power-bi/), el ISV crea un *vale de instalación* que contiene la configuración de parámetros específicos del usuario, tal y como la haya preparado el ISV.

1. El ISV redirige al usuario a Power BI mediante un método de redireccionamiento ```POST``` que contiene el vale de instalación.

1. Se redirige al usuario a su cuenta de Power BI con el vale de instalación y se le pide que instale la aplicación de plantilla. Cuando el usuario selecciona **Instalar**, la aplicación de plantilla se instala de forma automática.

>[!Note]
>Aunque el ISV configura los valores de parámetro durante el proceso de creación del vale de instalación, las credenciales relacionadas con el origen de datos solo las proporciona el usuario en las fases finales de la instalación. Esto está dispuesto así para evitar que las credenciales se expongan a un tercero y, asimismo, para garantizar una conexión segura entre el usuario y los orígenes de datos de la aplicación de plantilla.

## <a name="prerequisites"></a>Prerrequisitos

Para proporcionar una experiencia de instalación preconfigurada para la aplicación de plantilla, se necesitan los requisitos previos siguientes:

* Una licencia de Power BI Pro. . Si no está registrado para Power BI Pro, [regístrese para una evaluación gratuita](https://powerbi.microsoft.com/pricing/) antes de comenzar.
* Tener su propio inquilino de Azure Active Directory (Azure AD) configurado. Vea [Creación de un inquilino de Azure AD](../embedded/create-an-azure-active-directory-tenant.md) para obtener instrucciones sobre cómo configurar uno.
* Tener una **entidad de servicio (token de solo aplicación)** registrada en el inquilino anterior. Para obtener más información, vea [Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación](../embedded/embed-service-principal.md). Asegúrese de registrar la aplicación como una **aplicación web del lado servidor**. Una aplicación web del lado servidor se registra para crear un secreto de aplicación. A partir de este proceso, tendrá que guardar el *Id. de aplicación* (ClientID) y el *Secreto de aplicación* (ClientSecret) para los pasos posteriores.
* Tener una **aplicación de plantilla parametrizada** lista para la instalación. La aplicación de plantilla se debe crear en el mismo inquilino en el que registre la aplicación en Azure AD. Para obtener más información, vea [Sugerencias de aplicación de plantilla](../../connect-data/service-template-apps-tips.md) o [Creación de una aplicación de plantilla en Power BI](../../connect-data/service-template-apps-create.md). En la aplicación de plantilla debe anotar esta información para los pasos siguientes:
     * *Id. de la aplicación*, *clave del paquete* e *identificador del propietario*, tal y como aparecen en la dirección URL de instalación al final del proceso de [Definición de las propiedades de la aplicación de plantilla](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) cuando se ha creado la aplicación. También puede obtener el mismo vínculo si selecciona **Obtener vínculo** en el panel [Administración de versiones](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) de la aplicación de plantilla.
    * Los *nombres de parámetro* como se definen en el conjunto de datos de la aplicación de plantilla. Los nombres de parámetro son cadenas que distinguen mayúsculas de minúsculas y también se pueden recuperar en la pestaña **Configuración de parámetros** cuando se [definen las propiedades de la aplicación de plantilla](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), o bien desde la configuración del conjunto de datos de Power BI.

    >[!NOTE]
    >Puede probar la aplicación de instalación preconfigurada en la aplicación de plantilla si está lista para la instalación, incluso si todavía no está disponible de forma pública en AppSource. Para que los usuarios ajenos al inquilino puedan utilizar la aplicación de instalación automatizada para instalar la aplicación de plantilla, esta debe estar disponible de forma pública en el [marketplace de aplicaciones de Power BI](https://app.powerbi.com/getdata/services). Antes de distribuir la aplicación de plantilla con la aplicación de instalación automatizada que va a crear, asegúrese de publicarla en el [Centro de partners](/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Pasos principales y API

Los pasos principales para automatizar la configuración de una instalación de aplicación de plantilla y las API que necesitará se describen en las secciones siguientes. Aunque la mayoría de los pasos se realizan con las [API REST de Power BI](/rest/api/power-bi/), los ejemplos de código que se describen aquí se realizan con el SDK de .NET.

## <a name="step-1-create-a-power-bi-client-object"></a>Paso 1: Creación de un objeto de cliente de Power BI

Para usar las API REST de Power BI es necesario obtener de Azure AD un *token de acceso* de la [entidad de servicio](../embedded/embed-service-principal.md). Tendrá que obtener un [token de acceso de Azure AD](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para la aplicación de Power BI antes de llamar a las [API REST de Power BI](/rest/api/power-bi/).
Para crear el cliente de Power BI con el token de acceso, tiene que crear el objeto de cliente de Power BI, que permite interactuar con las [API REST de Power BI](/rest/api/power-bi/). Para crear un objeto de cliente de Power BI, ajuste el valor de **AccessToken** con un objeto **Microsoft.Rest.TokenCredentials**.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI client object. It's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Paso 2: Creación de un vale de instalación

Cree un vale de instalación, que se usa cuando se redirige a los usuarios a Power BI. La API que se usa para esta operación es **CreateInstallTicket**.
* [CreateInstallTicket para aplicaciones de plantilla](/rest/api/power-bi/templateapps/createinstallticket)

Un ejemplo de cómo crear un vale de instalación para la instalación y configuración de la aplicación de plantilla está disponible en el archivo [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) de la [aplicación de ejemplo](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


El siguiente ejemplo de código muestra cómo usar la API REST **CreateInstallTicket** de la aplicación de plantilla.
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK.
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Paso 3: Redireccionamiento de los usuarios a Power BI con el vale

Una vez que haya creado un vale de instalación, lo usará con el fin de redirigir a los usuarios a Power BI para continuar con la instalación y la configuración de la aplicación de plantilla. Hay que usar un redireccionamiento de método ```POST``` a la dirección URL de instalación de la aplicación de plantilla, con el vale de instalación en el cuerpo de la solicitud.

Existen varios métodos documentados sobre cómo emitir un redireccionamiento mediante solicitudes ```POST```. La elección de uno u otro depende del escenario y de cómo interactúen los usuarios con el portal o el servicio.

Un ejemplo simple, que se usa principalmente con fines de prueba, emplea un formulario con un campo oculto, que se envía de forma automática tras la carga.

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

El siguiente ejemplo de la respuesta de la [aplicación de ejemplo](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample) contiene el vale de instalación y redirige automáticamente a los usuarios a Power BI. La respuesta para esta función de Azure es, en realidad, el mismo formulario de envío automático que se ve en el ejemplo HTML anterior.

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>Aunque hay varios métodos para usar redireccionamientos de explorador ```POST```, siempre debe usar el método más seguro, que dependerá de las necesidades y restricciones del servicio. Recuerde que algunas formas de redireccionamiento no seguro pueden dar lugar a la exposición de los usuarios o del servicio a problemas de seguridad.

## <a name="step-4-move-your-automation-to-production"></a>Paso 4: Traslado de la automatización a producción

Cuando la automatización que ha diseñado esté lista, asegúrese de moverla a producción.

## <a name="next-steps"></a>Pasos siguientes

* Pruebe el [tutorial](template-apps-auto-install-tutorial.md) en el que se usa una función sencilla de Azure para automatizar la configuración de la instalación de una aplicación de plantilla.
* ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).