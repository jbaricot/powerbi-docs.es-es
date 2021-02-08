---
title: Inserción de contenido en la aplicación de análisis integrados de Power BI para procurar una mejor información de BI insertada para su organización
description: Aprenda a integrar Power BI en su aplicación mediante software de análisis integrado, herramientas de análisis integrado o herramientas de inteligencia empresarial integrada. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/17/2020
ms.openlocfilehash: fbae63597ecf4ff36783ad83785f87c242359f90
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494993"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-organization-application"></a>Tutorial: Inserción de contenido de Power BI por medio de una aplicación de ejemplo de *inserción para la organización*

Los análisis insertados de Power BI le permiten insertar contenido de Power BI, como son los informes, los paneles y los iconos, en una aplicación.

En este tutorial, aprenderá a:

>[!div class="checklist"]
>* Configurar el entorno integrado
>* Configurar una aplicación de ejemplo de *inserción para la organización* (también conocida como *datos en posesión del usuario*)

Para usar esa aplicación, los usuarios tendrán que iniciar sesión en Power BI.

La solución de inserción para la organización suelen usarla empresas y organizaciones de gran tamaño, y está pensada para los usuarios internos.

## <a name="code-sample-specifications"></a>Especificaciones de ejemplos de código

En este tutorial se incluyen instrucciones para configurar una aplicación de ejemplo de *inserción para la organización* en uno de los siguientes marcos:

* .NET Framework
* .NET Core
* React TypeScript

>[!NOTE]
>Los ejemplos de *.NET Core* y *.NET Framework* permitirán al usuario final ver cualquier panel, informe o icono de Power BI al que tenga acceso en el servicio Power BI. El ejemplo de *React TypeScript* solo le permite insertar un informe al que el usuario final ya tenga acceso en el servicio Power BI.

Los ejemplos de código admiten los siguientes exploradores:

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar este tutorial, compruebe que tiene las siguientes dependencias de código y de Power BI:

* **Dependencias de Power BI**

    * Un [inquilino de Azure Active Directory](create-an-azure-active-directory-tenant.md) propio.

    * Una de las siguientes licencias:

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)

        * [Prémium por usuario (PPU)](../../admin/service-premium-per-user-faq.md)

    >[!NOTE]
    >Para [pasar a producción](move-to-production.md), necesitará una de las siguientes configuraciones:
    >* Todos los usuarios con licencias Pro.
    >* Todos los usuarios con licencias PPU.
    >* Una [capacidad](embedded-capacity.md). Esta configuración permite que todos los usuarios tengan licencias gratuitas.

* **Dependencias de código**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)

    * [SDK de .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core) (o superior)
    
    * Un entorno de desarrollo integrado (IDE). Se recomienda usar uno de los siguientes:

        * [Visual Studio](https://visualstudio.microsoft.com/)

        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="react-typescript"></a>[React TypeScript](#tab/react)

    * Un editor de texto

    * Terminal de línea de comandos (o PowerShell)

---

## <a name="method"></a>Método

Para crear una aplicación de ejemplo de *inserción para la organización*, siga los siguientes pasos:

1. [Registrar una de aplicación de Azure AD](#step-1---register-an-azure-ad-application)

2. [Crear un área de trabajo de Power BI](#step-2---create-a-power-bi-workspace)

3. [Crear y publicar un informe de Power BI](#step-3---create-and-publish-a-power-bi-report)

4. [Obtener los valores de parámetro de la inserción](#step-4---get-the-embedding-parameter-values)

5. [Insertar el contenido](#step-5---embed-your-content)

## <a name="step-1---register-an-azure-ad-application"></a>Paso 1: Registrar una aplicación de Azure AD

El registro de la aplicación con Azure AD le permite establecer una identidad para la aplicación.

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

## <a name="step-2---create-a-power-bi-workspace"></a>Paso 2: Crear un área de trabajo de Power BI

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-3---create-and-publish-a-power-bi-report"></a>Paso 3: Crear y publicar un informe de Power BI

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-4---get-the-embedding-parameter-values"></a>Paso 4: Obtener los valores de parámetro de la inserción

Para insertar el contenido, debe obtener una serie de valores de parámetros. Los valores de parámetros necesarios dependerán del lenguaje de la aplicación de ejemplo que quiera usar. En la siguiente tabla se enumeran los valores de parámetros necesarios para cada ejemplo.

|Parámetro  |.NET Core  |.NET Framework  |React TypeScript |
|---------|---------|---------|---------|
|[Id. de cliente](#client-id) |![Se aplica a.](../../media/yes.png) |![Se aplica a.](../../media/yes.png)         |![Se aplica a.](../../media/yes.png) |
|[Secreto de cliente](#workspace-id) |![Se aplica a.](../../media/yes.png) |![Se aplica a.](../../media/yes.png) |![No se aplica.](../../media/no.png) |
|[Id. del área de trabajo]() |![No se aplica.](../../media/no.png) |![No se aplica.](../../media/no.png) |![Se aplica a.](../../media/yes.png) |
|[Id. del informe]() |![No se aplica.](../../media/no.png) |![No se aplica.](../../media/no.png) |![Se aplica a.](../../media/yes.png) |

### <a name="client-id"></a>Id. de cliente

>[!TIP]
>**Se aplica a:** ![Se aplica a ](../../media/yes.png).NET Core ![Se aplica a ](../../media/yes.png).NET Framework ![Se aplica a ](../../media/yes.png)React TypeScript

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="client-secret"></a>Secreto del cliente

>[!TIP]
>**Se aplica a:** ![Se aplica a ](../../media/yes.png).NET Core ![Se aplica a ](../../media/yes.png).NET Framework ![No se aplica a ](../../media/no.png)React TypeScript

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="workspace-id"></a>Id. del área de trabajo

>[!TIP]
>**Se aplica a:** ![No se aplica a ](../../media/no.png).NET Core ![No se aplica a ](../../media/no.png).NET Framework ![Se aplica a ](../../media/yes.png)React TypeScript

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>Report ID (Id. de informe)

>[!TIP]
>**Se aplica a:** ![No se aplica a ](../../media/no.png).NET Core ![No se aplica a ](../../media/no.png).NET Framework ![Se aplica a ](../../media/yes.png)ReactTypeScript

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

## <a name="step-5---embed-your-content"></a>Paso 5: Inserción del contenido

La aplicación de ejemplo insertada de Power BI permite crear una aplicación de Power BI de *inserción para la organización*.

Siga estos pasos para modificar la aplicación de ejemplo de *inserción para la organización* con el fin de insertar su informe de Power BI.

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. Abra una de estas carpetas según el lenguaje que quiera que use la aplicación:

    * .NET Core
    * .NET Framework
    * React-TS

    >[!NOTE]
    >Las aplicaciones de ejemplo de *inserción para la organización* solo admiten los marcos que figuran arriba. Las aplicaciones de ejemplo de *Java*, *Node JS* y *Python* solo admiten la *[inserción para la solución de los clientes](embed-sample-for-customers.md)* .

# <a name="net-core"></a>[.NET Core](#tab/net-core)

### <a name="configure-your-azure-ad-app"></a>Configuración de su aplicación de Azure AD

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. En *Configuraciones de plataforma*, abra la plataforma *Web* y, en la sección **URI de redirección**, agregue `https://localhost:5000/signin-oidc`.

    > [!NOTE]
    >Si no tiene una plataforma **Web**, seleccione **Agregar una plataforma** y, en la ventana *Configurar plataformas*, seleccione **Web**.

6. Guarde los cambios.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-net-configurations.png" alt-text="Captura de pantalla que muestra las configuraciones de autenticación de la aplicación de Azure AD, incluido el URI de redireccionamiento web para la aplicación .NET Core de ejemplo.":::

### <a name="configure-the-sample-embedding-app"></a>Configuración de la aplicación de inserción de ejemplo

1. Abra la carpeta **Embed for your organization** (Inserción para la organización).

2. Abra la *aplicación de ejemplo Embed for your organization* (Inserción para la organización) con uno de estos métodos:

    * Si usa [Visual Studio](https://visualstudio.microsoft.com/), abra el archivo **UserOwnsData.sln**.

    * Si usa [Visual Studio Code](https://code.visualstudio.com/), abra la carpeta **UserOwnsData**.

3. Abra **appsettings.json** y rellene los siguientes valores de parámetros:

    * `ClientId`: use el GUID de [id. de cliente](#client-id).

    * `ClientSecret`: use el [secreto de cliente](#client-secret).

### <a name="run-the-sample-app"></a>Ejecutar la aplicación de ejemplo

1. Ejecute el proyecto seleccionando la opción que proceda:

    * Si usa **Visual Studio**, seleccione **IIS Express** (Reproducir).

    * Si usa **Visual Studio Code**, seleccione **Ejecutar > Iniciar depuración**.

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

### <a name="configure-your-azure-ad-app"></a>Configuración de su aplicación de Azure AD

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. En *Configuraciones de plataforma*, configure lo siguiente:

    1. En la sección **URI de redirección** de la plataforma *Web*, agregue `https://localhost:44300/`.

        > [!NOTE]
        >Si no tiene una plataforma **Web**, seleccione **Agregar una plataforma** y, en la ventana *Configurar plataformas*, seleccione **Web**.
    
    2. Habilite la opción **Tokens de id.** en *Implicit grant and hybrid flows* (Flujos híbridos y concesión implícita).
    
6. Guarde los cambios.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-framework-configurations.png" alt-text="Captura de pantalla que muestra las configuraciones de autenticación de la aplicación de Azure AD, incluido el URI de redireccionamiento web y la opción de token de acceso seleccionada para la aplicación .NET Framework de ejemplo.":::

### <a name="configure-the-sample-embedding-app"></a>Configuración de la aplicación de inserción de ejemplo

1. Abra la carpeta **Embed for your organization** (Inserción para la organización).

2. Si usa [Visual Studio](https://visualstudio.microsoft.com/), abra el archivo **UserOwnsData.sln**.

3. Abra **Web.config** y rellene los siguientes valores de parámetros:

    * `clientId`: use el GUID de [id. de cliente](#client-id).

    * `clientSecret`: use el [secreto de cliente](#client-secret).

### <a name="run-the-sample-app"></a>Ejecutar la aplicación de ejemplo

1. Ejecute el proyecto seleccionando **IIS Express** (Reproducir).

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="react-typescript"></a>[React TypeScript](#tab/react)

### <a name="configure-your-azure-ad-app"></a>Configuración de su aplicación de Azure AD

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. En *Configuraciones de plataforma*, configure la plataforma **Web** de la siguiente manera:

    1. En **URI de redirección**, agregue `https://localhost:3000` y seleccione **Configurar**.

        > [!NOTE]
        >Si no tiene una plataforma **Web**, seleccione **Agregar una plataforma** y, en la ventana *Configurar plataformas*, seleccione **Web**.

    2. Habilite ambas opciones en *Implicit grant and hybrid flows* (Flujos híbridos y concesión implícita).
        * **Tokens de acceso**
        * **Tokens de identificador**
    
6. Guarde los cambios.

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-react-configurations.png" alt-text="Captura de pantalla que muestra las configuraciones de autenticación de la aplicación de Azure AD, incluido el URI de redireccionamiento web, establecidas para el localhost 3000.":::

### <a name="configure-the-sample-embedding-app"></a>Configuración de la aplicación de inserción de ejemplo

1. Abra la carpeta **Embed for your organization** > **UserOwnsData** > **src**.

2. Con un editor de texto, abra el archivo **Config.ts** y rellene los siguientes valores de parámetros:

    * `clientId`: use el GUID de [id. de cliente](#client-id).

    * `workspaceId`: use el [id. de área de trabajo](#client-secret).

    * `reportId`: use el [id. de informe](#report-id).

3. Guarde el archivo.

### <a name="run-the-sample-app"></a>Ejecutar la aplicación de ejemplo

1. Abra un terminal y navegue a **Embed for your organization** > **UserOwnsData**.

2. Ejecute el siguiente comando para instalar las dependencias requeridas:

   `npm install`

3. Ejecute la aplicación mediante la ejecución del siguiente comando:

   `npm run start`

    >[!NOTE]
    >La primera vez que inicie sesión, se le pedirá que acepte los permisos de Azure AD para la aplicación.

---

## <a name="developing-your-application"></a>Desarrollo de la aplicación

Tras configurar y ejecutar la aplicación de ejemplo de *inserción para los clientes*, puede empezar a desarrollar su propia aplicación.

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
>[Paso a producción](move-to-production.md)

>[!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserción de informes paginados para clientes](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Inserción de informes paginados para la organización](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Pregunte a la comunidad de Power BI](https://community.powerbi.com/)