---
title: Aplicación de creación de entidad de servicio
description: Aplicación de creación de entidad de servicio
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210878"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>Paso 2: Creación de un grupo de seguridad de Azure AD

La entidad de servicio no tiene acceso al contenido ni a las API de Power BI. Para conceder acceso a la entidad de servicio, cree un grupo de seguridad en Azure AD y agregue la entidad de servicio que creó a ese grupo de seguridad.

Hay dos maneras de crear un grupo de seguridad de Azure AD:
* Manualmente (en Azure)
* Uso de PowerShell

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

Agregue el grupo de seguridad que ha creado en Azure AD a la sección de grupos de seguridad específicos en la **Configuración del desarrollador** .

>[!IMPORTANT]
>Las entidades de servicio tienen acceso a cualquier configuración de inquilino para la que estén habilitadas. En función de la configuración de administración, esto incluye grupos de seguridad específicos o toda la organización.
>
>Para restringir el acceso de la entidad de servicio a una configuración de inquilino específica, permita el acceso únicamente a grupos de seguridad específicos. También puede crear un grupo de seguridad dedicado para entidades de servicio y excluirlo de la configuración de inquilino que desee.

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="Captura de pantalla que muestra la configuración del desarrollador en las opciones de administración en el portal de Power BI.":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Paso 4: Adición de la entidad de servicio al área de trabajo

Para habilitar los artefactos de acceso a la aplicación de Azure AD como informes, paneles y conjuntos de datos en el servicio Power BI, agregue la instancia de la entidad de servicio como miembro o administrador al área de trabajo.

>[!NOTE]
>En esta sección se proporcionan instrucciones para la interfaz de usuario. También puede agregar una entidad de servicio a un área de trabajo mediante la [API Grupos: agregar usuario de grupo](/rest/api/power-bi/groups/addgroupuser).

1. Desplácese hasta el área de trabajo para el que desea habilitar el acceso y, en el menú **Más** , seleccione **Acceso al área de trabajo** .

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="Captura de pantalla que muestra la configuración del desarrollador en las opciones de administración en el portal de Power BI.":::

2. Agregue la entidad de servicio como **administrador** o **miembro** al área de trabajo.

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="Captura de pantalla que muestra la configuración del desarrollador en las opciones de administración en el portal de Power BI.":::