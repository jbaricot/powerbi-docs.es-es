---
title: Registro de una aplicación para insertar contenido de Power BI en una aplicación de análisis integrados de Power BI para obtener una mejor información de BI insertada
description: Aprenda a registrar una aplicación en Azure Active Directory para su uso con la inserción de contenido de Power BI. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 624e0a2838a08d1cf68ae58223fe979a56312b48
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565925"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>Registro de una aplicación de Azure AD para usarla con Power BI

Para usar el análisis de Power BI Embedded, debe registrar una aplicación de Azure Active Directory (Azure AD) en Azure. La aplicación de Azure AD establece permisos para los recursos REST de Power BI y permite el acceso a las [API REST de Power BI](/rest/api/power-bi/).

## <a name="determine-your-embedding-solution"></a>Determinación de la solución de inserción

Antes de registrar la aplicación, decida cuál de las siguientes soluciones es la más adecuada para usted:

* Inserción para los clientes
* Inserción para la organización

### <a name="embed-for-your-customers"></a>Inserción para los clientes

Use la solución de [inserción para los clientes](embed-sample-for-customers.md), lo que también se conoce como *aplicación poseedora de los datos*, si tiene previsto crear una aplicación diseñada para los clientes. Los usuarios no tendrán que iniciar sesión en Power BI ni disponer de una licencia de Power BI para usar la aplicación. La aplicación usará uno de los métodos siguientes para autenticarse en Power BI:

* Cuenta de **usuario principal** (licencia de Power BI Pro usada para iniciar sesión en Power BI)

* [Entidad de servicio](embed-service-principal.md)

Los fabricantes de software independientes (ISV) y los desarrolladores que crean aplicaciones para terceros suelen usar la solución de inserción para los clientes.

### <a name="embed-for-your-organization"></a>Inserción para la organización

Use la solución de [inserción para la organización](embed-sample-for-your-organization.md), lo que también se conoce como *usuario poseedor de los datos*, si tiene previsto crear una aplicación que requiera que los usuarios empleen sus credenciales para autenticarse en Power BI.

La solución de inserción para la organización suelen usarla empresas y organizaciones de gran tamaño, y está pensada para los usuarios internos.

## <a name="register-an-azure-ad-app"></a>Registrar una aplicación de Azure AD

La forma más fácil de registrar una aplicación de Azure AD es mediante la [herramienta de configuración de la inserción de Power BI](https://app.powerbi.com/embedsetup). La herramienta ofrece un proceso de registro rápido para ambas soluciones de inserción mediante una simple interfaz gráfica.

Si va a crear una aplicación de *inserción para la organización* y quiere tener más control sobre la aplicación de Azure AD, puede registrarla manualmente en Azure Portal.

> [!IMPORTANT]
> Antes de registrar una aplicación de Power BI, necesita un [inquilino de Azure Active Directory y un usuario de la organización](create-an-azure-active-directory-tenant.md).

# <a name="embed-for-your-customers"></a>[Insertar para los clientes](#tab/customers)

En estos pasos se describe cómo registrar una aplicación de Azure AD para la solución de [inserción para los clientes](embed-sample-for-customers.md) de Power BI.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. En la sección *Choose an embedding solution* (Elegir una solución de inserción), seleccione **Embed for your customers** (Inserción para los clientes).

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. En el *Paso 2: registro de la aplicación*, rellene los campos siguientes:

    * **Nombre de la aplicación**: asigne un nombre a la aplicación.

    * **Acceso de API**: seleccione las API de Power BI (también conocidas como ámbitos) que la aplicación necesita. Puede usar *Seleccionar todo* para seleccionar todas las API. Para obtener más información sobre los permisos de acceso de Power BI, vea [Permisos y consentimiento en el punto de conexión de la Plataforma de identidad de Microsoft](/azure/active-directory/develop/v2-permissions-and-consent).

5. Seleccione **Registrar**.

    El valor **Id. de aplicación** de la aplicación de Azure AD se muestra en el cuadro *Resumen*. Copie este valor para su uso posterior.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. En el *Paso 5: concesión de permisos*, seleccione **Conceder permisos** y, en la ventana emergente, seleccione **Aceptar**. Esto permite que la aplicación de Azure AD acceda a las API seleccionadas (también conocidas como ámbitos) con el usuario que ha iniciado sesión. Este usuario también se conoce como **usuario principal**.

9. (Opcional) Si ha creado un área de trabajo de Power BI y ha cargado contenido en ella mediante la herramienta, ahora puede seleccionar **Download sample application** (Descargar aplicación de ejemplo). Asegúrese de copiar toda la información en el cuadro *Resumen*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[Insertar para la organización](#tab/organization)

En estos pasos se describe cómo registrar una aplicación de Azure AD para la solución de [inserción para la organización](embed-sample-for-your-organization.md) de Power BI.

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. En la sección *Choose an embedding solution* (Elegir una solución de inserción), seleccione **Embed for your organization** (Inserción para la organización).

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. En el *Paso 2: registro de la aplicación*, rellene los campos siguientes:

    * **Nombre de la aplicación**: asigne un nombre a la aplicación.

    * **Dirección URL de la página principal**: escriba una dirección URL de la página principal.

    * **URL de redireccionamiento**: tras iniciar sesión, se redirigirá a los usuarios de la aplicación a esta dirección, mientras la aplicación recibe un código de autenticación de Azure. Seleccione una de estas opciones:

        * **Use a default URL** (Usar una URL predeterminada): esta opción creará y descargará automáticamente una aplicación de análisis insertada de ejemplo. La dirección URL predeterminada es http://localhost:13526/.

        * **Use a custom URL** (Usar una URL personalizada): seleccione esta opción si ya tiene una aplicación de análisis insertada y sabe qué quiere usar como URL de redireccionamiento.

    * **Acceso de API**: seleccione las API de Power BI (también conocidas como ámbitos) que la aplicación necesita. Puede usar *Seleccionar todo* para seleccionar todas las API. Para obtener más información sobre los permisos de acceso de Power BI, vea [Permisos y consentimiento en el punto de conexión de la Plataforma de identidad de Microsoft](/azure/active-directory/develop/v2-permissions-and-consent).

5. Seleccione **Registrar**.

    Los valores **Id. de aplicación** y **Secreto de aplicación** de la aplicación de Azure AD se muestran en el cuadro *Resumen*. Copie estos valores para su uso posterior.

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (Opcional) Si ha creado un área de trabajo de Power BI y ha cargado contenido en ella mediante la herramienta, ahora puede seleccionar **Download sample application** (Descargar aplicación de ejemplo). Asegúrese de copiar toda la información en el cuadro *Resumen*.

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[Registro manual](#tab/manual)

Use el registro manual de la aplicación de Azure AD solo si va a crear una de las siguientes soluciones:

* Una aplicación de *inserción para la organización*.

* Una aplicación de *inserción para los clientes* con una *entidad de servicio*.

    >[!NOTE]
    >Si elige esta opción, después de registrar la aplicación de Azure AD deberá [agregarle permisos de Power BI](#change-your-azure-ad-apps-permissions).

Para obtener más información sobre cómo registrar aplicaciones en Azure Active Directory, consulte [Registro de una aplicación en Azure Active Directory](/azure/active-directory/develop/quickstart-v2-register-an-app).

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).

2. Elija el inquilino de Azure AD mediante la selección de la cuenta en la esquina superior derecha de la página.

3. Seleccione **App registrations** (Registros de aplicaciones). Si no puede ver esta opción, búsquela.
 
4. En *Registros de aplicaciones*, seleccione **Nuevo registro**.

5. Rellene los campos siguientes:

    * **Nombre**: asigne un nombre a la aplicación.

    * **Supported account type** (Tipo de cuenta admitido): seleccione quién puede usar la aplicación.

6. (Opcional) En el **URI de redireccionamiento**, agregue una dirección URL de redireccionamiento.

7. Seleccione **Registrar**. Una vez registrada la aplicación, se le dirigirá a la página de información general de la aplicación, donde puede obtener el valor *Id. de aplicación*.

---

## <a name="change-your-azure-ad-apps-permissions"></a>Cambio de los permisos de la aplicación de Azure AD

Después de registrar la aplicación, puede realizar cambios en los permisos. Los cambios en los permisos se pueden realizar mediante programación o en Azure Portal.

>[!NOTE]
>Los permisos de la aplicación de Azure AD solo se pueden aplicar a la solución *inserción para los clientes* con el método de autenticación de *usuario maestro*.

# <a name="azure"></a>[Azure](#tab/Azure)

En Azure Portal, puede ver la aplicación y realizar cambios en los permisos.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).

2. Elija el inquilino de Azure AD mediante la selección de la cuenta en la esquina superior derecha de la página.

3. Seleccione **App registrations** (Registros de aplicaciones). Si no puede ver esta opción, búsquela.

4. En la pestaña **Aplicaciones propias**, seleccione la aplicación. La aplicación se abre en la pestaña *Información general*, donde puede revisar el valor *Id. de la aplicación*.

5. Seleccione la pestaña **Permisos de API**.

6. Para agregar permisos, siga estos pasos:

    1. Seleccione **Agregar un permiso** y, luego, **Servicio Power BI**.

    2. Seleccione **Permisos delegados**, y agregue o quite los permisos específicos que necesite.

    3. Cuando haya terminado, seleccione **Agregar permisos** para guardar los cambios.

7. Para quitar un permiso, siga estos pasos:

    1. Seleccione los puntos suspensivos (…) situados a la derecha del permiso.
    
    2. Seleccione **Quitar permiso**.
    
    3. En la ventana emergente *Quitar permiso*, seleccione **Sí, quitar**.

# <a name="http"></a>[HTTP](#tab/HTTP)

Para cambiar los permisos de la aplicación de Azure AD mediante programación, deberá obtener las entidades de servicio (usuarios) existentes en el inquilino. Para información sobre cómo hacerlo, consulte [servicePrincipal](/graph/api/resources/serviceprincipal).

1. Para obtener todas las entidades de servicio del inquilino, llame a la API `Get servicePrincipal` sin `{ID}`.

2. Busque una entidad de servicio con el *Id. de la aplicación* de su aplicación como propiedad `appId`.

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` es opcional.

3. Conceda permisos de Power BI a la aplicación. Para ello, asigne uno de estos valores a `consentType`:

    * `AllPrincipals`: solo lo puede usar un administrador de Power BI para conceder permisos en nombre de todos los usuarios del inquilino.

    * `Principal`: se usa para conceder permisos en nombre de un usuario específico. Si usa esta opción, agregue la propiedad `principalId={User_ObjectId}` al cuerpo de la solicitud.

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* Si usa un **usuario principal**, para evitar que Azure AD le pida consentimiento, debe conceder permisos a la cuenta maestra.
    >* El valor `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* depende del inquilino y no es universal. Este valor es el elemento *objectId* de la aplicación *Servicio Power BI* en Azure AD. Para obtener este valor en Azure Portal, vaya a [Aplicaciones empresariales > Todas las aplicaciones](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps) y busque *Servicio Power BI*.

4. Conceda permisos de aplicación a Azure AD mediante la asignación de un valor a `consentType`.

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

También puede cambiar los permisos de la aplicación de Azure AD mediante C#. Para más información, vea la API [oAuth2PermissionGrant](/graph/api/oauth2permissiongrant-get). Este método puede ser útil si está pensando en automatizar algunos de los procesos.

Para obtener más información sobre las solicitudes HTTP, consulte la [pestaña HTTP](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions).

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

GraphServiceClient graphClient = new GraphServiceClient(authProvider);

// Use oAuth2PermissionGrant to change permissions
var oAuth2PermissionGrant = await graphClient.Oauth2PermissionGrants["{id}"]
               .Request()
               .GetAsync();
```

---

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Obtención de un token de acceso de Azure AD para la aplicación de Power BI](get-azuread-access-token.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)