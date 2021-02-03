---
title: Obtención de un token de acceso de autenticación en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: 'Tutorial para insertar datos: obtención de un token de acceso de autenticación. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.'
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 8959a0ac63ff1f182bcb3544b1925529b1ad3663
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/02/2021
ms.locfileid: "99422407"
---
# <a name="step-2-get-an-authentication-access-token"></a>Paso 2: Obtener un token de acceso de autenticación

Este artículo es el segundo paso de la serie [Inserción de datos en un conjunto de datos de Power BI](walkthrough-push-data.md).

En el paso 1, [registró una aplicación cliente en Azure AD](../embedded/register-app.md). En este paso, obtendrá un token de acceso de autenticación. Las aplicaciones de Power BI se integran con Azure Active Directory para proporcionar a la aplicación un inicio de sesión seguro y autorización. La aplicación usa un token para autenticarse en Azure AD y acceder a los recursos de Power BI.

## <a name="get-an-authentication-access-token"></a>Obtener un token de acceso de autenticación

Antes de comenzar, asegúrese de que ha completado el [paso anterior](../embedded/register-app.md) de la serie [Inserción de datos en un conjunto de datos de Power BI](walkthrough-push-data.md). 

Este procedimiento requiere Visual Studio 2015 o posterior.

1. En Visual Studio 2015, cree un nuevo proyecto de **aplicación de consola** de C#.

2. Instale la [Biblioteca de autenticación de Azure AD para el paquete NuGet de .NET](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727) La aplicación de .NET necesita este paquete para obtener un token de seguridad de autenticación. 

     a. Seleccione **Herramientas** > **Administrador de paquetes NuGet** > **Consola del Administrador de paquetes**.

     b. Escriba **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**.

     c. En Program.cs, agregue `using Microsoft.IdentityModel.Clients.ActiveDirectory;`.

3. Agregue el código de ejemplo que aparece después de estos pasos a Program.cs.

4. Reemplace "{ClientID}" por el **Identificador de cliente** que obtuvo en el [anterior artículo de la serie](../embedded/register-app.md) cuando registró la aplicación.

5. Ejecute la aplicación de consola e inicie sesión en su cuenta de Power BI. 

   Debería aparecer una cadena de token en la ventana de consola.

**Ejemplo de código para obtener un token de seguridad de autenticación**

Agregue este código a Program {...}.

* Una variable de token para llamar a las operaciones: 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* En static void Main(string[] args):
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* Agregue un método GetToken():

```csharp
       #region Get an authentication access token
       private static async Task<string> GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.com/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

Después de obtener un token de autenticación, puede llamar a cualquier operación de Power BI.

El siguiente artículo de esta serie muestra cómo [crear un conjunto de datos en Power BI](walkthrough-push-data-create-dataset.md).


## <a name="complete-code-listing"></a>Lista de código completa

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static async Task<string> GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>Pasos siguientes

* El siguiente artículo de esta serie es [Paso 3: Creación de un conjunto de datos en Power BI](walkthrough-push-data-create-dataset.md)
* [Información general sobre la API de REST de Power BI](overview-of-power-bi-rest-api.md)  
* [API REST de Power BI](/rest/api/power-bi/)  

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)