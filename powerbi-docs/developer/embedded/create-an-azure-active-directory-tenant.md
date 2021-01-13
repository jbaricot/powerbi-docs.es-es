---
title: Creación de un inquilino de Azure Active Directory para su uso con BI insertada de análisis integrados de Power BI
description: Información sobre cómo crear un inquilino de Azure Active Directory (Azure AD) para una aplicación personalizada de análisis integrados que llama a API REST de Power BI y permite una BI insertada para los clientes.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 05/28/2019
ms.openlocfilehash: 24e1d8678234b7b355d99985f8e8a567954d6211
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889027"
---
# <a name="create-an-azure-active-directory-tenant-to-use-with-power-bi"></a>Crear un inquilino de Azure Active Directory para su uso con Power BI

Aprenda a crear un nuevo inquilino de Azure Active Directory (Azure AD) para una aplicación personalizada que llama a las [API REST de Power BI](../automation/rest-api-reference.md).

Un inquilino representa a una organización en Azure Active Directory. Es una instancia dedicada del servicio de Azure AD que una organización recibe y posee cuando se suscribe a un servicio en la nube de Microsoft como Azure, Microsoft Intune o Microsoft 365. Cada inquilino de Azure AD es distinto e independiente de otros inquilinos de Azure AD.

Una vez que tenga un inquilino de Azure AD, puede definir una aplicación y asignar permisos para que la aplicación pueda llamar a las [API REST de Power BI](../automation/rest-api-reference.md).

Es posible que su organización ya tenga un inquilino de Azure AD que puede usar para la aplicación. También puede crear un nuevo inquilino específicamente para la aplicación. Este artículo explica cómo crear un nuevo inquilino.

## <a name="create-an-azure-active-directory-tenant"></a>Crear un inquilino de Azure Active Directory

Para integrar Power BI en su aplicación personalizada, debe definir primero una aplicación en Azure AD, lo que requiere un directorio de Azure AD. Este directorio es su *inquilino*. Si su organización aún no tiene un inquilino porque no usa Power BI ni Microsoft 365, [deberá configurar un entorno de desarrollo](/azure/active-directory/develop/active-directory-howto-tenant). También deberá crear uno si no desea que la aplicación se combine con el inquilino de su organización para mantener los elementos aislados. O bien, puede crear un inquilino solo con fines de prueba.

Para crear un nuevo inquilino de Azure AD:

1. Vaya a [Azure Portal](https://portal.azure.com) e inicie sesión con una cuenta que tenga una suscripción de Azure.

2. Seleccione el **icono del signo más (+)** y busque **Azure Active Directory**.

    ![Icono de signo más (+)](media/create-an-azure-active-directory-tenant/new-directory.png)

3. Seleccione **Azure Active Directory** en los resultados de búsqueda.

    ![Búsqueda en AAD](media/create-an-azure-active-directory-tenant/new-directory2.png)

4. Seleccione **Crear**.

5. Proporcione un **Nombre de organización** y un **Nombre de dominio inicial**. Después, seleccione **Crear**. Se ha creado el directorio.

    ![Organización y dominio](media/create-an-azure-active-directory-tenant/organization-and-domain.png)

   > [!NOTE]
   > El dominio inicial es parte de onmicrosoft.com. Posteriormente puede agregar otros nombres de dominio. El directorio de un inquilino puede tener varios dominios asignados a él.

6. Una vez completada la creación del directorio, seleccione el cuadro de información para administrarlo.

A continuación, va a agregar los usuarios del inquilino.

## <a name="create-azure-active-directory-tenant-users"></a>Creación de los usuarios de un inquilino de Azure Active Directory

Ahora que tiene un directorio, vamos a crear al menos dos usuarios. Uno es un administrador global del inquilino y otro es un usuario maestro para la inserción. Se puede considerar este último como una cuenta de servicio.

1. En Azure Portal, asegúrese de que está en el menú emergente de Azure Active Directory.

    ![Menú emergente de Azure AD](media/create-an-azure-active-directory-tenant/aad-flyout.png)

    Si no lo está, seleccione el icono de Azure Active Directory en la barra de servicios situada a la izquierda.

    ![Icono de Azure AD](media/create-an-azure-active-directory-tenant/aad-service.png)

2. En **Administrar**, seleccione **Usuarios**.

    ![Usuarios y grupos de Azure AD](media/create-an-azure-active-directory-tenant/users-and-groups.png)

3. Seleccione **Todos los usuarios** y, a continuación, seleccione **+ Nuevo usuario**.

4. Proporcione un **Nombre** y un **Nombre de usuario** para el administrador global del inquilino. Cambie el **Rol del directorio** a **Administrador global**. También puede mostrar la contraseña temporal. Cuando haya terminado, seleccione **Crear**.

    ![Administrador global de Azure AD](media/create-an-azure-active-directory-tenant/global-admin.png)

5. Realice lo mismo para un usuario del inquilino normal. Puede usar esta cuenta para la cuenta de inserción maestra. En esta ocasión, para **Rol del directorio**, déjelo como **Usuario**. Anote la contraseña y, a continuación, seleccione **Crear**.

    ![Usuario de Azure AD](media/create-an-azure-active-directory-tenant/pbiembed-user.png)

6. Regístrese en Power BI con la cuenta de usuario que creó en el paso 5. Vaya a [powerbi.com](https://powerbi.microsoft.com/get-started/) y seleccione **Probar gratis** en **Power BI: colaboración y uso compartido en la nube**.

    ![Crear inquilino](media/create-an-azure-active-directory-tenant/try-powerbi-free.png)

    Al registrarse, se le pedirá que pruebe Power BI Pro gratis durante 60 días. Puede optar por convertirse en un usuario Pro, le ofrece la opción de [empezar a desarrollar una solución insertada](embed-sample-for-customers.md).

   > [!NOTE]
   > Asegúrese de que se registra con la dirección de correo electrónico de la cuenta de usuario.

## <a name="next-steps"></a>Pasos siguientes

Ahora que tiene un inquilino de Azure AD, puede usarlo para probar los elementos de Power BI. También puede insertar informes y paneles de Power BI en la aplicación. Para más información, consulte [Procedimiento para insertar paneles, informes e iconos de Power BI](embed-sample-for-customers.md).

[¿Qué es Azure Active Directory?](/azure/active-directory/active-directory-whatis) 
 
[Inicio rápido: Configuración de un entorno de desarrollo](/azure/active-directory/develop/active-directory-howto-tenant)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)