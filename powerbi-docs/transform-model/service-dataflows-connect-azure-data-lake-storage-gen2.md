---
title: Conexión de Azure Data Lake Storage Gen 2 a Power BI para el almacenamiento del flujo de datos
description: Traiga sus propios datos a los flujos de datos mediante Azure Data Lake Storage Gen2.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 01/22/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ee24e4aaa54fdbc60c631dc319caf6b1465aed28
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859828"
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>Conexión a Azure Data Lake Storage Gen2 para el almacenamiento del flujo de datos

Puede configurar las áreas de trabajo de Power BI para almacenar los flujos de datos de la cuenta de Azure Data Lake Storage Gen2 de su organización. En este artículo se describen los pasos generales necesarios para hacerlo y se proporcionan además instrucciones y procedimientos recomendados. Existen algunas ventajas en la configuración de áreas de trabajo para almacenar archivos de definición de flujo de datos y de datos en su instancia de Data Lake, como las siguientes:

* Azure Data Lake Storage Gen2 proporciona una funcionalidad de almacenamiento enormemente escalable para los datos.
* Los desarrolladores del departamento de TI pueden aprovechar los datos y los archivos de definición de flujo de datos para sacar provecho de los servicios de datos e inteligencia artificial (AI) de Azure, tal y como se muestra los [ejemplos de GitHub de Azure Data Services](https://aka.ms/cdmadstutorial).
* Permite a los desarrolladores de la organización integrar los datos del flujo de datos en aplicaciones internas y soluciones de línea de negocio, mediante recursos de desarrollador para flujos de datos y Azure.

Para usar Azure Data Lake Storage Gen2 para los flujos de datos, necesita lo siguiente:

* **Inquilino de Power BI:** : al menos una cuenta del inquilino de Azure Active Directory (AAD) debe haberse registrado en Power BI.
* **Una cuenta de administrador Global**: esta cuenta es necesaria para conectarse a Power BI y configurarlo para almacenar la definición de flujo de datos, y los datos, en su cuenta de Azure Data Lake Storage Gen2.
* **Una suscripción a Azure**: necesita una suscripción a Azure para usar Azure Data Lake Storage Gen2.
* **Grupo de recursos**: use un grupo de recursos existente o cree uno.
* **Una cuenta de Azure Storage con la característica Data Lake Storage Gen2 habilitada** 

> [!TIP]
> Si no tiene ninguna suscripción a Azure, cree una [cuenta gratuita](https://azure.microsoft.com/free/) antes de empezar.

> [!WARNING]
> Una vez que se ha configurado una ubicación de almacenamiento de flujo de datos, no se puede cambiar. Consulte la sección de [consideraciones y limitaciones](#considerations-and-limitations) que se encuentra al final de este artículo para ver otros elementos importantes que se deben tener en cuenta.

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-bi"></a>Preparar Azure Data Lake Storage Gen2 para Power BI

Antes de configurar Power BI con una cuenta de Azure Data Lake Storage Gen2, debe crear y configurar una cuenta de almacenamiento. Echemos un vistazo a los requisitos para Power BI:

1. Debe ser el propietario de la cuenta de almacenamiento de ADLS. Se debe asignar en el nivel de recurso, no heredarse del nivel de la suscripción.
2. La cuenta de almacenamiento debe crearse en el mismo inquilino de AAD que el inquilino de Power BI.
3. La cuenta de almacenamiento debe crearse en la misma región que el inquilino de Power BI. Para determinar dónde se encuentra el inquilino de Power BI, consulte [¿Dónde se encuentra mi inquilino de Power BI?](../admin/service-admin-where-is-my-tenant-located.md).
4. La cuenta de almacenamiento debe tener habilitada la característica *Espacio de nombres jerárquico*.
5. Si el usuario actual no ha creado la cuenta de almacenamiento, asegúrese de que se le haya asignado el permiso [Propietario de datos de Storage Blob](/azure/role-based-access-control/built-in-roles#storage-blob-data-owner) y [Propietario](/azure/role-based-access-control/built-in-roles#owner). (Como el propietario no contiene el permiso de nivel de datos, se necesita el Propietario de datos de blob).

En las siguientes secciones se describen de forma detallada los pasos necesarios para configurar la cuenta de Azure Data Lake Storage Gen2.

### <a name="create-the-storage-account"></a>Crear la cuenta de almacenamiento

Siga los pasos descritos en el artículo [Creación de una cuenta de almacenamiento de Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-quickstart-create-account).

1. Asegúrese de seleccionar la misma ubicación que la del inquilino de Power BI y establezca su almacenamiento como **StorageV2 (v2 de uso general)** .
2. Asegúrese de habilitar la característica de espacio de nombres jerárquico.
3. Se recomienda establecer la configuración de replicación en **Almacenamiento con redundancia geográfica con acceso de lectura (RA-GRS)** .

### <a name="grant-permissions-to-power-bi-services"></a>Concesión de permisos a servicios de Power BI

Después, debe conceder al servicio Power BI los roles de lector y acceso a datos en la cuenta de almacenamiento creada. Se trata de roles integrados, por lo que los pasos son sencillos. 

Siga los pasos en [Assign a built-in RBAC role](/azure/storage/common/storage-auth-aad-rbac#assign-a-built-in-rbac-role) (Asignar un rol RBAC integrado).

En la ventana **Agregar asignación de roles**, seleccione el rol **Lector y acceso a los datos**. Después, use la búsqueda para encontrar la aplicación **Servicio Power BI**.
Repita los mismos pasos para el rol **Propietario de datos de blobs de almacenamiento** y asígnelo a las aplicaciones **Servicio Power BI** y **Power BI Premium**.

> [!NOTE]
> Deje pasar al menos 30 minutos para que el permiso se propague a Power BI desde el portal. Siempre que cambie permisos en el portal, espere 30 minutos para que esos permisos se reflejen en Power BI. 

## <a name="connect-your-azure-data-lake-storage-gen2-to-power-bi"></a>Conectar la instancia de Azure Data Lake Storage Gen2 a Power BI

Una vez que ha configurado su cuenta de Azure Data Lake Storage Gen2 en Azure Portal, la conectará a Power BI en el **portal de administración de Power BI**. También administrará el almacenamiento de flujo de datos de Power BI en la sección de configuración de **Almacenamiento de flujo de datos** del portal de administración de Power BI. Para instrucciones e información detallada sobre el inicio y el uso básico, consulte [Acceso al portal de administración](../admin/service-admin-portal.md).

Conectará la cuenta de **Azure Data Lake Storage Gen2** con los siguientes pasos:

1. Navegue a la pestaña **Configuración de flujo de datos** del **portal de administración de Power BI**

    ![Portal de administración de Power BI](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-08b.png) 

2. Seleccione el botón **Conectar Azure Data Lake Storage Gen2**. Aparecerá la siguiente ventana.

    ![Azure Data Lake Storage Gen2](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_09.jpg) 

3. Proporcione el **identificador de suscripción** de la cuenta de almacenamiento.
4. Proporcione el **nombre del grupo de recursos** en el que se creó la cuenta de almacenamiento.
5. Proporcione el **nombre de la cuenta de almacenamiento**.
6. Seleccione **Conectar**.

Una vez completados esos pasos correctamente, la cuenta de Azure Data Lake Storage Gen2 está conectada a Power BI. 

> [!NOTE]
> Para configurar una conexión a Azure Data Lake Storage Gen2 en el portal de administración de Power BI, debe tener permisos de administrador global. Sin embargo, los administradores globales no pueden conectar el almacenamiento externo en el portal de administración.  

A continuación, debe permitir que las personas de su organización configuren sus áreas de trabajo, de forma que puedan usar esta cuenta de almacenamiento para la definición del flujo de datos y el almacenamiento de datos. Lo haremos en la sección siguiente. 


## <a name="allow-admins-to-assign-workspaces"></a>Permitir que los administradores asignen áreas de trabajo

De forma predeterminada, los archivos de definición de flujo de datos y de datos se almacenan en el almacenamiento proporcionado por Power BI. Para acceder a los archivos de flujo de datos en su propia cuenta de almacenamiento, los administradores del área de trabajo deben configurar primero el área de trabajo para permitir la asignación y el almacenamiento de flujos de datos en la nueva cuenta de almacenamiento. Para que un administrador del área de trabajo pueda configurar los parámetros de almacenamiento de flujo de datos, dicho administrador debe tener permisos de asignación de almacenamiento en el **portal de administración de Power BI**.

Para conceder permisos de asignación de almacenamiento, vaya a la pestaña **Configuración de flujo de datos** en el **portal de administración de Power BI**. Hay un botón de radio para *Permitir que los administradores de áreas de trabajo asignen áreas de trabajo a esta cuenta de almacenamiento* que debe establecerse en **permitir**. Una vez que habilite ese control deslizante, seleccione el botón **Aplicar** para que el cambio surta efecto. 

![Permitir que los administradores asignen áreas de trabajo](media/service-dataflows-connect-azure-data-lake-storage-gen2/dataflows-connect-adlsg2_10.jpg) 

Ya está. Los administradores del área de trabajo de Power BI ahora pueden asignar los flujos de trabajo al sistema de archivos que ha creado.


## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Esta es una característica en versión preliminar y su comportamiento puede cambiar a medida que se acerque el lanzamiento. Hay algunas consideraciones y limitaciones que se deben tener en cuenta al trabajar con el almacenamiento de flujo de datos:

* Una vez que se ha configurado una ubicación de almacenamiento de flujo de datos, no se puede cambiar.
* Solo los propietarios de un flujo de datos almacenado en Azure Data Lake Storage Gen2 pueden acceder a sus datos de forma predeterminada. Para autorizar los flujos de datos almacenados en Azure para otras personas, debe agregarlos a la carpeta de CDS del flujo de datos. 
* La creación de flujos de datos con entidades vinculadas solo es posible cuando se almacenan en la misma cuenta de almacenamiento.
* Los orígenes de datos locales, en capacidades compartidas de Power BI, no se admiten en los flujos de datos almacenados en la instancia de Data Lake de su organización.
* Las instantáneas no se eliminan automáticamente de ADLS Gen 2. Si quiere liberar espacio, puede crear una función de Azure para limpiar periódicamente las instantáneas antiguas.

También hay algunos problemas conocidos, como se describe en esta sección.

Los clientes de Power BI Desktop no pueden acceder a los flujos de datos almacenados en una **cuenta de Azure Data Lake Storage** a menos que sean propietarios del flujo de datos, o que tengan autorización explícita para la carpeta de CDS en la instancia de Data Lake. El escenario es el siguiente:

1. Anna ha creado un área de trabajo y la ha configurado para almacenar flujos de datos en la instancia de Data Lake de la organización. 
2. Ben, que también es miembro del área de trabajo que ha creado Anna, querría usar Power BI Desktop y el conector de flujo de datos para obtener datos del flujo de datos que ha creado su compañera.
3. Ben recibe un error similar, ya que no tiene autorización en la carpeta de CDM del flujo de datos en la instancia de Data Lake.

Algunas de las preguntas y respuestas más frecuentes son:

**Pregunta:** ¿Y si hubiera creado anteriormente flujos de datos en un área de trabajo y quisiera cambiar su ubicación de almacenamiento?

**Respuesta:** No puede cambiar la ubicación de almacenamiento de un flujo de datos después de que se ha creado. 

**Pregunta:** ¿Cuándo se puede cambiar la ubicación de almacenamiento del flujo de datos de un área de trabajo?

**Respuesta:** Solo se permite cambiar la ubicación de almacenamiento del flujo de datos de un área de trabajo si el área de trabajo no contiene flujos de datos.


## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporcionan instrucciones sobre cómo conectar una instancia de Azure Data Lake Gen2 para el almacenamiento de flujo de datos. Para más información, eche un vistazo a los siguientes artículos:

Para más información sobre flujos de datos, CDS y Azure Data Lake Storage Gen2, eche un vistazo a los siguientes artículos:

* [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md)
* [Configuración de opciones de flujo de datos del área de trabajo (versión preliminar)](service-dataflows-configure-workspace-storage-settings.md)
* [Incorporación de una carpeta de CDS a Power BI como flujo de datos (versión preliminar)](service-dataflows-add-cdm-folder.md)

Para información sobre los flujos de datos en general, consulte estos artículos:

* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)
* [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)

Para más información sobre Azure Storage, puede leer estos artículos:
* [Guía de seguridad de Azure Storage](/azure/storage/common/storage-security-guide)

Para más información sobre Common Data Service, puede leer su artículo de introducción:
* [Introducción a Common Data Service](/powerapps/common-data-model/overview)
* [Carpetas de CDS](/common-data-model/data-lake)
* [Definición del archivo de modelo de CDS](/common-data-model/model-json)

Y, siempre puede intentar [plantear preguntas a la comunidad de Power BI](https://community.powerbi.com/).