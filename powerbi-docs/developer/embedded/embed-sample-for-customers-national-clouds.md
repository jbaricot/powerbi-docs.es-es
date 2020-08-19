---
title: Inserción de contenido en la aplicación para nubes de administración pública y nacionales
description: Aprenda a integrar, o insertar, un informe, un panel o un icono, en una aplicación web mediante las API de Power BI para realizar análisis integrados para los clientes. Aprenda a integrar Power BI en una aplicación mediante software de análisis integrado, herramientas de análisis integrado o herramientas de inteligencia empresarial integrada para nubes de administración pública o nacionales.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: tutorial
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: 4087f3d09d509022cb4dd91caebae0f8038e203b
ms.sourcegitcommit: 64139587061136a43c5aea3b6db4d1a94e4e7795
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2020
ms.locfileid: "88204305"
---
# <a name="tutorial-embed-a-power-bi-content-into-your-application-for-national-clouds"></a>Tutorial: Inserción de contenido de Power BI en una aplicación para nubes nacionales

Aprenda a insertar contenido analítico en las aplicaciones de proceso de negocio para la nube nacional. Puede usar .NET SDK de Power BI con la API de JavaScript de Power BI para insertar un informe, panel o icono en las aplicaciones web.

Power BI también admite [nubes nacionales](https://docs.microsoft.com/azure/active-directory/develop/authentication-national-cloud).

Las distintas nubes nacionales son:

* EE. UU. Government Community Cloud (GCC)

* EE. UU. Government Community Cloud High (GCC High)

* EE. UU. Military Contractors (DoDCON)

* EE. UU. Military (DoD)

* Power BI para la nube de Alemania

* Power BI para la nube de China

![Panel insertado](media/embed-sample-for-customers/powerbi-embed-dashboard.png)

Para empezar a trabajar con este tutorial, necesita una **cuenta de Power BI**. Si no tiene una cuenta configurada, según el tipo de gobierno o país, puede elegir la nube nacional adecuada para usted. Puede registrarse para obtener una [cuenta de Power BI del gobierno de EE. UU.](../../admin/service-govus-signup.md), una [cuenta de Power BI para la nube de Alemania](https://powerbi.microsoft.com/power-bi-germany/?ru=https%3A%2F%2Fapp.powerbi.de%2F%3FnoSignUpCheck%3D1) o una [cuenta de Power BI para la nube de China](https://www.21vbluecloud.com/powerbi/).

> [!NOTE]
> En lugar de eso, ¿desea insertar un panel para la organización? Consulte [Integrar un panel en una aplicación para la organización](embed-sample-for-your-organization.md).

Para integrar un panel en una aplicación web, use la API de **Power BI** y un **token de acceso** de autorización de Azure Active Directory (AD) para obtener un panel. A continuación, cargue el panel mediante un token de inserción. La API de **Power BI** proporciona acceso mediante programación a recursos concretos de **Power BI**. Para más información, consulte la [API REST de Power](https://docs.microsoft.com/rest/api/power-bi/), el [SDK de .NET de Power BI] y la [API de JavaScript de Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

## <a name="download-the-sample"></a>Descarga del ejemplo

Este artículo muestra el código usado en [App Owns Data sample](https://github.com/Microsoft/PowerBI-Developer-Samples) de GitHub. Para seguir este tutorial, puede descargar el ejemplo. 

![Ejemplo App Owns Data](media/embed-sample-for-customers-national-clouds/embed-sample-for-customers-026.png)

* Government Community Cloud (GCC):

    > [!NOTE]
    > La inserción de contenido de Power BI desde una nube de comunidad gubernamental (GCC) solo se puede realizar con una SKU de Microsoft 365. Otros clientes de una nube nacional pueden usar las [SKU de Microsoft 365 o de Azure](embedded-faq.md).

1. Sobrescriba el archivo Cloud.config con el contenido de GCCCloud.config.

2. Actualice los campos applicationId (identificador de la aplicación nativa), workspaceId, user (el usuario principal) y password del archivo Web.config.

3. Agregue los parámetros GCC en el archivo web.config como se indica a continuación.

```xml
<add key="authorityUrl" value="https://login.microsoftonline.com/common/" />
<add key="resourceUrl" value="https://analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.powerbigov.us" />
```

* Military Contractors (DoDCON):

1. Sobrescriba el archivo Cloud.config con el contenido de TBCloud.config.

2. Actualice los campos applicationId (identificador de la aplicación nativa), workspaceId, user (el usuario principal) y password del archivo Web.config.

3. Agregue los parámetros DoDCON en el archivo web.config como se indica a continuación.

```xml
<add key="authorityUrl" value="https://login.microsoftonlineS.net/common/" />
<add key="resourceUrl" value="https://high.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.high.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.high.powerbigov.us" />
```

* Military (DoD):

1. Sobrescriba el archivo Cloud.config con el contenido de PFCloud.config.

2. Actualice los campos applicationId (identificador de la aplicación nativa), workspaceId, user (el usuario principal) y password del archivo Web.config.

3. Agregue los parámetros DoDCON en el archivo web.config como se indica a continuación.

```xml
<add key="authorityUrl" value="https://login.microsoftonline.net/common/" />
<add key="resourceUrl" value="https://mil.analysis.usgovcloudapi.net/powerbi/api" />
<add key="apiUrl" value="https://api.mil.powerbigov.us/" />
<add key="embedUrlBase" value="https://app.mil.powerbigov.us" />
```

* Parámetros de Power BI para la nube de Alemania

1. Sobrescriba el archivo Cloud.config con el contenido de Power BI para la nube de Alemania.

2. Actualice los campos applicationId (identificador de la aplicación nativa), workspaceId, user (el usuario principal) y password del archivo Web.config.

3. Agregue los parámetros de Power BI para la nube de Alemania en el archivo web.condig como se indica a continuación.

```xml
<add key="authorityUrl" value="https://login.microsoftonline.de/common/" />
<add key="resourceUrl" value="https://analysis.cloudapi.de/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.de/" />
<add key="embedUrlBase" value="https://app.powerbi.de" />
```

* Parámetros de Power BI para la nube de China

1. Sobrescriba el archivo Cloud.config con el contenido de [Power BI para la nube de China](https://github.com/microsoft/PowerBI-Developer-Samples/blob/master/.NET%20Framework/Embed%20for%20your%20organization/CloudConfigs/Power%20BI%20operated%20by%2021Vianet%20in%20China/Cloud.config).

2. Actualice los campos applicationId (identificador de la aplicación nativa), workspaceId, user (el usuario principal) y password del archivo Web.config.

3. Agregue los parámetros de Power BI para la nube de China en el archivo web.config como se indica a continuación.

```xml
<add key="authorityUrl" value="https://login.chinacloudapi.cn/common/" />
<add key="resourceUrl" value="https://analysis.chinacloudapi.cn/powerbi/api" />
<add key="apiUrl" value="https://api.powerbi.cn/" />
<add key="embedUrlBase" value="https://app.powerbi.cn" />
```

## <a name="step-1---register-an-app-in-azure-ad"></a>Paso 1: Registrar una aplicación en Azure AD

Para realizar llamadas a la API REST, registre la aplicación en Azure AD. Para más información, consulte [Registro de una aplicación de Azure AD para insertar contenido de Power BI](register-app.md). Como hay distintas afiliaciones de nube nacional, hay distintas direcciones URL para registrar la aplicación.

* Government Community Cloud (GCC): ```https://app.powerbigov.us/apps```

* Military Contractors (DoDCON): ```https://app.high.powerbigov.us/apps```

* Military (DoD): ```https://app.mil.powerbigov.us/apps```

* Power BI para la nube de Alemania: ```https://app.powerbi.de/apps```

* Power BI para la nube de China: ```https://app.powerbi.cn/apps```

Si ha descargado el [ejemplo de inserción de contenido para el cliente](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData), use el **identificador de aplicación** que obtenga para que el ejemplo pueda autenticarse en Azure AD. Para configurar el ejemplo, cambie el **identificador de aplicación** en el archivo *web.config*.

## <a name="step-2---get-an-access-token-from-azure-ad"></a>Paso 2: Obtener un token de acceso de Azure AD

En la aplicación, debe obtener un **token de acceso**, desde Azure AD, para poder realizar llamadas a la API de REST de Power BI. Para más información, consulte [Authenticate users and get an Azure AD access token for your Power BI app](get-azuread-access-token.md) (Autenticación de usuarios y obtención de un token de acceso de Azure AD para su aplicación de Power BI). Como hay distintas afiliaciones de nube nacional, hay distintas direcciones URL para obtener un token de acceso para la aplicación.

* Government Community Cloud (GCC): ```https://login.microsoftonline.com```

* Military Contractors (DoDCON): ```https://login.microsoftonline.us```

* Military (DoD): ```https://login.microsoftonline.us```

* Power BI para la nube de Alemania: ```https://login.microsoftonline.de```

* Power BI para la nube de China: ```https://login.chinacloudapi.cn```

Puede ver ejemplos de estos tokens de acceso dentro de cada tarea de elemento de contenido en el archivo **Controllers\HomeController.cs**.

## <a name="step-3---get-a-content-item"></a>Paso 3: Obtener un elemento de contenido

Para insertar el contenido de Power BI, debe hacer un par de cosas para asegurarse de que se inserta correctamente. Aunque todos estos pasos se pueden realizar con la API de REST directamente, la aplicación de ejemplo y los ejemplos siguientes usan el SDK de .NET.

### <a name="create-the-power-bi-client-with-your-access-token"></a>Creación del cliente de Power BI con el token de acceso

Con el token de acceso, debe crear el objeto de cliente de Power BI que le permitirá interactuar con las API de Power BI. Para crear un objeto de cliente de Power BI, ajuste el valor de AccessToken con un objeto *Microsoft.Rest.TokenCredentials*.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI Client object. This is used to call the Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code to embed items.
}
```

### <a name="get-the-content-item-you-want-to-embed"></a>Obtención del elemento de contenido que desea insertar

Use el objeto de cliente de Power BI para recuperar una referencia al elemento que desea insertar. Puede insertar informes, iconos o paneles. Este es un ejemplo de cómo recuperar el primer panel, icono o informe de un área de trabajo determinada.

Un ejemplo está disponible en **Controllers\HomeController.cs** en [el ejemplo de App Owns Data](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

#### <a name="reports"></a>Informes

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListReport reports = client.Reports.GetReportsInGroupAsync(workspaceId);

// Get the first report in the group.
Report report = reports.Value.FirstOrDefault();
```

#### <a name="dashboards"></a>Paneles

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();
```

#### <a name="tiles"></a>Iconos

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// To retrieve the tile, you first need to retrieve the dashboard.

// You need to provide the workspaceId where the dashboard resides.
ODataResponseListDashboard dashboards = client.Dashboards.GetDashboardsInGroup(workspaceId);

// Get the first report in the group.
Dashboard dashboard = dashboards.Value.FirstOrDefault();

// Get a list of tiles from a specific dashboard
ODataResponseListTile tiles = client.Dashboards.GetTilesInGroup(workspaceId, dashboard.Id);

// Get the first tile in the group.
Tile tile = tiles.Value.FirstOrDefault();
```

### <a name="create-the-embed-token"></a>Creación del token de inserción

Con la API de JavaScript, puede generar un token de inserción. El token de inserción es específico del elemento que va a insertar. Siempre que inserte un fragmento de contenido de Power BI, tendrá que crear un token de inserción para él. Para más información, incluido el **accessLevel** que se debe usar, vea [Embed Token](https://docs.microsoft.com/rest/api/power-bi/embedtoken) (Insertar token).

> [!IMPORTANT]
> Dado que la inserción de tokens está pensada solo para que los desarrolladores efectúen pruebas, el número de tokens que puede generar una cuenta maestra de Power BI es limitado. Debe [adquirirse capacidad](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) para escenarios de inserción para producción. No hay ningún límite en la generación de tokens de inserción cuando se compra una capacidad.

Un ejemplo está disponible en **Controllers\HomeController.cs** en el [ejemplo de inserción de contenido para la organización](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

Se crea una clase para **EmbedConfig** y **TileEmbedConfig**. Un ejemplo está disponible en **Models\EmbedConfig.cs** y **Models\TileEmbedConfig.cs**.

#### <a name="reports"></a>Informes

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Reports.GenerateTokenInGroup(workspaceId, report.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = report.EmbedUrl,
    Id = report.Id
};
```

#### <a name="dashboards"></a>Paneles

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Dashboards.GenerateTokenInGroup(workspaceId, dashboard.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new EmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = dashboard.EmbedUrl,
    Id = dashboard.Id
};
```

#### <a name="tiles"></a>Iconos

```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Generate Embed Token for a tile.
var generateTokenRequestParameters = new GenerateTokenRequest(accessLevel: "view");
EmbedToken tokenResponse = client.Tiles.GenerateTokenInGroup(workspaceId, dashboard.Id, tile.Id, generateTokenRequestParameters);

// Generate Embed Configuration.
var embedConfig = new TileEmbedConfig()
{
    EmbedToken = tokenResponse,
    EmbedUrl = tile.EmbedUrl,
    Id = tile.Id,
    dashboardId = dashboard.Id
};
```

## <a name="step-4---load-an-item-using-javascript"></a>Paso 4: Cargar un elemento mediante JavaScript

Puede usar JavaScript para cargar un panel en un elemento div en su página web. El ejemplo utiliza un modelo de EmbedConfig/TileEmbedConfig junto con vistas de un panel, icono o informe. Para obtener un ejemplo completo del uso de la API de JavaScript, puede usar [Microsoft Power BI Embedded Sample](https://microsoft.github.io/PowerBI-JavaScript/demo) (Ejemplo de inserción en Microsoft Power BI).

Hay una aplicación de ejemplo disponible en el [ejemplo Inserción de contenido para la organización](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

### <a name="viewshomeembeddashboardcshtml"></a>Views\Home\EmbedDashboard.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="dashboardContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'dashboard',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedDashboardId
    };

    // Get a reference to the embedded dashboard HTML element
    var dashboardContainer = $('#dashboardContainer')[0];

    // Embed the dashboard and display it within the div container.
    var dashboard = powerbi.embed(dashboardContainer, config);
</script>
```

### <a name="viewshomeembedtilecshtml"></a>Views\Home\EmbedTile.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="tileContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read tile Id from Model
    var embedTileId = "@Model.Id";

    // Read dashboard Id from Model
    var embedDashboardId = "@Model.dashboardId";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'tile',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedTileId,
        dashboardId: embedDashboardId
    };

    // Get a reference to the embedded tile HTML element
    var tileContainer = $('#tileContainer')[0];

    // Embed the tile and display it within the div container.
    var tile = powerbi.embed(tileContainer, config);
</script>
```

### <a name="viewshomeembedreportcshtml"></a>Views\Home\EmbedReport.cshtml

```csharp
<script src="~/scripts/powerbi.js"></script>
<div id="reportContainer"></div>
<script>
    // Read embed application token from Model
    var accessToken = "@Model.EmbedToken.Token";

    // Read embed URL from Model
    var embedUrl = "@Html.Raw(Model.EmbedUrl)";

    // Read report Id from Model
    var embedReportId = "@Model.Id";

    // Get models. models contains enums that can be used.
    var models = window['powerbi-client'].models;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // This also includes settings and options such as filters.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        tokenType: models.TokenType.Embed,
        accessToken: accessToken,
        embedUrl: embedUrl,
        id: embedReportId,
        permissions: models.Permissions.All,
        settings: {
            filterPaneEnabled: true,
            navContentPaneEnabled: true
        }
    };

    // Get a reference to the embedded report HTML element
    var reportContainer = $('#reportContainer')[0];

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);
</script>
```

## <a name="next-steps"></a>Pasos siguientes

* Una aplicación de ejemplo está disponible en GitHub para que la revise. Los ejemplos anteriores se basan en ese ejemplo. Para más información, consulte el [ejemplo de inserción de contenido para la organización](https://github.com/microsoft/PowerBI-Developer-Samples/tree/master/.NET%20Framework/Embed%20for%20your%20customers/PowerBIEmbedded_AppOwnsData).

* Para más información sobre la API de JavaScript, consulte [API de JavaScript para Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

* Para más información sobre Power BI para la nube de Alemania, consulte [Preguntas más frecuentes sobre Power BI para clientes en la nube de Alemania](https://docs.microsoft.com/power-bi/service-govde-faq).

* [Migración de contenido de la colección de áreas de trabajo de Power BI a Power BI](migrate-from-powerbi-embedded.md)

Consideraciones y limitaciones

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
