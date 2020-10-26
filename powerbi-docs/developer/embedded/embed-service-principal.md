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
ms.date: 10/15/2020
ms.openlocfilehash: 6f6a13f239d1bcfa7731361f4efcd129da7e2031
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197754"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

En este artículo se describe la autenticación de la entidad de servicio mediante el *identificador de aplicación* y el *secreto de aplicación* .

>[!NOTE]
>Se recomienda proteger los servicios de back-end mediante certificados, en lugar de claves secretas.
>* [Obtenga más información sobre cómo obtener tokens de acceso de Azure AD mediante claves secretas o certificados](/azure/architecture/multitenant-identity/client-assertion).
>* [Inserción de contenido de Power BI con entidades de servicio y un certificado](embed-service-principal-certificate.md).

## <a name="method"></a>Método

Para usar la entidad de servicio y un identificador de aplicación con análisis insertados, siga estos pasos:

1. Cree una [aplicación de Azure AD](/azure/active-directory/manage-apps/what-is-application-management).

    1. Cree el secreto de la aplicación de Azure AD.
    
    2. Obtenga el *identificador de aplicación* y el *secreto de aplicación* de la aplicación.

    >[!NOTE]
    >Estos pasos se describen en el **paso 1** . Para obtener más información sobre la creación de una aplicación de Azure AD, consulte el artículo [Creación de una aplicación de Azure AD](/azure/active-directory/develop/howto-create-service-principal-portal).

2. Cree de un grupo de seguridad de Azure AD.

3. Habilite la configuración de administración del servicio Power BI.

4. Agregue la entidad de servicio a su área de trabajo.

5. Inserte el contenido.

> [!IMPORTANT]
> Después de habilitar la entidad de servicio para usarla con Power BI, los permisos de AD de la aplicación ya no tendrán efecto. Los permisos de la aplicación se administrarán desde el portal de administración de Power BI.

## <a name="step-1---create-an-azure-ad-app"></a>Paso 1: Creación de una aplicación de Azure AD

Cree una aplicación de Azure AD con uno de estos métodos:

* Cree la aplicación en [Microsoft Azure Portal](https://portal.azure.com/#allservices).

* Cree la aplicación mediante [PowerShell](/powershell/azure/create-azure-service-principal-azureps).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Creación de una aplicación de Azure AD en Microsoft Azure Portal

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Haga clic en la pestaña **Certificados y secretos** .

     ![Captura de pantalla que muestra el panel Certificados y secretos para una aplicación en Azure Portal.](media/embed-service-principal/certificates-and-secrets.png)


8. Haga clic en **Nuevo secreto de cliente** .

    ![Captura de pantalla que muestra el botón Nuevo secreto de cliente en el panel Certificados y secretos.](media/embed-service-principal/new-client-secret.png)

9. En la ventana *Agregar un secreto de cliente* , escriba una descripción, especifique cuándo desea que expire el secreto de cliente y haga clic en **Agregar** .

10. Copie y guarde el valor del *secreto de cliente* .

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
[!INCLUDE[service create steps two, three and four](../../includes/service-principal-create-steps.md)]

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
>[Objetos de aplicación y de entidad de servicio de Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Seguridad de nivel de fila mediante puerta de enlace de datos local con entidad de servicio](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Inserción de contenido de Power BI con entidades de servicio y un certificado](embed-service-principal-certificate.md)