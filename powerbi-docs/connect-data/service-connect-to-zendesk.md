---
title: Conexión a Zendesk con Power BI
description: Zendesk para Power BI
author: paulinbar
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/04/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: e32824a58faa3a6a98e4d38f7362c62ab13b069e
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034460"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Conexión a Zendesk con Power BI

En este artículo, se explica cómo obtener datos de una cuenta de Zendesk con una aplicación de plantilla de Power BI. La aplicación de Zendesk ofrece un panel de Power BI y un conjunto de informes de Power BI que proporcionan información acerca de los volúmenes de vales y el rendimiento del agente. Los datos se actualizan automáticamente una vez al día. 

Después de instalar la aplicación de plantilla, puede personalizar el panel y el informe para resaltar la información que más le interese. A continuación, puede distribuirlo como una aplicación entre los compañeros de su organización.

Conéctese a la [aplicación de plantilla de Zendesk](https://app.powerbi.com/getdata/services/zendesk) o lea más sobre la [integración de Zendesk ](https://powerbi.microsoft.com/integrations/zendesk)con Power BI.

Después de instalar la aplicación de plantilla, puede cambiar el panel y el informe. A continuación, puede distribuirlo como una aplicación entre los compañeros de su organización.

>[!NOTE]
>Necesita una cuenta de administrador de Zendesk para conectarse. Consulte más detalles sobre los [requisitos](#system-requirements) a continuación.

>[!WARNING]
>Antes del 15 de octubre de 2019, la API de búsqueda de Zendesk Support permitía recibir un total de 200 000 resultados a través de la paginación de consultas de gran tamaño. Para alinear el uso de búsqueda con su ámbito previsto, Zendesk limita ahora el número máximo de resultados que se devuelven a 1000 resultados totales, con un máximo de 100 resultados por página. Sin embargo, el conector de Zendesk actual para Power BI todavía puede crear llamadas API que superen estos nuevos límites, lo que podría dar lugar a resultados engañosos.

## <a name="how-to-connect"></a>Cómo conectarse

[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

3. Seleccione **Zendesk** \> **Obtenerla ahora**.
4. En **¿Instalar esta aplicación de Power BI?** , seleccione **Instalar**.
4. En el panel **Aplicaciones**, seleccione el icono de **Zendesk**.

    ![Icono de la aplicación de Zendesk para Power BI](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. En **Empezar a trabajar con la nueva aplicación**, seleccione **Conectar**.

    ![Empezar a trabajar con la nueva aplicación](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

4. Proporcione la dirección URL asociada a su cuenta. La dirección URL tiene el formato **https://company.zendesk.com** . Consulte los detalles acerca de la [búsqueda de parámetros](#finding-parameters) más adelante.
   
   ![Conectarse a Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. Cuando se le solicite, escriba sus credenciales de Zendesk.  Seleccione **oAuth 2** como el mecanismo de autenticación y haga clic en **Iniciar sesión**. Siga el flujo de autenticación de Zendesk. (Si ya inició sesión en Zendesk con el explorador, no se le solicitarán las credenciales).
   
   > [!NOTE]
   > Esta aplicación de plantilla requiere conectarse con una cuenta de administrador de Zendesk. 
   > 
   
   ![Inicio de sesión con oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Haga clic en **Permitir** para permitir que Power BI tenga acceso a los datos de Zendesk.
   
   ![Hacer clic en Permitir](media/service-connect-to-zendesk/zendesk2.jpg)
7. Haga clic en **Conectar** para comenzar el proceso de importación. 
8. Una vez que Power BI importe los datos, verá la lista de contenidos de su aplicación de Zendesk: un nuevo panel, el informe y el conjunto de datos.
9. Seleccione el panel para iniciar el proceso de exploración.

    ![Panel de Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Modificar y distribuir una aplicación

Ha instalado la aplicación de plantilla de Zendesk. Esto significa que también ha creado el área de trabajo de la aplicación de Zendesk. En el área de trabajo, puede cambiar el informe y el panel y, después, distribuirlo como una *aplicación* a los compañeros de su organización. 

1. Para ver todo el contenido del nuevo área de trabajo de Zendesk, en el panel de navegación, seleccione **Áreas de trabajo** > **Zendesk**. 

    ![Área de trabajo de Zendesk en el panel de navegación](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Esta vista es la lista de contenidos del área de trabajo. En la esquina superior derecha, verá **Actualizar aplicación**. Aquí empezará cuando esté preparado para distribuir la aplicación a sus compañeros. 

    ![Lista de contenido de Zendesk](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Seleccione **Informes** y **Conjuntos de datos** para ver el resto de los elementos del área de trabajo.

    Obtenga información sobre cómo [distribuir aplicaciones](../collaborate-share/service-create-distribute-apps.md) a sus compañeros.

## <a name="system-requirements"></a>Requisitos del sistema
Se necesita una cuenta de administrador de Zendesk para acceder a la aplicación de plantilla de Zendesk. Si es un agente o un usuario final y está interesado en ver sus datos de Zendesk, agregue una sugerencia y revise el conector de Zendesk en [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Búsqueda de parámetros
La dirección URL de Zendesk coincidirá con la dirección URL que usa para iniciar sesión en su cuenta de Zendesk. Si no está seguro de su dirección URL de Zendesk, puede usar la [ayuda de inicio de sesión](https://www.zendesk.com/login/) de Zendesk.

## <a name="troubleshooting"></a>Solución de problemas
Si tiene problemas para conectarse, compruebe la dirección URL de Zendesk y confirme que está usando una cuenta de administrador de Zendesk.

## <a name="next-steps"></a>Pasos siguientes

* [Crear las nuevas áreas de trabajo en Power BI](../collaborate-share/service-create-the-new-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](../consumer/end-user-apps.md)
* [Conectarse a aplicaciones de Power BI para servicios externos](service-connect-to-services.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
