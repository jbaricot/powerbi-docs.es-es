---
title: Conexión a Smartsheet con Power BI
description: Smartsheet para Power BI
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: a1cf9c96b976acbfd9a5cefe4d413b4aa0fac9bf
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236269"
---
# <a name="connect-to-smartsheet-with-power-bi"></a>Conexión a Smartsheet con Power BI
En este artículo, se explica cómo obtener datos de una cuenta de Smartsheet con una aplicación de plantilla de Power BI. Smartsheet ofrece una plataforma sencilla para la colaboración y el uso compartido de archivos. La aplicación de plantilla de Smartsheet para Power BI proporciona un panel, informes y un conjunto de datos que presenta una visión general de la cuenta de Smartsheet. También puede usar [Power BI Desktop](desktop-connect-to-data.md) para conectarse directamente a hojas individuales en su cuenta. 

Después de instalar la aplicación de plantilla, puede cambiar el panel y el informe. A continuación, puede distribuirlo como una aplicación entre los compañeros de su organización.

Conéctese a la [aplicación de plantilla de Smartsheet](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.pbiapps-smartsheet) para Power BI.

>[!NOTE]
>Es preferible usar una cuenta de administrador de Smartsheet para conectarse a la aplicación de plantilla Power BI y cargarla, ya que tiene acceso adicional.

## <a name="how-to-connect"></a>Cómo conectarse

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Seleccione **Smartsheet** \> **Obtener**.
4. En **¿Instalar esta aplicación de Power BI?** , seleccione **Instalar**.
4. En el panel **Aplicaciones**, seleccione el icono de **Smartsheet**.

    ![Icono de la aplicación de Smartsheet para Power BI](media/service-connect-to-smartsheet/power-bi-smartsheet-tile.png)

6. En **Empezar a trabajar con la nueva aplicación**, seleccione **Conectar**.

    ![Empezar a trabajar con la nueva aplicación](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. En Método de autenticación, seleccione **oAuth2 \> Iniciar sesión**.
   
   Cuando se le solicite, escriba las credenciales de Smartsheet y siga el proceso de autenticación.
   
   ![Credenciales de Smartsheet](media/service-connect-to-smartsheet/creds.png)
   
   ![Inicio de sesión de Smartsheet](media/service-connect-to-smartsheet/creds2.png)

5. Después de que Power BI importe los datos, se abre el panel de Smartsheet.
   
   ![Panel de Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-dashboard.png)

## <a name="modify-and-distribute-your-app"></a>Modificar y distribuir una aplicación

Ha instalado la aplicación de plantilla de Smartsheet. Esto significa que también ha creado el área de trabajo de la aplicación de Smartsheet. En el área de trabajo, puede cambiar el informe y el panel y, después, distribuirlo como una *aplicación* a los compañeros de su organización. 

1. Para ver todo el contenido del nuevo área de trabajo de Smartsheet, en el panel de navegación, seleccione **Áreas de trabajo** > **Smartsheet**. 

    ![Área de trabajo de Smartsheet en el panel de navegación](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace.png)

    Esta vista es la lista de contenidos del área de trabajo. En la esquina superior derecha, verá **Actualizar aplicación**. Aquí empezará cuando esté preparado para distribuir la aplicación a sus compañeros. 

    ![Lista de contenido de Smartsheet](media/service-connect-to-smartsheet/power-bi-smartsheet-workspace-content.png)

2. Seleccione **Informes** y **Conjuntos de datos** para ver el resto de los elementos del área de trabajo.

    Obtenga información sobre cómo [distribuir aplicaciones](../collaborate-share/service-create-distribute-apps.md) a sus compañeros.

## <a name="whats-included"></a>Qué se incluye
La aplicación de plantilla de Smartsheet para Power BI incluye información general de la cuenta de Smartsheet, como el número de áreas de trabajo, informes y hojas que tiene, cuándo se modifican, etc. Los usuarios administradores también ven información sobre los usuarios en su sistema, como los creadores de hojas más destacados.  

Para conectarse directamente a hojas individuales de su cuenta, puede usar el conector de Smartsheet en [Power BI Desktop](desktop-connect-to-data.md).  

## <a name="next-steps"></a>Pasos siguientes

* [Crear las nuevas áreas de trabajo en Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](../consumer/end-user-apps.md)
* [Conectarse a aplicaciones de Power BI para servicios externos](service-connect-to-services.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)