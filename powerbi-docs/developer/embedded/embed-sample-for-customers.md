---
title: Inserción de contenido en la aplicación de análisis integrados de Power BI para procurar una mejor información de BI insertada para sus clientes
description: Información sobre cómo insertar un informe, un panel o un icono en una aplicación de ejemplo de análisis insertado de Power BI Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/22/2020
ms.openlocfilehash: de954c5950f550c3ed2f3c340714851f5233d3e8
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969774"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>Tutorial: Inserción de contenido de Power BI por medio de una aplicación de ejemplo de *inserción para los clientes*

Los **análisis insertados** y **Power BI Embedded** (la oferta de Azure) permiten insertar contenido de Power BI (como, por ejemplo, informes, paneles e iconos) en una aplicación.

En este tutorial, aprenderá a:
>[!div class="checklist"]
>* Configurar el entorno integrado
>* Configurar una aplicación de ejemplo de *inserción para los clientes* (también conocida como *app owns data*)

Para usar esa aplicación, los usuarios no tendrán que iniciar sesión en Power BI ni disponer de una licencia de Power BI.

Si es un fabricante de software independiente o un desarrollador que quiere crear aplicaciones para terceros, se recomienda usar el método de *inserción para los clientes* para insertar contenido de Power BI.

## <a name="code-sample-specifications"></a>Especificaciones de ejemplos de código

En este tutorial se incluyen instrucciones para configurar una aplicación de ejemplo de *inserción para los clientes* en uno de los siguientes lenguajes:

* .NET Framework
* .NET Core
* Java
* Node.js
* Python

Los ejemplos de código admiten los siguientes exploradores:

* Google Chrome

* Microsoft Edge

* Mozilla Firefox

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar este tutorial, compruebe que tiene las siguientes dependencias de código y de Power BI:

* **Dependencias de Power BI**

    * Un [inquilino de Azure Active Directory](create-an-azure-active-directory-tenant.md) propio.

    * Para autenticar la aplicación en Power BI, necesitará uno de los siguientes elementos:

        * [Entidad de servicio](embed-service-principal.md): un [objeto de entidad de servicio](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) de Azure Active Directory (Azure AD) que permite que Azure AD autentique la aplicación.

        * Licencia de [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md): actuará como **usuario maestro** y la aplicación la usará para autenticarse en Power BI.

        * Licencia de Power BI [Premium por usuario (PPU)](../../admin/service-premium-per-user-faq.md): actuará como **usuario maestro** y la aplicación la usará para autenticarse en Power BI.

    >[!NOTE]
    >Para [pasar a producción](move-to-production.md), necesitará una [capacidad](embedded-capacity.md).

* **Dependencias de código**

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)
    
    
    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [SDK de .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core) (o superior)
    
    * Un entorno de desarrollo integrado (IDE). Se recomienda usar uno de los siguientes:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (o JRE)](https://www.oracle.com/java/technologies/)
    
    * [IDE de Eclipse](https://www.eclipse.org/downloads/packages/): confirme que tiene la versión *Eclipse for Java EE Developers* (Enterprise Edition)
    
    * [Apache Tomcat Binary Distributions](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node.js](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * Un entorno de desarrollo integrado (IDE). Se recomienda usar uno de los siguientes:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (o superior)
    
        >[!NOTE]
        >* Si va a instalar *Python* por primera vez, seleccione la opción **Agregar Python a PATH** para agregar la instalación a la variable `PATH`.
        >* Si ya tiene *Python* instalado, compruebe que la variable `PATH` incluye la ruta de instalación correspondiente. Para más información, consulte la documentación de Python [Excursus: Establecer variables de entorno](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) (este vínculo remite a Python 3).
    
    * Un entorno de desarrollo integrado (IDE). Se recomienda usar uno de los siguientes:
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>Método

Para crear una aplicación de ejemplo de *inserción para los clientes*, realice estos pasos:

1. [Seleccionar el método de autenticación](#step-1---select-your-authentication-method)

2. [Registrar una de aplicación de Azure AD](#step-2---register-an-azure-ad-application)

3. [Crear un área de trabajo de Power BI](#step-3---create-a-power-bi-workspace)

4. [Crear y publicar un informe de Power BI](#step-4---create-and-publish-a-power-bi-report)

5. [Obtener los valores de parámetro de la inserción](#step-5---get-the-embedding-parameter-values)

6. [Habilitar el acceso a la API de la entidad de servicio](#step-6---service-principal-api-access)
 
7. [Permitir el acceso al área de trabajo](#step-7---enable-workspace-access)

8. [Insertar el contenido](#step-8---embed-your-content)

## <a name="step-1---select-your-authentication-method"></a>Paso 1: Seleccionar el método de autenticación

La solución insertada variará según el método de autenticación que se seleccione. Por lo tanto, es importante comprender las diferencias entre los métodos de autenticación y decidir cuál se adapta mejor a su solución.

En la siguiente tabla se describen algunas diferencias clave entre los métodos de autenticación de [entidad de servicio](embed-service-principal.md) y de **usuario maestro**.

|Consideración  |Entidad de servicio  |Usuario maestro  |
|---------|---------|---------|
|Mechanism     |El [objeto de entidad de servicio](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) de la aplicación Azure AD permite a Azure AD autenticar en Power BI a la aplicación de solución insertada.        |La aplicación de Azure AD usa las credenciales (nombre de usuario y contraseña) de un usuario de Power BI para autenticarse en Power BI.         |
|Seguridad     |La *entidad de servicio* es el método de autorización recomendado de Azure AD. Si usa una entidad de servicio*, puede realizar la autenticación con un *secreto de aplicación* o con un *certificado*.</br></br>En este tutorial solo se explica el uso de una *entidad de servicio* con un *secreto de aplicación*. Para realizar la inserción con una *entidad de servicio* y un *certificado*, consulte el artículo sobre el uso de una [entidad de servicio con un certificado](embed-service-principal-certificate.md).         |Este método de autenticación no se considera tan seguro como usar una *entidad de servicio*, ya que hay que tener cuidado con las credenciales de *usuario maestro* (nombre de usuario y contraseña). Por ejemplo, esos datos no deben quedar expuestos en la aplicación de inserción, aparte de que conviene cambiar la contraseña con frecuencia.         |
|Permisos delegados de Azure AD |No es necesario. |El *usuario maestro* o un administrador deben dar su consentimiento para que la aplicación acceda a los [permisos](/azure/active-directory/develop/v2-permissions-and-consent) de la API REST de Power BI (también denominados ámbitos). Por ejemplo, *Report.ReadWrite.All*. |
|Acceso al servicio Power BI |No se puede acceder al servicio Power BI con una *entidad de servicio*.|Se puede acceder al servicio Power BI con las credenciales de *usuario maestro*.|
|Licencia     |No se requiere una licencia Pro. Puede usar el contenido de cualquier área de trabajo de la que sea miembro o administrador.         |Se requiere una licencia [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md).         |

## <a name="step-2---register-an-azure-ad-application"></a>Paso 2: Registrar una de aplicación de Azure AD

Registrar su aplicación con Azure AD le permite lo siguiente:
> [!div class="checklist"]
>* Establecer una identidad de la aplicación
>* Dejar que la aplicación acceda a las [API REST de Power BI](/rest/api/power-bi/)
>* Si usa un *usuario maestro*, especificar los [permisos de REST de Power BI](/azure/active-directory/develop/v2-permissions-and-consent) de la aplicación

Para registrar la aplicación con Azure AD, siga las instrucciones en [Registro de su aplicación](register-app.md).

>[!NOTE]
>Antes de registrar la aplicación, deberá decidir qué método de autenticación usar, si una *entidad de servicio* o un *usuario maestro*.

## <a name="step-3---create-a-power-bi-workspace"></a>Paso 3: Crear un área de trabajo de Power BI

Power BI mantiene los informes, paneles e iconos en un área de trabajo. Para insertar estos elementos, hay que crearlos y cargarlos en un área de trabajo.

>[!TIP]
>Si ya tiene un área de trabajo, puede omitir este paso.

Para crear un área de trabajo, haga lo siguiente:

1. Inicie sesión en Power BI.

2. Seleccione **Áreas de trabajo**.

3. Seleccione **Crear un área de trabajo**.

4. Asigne un nombre al área de trabajo y seleccione **Guardar**.

## <a name="step-4---create-and-publish-a-power-bi-report"></a>Paso 4: Crear y publicar un informe de Power BI

El siguiente paso consiste en crear un informe y cargarlo en el área de trabajo. Puede [crear su propio informe](/power-bi/fundamentals/desktop-getting-started#build-reports) usando Power BI Desktop y, después, [publicarlo](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) en el área de trabajo. Otra opción sería cargar un informe de ejemplo en el área de trabajo.

>[!Tip]
>Si ya tiene un área de trabajo con un informe, puede omitir este paso.

Para descargar un informe de ejemplo y publicarlo en el área de trabajo, haga lo siguiente:

1. Abra la carpeta de [ejemplos de Power BI Desktop](https://github.com/Microsoft/PowerBI-Desktop-Samples) de GitHub.

2. Seleccione **Code** (Código) y, después, **Download ZIP** (Descargar ZIP).

    :::image type="content" source="media/embed-sample-for-customers/download-sample-report.png" alt-text="Captura de pantalla que muestra la opción de descarga de ZIP en los ejemplos de Power BI de GitHub Desktop":::

3. Extraiga el archivo ZIP descargado y vaya a la carpeta **Samples Reports**.

4. Seleccione un informe para insertarlo y [publíquelo](/powerbi-docs/fundamentals/desktop-getting-started#share-your-work) en su área de trabajo.

## <a name="step-5---get-the-embedding-parameter-values"></a>Paso 5: Obtener los valores de parámetro de la inserción

Para insertar el contenido, debe obtener una serie de valores de parámetro. En esta tabla se muestran los valores necesarios y se señala si se corresponden con el método de autenticación de *entidad de servicio* , con el método de autenticación de *usuario maestro* o con ambos.

Antes de insertar el contenido, asegúrese de que tiene todos los valores que figuran aquí. Algunos de los valores variarán según el método de autenticación que use.

|Parámetro   |Entidad de servicio   |Usuario maestro  |
|-------------------|---|---|
|[Id. de cliente](#client-id) |![Se aplica a.](../../media/yes.png) |![Se aplica a.](../../media/yes.png) |
|[Id. del área de trabajo](#workspace-id)     |![Se aplica a.](../../media/yes.png) |![Se aplica a.](../../media/yes.png) |
|[Id. del informe](#report-id)           |![Se aplica a.](../../media/yes.png) |![Se aplica a.](../../media/yes.png) |
|[Secreto de cliente](#client-secret) |![Se aplica a.](../../media/yes.png) |![No se aplica.](../../media/no.png) |
|[Id. de inquilino](#tenant-id)                 |![Se aplica a.](../../media/yes.png) |![No se aplica.](../../media/no.png) |
|[Nombre de usuario de Power BI](#power-bi-username-and-password)   |![No se aplica.](../../media/no.png) |![Se aplica a.](../../media/yes.png) |
|[Contraseña de Power BI](#power-bi-username-and-password)   |![No se aplica.](../../media/no.png) |![Se aplica a.](../../media/yes.png) |

### <a name="client-id"></a>Id. de cliente

>[!TIP]
>**Se aplica a:** ![Se aplica a.](../../media/yes.png)Entidad de servicio ![Se aplica a.](../../media/yes.png)Usuario maestro

Para obtener el GUID del identificador de cliente (también conocido como *id. de la aplicación*), haga lo siguiente:

1. Inicie sesión en [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Busque **Registros de aplicaciones** y seleccione el vínculo **Registros de aplicaciones**.

3. Seleccione la aplicación de Azure AD que use para insertar el contenido de Power BI.

4. En la sección **Información general**, copie el GUID del **identificador de la aplicación (cliente)** .

### <a name="workspace-id"></a>Id. del área de trabajo

>[!TIP]
>**Se aplica a:** ![Se aplica a.](../../media/yes.png)Entidad de servicio ![Se aplica a.](../../media/yes.png)Usuario maestro

Para obtener el GUID del identificador del área de trabajo, haga lo siguiente:

1. Inicie sesión en el servicio Power BI.

2. Abra el informe que quiera insertar.

3. Copie el GUID de la dirección URL. El GUID es el número que hay entre **/groups/** y **/reports/** .

    :::image type="content" source="media/embed-sample-for-customers/workspace-id.png" alt-text="Captura de pantalla que muestra el GUID del identificador del área de trabajo en la dirección URL del servicio Power BI":::

### <a name="report-id"></a>Report ID (Id. de informe)

>[!TIP]
>**Se aplica a:** ![Se aplica a.](../../media/yes.png)Entidad de servicio ![Se aplica a.](../../media/yes.png)Usuario maestro

1. Inicie sesión en el servicio Power BI.

2. Abra el informe que quiera insertar.

3. Copie el GUID de la dirección URL. El GUID es el número que hay entre **/reports/** y **/ReportSection**.

    :::image type="content" source="media/embed-sample-for-customers/report-id.png" alt-text="Captura de pantalla que muestra el GUID del identificador del informe en la dirección URL del servicio Power BI":::

### <a name="client-secret"></a>Secreto del cliente

>[!TIP]
>**Se aplica a:** ![Se aplica a.](../../media/yes.png)Entidad de servicio![No se aplica.](../../media/no.png)Usuario maestro

Para obtener el secreto de cliente, haga lo siguiente:

1. Inicie sesión en [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Busque **Registros de aplicaciones** y seleccione el vínculo **Registros de aplicaciones**.

3. Seleccione la aplicación de Azure AD que use para insertar el contenido de Power BI.

4. En **Administrar**, seleccione **Certificados y secretos**.

5. En **Secretos de cliente**, seleccione **Nuevo secreto de cliente**.

6. En la ventana emergente **Agregar un secreto de cliente**, escriba una descripción del secreto de la aplicación, seleccione cuándo expira el secreto de la aplicación y seleccione **Agregar**.

7. En la sección **Secretos de cliente**, copie la cadena de la columna **Valor** del secreto de aplicación recién creado. El valor del secreto de cliente es el *identificador de cliente*.

### <a name="tenant-id"></a>Id. de inquilino

>[!TIP]
>**Se aplica a:** ![Se aplica a.](../../media/yes.png)Entidad de servicio![No se aplica.](../../media/no.png)Usuario maestro

Para obtener el GUID del identificador del inquilino, haga lo siguiente:

1. Inicie sesión en [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Busque **Registros de aplicaciones** y seleccione el vínculo **Registros de aplicaciones**.

3. Seleccione la aplicación de Azure AD que use para insertar el contenido de Power BI.

4. En la sección **Información general**, copie el GUID de **Id. de directorio (inquilino)** .

### <a name="power-bi-username-and-password"></a>Nombre de usuario y contraseña de Power BI

>[!TIP]
>**Se aplica a:** ![No se aplica.](../../media/no.png)Entidad de servicio ![Se aplica.](../../media/yes.png)Usuario maestro

Obtenga el *nombre de usuario* y la *contraseña* del usuario de Power BI que esté usando como **usuario maestro**. Se trata del mismo usuario que usó para crear un área de trabajo y cargar un informe en el servicio Power BI.

## <a name="step-6---service-principal-api-access"></a>Paso 6: Habilitar el acceso a la API de la entidad de servicio

>[!TIP]
>**Se aplica a:** ![Se aplica a.](../../media/yes.png)Entidad de servicio![No se aplica.](../../media/no.png)Usuario maestro
>
>Este paso solo procede si usa el método de autenticación de *entidad de servicio*. Si usa un *usuario maestro*, omita este paso y avance al [Paso 7: Permitir el acceso al área de trabajo](#step-7---enable-workspace-access).

Para que una aplicación de Azure AD pueda acceder al contenido y las API de Power BI, un administrador de Power BI debe habilitar el acceso de entidad de servicio en el portal de administración de Power BI. Si no es el administrador de su inquilino, pida al administrador del inquilino que habilite *Configuración de inquilinos*.
        
1. En *Servicio Power BI*, seleccione **Configuración** > **Configuración** > **Portal de administración**.
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="Captura de pantalla que muestra la opción de menú configuración de administración en el menú de configuración del servicio Power BI":::
        
2. Seleccione **Configuración de inquilinos** y desplácese hacia abajo hasta la sección **Configuración de desarrollador**.
        
3. Expanda **Concesión de permisos a las entidades de servicio para utilizar las API de Power BI** y habilite esta opción.
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="Captura de pantalla que muestra cómo habilitar la opción de configuración de desarrollador en la opción de menú de configuración de inquilinos del servicio Power BI":::
        
>[!NOTE]
>Si usa una *entidad de servicio*, se recomienda limitar su acceso a la configuración de inquilinos por medio de un *grupo de seguridad*. Para obtener más información sobre esta característica, consulte estas secciones en el artículo relativo a la [entidad de servicio](embed-service-principal.md):
> * [Crear un grupo de seguridad de Azure AD](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [Habilitar la configuración de administración del servicio Power BI](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>Paso 7: Permitir el acceso al área de trabajo

Para habilitar los artefactos de acceso a la aplicación de Azure AD como informes, paneles y conjuntos de datos en el servicio Power BI, agregue al área de trabajo la *entidad de servicio*  o el *usuario maestro*, ya sea como *miembro* o como *administrador*.

1. Inicie sesión en el servicio Power BI.

2. Desplácese hasta el área de trabajo para el que desea habilitar el acceso y, en el menú **Más**, seleccione **Acceso al área de trabajo**.

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="Captura de pantalla que muestra el botón de acceso al área de trabajo en el menú Más de un área de trabajo de Power BI.":::

3. En función del método de autenticación que use, en el panel **Acceso**, copie la *entidad de servicio* o el *usuario maestro* en el cuadro de texto **Escribir la dirección de correo electrónico**.

    >[!NOTE]
    >Si usa una *entidad de servicio*, su nombre es el nombre que dio a la aplicación de Azure AD.

5. Seleccione **Agregar**.

## <a name="step-8---embed-your-content"></a>Paso 8: Insertar el contenido

La aplicación de ejemplo insertada de Power BI permite crear una aplicación de Power BI de *inserción para los clientes*.

Siga estos pasos para modificar aplicación de ejemplo de *inserción para los clientes* para insertar su informe de Power BI.  

1. Abra la carpeta [Power BI developer samples](https://github.com/microsoft/PowerBI-Developer-Samples).

2. Seleccione **Code** (Código) y, después, **Download ZIP** (Descargar ZIP).

    :::image type="content" source="media/embed-sample-for-customers/developer-samples.png" alt-text="Captura de pantalla que muestra la opción de descarga de ZIP en los ejemplos de desarrollador de Power BI de GitHub":::

3. Extraiga el archivo ZIP descargado y vaya a la carpeta **PowerBI-Developer-Samples-master**.

4. Abra una de estas carpetas según el lenguaje que quiera que use la aplicación:

* .NET Core
* .NET Framework
* Java
* Node.js
* Python
    >[!NOTE]
    >Las aplicaciones de ejemplo de *inserción para los clientes* solo admiten los lenguajes que figuran arriba. La aplicación de ejemplo *React TS* solo admite la solución de *[inserción para la organización](embed-sample-for-your-organization.md)* .

5. Abra la carpeta **Embed for your customers**.

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. Abra la *aplicación de ejemplo de inserción para los clientes* con uno de estos métodos:

    * Si usa [Visual Studio](https://visualstudio.microsoft.com/), abra el archivo **AppOwnsData.sln**.

    * Si usa [Visual Studio Code](https://code.visualstudio.com/), abra la carpeta **AppOwnsData**.

7. Abra **appsettings.json**.

8. Según su método de autenticación, rellene los siguientes valores de parámetro:

    |Parámetro            |Entidad de servicio  |Usuario maestro  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |Su [identificador de cliente](#client-id) de la aplicación Azure         |Su [identificador de cliente](#client-id) de la aplicación Azure         |
    |`TenantId`           |Su [identificador de inquilino](#tenant-id) de Azure AD         |N/D         |
    |`PbiUsername`        |N/D         |El nombre de usuario de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`PbiPassword`        |N/D         |La contraseña de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`ClientSecret`       |El [secreto de cliente](#client-secret) de Azure AD         |N/D         |
    |`WorkspaceId`        |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))          |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))         |
    |`ReportId`           |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))            |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))         |

9. Ejecute el proyecto seleccionando la opción que proceda:

    * Si usa **Visual Studio**, seleccione **IIS Express** (Reproducir).

    * Si usa **Visual Studio Code**, seleccione **Ejecutar > Iniciar depuración**.

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. Si usa [Visual Studio](https://visualstudio.microsoft.com/), abra el archivo **AppOwnsData.sln**.

7. Abra **Web.config**.

8. Según su método de autenticación, rellene los siguientes valores de parámetro:

    |Parámetro            |Entidad de servicio  |Usuario maestro  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |Su [identificador de cliente](#client-id) de la aplicación Azure         |Su [identificador de cliente](#client-id) de la aplicación Azure         |
    |`workspaceId`        |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))          |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))         |
    |`reportId`           |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))            |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))         |
    |`pbiUsername`        |N/D         |El nombre de usuario de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`pbiPassword`        |N/D         |La contraseña de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`applicationSecret`       |El [secreto de cliente](#client-secret) de Azure AD         |N/D         |
    |`tenant`           |Su [identificador de inquilino](#tenant-id) de Azure AD         |N/D         |

9. Ejecute el proyecto seleccionando **IIS Express** (Reproducir).

>[!NOTE]
>Si no ve el informe insertado al ejecutar la aplicación de ejemplo, actualice los paquetes de Power BI del siguiente modo:
>1. Haga clic con el botón derecho en el nombre del proyecto (AppOwnesData) y seleccione **Administrar paquetes NuGet**.
>2. Busque **Power BI JavaScript** (JavaScript de Power BI) y vuelva a instalar el paquete.
>
>Para obtener más información, consulte [Cómo volver a instalar y actualizar paquetes](/nuget/consume-packages/reinstalling-and-updating-packages).

# <a name="java"></a>[Java](#tab/java)

6. Abra **Eclipse** y siga las instrucciones que se describen a continuación.

    >[!NOTE]
    >Encontrará las instrucciones relativas a la *aplicación de ejemplo de inserción para los clientes* de Java en [Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/packages/) (Enterprise Edition). Si usa otra aplicación, tendrá que configurarla usted mismo.

7. Agregue el servidor de Tomcat a Eclipse:

    a. Seleccione **Window** > **Show View** > **Servers** (Ventana > Mostrar vista > Servidores).

    b. En la pestaña Servers, seleccione **No servers are available. Click this link to create new server** (No hay servidores disponibles. Haga clic en este vínculo para crear uno nuevo).

    c. En la ventana **Define a New Server** (Definir un servidor nuevo), expanda **Apache** y seleccione el servidor de Tomcat que se esté ejecutando en el equipo. Por ejemplo, *Tomcat v9.0 Server* (Servidor Tomcat v9.0).

    d. Seleccione **Siguiente**.

    e. En la ventana **Tomcat Server** (Servidor de Tomcat), seleccione **Browse** (Examinar) y vaya a la carpeta que contiene el servidor de Tomcat.

    f. En la ventana **Tomcat Server** (Servidor de Tomcat), seleccione **Installed JREs** (JRE instalados).

    g. En la ventana **Installed JREs** (JRE instalados), seleccione el *jre* disponible y, después, **Apply and Close** (Aplicar y cerrar).

    h. En la ventana **Tomcat Server** (Servidor de Tomcat), seleccione **Finish** (Finalizar). El servidor de Tomcat aparecerá en la pestaña *Servers*.

8. Abra el proyecto en Eclipse:

    >[!IMPORTANT]
    >Si el nombre de la ruta de acceso es demasiado largo, pueden surgir problemas en Eclipse. Para evitarlo, compruebe que la carpeta de la aplicación de ejemplo no esté demasiado anidada en la estructura de carpetas del equipo.

    a. Seleccione **File** (Archivo) y, después, seleccione **Open Projects from File System** (Abrir proyectos desde el sistema de archivos).

    b. En la ventana **Import Projects form File System or Archive** (Importar proyectos desde archivo o sistema de archivos), seleccione **Directory** (Directorio) y abra la carpeta **AppOwnsData**.

    c. Seleccione **Finalizar**.

9. Agregue el servidor de Tomcat al proyecto:

    a. En el panel **Package Explorer** (Explorador de paquetes), haga clic con el botón derecho en **AppOwnsData** y seleccione **Properties** (Propiedades).

    b. En la ventana **Properties for AppOwnesData** (Propiedades de AppOwnesData), seleccione **Targeted Runtimes** (Tiempos de ejecución de destino) y, después, **Apache Tomcat**. Esta selección incluirá la versión de *Apache Tomcat* que esté usando, por ejemplo *Apache Tomact v9.0*.

    c. Seleccione **Apply and Close** (Aplicar y cerrar).

10. Rellene los parámetros necesarios.

    a. En **Package Explorer** (Explorador de paquetes), expanda el proyecto **AppOwnsData**.

    b. Expanda **Java Resources** (Recursos de Java).

    c. Expanda **src**.

    d. Expanda **com.embedsample.appoensdata.config**.

    e. Abra **Config.java**.

    f. Según su método de autenticación, rellene los siguientes valores de parámetro:

    |Parámetro            |Entidad de servicio  |Usuario maestro  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))          |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))         |
    |`reportId`           |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))            |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))         | 
    |`clientId`           |Su [identificador de cliente](#client-id) de la aplicación Azure         |Su [identificador de cliente](#client-id) de la aplicación Azure         |
    |`pbiUsername`        |N/D         |El nombre de usuario de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`pbiPassword`        |N/D         |La contraseña de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`tenantId`           |Su [identificador de inquilino](#tenant-id) de Azure AD         |N/D         |
    |`appSecret`       |El [secreto de cliente](#client-secret) de Azure AD         |N/D         |

11. Ejecución del proyecto

    a. En **Package Explorer** (Explorador de paquetes), haga clic con el botón derecho en **AppOwnesData**.

    b. Seleccione **Run As**  > **Run on Server** (Ejecutar como > Ejecutar en el servidor).

    c. En la ventana **Run on Server** (Ejecutar en el servidor), seleccione **Choose an existing server** (Elegir un servidor existente) y, después, el servidor de *Tomcat*.

    d. Seleccione **Finalizar**.

# <a name="node-js"></a>[Node.js](#tab/node-js)

6. Abra la carpeta **App Owns Data** con el IDE de su elección. Se recomienda usar uno de los siguientes:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. Abra un terminal y ejecute lo siguiente para instalar las dependencias necesarias: `npm install`.

8. Expanda la carpeta **Config** y abra **config.json**.

9. Según su método de autenticación, rellene los siguientes valores de parámetro:

    |Parámetro            |Entidad de servicio  |Usuario maestro  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |Su [identificador de cliente](#client-id) de la aplicación Azure         |Su [identificador de cliente](#client-id) de la aplicación Azure         |
    |`workspaceId`        |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))          |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))         |
    |`reportId`           |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))            |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))         |
    |`pbiUsername`        |N/D         |El nombre de usuario de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`pbiPassword`        |N/D         |La contraseña de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`clientSecret`       |El [secreto de cliente](#client-secret) de Azure AD         |N/D         |
    |`tenantId`           |Su [identificador de inquilino](#tenant-id) de Azure AD         |N/D         |

10. Haga lo siguiente para ejecutar el proyecto:

    a. En el terminal del IDE, ejecute `npm start`.

    b. Abra una pestaña nueva en el explorador y vaya a `http://localhost:5300`.

# <a name="python"></a>[Python](#tab/python)

6. Abra **PowerShell** o **Command Prompt** (Símbolo del sistema).

7. Confirme que está en la carpeta **Python** > **Embed for your customers** y que dicha carpeta contiene el archivo **requirements.txt** y, después, ejecute `pip3 install -r requirements.txt`.

8. Abra la carpeta **App Owns Data** con el IDE de su elección. Se recomienda usar uno de los siguientes:

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. Abra **config.py**.

10. Según su método de autenticación, rellene los siguientes valores de parámetro:

    |Parámetro            |Entidad de servicio  |Usuario maestro  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))          |El identificador del área de trabajo con el informe insertado (consulte [Id. del área de trabajo](#workspace-id))         |
    |`REPORT_ID`           |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))            |El identificador del informe que está insertando (consulte [Id. de informe](#report-id))         |
    |`TENANT_ID`           |Su [identificador de inquilino](#tenant-id) de Azure AD         |N/D         |
    |`CLIENT_ID`           |Su [identificador de cliente](#client-id) de la aplicación Azure         |Su [identificador de cliente](#client-id) de la aplicación Azure         |
    |`CLIENT_SECRET`       |El [secreto de cliente](#client-secret) de Azure AD         |N/D         |
    |`POWER_BI_USER`        |N/D         |El nombre de usuario de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |
    |`POWER_BI_PASS`        |N/D         |La contraseña de su *usuario maestro* (consulte [Nombre de usuario y contraseña de Power BI](#power-bi-username-and-password))         |

11. Guarde el archivo.

12. Haga lo siguiente para ejecutar el proyecto:

    a. En **PowerShell** o **Command Prompt** (Símbolo del sistema), vaya a la capeta **Python** > **Embed for your customers** > **AppOwnesData** y ejecute `flask run`.

    b. Abra una pestaña nueva en el explorador y vaya a `http://localhost:5300`.

---

## <a name="developing-your-application"></a>Desarrollo de la aplicación

Tras configurar y ejecutar la aplicación de ejemplo de *inserción para los clientes*, puede empezar a desarrollar su propia aplicación.

Cuando esté listo, revise los requisitos necesarios para [pasar a producción](move-to-production.md). También necesitará una [capacidad](embedded-capacity.md) y debería revisar el artículo [Planificación de la capacidad](embedded-capacity-planning.md) para determinar cuál es la SKU que mejor se adapta a las necesidades.


## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
>[Paso a producción](move-to-production.md)

>[!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Inserción de informes paginados para clientes](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[Inserción de informes paginados para la organización](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[Pregunte a la comunidad de Power BI](https://community.powerbi.com/)
