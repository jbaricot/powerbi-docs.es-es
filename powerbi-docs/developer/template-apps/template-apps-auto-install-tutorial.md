---
title: Automatización de la configuración de la instalación de aplicaciones de plantilla con una función de Azure
description: Use una aplicación de ejemplo para aprender a instalar y configurar aplicaciones de plantilla para los clientes.
author: paulinbar
ms.author: painbar
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: a44bd7837e7605fd23e49a91e3e9eba106d5a933
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565778"
---
# <a name="tutorial-automate-configuration-of-template-app-installation-using-an-azure-function"></a>Tutorial: Automatización de la configuración de la instalación de aplicaciones de plantilla con una función de Azure

Las aplicaciones de plantilla son una excelente manera de que los clientes empiecen a obtener conclusiones de sus datos. Esto se debe a que con estas aplicaciones de plantilla se pueden poner manos a la obra rápidamente conectándose a sus datos. Las aplicaciones de plantilla proporcionan a los clientes informes generados previamente que pueden personalizar si así lo desean.

Los clientes no siempre están al tanto de todos los detalles sobre cómo conectarse a sus datos, de modo que tener que proporcionar estos detalles al instalar una aplicación de plantilla puede ser un problema para ellos.

Si es un proveedor de servicios de datos y ha creado una aplicación de plantilla para ayudar a los clientes a empezar a trabajar con sus datos en el servicio, puede facilitarles la instalación de la aplicación de plantilla, automatizando para ello la configuración de los parámetros de la aplicación de plantilla.

Cuando un cliente inicia sesión en el portal, selecciona un vínculo especial que usted ha preparado. Este vínculo:

- Inicia la automatización, que recopila la información que necesita.
- Preconfigura los parámetros de la aplicación de plantilla.
- Redirige al cliente a su cuenta de Power BI, donde puede instalar la aplicación.

Solo tiene que seleccionar **Instalar**, autenticarse en su origen de datos y listo.

Aquí se ilustra esta experiencia del cliente.

![Ilustración de la experiencia de usuario con la aplicación de instalación automática](media/template-apps-auto-install/high-level-flow.png)

En este tutorial usará un ejemplo de Azure Functions de instalación automática que se ha creado para preconfigurar e instalar la aplicación de plantilla. Este ejemplo se ha mantenido deliberadamente sencillo con fines de demostración. Encapsula la configuración de una función de Azure para usar las API de Power BI para instalar una aplicación de plantilla y configurarla de forma automática para los usuarios.

Para obtener más información sobre el flujo de automatización general y las API que la aplicación usa, vea [Automatización de la configuración de la instalación de una aplicación de plantilla](template-apps-auto-install.md).

En la aplicación se usa una función de Azure. Para obtener más información sobre Azure Functions, consulte [Documentación de Azure Functions](/azure/azure-functions/).

## <a name="basic-flow"></a>Flujo básico

Este es el flujo básico de lo que la aplicación hace cuando el cliente la inicia al seleccionar el vínculo del portal.

1. El usuario inicia sesión en el portal del ISV y selecciona el vínculo proporcionado. Esta acción inicia el flujo. En esta fase, el portal del ISV prepara la configuración específica del usuario.

1. El ISV adquiere un token *de solo aplicación* basado en una [entidad de servicio (token de solo aplicación)](../embedded/embed-service-principal.md), que está registrada en el inquilino del ISV.

1. Mediante las [API REST de Power BI](/rest/api/power-bi/), el ISV crea un *vale de instalación* que contiene la configuración de parámetros específicos del usuario, tal y como la haya preparado el ISV.

1. El ISV redirige al usuario a Power BI mediante un método de redireccionamiento ```POST``` que contiene el vale de instalación.

1. Se redirige al usuario a su cuenta de Power BI con el vale de instalación y se le pide que instale la aplicación de plantilla. Cuando el usuario selecciona **Instalar**, la aplicación de plantilla se instala de forma automática.

>[!Note]
>Aunque el ISV configura los valores de parámetro durante el proceso de creación del vale de instalación, las credenciales relacionadas con el origen de datos solo las proporciona el usuario en las fases finales de la instalación. Esto está dispuesto así para evitar que las credenciales se expongan a un tercero y, asimismo, para garantizar una conexión segura entre el usuario y los orígenes de datos de la aplicación de plantilla.

## <a name="prerequisites"></a>Requisitos previos

* Tener su propio inquilino de Azure Active Directory (Azure AD) configurado. Vea [Creación de un inquilino de Azure AD](../embedded/create-an-azure-active-directory-tenant.md) para obtener instrucciones sobre cómo configurar uno.
* Tener una [entidad de servicio (token de solo aplicación)](../embedded/embed-service-principal.md) registrada en el inquilino anterior.
* Tener una [aplicación de plantilla parametrizada](../../connect-data/service-template-apps-overview.md) lista para la instalación. La aplicación de plantilla se debe crear en el mismo inquilino en el que registre la aplicación en Azure AD. Para obtener más información, vea [Sugerencias de aplicación de plantilla](../../connect-data/service-template-apps-tips.md) o [Creación de una aplicación de plantilla en Power BI](../../connect-data/service-template-apps-create.md).
* Una licencia de Power BI Pro. . Si no está registrado para Power BI Pro, [regístrese para una evaluación gratuita](https://powerbi.microsoft.com/pricing/) antes de comenzar.

## <a name="set-up-your-template-apps-automation-development-environment"></a>Configuración del entorno de desarrollo de automatización de aplicaciones de plantillas

Antes de continuar con la configuración de la aplicación, siga las instrucciones de [Inicio rápido: Creación de una aplicación de Azure Functions con Azure App Configuration](/azure/azure-app-configuration/quickstart-azure-functions-csharp) para desarrollar una función de Azure junto con una instancia de Azure App Configuration. Cree la instancia de App Configuration como se describe en el artículo.

### <a name="register-an-application-in-azure-ad"></a>Registrar una aplicación en Azure AD

Cree una entidad de servicio como se describe en [Inserción de contenido de Power BI con entidades de servicio y un secreto de aplicación](../embedded/embed-service-principal.md).

Asegúrese de registrar la aplicación como una **aplicación web del lado servidor**. Una aplicación web del lado servidor se registra para crear un secreto de aplicación.

Guarde el *Id. de aplicación* (ClientID) y el *Secreto de aplicación* (ClientSecret) para los pasos posteriores.

Puede probar la [herramienta de configuración de inserción](https://aka.ms/embedsetup/AppOwnsData) para empezar a crear un registro de aplicación sin dilación. Si usa la [herramienta de registro de aplicaciones de Power BI](https://app.powerbi.com/embedsetup), seleccione la opción **Embed for your customers** (Inserción para los clientes).

## <a name="template-app-preparation"></a>Preparación de la aplicación de plantilla

Una vez que haya creado la aplicación de plantilla y esté lista para la instalación, guarde la información siguiente para los pasos posteriores:

* *Id. de la aplicación*, *clave del paquete* e *identificador del propietario*, tal y como aparecen en la dirección URL de instalación al final del proceso [Definición de las propiedades de la aplicación de plantilla](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app) cuando se ha creado la aplicación.

    También puede obtener el mismo vínculo si selecciona **Obtener vínculo** en el panel [Administración de versiones](../../connect-data/service-template-apps-create.md#manage-the-template-app-release) de la aplicación de plantilla.

* Los *nombres de parámetro* como se definen en el conjunto de datos de la aplicación de plantilla. Los nombres de parámetros son cadenas en las que se distingue entre mayúsculas y minúsculas. También se pueden recuperar en la pestaña **Configuración de parámetros** cuando se [definen las propiedades de la aplicación de plantilla](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app), o bien desde la configuración del conjunto de datos de Power BI.

>[!NOTE]
>Puede probar la aplicación de instalación preconfigurada en la aplicación de plantilla si está lista para la instalación, incluso si todavía no está disponible de forma pública en AppSource. Para que los usuarios ajenos al inquilino puedan utilizar la aplicación de instalación automatizada para instalar la aplicación de plantilla, esta debe estar disponible de forma pública en el [marketplace de aplicaciones de Power BI](https://app.powerbi.com/getdata/services). Antes de distribuir la aplicación de plantilla con la aplicación de instalación automatizada que va a crear, asegúrese de publicarla en el [Centro de partners](/azure/marketplace/partner-center-portal/create-power-bi-app-offer).


## <a name="install-and-configure-your-template-app"></a>Instalación y configuración de la aplicación de plantilla

En esta sección, usará un ejemplo de Azure Functions de instalación automática que hemos creado para preconfigurar e instalar la aplicación de plantilla. Este ejemplo se ha mantenido deliberadamente sencillo con fines de demostración. Permite usar una instancia de [Azure Functions](/azure/azure-functions/functions-overview) y de [Azure App Configuration](/azure/azure-app-configuration/overview) para implementar y usar con facilidad la API de instalación automatizada para las aplicaciones de plantilla.

### <a name="download-visual-studio-version-2017-or-later"></a>Descargue [Visual Studio](https://www.visualstudio.com/) (versión 2017 o posterior).

Descargue [Visual Studio](https://www.visualstudio.com/) (versión 2017 o posterior). Asegúrese de descargar el [paquete NuGet](https://www.nuget.org/profiles/powerbi) más reciente.

### <a name="download-the-automated-installation-azure-functions-sample"></a>Descarga del ejemplo de Azure Functions de instalación automatizada

Descargue el [ejemplo de Azure Functions de instalación automatizada](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function) desde GitHub para empezar a trabajar.

![Captura de pantalla que muestra el ejemplo de Azure Functions de instalación automatizada](media/template-apps-auto-install/azure-function-sample.png)

### <a name="set-up-your-azure-app-configuration"></a>Configuración de Azure App Configuration

Para ejecutar este ejemplo, debe configurar Azure App Configuration con los valores y claves que se especifican aquí. Las claves son **Id. de la aplicación** y **Secreto de la aplicación**, además de los valores **AppId**, **PackageKey** y **OwnerId** de la aplicación de plantilla. Consulte las siguientes secciones para obtener información sobre cómo obtener estos valores.

Las claves también se definen en el archivo **Constants.cs**.

| Clave de configuración | Significado           |
|---------------    |-------------------|
| TemplateAppInstall:Application:AppId | **AppId** de la [dirección URL de instalación](#get-the-template-app-properties) |
| TemplateAppInstall:Application:PackageKey | **PackageKey** de la [dirección URL de instalación](#get-the-template-app-properties) |
| TemplateAppInstall:Application:OwnerId | **OwnerId** de la [dirección URL de instalación](#get-the-template-app-properties) |
| TemplateAppInstall:ServicePrincipal:ClientId | [Identificador de la aplicación](#get-the-application-id) de la entidad de servicio |
| TemplateAppInstall:ServicePrincipal:ClientSecret | [Secreto de la aplicación](#get-the-application-secret) de la entidad de servicio |
|||


Aquí se muestra el archivo **Constants.cs**.

![Captura de pantalla que muestra el archivo Constant.cs](media/template-apps-auto-install/constants-app-configuration.png)

#### <a name="get-the-template-app-properties"></a>Obtención de las propiedades de la aplicación de plantilla

Rellene todas las propiedades de la aplicación de plantilla relevantes, tal y como se han definido al crear la aplicación. Estas propiedades son los valores de **AppId**, **PackageKey** y **OwnerId** de la aplicación de plantilla.

Para obtener los valores anteriores, siga estos pasos:

1. Inicie sesión en [Power BI](https://app.powerbi.com).

1. Vaya al área de trabajo original de la aplicación.

1. Abra el panel **Administración de versiones**.

    ![Captura de pantalla que muestra el panel Administración de versiones](media/template-apps-auto-install/release-management-001.png)

1. Seleccione la versión de la aplicación y obtenga su vínculo de instalación.

    ![Captura de pantalla que muestra el botón Administración de versiones](media/template-apps-auto-install/release-management-002.png)

1. Copie el vínculo en el Portapapeles.

    ![Captura de pantalla que muestra el botón Obtener vínculo](media/template-apps-auto-install/release-management-003.png)

1. Esta dirección URL de instalación contiene los tres parámetros de dirección URL cuyos valores necesita. Use los valores **appId**, **packageKey** y **ownerId** de la aplicación. Una dirección URL de ejemplo será similar a la que se muestra aquí.

    ```html
    https://app.powerbi.com/Redirect?action=InstallApp&appId=3c386...16bf71c67&packageKey=b2df4b...dLpHIUnum2pr6k&ownerId=72f9...1db47&buildVersion=5
    ```

#### <a name="get-the-application-id"></a>Obtención del identificador de la aplicación

Rellene la información de **applicationId** con el identificador de aplicación de Azure. La aplicación usa el valor de **applicationId** para identificarse ante los usuarios a los que solicita permisos.

Para obtener el identificador de la aplicación, siga estos pasos:

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

1. En el panel izquierdo, seleccione **Todos los servicios** > **Registros de aplicaciones**.

    ![Captura de pantalla que muestra la búsqueda de registros de aplicaciones](media/template-apps-auto-install/embed-sample-for-customers-003.png)

1. Seleccione la aplicación que necesite el **identificador de la aplicación**.

    ![Captura de pantalla que muestra la selección de una aplicación](media/template-apps-auto-install/embed-sample-for-customers-006.png)

1. Hay un identificador de la aplicación que se muestra como un GUID. Úselo como **applicationId** de la aplicación.

    ![Captura de pantalla que muestra el valor de applicationId](media/template-apps-auto-install/embed-sample-for-customers-007.png)

#### <a name="get-the-application-secret"></a>Obtenga el secreto de la aplicación.

Rellene la información de **ApplicationSecret** a partir de la sección **Claves** de la sección **Registros de aplicaciones** de Azure. Este atributo funciona cuando se usa la [entidad de servicio](../embedded/embed-service-principal.md).

Para obtener el secreto de la aplicación, siga estos pasos:

 1. Inicie sesión en [Azure Portal](https://portal.azure.com).

 1. En el panel izquierdo, seleccione **Todos los servicios** > **Registros de aplicaciones**.

    ![Captura de pantalla que muestra la búsqueda de registros de aplicaciones](media/template-apps-auto-install/embed-sample-for-customers-003.png)

1. Seleccione la aplicación que necesite usar el **secreto de la aplicación**.

    ![Captura de pantalla que muestra la selección de una aplicación](media/template-apps-auto-install/embed-sample-for-customers-0038.png)

1. Seleccione **Certificates and secrets** (Certificados y secretos) en **Administrar**.

1. Seleccione **New client secrets** (Nuevos secretos de cliente).

1. Escriba un nombre en el cuadro **Descripción** y seleccione una duración. Después, haga clic en **Guardar** para obtener el valor de la aplicación. Cuando el panel **Claves** se cierra después de haber guardado el valor de clave, el campo **Valor** solo se muestra como oculto. En ese momento, no puede recuperar el valor de clave. Si pierde el valor de clave, cree uno nuevo en Azure Portal.

    ![Captura de pantalla que muestra el valor de clave](media/template-apps-auto-install/embed-sample-for-customers-042.png)

## <a name="test-your-function-locally"></a>Prueba local de la función

Siga los pasos que se describen en [Ejecución local de la función](/azure/azure-functions/functions-create-your-first-function-visual-studio#run-the-function-locally) para ejecutar la función.

Configure el portal para que emita una solicitud ```POST``` a la dirección URL de la función. Un ejemplo es ```POST http://localhost:7071/api/install```. El cuerpo de la solicitud debe ser un objeto JSON que describa los pares clave-valor. Las claves son *nombres de parámetro* según se definen en Power BI Desktop. Los valores son los valores deseados que se van a establecer por cada parámetro de la aplicación de plantilla.

>[!Note]
> En producción, los valores de parámetro se deducen para cada usuario según la lógica prevista del portal.

El flujo deseado debe ser el siguiente:

1. El portal prepara la solicitud, por usuario o sesión.
1. Se emite la solicitud ```POST /api/install``` a la función de Azure. El cuerpo de la solicitud consta de pares clave-valor. La clave es el nombre del parámetro. El valor es el valor deseado que se va a establecer.
1. Si todo está configurado correctamente, el explorador se debe redirigir automáticamente a la cuenta de Power BI del cliente y mostrar el flujo de instalación automatizada.
1. Tras la instalación, los valores de parámetro se establecen tal y como están configurados en los pasos 1 y 2.
 
## <a name="next-steps"></a>Pasos siguientes

### <a name="publish-your-project-to-azure"></a>Publicación del proyecto en Azure

Para publicar el proyecto en Azure, siga las instrucciones de la [documentación de Azure Functions](/azure/azure-functions/functions-create-your-first-function-visual-studio#publish-the-project-to-azure). Tras ello, puede integrar API de instalación automatizada de aplicaciones de plantilla en el producto y comenzar a probarlas en entornos de producción.