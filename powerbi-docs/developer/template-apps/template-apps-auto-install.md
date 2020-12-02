---
title: Automatización de la configuración de la instalación de aplicaciones de plantilla para los clientes
description: Obtenga información sobre la automatización de la configuración de la instalación de aplicaciones de plantilla.
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: ca5db6ed7a07d5a6fb10133285378e8318527464
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386101"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>Configuración automatizada de la instalación de una aplicación de plantilla

Las aplicaciones de plantilla son una excelente manera de que los clientes empiecen a obtener conclusiones de sus datos. Estas aplicaciones les permiten ponerse en marcha rápidamente, les conectan a sus datos y les proporcionan informes pregenerados que luego pueden personalizar si lo prefieren.

Los clientes no siempre están familiarizados con los detalles de cómo conectarse a sus datos, y tener que proporcionar estos detalles al instalar una aplicación de plantilla puede resultarles muy complicado.

Si es un proveedor de servicios de datos y ha creado una aplicación de plantilla para ayudar a los clientes a empezar a trabajar con sus datos en el servicio, puede facilitarles la instalación de la aplicación de plantilla automatizando la configuración de sus parámetros. Cuando un cliente inicia sesión en el portal, hace clic en un vínculo especial que usted ha preparado. Esto inicia la automatización, que recopila la información que necesita, configura previamente los parámetros de la aplicación de plantilla y redirige al cliente a su cuenta de Power BI, donde puede instalar la aplicación. Solo tiene que hacer clic en Instalar, autenticarse en su origen de datos y listo. 

A continuación se ilustra esta experiencia del cliente.

![Ilustración de la experiencia del usuario con la aplicación de instalación automática.](media/template-apps-auto-install/high-level-flow.png)

En este artículo se describe el flujo básico, los requisitos previos y los pasos principales y las API que necesita para automatizar la configuración de la instalación de una aplicación de plantilla. Pero si prefiere profundizar y dar los primeros pasos, puede ir directamente al [tutorial](template-apps-auto-install-tutorial.md) en el que se automatiza la configuración de la instalación de la aplicación de plantilla con una aplicación de ejemplo sencilla que se ha preparado y en la que se usa una función de Azure.

## <a name="basic-flow"></a>Flujo básico

El flujo básico de automatización de la configuración de la instalación de una aplicación de plantilla es el siguiente:

1. El usuario inicia sesión en el portal del ISV y hace clic en el vínculo proporcionado. Esto inicia el flujo automatizado. En esta fase, el portal del ISV prepara la configuración específica del usuario.

2. El ISV adquiere un token **de solo aplicación** basado en una [entidad de servicio (token de solo aplicación)](../embedded/embed-service-principal.md), que está registrada en el inquilino del ISV.

3. Mediante las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), el ISV crea un **vale de instalación** que contiene la configuración de parámetros específicos del usuario, tal y como la haya preparado el ISV.

4. El ISV redirige al usuario a Power BI mediante un método de redireccionamiento ```POST``` que contiene el vale de instalación.

5. Se redirige al usuario a su cuenta de Power BI con el vale de instalación y se le pide que instale la aplicación de plantilla. Cuando el usuario hace clic en instalar, la aplicación de plantilla se instala de forma automática.

>[!Note]
>Aunque el ISV configura los valores de parámetro al crear el vale de instalación, las credenciales relacionadas con el origen de datos solo las proporciona el usuario en las fases finales de la instalación. Esto evita que se expongan a un tercero, lo que garantiza una conexión segura entre el usuario y los orígenes de datos de la aplicación de plantilla.

## <a name="prerequisites"></a>Prerrequisitos

Para proporcionar una experiencia de instalación preconfigurada para la aplicación de plantilla, se necesitan los requisitos previos siguientes:

* Una **licencia de Power BI Pro.** . Si no está registrado para Power BI Pro, [regístrese para una evaluación gratuita](https://powerbi.microsoft.com/pricing/) antes de comenzar.

* Una **configuración de inquilino de Azure Active Directory** propia. Vea [Creación de un inquilino de Azure Active Directory](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant) para obtener instrucciones sobre cómo configurar uno.

* Una **entidad de servicio (token de solo aplicación)** registrada en el inquilino anterior. Vea [Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal) para obtener más información. Asegúrese de registrar la aplicación como una **aplicación web del lado servidor**. Una aplicación web del lado servidor se registra para crear un secreto de aplicación. A partir de este proceso, tendrá que guardar el *Id. de aplicación* (Id. de cliente) y el *Secreto de aplicación* (Secreto de cliente) para los pasos posteriores.

* Una **aplicación de plantilla parametrizada** lista para la instalación. La aplicación de plantilla se debe crear en el mismo inquilino en el que registre la aplicación en Azure Active Directory (Azure AD). Para obtener más información, vea [Sugerencias de aplicación de plantilla](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips.md) o [Creación de una aplicación de plantilla en Power BI](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create). En la aplicación de plantilla debe anotar esta información para los pasos siguientes:
     * *Id. de la aplicación*, *clave del paquete* e *identificador del propietario*, tal y como aparecen en la dirección URL de instalación al final del proceso [Definición de las propiedades de la aplicación de plantilla](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) cuando se ha creado la aplicación. También puede obtener el mismo vínculo si hace clic en **Obtener vínculo** en [Administración de versiones](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) de la aplicación de plantilla.

    * Los *nombres de parámetro* como se definen en el conjunto de datos de la aplicación de plantilla. Los nombres de parámetro son cadenas que distinguen mayúsculas de minúsculas y también se pueden recuperar en la pestaña **Configuración de parámetros** cuando se [definen las propiedades de la aplicación de plantilla](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), o bien desde la configuración del conjunto de datos de Power BI.

    >[!NOTE]
    >Puede probar la aplicación de instalación preconfigurada en la aplicación de plantilla si está lista para la instalación, incluso si todavía no está disponible de forma pública en AppSource. Pero para que los usuarios ajenos al inquilino puedan utilizar la aplicación de instalación automatizada para instalar la aplicación de plantilla, esta debe estar disponible de forma pública en el [marketplace de aplicaciones de Power BI](https://app.powerbi.com/getdata/services). Por tanto, antes de distribuir la aplicación de plantilla con la aplicación de instalación automatizada que va a crear, asegúrese de publicarla en el [Centro de partners](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer).

## <a name="main-steps-and-apis"></a>Pasos principales y API

Los pasos principales para automatizar la configuración de una instalación de aplicación de plantilla y las API que necesitará se describen en las secciones siguientes. Aunque la mayoría de los pasos se realizan con las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), los ejemplos de código que se describen a continuación se realizan con el **SDK de .NET**.

## <a name="step-1-create-a-power-bi-client-object"></a>Paso 1: Creación de un objeto de cliente de Power BI 

Para usar las API REST de Power BI es necesario obtener de **Azure AD** un **token de acceso** para la [entidad de servicio](../embedded/embed-service-principal.md). Tendrá que obtener un [token de acceso de Azure AD](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data) para la aplicación de Power BI antes de llamar a las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/).
Para crear el cliente de Power BI con el **token de acceso**, tiene que crear el objeto de cliente de Power BI, que permite interactuar con las [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/). Para crear un objeto de cliente de Power BI, ajuste el valor de **AccessToken** con un objeto **_Microsoft.Rest.TokenCredentials_* _.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. it's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>Paso 2: Creación de un vale de instalación

Cree un vale de instalación, que se usa cuando se redirige a los usuarios a Power BI. La API que se usa para esta operación es _ *CreateInstallTicket**.
* [CreateInstallTicket para aplicaciones de plantilla](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

Un ejemplo de cómo crear un vale de instalación para la instalación y configuración de la aplicación de plantilla está disponible en el archivo [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) de la [aplicación de ejemplo](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample).


A continuación se muestra un ejemplo de código del uso de la API REST *CreateInstallTicket* de la aplicación de plantilla.
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

// Issue the request to the REST API using .NET SDK
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>Paso 3: Redireccionamiento de los usuarios a Power BI con el vale

Una vez que haya creado un vale de instalación, lo usará con el fin de redirigir a los usuarios a Power BI para continuar con la instalación y la configuración de la aplicación de plantilla. Esto se hace mediante un redireccionamiento de método ```POST``` a la dirección URL de instalación de la aplicación de plantilla, con el vale de instalación en el cuerpo de la solicitud.

Hay varios métodos documentados sobre cómo emitir un redireccionamiento mediante solicitudes ```POST```. La elección de uno u otro depende del escenario y de cómo interactúen los usuarios con el portal o el servicio.

Un ejemplo simple, que se usa principalmente con fines de prueba, aprovecha un formulario con un campo oculto, que se envía de forma automática tras la carga.

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

A continuación se muestra un ejemplo de la respuesta de la [aplicación de ejemplo](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample), que contiene el vale de instalación y redirige automáticamente a los usuarios a Power BI. La respuesta para esta función de Azure es, en realidad, el mismo formulario de envío automático que se ve en el ejemplo HTML anterior.

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
>Aunque hay varios métodos para usar redireccionamientos de explorador ```POST```, siempre debe usar el método más seguro, que depende de las necesidades y restricciones del servicio. Recuerde que algunas formas de redireccionamiento no seguro pueden dar lugar a la exposición de los usuarios o del servicio a problemas de seguridad.

## <a name="step-4-move-your-automation-to-production"></a>Paso 4: Traslado de la automatización a producción

Cuando la automatización que ha diseñado esté lista, asegúrese de moverla a producción.

## <a name="next-steps"></a>Pasos siguientes

* Pruebe el [tutorial](template-apps-auto-install-tutorial.md) en el que se usa una función sencilla de Azure para automatizar la configuración de la instalación de una aplicación de plantilla.

* ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
