---
title: Inserción de contenido de Power BI en una aplicación de análisis insertados con una entidad de servicio y un secreto de aplicación que permita una mejor información insertada de BI
description: Obtenga información sobre cómo autenticarse en análisis insertados mediante una entidad de servicio de aplicación de Azure Active Directory y un secreto de aplicación. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 02/04/2021
ms.openlocfilehash: 6a322d331dce9fd989a93545745cf7feb2d9eb70
ms.sourcegitcommit: afdc9d41da6a4fced63030648d3f976425131732
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99569977"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación

La entidad de servicio es un método de autenticación que se puede usar para permitir que una aplicación de Azure AD tenga acceso a las API y el contenido del servicio Power BI.

Al crear una aplicación de Azure Active Directory (Azure AD), se crea un [objeto de entidad de servicio](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). El objeto de entidad de servicio, también conocido como *entidad de servicio*, permite que Azure AD autentique su aplicación. Una vez autenticada, la aplicación puede acceder a los recursos del inquilino de Azure AD.

Para realizar la autenticación, la entidad de servicio usa el *identificador de aplicación* de la aplicación de Azure AD y uno de los siguientes:

* Certificado
* Secreto de aplicación

En este artículo se describe la autenticación de la entidad de servicio mediante el *identificador de aplicación* y el *secreto de aplicación*.

>[!NOTE]
>Azure AD recomienda proteger los servicios de back-end mediante certificados, en lugar de claves secretas.
>* [Obtenga más información sobre cómo obtener tokens de acceso de Azure AD mediante claves secretas o certificados](/azure/architecture/multitenant-identity/client-assertion).
>* Para proteger la solución mediante un certificado, complete las instrucciones de este artículo y, después, siga los pasos descritos en [Inserción de contenido de Power BI con entidades de servicio y un certificado](embed-service-principal-certificate.md).

## <a name="method"></a>Método

Para usar la entidad de servicio y un identificador de aplicación con análisis insertados, siga estos pasos:

1. Cree una [aplicación de Azure AD](/azure/active-directory/manage-apps/what-is-application-management).

    1. Cree el secreto de la aplicación de Azure AD.
    
    2. Obtenga el *identificador de aplicación* y el *secreto de aplicación* de la aplicación.

    >[!NOTE]
    >Estos pasos se describen en el **paso 1**. Para obtener más información sobre la creación de una aplicación de Azure AD, consulte el artículo [Creación de una aplicación de Azure AD](/azure/active-directory/develop/howto-create-service-principal-portal).

2. Cree de un grupo de seguridad de Azure AD.

3. Habilite la configuración de administración del servicio Power BI.

4. Agregue la entidad de servicio a su área de trabajo.

5. Inserte el contenido.

> [!IMPORTANT]
> Después de habilitar la entidad de servicio para usarla con Power BI, los permisos de AD de la aplicación ya no tendrán efecto. Los permisos de la aplicación se administrarán desde el portal de administración de Power BI.

## <a name="step-1---create-an-azure-ad-app"></a>Paso 1: Creación de una aplicación de Azure AD

Cree una aplicación de Azure AD con uno de estos métodos:

* [Cree la aplicación en Microsoft Azure Portal](embed-service-principal.md#creating-an-azure-ad-app-in-the-microsoft-azure-portal)

* [Cree la aplicación mediante PowerShell](embed-service-principal.md#creating-an-azure-ad-app-using-powershell)

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Creación de una aplicación de Azure AD en Microsoft Azure Portal

1. Inicie sesión en [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Busque **Registros de aplicaciones** y haga clic en el vínculo **Registros de aplicaciones**.

    ![registro de aplicaciones de Azure](media/embed-service-principal/azure-app-registration.png)

3. Haga clic en **Nuevo registro**.

    ![nuevo registro](media/embed-service-principal/new-registration.png)

4. Rellene la información necesaria:
    * **Nombre**: escriba un nombre para la aplicación.
    * **Tipos de cuenta admitidos**: seleccione tipos de cuenta admitidos.
    * (Opcional) **URI de redireccionamiento**: escriba un URI si es necesario.

5. Haga clic en **Registrar**.

6. Después del registro, el *identificador de la aplicación* está disponible en la pestaña **Información general**. Copie y guarde el *identificador de aplicación* para su uso posterior.

    ![Captura de pantalla en la que se muestra dónde obtener un identificador de aplicación en la pestaña Información general.](media/embed-service-principal/application-id.png)

7. Haga clic en la pestaña **Certificados y secretos**.

     ![Captura de pantalla que muestra el panel Certificados y secretos para una aplicación en Azure Portal.](media/embed-service-principal/certificates-and-secrets.png)

8. Haga clic en **Nuevo secreto de cliente**.

    ![Captura de pantalla que muestra el botón Nuevo secreto de cliente en el panel Certificados y secretos.](media/embed-service-principal/new-client-secret.png)

9. En la ventana *Agregar un secreto de cliente*, escriba una descripción, especifique cuándo desea que expire el secreto de cliente y haga clic en **Agregar**.

10. Copie y guarde el valor del *secreto de cliente*.

    ![Captura de pantalla que muestra un valor de secreto desenfocado en el panel Certificados y secretos.](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Después de salir de esta ventana, se ocultará el valor de secreto de cliente y no podrá verlo ni copiarlo de nuevo.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Creación de una aplicación de Azure AD con PowerShell

En esta sección se incluye un script de ejemplo para crear una nueva aplicación de Azure AD con [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>Paso 2: Creación de un grupo de seguridad de Azure AD

La entidad de servicio no tiene acceso al contenido ni a las API de Power BI. Para conceder acceso a la entidad de servicio, cree un grupo de seguridad en Azure AD y agregue la entidad de servicio que creó a ese grupo de seguridad.

Hay dos maneras de crear un grupo de seguridad de Azure AD:
* [Manualmente (en Azure)](embed-service-principal.md#create-a-security-group-manually)
* [Uso de PowerShell](embed-service-principal.md#create-a-security-group-using-powershell)

### <a name="create-a-security-group-manually"></a>Creación de un grupo de seguridad manualmente

Para crear un grupo de seguridad de Azure manualmente, siga las instrucciones del artículo [Creación de un grupo básico e incorporación de miembros con Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Creación de un grupo de seguridad mediante PowerShell

A continuación se muestra un script de ejemplo para crear un nuevo grupo de seguridad y agregar una aplicación a ese grupo de seguridad.

>[!NOTE]
>Si desea habilitar el acceso de la entidad de servicio para toda la organización, omita este paso.

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Paso 3: Habilitación de la configuración de administración del servicio Power BI

Para que una aplicación de Azure AD pueda acceder al contenido y las API de Power BI, un administrador de Power BI debe habilitar el acceso de entidad de servicio en el portal de administración de Power BI.

Agregue el grupo de seguridad que ha creado en Azure AD a la sección de grupos de seguridad específicos en la **Configuración del desarrollador**.

>[!IMPORTANT]
>Las entidades de servicio tienen acceso a cualquier configuración de inquilino para la que estén habilitadas. En función de la configuración de administración, esto incluye grupos de seguridad específicos o toda la organización.
>
>Para restringir el acceso de la entidad de servicio a una configuración de inquilino específica, permita el acceso únicamente a grupos de seguridad específicos. También puede crear un grupo de seguridad dedicado para entidades de servicio y excluirlo de la configuración de inquilino que desee.

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-service-principal/admin-portal.png" alt-text="Captura de pantalla que muestra la configuración del desarrollador en las opciones de administración del servicio Power BI":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Paso 4: Adición de la entidad de servicio al área de trabajo

Para permitir que la aplicación de Azure AD acceda a artefactos como informes, paneles y conjuntos de datos en el servicio Power BI, agregue la instancia de la entidad de servicio, o bien el grupo de seguridad en el que se incluya, como miembro o administrador al área de trabajo.

>[!NOTE]
>En esta sección se proporcionan instrucciones para la interfaz de usuario. También puede agregar una entidad de servicio o un grupo de seguridad a un área de trabajo mediante la [API Grupos: agregar usuario de grupo](/rest/api/power-bi/groups/addgroupuser).

1. Desplácese hasta el área de trabajo para el que desea habilitar el acceso y, en el menú **Más**, seleccione **Acceso al área de trabajo**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Captura de pantalla que muestra el botón de acceso al área de trabajo en el menú Más de un área de trabajo de Power BI.":::

2. En el panel **Acceso**, agregue uno de los elementos siguientes:

    * La **entidad de servicio**. El nombre de la entidad de servicio es el *Nombre para mostrar* de la aplicación de Azure AD, tal y como aparece en la pestaña Información general de la aplicación.

    * El **grupo de seguridad** en el que se incluye la entidad de servicio.

3. En el menú desplegable, seleccione **Miembro** o **Administrador**.

4. Seleccione **Agregar**.

### <a name="add-a-service-principal-as-a-workspace-member-using-powershell"></a>Incorporación de una entidad de servicio como miembro de un área de trabajo mediante PowerShell

En esta sección se incluye un script de ejemplo para agregar una entidad de servicio como miembro de un área de trabajo mediante [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

```powershell
Login-PowerBI

# Service Principal Object ID for the created Service Principal
$SPObjectId = 'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX'

$pbiWorkspace = Get-PowerBIWorkspace -Name "YourWorkspaceName"

Add-PowerBIWorkspaceUser -Id $pbiWorkspace.Id -AccessRight Member -PrincipalType App -Identifier $SPObjectId 

```

### <a name="add-a-security-group-as-a-workspace-member-using-powershell"></a>Incorporación de un grupo de seguridad como miembro de un área de trabajo mediante PowerShell

En esta sección se incluye un script de ejemplo para agregar un grupo de seguridad como miembro de un área de trabajo mediante [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

```powershell
Login-PowerBI

# Security Group Object ID for the created Security Group
$SGObjectId = 'XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX'

$pbiWorkspace = Get-PowerBIWorkspace -Name "YourWorkspaceName"

Add-PowerBIWorkspaceUser -Id $pbiWorkspace.Id -AccessRight Member -PrincipalType Group -Identifier $SGObjectId 

```

## <a name="step-5---embed-your-content"></a>Paso 5: Inserción del contenido

Puede [insertar el contenido en una aplicación de ejemplo](embed-sample-for-customers.md) o en una propia.

Una vez insertado el contenido, está listo para [pasar a producción](move-to-production.md).

>[!NOTE]
>Para proteger la solución mediante un certificado, siga los pasos descritos en [Inserción de contenido de Power BI con entidades de servicio y un certificado](embed-service-principal-certificate.md).

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

* La entidad de servicio solo funciona con [áreas de trabajo nuevas](../../collaborate-share/service-create-the-new-workspaces.md).
* Cuando se usa la entidad de servicio, no se admite **Mi área de trabajo**.
* Para pasar a producción, se necesita una capacidad.
* No se puede iniciar sesión en el portal de Power BI con la entidad de servicio.
* Se necesitan derechos de administrador de Power BI para habilitar la entidad de servicio en la configuración de desarrollador en el portal de administración de Power BI.
* Las aplicaciones de [inserción para la organización](embed-sample-for-your-organization.md) no pueden usar la entidad de servicio.
* No se admite la administración de [flujos de datos](../../transform-model/dataflows/dataflows-introduction-self-service.md).
* La entidad de servicio solo admite algunas API de administración de solo lectura. Para habilitar la compatibilidad de la entidad de servicio con las API de administración de solo lectura, debe habilitar la configuración de administración del servicio Power BI en su inquilino. Para más información, vea [Habilitación de la autenticación de entidad de servicio para las API de administración de solo lectura](../../admin/read-only-apis-service-principal-authentication.md).
* Al usar una entidad de servicio con un origen de datos de [Azure Analysis Services](/azure/analysis-services/analysis-services-overview), la propia entidad de servicio debe tener permisos de una instancia de Azure Analysis Services. El uso de un grupo de seguridad que contiene la entidad de servicio para este propósito no funciona.

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Registro de una aplicación](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded para los clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Inserción mediante una entidad de servicio y un certificado](embed-service-principal-certificate.md)

>[!div class="nextstepaction"]
>[Objetos de aplicación y de entidad de servicio de Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Seguridad de nivel de fila mediante puerta de enlace de datos local con entidad de servicio](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)