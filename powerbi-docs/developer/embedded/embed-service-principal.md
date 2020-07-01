---
title: Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación
description: Obtenga información sobre cómo autenticarse en análisis insertados mediante una entidad de servicio de aplicación de Azure Active Directory y un secreto de aplicación.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 05/12/2020
ms.openlocfilehash: e7b1e33322e0c1174b05a4e7b3617b5d3f7a18e8
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231233"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

En este artículo se describe la autenticación de la entidad de servicio mediante el *identificador de aplicación* y el *secreto de aplicación*.

>[!NOTE]
>Se recomienda proteger los servicios de back-end mediante certificados, en lugar de claves secretas.
>* [Obtenga más información sobre cómo obtener tokens de acceso de Azure AD mediante claves secretas o certificados](https://docs.microsoft.com/azure/architecture/multitenant-identity/client-assertion).
>* [Inserción de contenido de Power BI con entidades de servicio y un certificado](embed-service-principal-certificate.md).

## <a name="method"></a>Método

Para usar la entidad de servicio y un identificador de aplicación con análisis insertados, siga estos pasos:

1. Cree una [aplicación de Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-application-management).

    1. Cree el secreto de la aplicación de Azure AD.
    
    2. Obtenga el *identificador de aplicación* y el *secreto de aplicación* de la aplicación.

    >[!NOTE]
    >Estos pasos se describen en el **paso 1**. Para obtener más información sobre la creación de una aplicación de Azure AD, consulte el artículo [Creación de una aplicación de Azure AD](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal).

2. Cree de un grupo de seguridad de Azure AD.

3. Habilite la configuración de administración del servicio Power BI.

4. Agregue la entidad de servicio a su área de trabajo.

5. Inserte el contenido.

> [!IMPORTANT]
> Después de habilitar la entidad de servicio para usarla con Power BI, los permisos de AD de la aplicación ya no tendrán efecto. Los permisos de la aplicación se administrarán desde el portal de administración de Power BI.

## <a name="step-1---create-an-azure-ad-app"></a>Paso 1: Creación de una aplicación de Azure AD

Cree una aplicación de Azure AD con uno de estos métodos:
* Cree la aplicación en [Microsoft Azure Portal](https://portal.azure.com/#allservices).
* Cree la aplicación mediante [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Creación de una aplicación de Azure AD en Microsoft Azure Portal

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Haga clic en la pestaña **Certificados y secretos**.

     ![identificador de aplicación](media/embed-service-principal/certificates-and-secrets.png)


8. Haga clic en **Nuevo secreto de cliente**.

    ![nuevo secreto de cliente](media/embed-service-principal/new-client-secret.png)

9. En la ventana *Agregar un secreto de cliente*, escriba una descripción, especifique cuándo desea que expire el secreto de cliente y haga clic en **Agregar**.

10. Copie y guarde el valor del *secreto de cliente*.

    ![valor de secreto de cliente](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >Después de salir de esta ventana, se ocultará el valor de secreto de cliente y no podrá verlo ni copiarlo de nuevo.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Creación de una aplicación de Azure AD con PowerShell

En esta sección se incluye un script de ejemplo para crear una nueva aplicación de Azure AD con [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0).

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
* Manualmente (en Azure)
* Uso de PowerShell

### <a name="create-a-security-group-manually"></a>Creación de un grupo de seguridad manualmente

Para crear un grupo de seguridad de Azure manualmente, siga las instrucciones del artículo [Creación de un grupo básico e incorporación de miembros con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Creación de un grupo de seguridad mediante PowerShell

A continuación se muestra un script de ejemplo para crear un nuevo grupo de seguridad y agregar una aplicación a ese grupo de seguridad.

>[!NOTE]
>Si desea habilitar el acceso de la entidad de servicio para toda la organización, omita este paso.

```powershell
# Required to sign in as a tenant admin
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

![Portal de administración](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Paso 4: Adición de la entidad de servicio al área de trabajo

Para habilitar los artefactos de acceso a la aplicación de Azure AD como informes, paneles y conjuntos de datos en el servicio Power BI, agregue la instancia de la entidad de servicio como miembro o administrador al área de trabajo.

>[!NOTE]
>En esta sección se proporcionan instrucciones para la interfaz de usuario. También puede agregar una entidad de servicio a un área de trabajo mediante la [API Grupos: agregar usuario de grupo](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser).

1. Desplácese hasta el área de trabajo para el que desea habilitar el acceso y, en el menú **Más**, seleccione **Acceso al área de trabajo**.

    ![Configuración del área de trabajo](media/embed-service-principal/workspace-access.png)

2. Agregue la entidad de servicio como **administrador** o **miembro** al área de trabajo.

    ![Administrador del área de trabajo](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>Paso 5: Inserción del contenido

Puede insertar el contenido en una aplicación de ejemplo o en una aplicación propia.

* [Inserción de contenido mediante la aplicación de ejemplo](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Inserción de contenido en una aplicación propia](embed-sample-for-customers.md#embed-content-within-your-application)

Una vez insertado el contenido, está listo para [pasar a producción](embed-sample-for-customers.md#move-to-production).

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Registro de una aplicación](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded para los clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objetos de aplicación y de entidad de servicio de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Seguridad de nivel de fila mediante puerta de enlace de datos local con entidad de servicio](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Inserción de contenido de Power BI con entidades de servicio y un certificado](embed-service-principal-certificate.md)
