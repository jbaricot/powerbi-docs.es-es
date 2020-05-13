---
title: 'Instalación y distribución de aplicaciones de plantilla en la organización: Power BI'
description: Obtenga información sobre cómo instalar, personalizar y distribuir aplicaciones de plantilla de la organización en Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
ms.openlocfilehash: 762d88789bb68777886a126589802b9e8d854879
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347456"
---
# <a name="install-and-distribute-template-apps-in-your-organization"></a>Instalación y distribución de aplicaciones de plantilla en la organización

¿Es un analista de Power BI? Si es así, en este artículo se explica cómo instalar [aplicaciones de plantilla](service-template-apps-overview.md) para conectarse a muchos de los servicios que usa para dirigir su negocio, como Salesforce, Microsoft Dynamics y Google Analytics. Puede modificar los informes y paneles integrados de la aplicación de plantilla para adaptarlos a las necesidades de la organización, y distribuirlos a sus compañeros de trabajo como [aplicaciones](../consumer/end-user-apps.md). 

![Aplicaciones de Power BI instaladas](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Si está interesado en crear aplicaciones de plantilla para distribuirlas fuera la organización, vea [Creación de una plantilla de aplicación en Power BI](service-template-apps-create.md). Los asociados de Power BI pueden compilar aplicaciones de Power BI con poca o ninguna codificación, y hacer que estén disponibles para los clientes de Power BI. 

## <a name="prerequisites"></a>Requisitos previos  

Para instalar, personalizar y distribuir una aplicación de plantilla, necesita lo siguiente: 

* Una [licencia de Power BI Pro](../fundamentals/service-self-service-signup-for-power-bi.md).
* Permisos para instalar aplicaciones de plantilla en el inquilino.
* Un vínculo de instalación válido para la aplicación, que se obtiene de AppSource o del creador de la aplicación.
* Estar familiarizado con los [conceptos básicos de Power BI](../fundamentals/service-basic-concepts.md).

## <a name="install-a-template-app"></a>Instalación de una aplicación de plantilla

1. En el panel de navegación del servicio Power BI, haga clic en **Aplicaciones** > **Obtener aplicaciones**.

    ![Obtener aplicaciones](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

1. En la ventana de AppSource que aparece, seleccione **Aplicaciones**. Examine o busque la aplicación que quiera y, después, seleccione **Obtenerla ahora**.

    ![Búsqueda en AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

1. En el cuadro de diálogo que aparece, haga clic en **Instalar**.

    ![Instalar aplicación](media/service-template-apps-install-distribute/power-install-dialog.png)
    
    La aplicación se instala con un área de trabajo asociada. **Si decide personalizar la aplicación, lo hará en este área de trabajo asociada**.

    > [!NOTE]
    > Si usa un vínculo de instalación para una aplicación que no aparece en AppSource, se le pedirá que confirme la elección en un cuadro de diálogo de validación.
    >
    >Para poder instalar una aplicación de plantilla que no aparece en AppSource, debe solicitar al administrador los permisos pertinentes. Vea la [configuración de aplicaciones de plantilla](../admin/service-admin-portal.md#template-apps-settings) en el portal de administración de Power BI para obtener más información.

    Cuando la instalación finalice correctamente, una notificación le indicará que la nueva aplicación está lista.

    ![Ir a la aplicación](media/service-template-apps-install-distribute/power-bi-go-to-app.png)

## <a name="connect-to-data"></a>Conectar a datos

1. Haga clic en **Ir a la aplicación**. Aparecerá la ventana **Empezar a trabajar con la nueva aplicación**.

   ![Empezar a trabajar con la aplicación](media/service-template-apps-install-distribute/power-bi-template-app-get-started.png)

1. Haga clic en **Conectar**.
    
    Esto abre un cuadro de diálogo o una serie de cuadros de diálogo en los que se cambia el origen de datos de los datos de ejemplo a uno propio. Normalmente, esto significa volver a definir los parámetros de conjunto de datos y las credenciales del origen de datos. Vea [Limitaciones conocidas](service-template-apps-overview.md#known-limitations).
    
    En el ejemplo de abajo, la conexión a los datos implica dos cuadros de diálogo.

   ![Cuadros de diálogo de conexión a los datos](media/service-template-apps-install-distribute/power-bi-template-app-connect-to-data-dialogs.png)

    Una vez que haya terminado de rellenar los cuadros de diálogo de conexión, se iniciará el proceso de conexión. Un banner le informa de que está viendo datos de ejemplo.

    ![Visualización de datos de ejemplo](media/service-template-apps-install-distribute/power-bi-template-app-viewing-sample-data.png)

    Espere a que los datos terminen de conectarse y actualizarse. Para saber cuándo ha finalizado este proceso, observe el indicador de progreso en la fila del conjunto de datos (nuevo aspecto) o en la pestaña (aspecto anterior).

   Una vez que haya finalizado la conexión y la actualización de los datos, actualice el explorador; ahora el banner le informará de que tiene que actualizar la aplicación para aplicar los cambios que realice en ella y compartirla.

    ![Personalización y uso compartido de la aplicación](media/service-template-apps-install-distribute/power-bi-template-app-customize-share.png)

## <a name="customize-and-share-the-app"></a>Personalización y uso compartido de la aplicación

Una vez que se haya actualizado el explorador después de conectarse a los datos y actualizarlos, verá el área de trabajo que está asociada a la aplicación. En este momento, puede editar cualquiera de los artefactos, como lo haría en cualquier área de trabajo. Pero recuerde que los cambios que realice se sobrescribirán al actualizar la aplicación con una nueva versión, a menos que guarde con otro nombre los elementos que ha cambiado. [Vea detalles sobre la sobrescritura](#overwrite-behavior).

Para obtener información sobre la edición de artefactos en el área de trabajo, consulte los vínculos siguientes:
* [Paseo por el editor de informes de Power BI](../create-reports/service-the-report-editor-take-a-tour.md)
* [Conceptos básicos para los diseñadores en el servicio Power BI](../fundamentals/service-basic-concepts.md)

Cuando haya terminado de realizar los cambios deseados en los artefactos del área de trabajo, estará a punto para publicar y compartir la aplicación. Vea [Publicación de la aplicación](../collaborate-share/service-create-distribute-apps.md#publish-your-app) para aprender a hacerlo.

## <a name="update-a-template-app"></a>Actualización de una aplicación de plantilla

En ocasiones, los creadores de aplicaciones de plantilla lanzan nuevas versiones mejoradas de sus aplicaciones de plantilla, a través de AppSource, un vínculo directo o ambos.

Si originalmente descargó la aplicación de AppSource, cuando haya disponible una nueva versión de la aplicación de plantilla, recibirá una notificación de dos maneras:
* Aparece un banner de actualización en el servicio Power BI que le informa de que hay disponible una nueva versión de la aplicación.
  ![Notificación de actualización de la aplicación de plantilla](media/service-template-apps-install-distribute/power-bi-new-app-version-notification-banner.png)
* Recibirá una notificación en el panel de notificaciones de Power BI.


  ![Notificación de actualización de la aplicación de plantilla](media/service-template-apps-install-distribute/power-bi-new-app-version-notification-pane.png)

>[!NOTE]
>Si originalmente ha obtenido la aplicación a través de un vínculo directo, y no desde AppSource, la única forma de saber cuándo hay una versión nueva disponible es ponerse en contacto con el creador de la aplicación de plantilla.

  Para instalar la actualización, haga clic en **Obtenerla** en el banner de notificación o en el centro de notificaciones, o bien busque de nuevo la aplicación en AppSource y elija **Obtenerla ahora**. Si ha obtenido un vínculo directo para la actualización del creador de la aplicación de plantilla, simplemente haga clic en el vínculo.
  
  Se le preguntará si quiere sobrescribir la versión actual o instalar la nueva en una nueva área de trabajo. De forma predeterminada, está seleccionada la opción de "sobrescritura".

  ![Actualización de una aplicación de plantilla](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **Sobrescritura de una versión existente:** sobrescribe el área de trabajo existente con la versión actualizada de la aplicación de plantilla. [Vea detalles sobre la sobrescritura](#overwrite-behavior).

- **Instalación en una nueva área de trabajo:** Instala una versión nueva del área de trabajo y la aplicación que tiene que volver a configurar (es decir, conectarse a los datos, definir la navegación y los permisos).

### <a name="overwrite-behavior"></a>Comportamiento de sobrescritura

* Al sobrescribir, se actualizan los informes, los paneles y el conjunto de datos dentro del área de trabajo, no de la aplicación. La sobrescritura no cambia la navegación, la configuración ni los permisos de la aplicación.
* Después de actualizar el área de trabajo, **debe actualizar la aplicación para aplicar sobre esta los cambios del área de trabajo**.
* La sobrescritura mantiene los parámetros y la autenticación configurados. Después de la actualización, se inicia una actualización automática del conjunto de datos. **Durante esta actualización, la aplicación, los informes y los paneles presentan datos de ejemplo**.

  ![Datos de ejemplo](media/service-template-apps-install-distribute/power-bi-sample-data.png)

* Al sobrescribir siempre se muestran datos de ejemplo hasta que se completa la actualización. Si el autor de la aplicación de plantilla ha realizado cambios en el conjunto de datos o en los parámetros, los usuarios del área de trabajo y la aplicación no verán los datos nuevos hasta que finalice la actualización. En su lugar, durante este tiempo seguirán viendo datos de ejemplo.
* Al sobrescribir nunca se eliminan los informes o paneles nuevos que haya agregado al área de trabajo. Solamente se sobrescriben los informes y paneles originales con los cambios del autor original.

>[!IMPORTANT]
>Recuerde [actualizar la aplicación](#customize-and-share-the-app) después de sobrescribir para aplicar los cambios en los informes y el panel de los usuarios de la aplicación de la organización.

## <a name="next-steps"></a>Pasos siguientes

[Creación de áreas de trabajo con sus compañeros en Power BI](../collaborate-share/service-create-workspaces.md)
