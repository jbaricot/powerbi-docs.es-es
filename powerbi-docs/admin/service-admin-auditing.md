---
title: Seguimiento de actividades de usuario en Power BI
description: Obtenga información sobre cómo puede usar los registros de actividad y auditoría con Power BI para supervisar e investigar las acciones realizadas.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/20/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 0c1c113f100c3ae1db0902c90833c44788fa7ec6
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90857712"
---
# <a name="track-user-activities-in-power-bi"></a>Seguimiento de actividades de usuario en Power BI

Es fundamental saber quién realiza cada acción en cada elemento del inquilino de Power BI para ayudar a la organización a satisfacer sus requisitos, como el cumplimiento normativo y la administración de registros. Con Power BI, tiene dos opciones para realizar el seguimiento de la actividad del usuario: El [Registro de actividad de Power BI](#use-the-activity-log) y el [Registro de auditoría unificado](#use-the-audit-log). Estos registros contienen una copia completa de los [datos de auditoría de Power BI](#operations-available-in-the-audit-and-activity-logs), pero hay varias diferencias clave, como se resume en la tabla siguiente.

| **Registro de auditoría unificado** | **Registro de actividad de Power BI** |
| --- | --- |
| Incluye eventos de SharePoint Online, Exchange Online, Dynamics 365 y otros servicios además de los eventos de auditoría de Power BI. | Solo incluye los eventos de auditoría de Power BI. |
| Solo tienen acceso, como administradores globales y auditores, los usuarios con permisos Registros de auditoría o Registros de auditoría de solo lectura. | Los administradores globales y los administradores del servicio Power BI tienen acceso. |
| Los administradores y auditores globales pueden buscar en el registro de auditoría unificado mediante el Centro de seguridad de Microsoft 365 y el Centro de cumplimiento de Microsoft 365. | Todavía no hay ninguna interfaz de usuario para buscar en el registro de actividad. |
| Los administradores y auditores globales pueden descargar entradas del registro de auditoría mediante los cmdlets y las API de administración de Microsoft 365. | Los administradores globales y los administradores del servicio Power BI pueden descargar entradas del registro de actividad mediante una API REST de Power BI y un cmdlet de administración. |
| Mantiene los datos de auditoría durante 90 días | Mantiene los datos de actividad durante 30 días (versión preliminar pública). |
| Conserva los datos de auditoría, incluso si el inquilino se mueve a otra región de Azure. | No conserva los datos de actividad cuando el inquilino se mueve a otra región de Azure. |


## <a name="use-the-activity-log"></a>Uso del registro de actividad

> [!NOTE]
> El registro de actividad no es compatible con Microsoft Cloud Deutschland. Obtenga más información sobre las limitaciones del servicio para la nube de Alemania en [Preguntas más frecuentes sobre Power BI para clientes en la nube de Alemania](service-govde-faq.md).


Como administrador del servicio Power BI, puede analizar el uso de todos los recursos de Power BI en el nivel de inquilino mediante informes personalizados basados en el registro de actividad de Power BI. Puede descargar las actividades mediante una API REST o un cmdlet de PowerShell. También puede filtrar los datos de actividad por intervalo de fechas, usuario y tipo de actividad.

### <a name="activity-log-requirements"></a>Requisitos del registro de actividad

Debe cumplir estos requisitos para acceder al registro de actividad de Power BI:

- Debe ser un administrador global o un administrador del servicio Power BI.
- Ha instalado los [cmdlets de administración de Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) localmente o usa los cmdlets de administración de Power BI en Azure Cloud Shell.

### <a name="activityevents-rest-api"></a>API REST ActivityEvents

Puede usar una aplicación administrativa basada en las API REST de Power BI para exportar eventos de actividad a un almacén de blobs o a una base de datos SQL. Después, puede crear un informe de uso personalizado sobre los datos exportados. En la llamada a la API REST **ActivityEvents**, debe especificar una fecha de inicio y una fecha de finalización y, opcionalmente, un filtro para seleccionar actividades por tipo de actividad o identificador de usuario. Como el registro de actividad puede contener una gran cantidad de datos, actualmente la API **ActivityEvents** solo admite la descarga de hasta un día de datos por solicitud. Es decir, la fecha de inicio y la fecha de finalización deben especificar el mismo día, como en el ejemplo siguiente. Asegúrese de especificar los valores de fecha y hora en formato UTC.

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?startDateTime='2019-08-31T00:00:00'&endDateTime='2019-08-31T23:59:59'
```

Si el número de entradas es grande, la API **ActivityEvents** solo devuelve entre 5 000 y 10 000 entradas, y un token de continuación. Vuelva a llamar a la API **ActivityEvents** con el token de continuación para obtener el siguiente lote de entradas, y así sucesivamente, hasta que haya recuperado todas las entradas y ya no reciba un token de continuación. En el ejemplo siguiente se muestra cómo usar el token de continuación.

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?continuationToken='%2BRID%3ARthsAIwfWGcVAAAAAAAAAA%3D%3D%23RT%3A4%23TRC%3A20%23FPC%3AARUAAAAAAAAAFwAAAAAAAAA%3D'
```

Con independencia del número de entradas devueltas, si los resultados incluyen un token de continuación, asegúrese de volver a llamar a la API con ese token para recuperar los datos restantes, hasta que ya no se devuelva un token de continuación. Es posible que una llamada devuelva incluso un token de continuación sin ninguna entrada de evento. En el ejemplo siguiente se muestra cómo crear un bucle con un token de continuación devuelto en la respuesta:

```
while(response.ContinuationToken != null)
{
   // Store the activity event results in a list for example
    completeListOfActivityEvents.AddRange(response.ActivityEventEntities);

    // Make another call to the API with continuation token
    response = GetPowerBIActivityEvents(response.ContinuationToken)
}
completeListOfActivityEvents.AddRange(response.ActivityEventEntities);
```
> [!NOTE]
> Los eventos pueden tardar hasta 24 horas en aparecer, aunque los datos completos suelen estar disponibles mucho antes.
>
>
Para obtener más información sobre el uso de la API de REST de Power BI, incluidos ejemplos de cómo obtener eventos de actividad de auditoría, vea [Administración: obtención de eventos de auditoría](/rest/api/power-bi/admin/getactivityevents) en la documentación de referencia de la API de REST de Power BI.

### <a name="get-powerbiactivityevent-cmdlet"></a>Cmdlet Get-PowerBIActivityEvent

Descargue eventos de actividad con los cmdlets de administración de Power BI para PowerShell. El cmdlet **Get-PowerBIActivityEvent** controla de forma automática el token de continuación. El cmdlet **Get-PowerBIActivityEvent** toma un parámetro StartDateTime y EndDateTime con las mismas restricciones que la API REST **ActivityEvents**. Es decir, la fecha de inicio y la fecha de finalización deben hacer referencia al mismo valor de fecha porque solo se pueden recuperar los datos de actividad de un día a la vez.

En el script siguiente se muestra cómo descargar todas las actividades de Power BI. El comando convierte los resultados de JSON en objetos de .NET para un acceso sencillo a las propiedades de cada actividad. En estos ejemplos se muestran las marcas de tiempo más pequeñas y más grandes posibles de un día para asegurarse de que no se pierde ningún evento.

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' | ConvertFrom-Json

$activities.Count
$activities[0]

```

### <a name="filter-activity-data"></a>Filtrado de datos de actividad

Puede filtrar los eventos de actividad por tipo de actividad e identificador de usuario. En el script siguiente se muestra cómo descargar solo los datos de evento para la actividad **ViewDashboard**. Para obtener más información sobre los parámetros admitidos, use el comando `Get-Help Get-PowerBIActivityEvent`.

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' -ActivityType 'ViewDashboard' | ConvertFrom-Json

$activities.Count
$activities[0]

```

> [!NOTE]
> Hay disponible una muestra de PowerShell para ayudarle a obtener información sobre cómo filtrar y recuperar eventos de registro de actividad de Power BI. Para obtener más información, consulte [Acceso al registro de actividad de Power BI](../guidance/admin-activity-log.md).

## <a name="use-the-audit-log"></a>Uso del registro de auditoría

Si su tarea consiste en realizar el seguimiento de las actividades del usuario en Power BI y Microsoft 365, trabaje con la auditoría en el Centro de seguridad y cumplimiento de Microsoft 365 o use PowerShell. La auditoría se basa en la funcionalidad de Exchange Online, que se aprovisiona automáticamente para admitir Power BI.

Puede filtrar los datos de auditoría por intervalo de fechas, usuario, panel, informe, conjunto de datos y tipo de actividad. También puede descargar las actividades en un archivo .csv (valores separados por comas) para analizarlo sin conexión.

### <a name="audit-log-requirements"></a>Requisitos del registro de auditoría

Debe cumplir estos requisitos para acceder a los registros de auditoría:

- Debe ser un administrador global o tener asignado el rol Registros de auditoría o Registros de auditoría de solo lectura de Exchange Online para obtener acceso al registro de auditoría. De manera predeterminada, los grupos de roles de Administración de cumplimiento y Administración de organizaciones incluyen estos roles asignados en la página **Permisos** en el centro de administración de Exchange. Para obtener más información sobre los roles que pueden ver registros de auditoría, vea [Requisitos para realizar búsquedas en el registro de auditoría](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance?view=o365-worldwide#requirements-to-search-the-audit-log).

    Para proporcionar acceso al registro de auditoría a las cuentas que no son de administrador, agregue el usuario como miembro de uno de estos grupos de roles. Si quiere hacerlo de otra manera, puede crear un grupo de roles personalizados en el centro de administración de Exchange, asignar el rol Registros de auditoría o Registros de auditoría de solo visualización a este grupo y, luego, agregar la cuenta que no es de administrador al nuevo grupo de roles. Para obtener más información, vea [Manage role groups in Exchange Online](/Exchange/permissions-exo/role-groups) (Administración de grupos de roles en Exchange Online).

    Si no puede acceder al centro de administración de Exchange desde el Centro de administración de Microsoft 365, vaya a https://outlook.office365.com/ecp e inicie sesión con las credenciales.

- Si tiene acceso al registro de auditoría pero no es administrador global ni administrador del servicio Power BI, no puede acceder al portal de administración de Power BI. En este caso, use un vínculo directo al [Centro de seguridad y cumplimiento de Office 365](https://sip.protection.office.com/#/unifiedauditlog).

### <a name="access-your-audit-logs"></a>Acceso a los registros de auditoría

Para acceder a los registros, asegúrese primero de habilitar el registro en Power BI. Para más información, vea [Registros de auditoría](service-admin-portal.md#audit-logs) en la documentación del portal de administración. Puede haber un retraso de hasta 48 horas entre el momento en que se habilita la auditoría y el momento en que se pueden ver los datos de auditoría. Si no ve los datos de inmediato, consulte los registros de auditoría más tarde. Puede haber una demora similar entre la obtención de permisos para ver los registros de auditoría y la posibilidad de acceder a estos.

Los registros de auditoría de Power BI están disponibles directamente en el [Centro de seguridad y cumplimiento de Office 365](https://sip.protection.office.com/#/unifiedauditlog). También hay un vínculo desde el portal de administración de Power BI:

1. En Power BI, seleccione el **icono de engranaje** en la esquina superior derecha y, luego, seleccione **Portal de administración**.

   ![Captura de pantalla del menú desplegable de engranaje con la opción de portal de administración resaltada.](media/service-admin-auditing/powerbi-admin.png)

1. Seleccione **Registros de auditoría**.

1. Seleccione **Ir al Centro de administración de Microsoft 365**.

   ![Captura de pantalla del portal de administración con la opción Registros de auditoría y las opciones Ir al centro de administración de Microsoft 365 resaltadas.](media/service-admin-auditing/audit-log-o365-admin-center.png)

### <a name="search-only-power-bi-activities"></a>Buscar solo actividades de Power BI

Restrinja los resultados solo a las actividades de Power BI; para ello siga estos pasos. Para obtener una lista de actividades, consulte la lista de [actividades auditadas por Power BI](#operations-available-in-the-audit-and-activity-logs) más adelante en este artículo.

1. En la página **Búsqueda de registros de auditoría**, seleccione la lista desplegable **Actividades** en **Buscar**.

2. Seleccione **Actividades de Power BI**.

   ![Captura de pantalla de la búsqueda de registros de auditoría con las actividades de Power BI resaltadas.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Seleccione un lugar fuera del cuadro de selección para cerrarlo.

Las búsquedas solo devolverán actividades de Power BI.

### <a name="search-the-audit-logs-by-date"></a>Buscar en los registros de auditoría por fecha

Puede buscar registros por intervalo de fechas mediante el campo **Fecha de inicio** y **Fecha de finalización**. La selección predeterminada son los últimos siete días. La pantalla muestra la fecha y hora en formato de hora universal coordinada (UTC). El intervalo de fechas máximo que se puede especificar es de 90 días. 

Recibirá un error si el intervalo de fechas seleccionado es superior a 90 días. Si usa el intervalo de fechas máximo de 90 días, debe seleccionar la hora actual en la **fecha de inicio**. De lo contrario, aparece un error que indica que la fecha de inicio es anterior a la fecha de finalización. Si ha activado la auditoría durante los 90 últimos días, el intervalo de fechas no puede empezar antes de la fecha de activación de la auditoría.

![Captura de pantalla de la búsqueda de registros de auditoría con las opciones Fecha de inicio y Fecha de finalización resaltadas.](media/service-admin-auditing/search-audit-log-by-date.png)

### <a name="search-the-audit-logs-by-users"></a>Buscar en los registros de auditoría por usuario

Puede buscar entradas del registro de auditoría para actividades realizadas por usuarios específicos. Escriba uno o varios nombres de usuario en el campo **Usuarios**. El nombre de usuario es similar a una dirección de correo electrónico. Es la cuenta con la que los usuarios inician sesión en Power BI. Si deja este cuadro en blanco, se devolverán las entradas de todos los usuarios (y las cuentas de servicio) de la organización.

![Captura de pantalla de la búsqueda de registros de auditoría con los usuarios resaltados.](media/service-admin-auditing/search-audit-log-by-user.png)

### <a name="view-search-results"></a>Ver los resultados de la búsqueda

Después de seleccionar **Buscar**, se cargan los resultados de la búsqueda. Después de unos momentos, aparecen en **Resultados**. Una vez finalizada la búsqueda, la pantalla muestra el número de resultados encontrados. **Búsqueda de registros de auditoría** muestra un máximo de 1000 eventos. Si son más de 1000 los eventos que cumplen los criterios de búsqueda, la aplicación mostrará los 1000 eventos más recientes.

#### <a name="view-the-main-results"></a>Ver los resultados principales

El área **Resultados** tiene la siguiente información sobre cada evento devuelto por la búsqueda. Seleccione un encabezado de columna en **Resultados** para ordenar los resultados.

| **Columna** | **Definición** |
| --- | --- |
| Fecha |Fecha y hora (en formato UTC) en las que se produjo el evento. |
| IP address (Dirección IP) |La dirección IP del dispositivo que se usa para la actividad registrada. La aplicación muestra la dirección IP en el formato de dirección IPv4 o IPv6. |
| Usuario |Usuario (o cuenta de servicio) que realizó la acción que desencadenó el evento. |
| Actividad |Actividad realizada por el usuario. Este valor corresponde a las actividades que se seleccionaron en la lista desplegable **Actividades**. En el caso de un evento del registro de auditoría de administración de Exchange, el valor de esta columna es un cmdlet de Exchange. |
| Artículo |El objeto creado o modificado debido a la actividad correspondiente. Por ejemplo, el archivo visto o modificado, o la cuenta de usuario actualizada. No todas las actividades tienen un valor en esta columna. |
| Detail (Detalle) |Detalles adicionales sobre una actividad. También en este caso, no todas las actividades tienen un valor. |

#### <a name="view-the-details-for-an-event"></a>Ver los detalles de un evento

Para ver más detalles de un evento, seleccione el registro de eventos en la lista de resultados de la búsqueda. Aparece una página **Detalles** con las propiedades detalladas del registro de eventos. En la página **Detalles** se muestran las propiedades en función del servicio de Microsoft 365 donde ocurre el evento.

Para mostrar estos detalles, seleccione **Más información**. Todas las entradas de Power BI tienen un valor de 20 para la propiedad RecordType. Para obtener información sobre otras propiedades, vea [Propiedades detalladas del registro de auditoría de Office 365](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Captura de pantalla del cuadro de diálogo de detalles de la auditoría con la opción Más información resaltada.](media/service-admin-auditing/audit-details.png)

### <a name="export-search-results"></a>Exportar los resultados de la búsqueda

Para exportar el registro de auditoría de Power BI a un archivo .csv, siga estos pasos.

1. Seleccione **Exportar resultados**.

1. Seleccione **Save loaded results** (Guardar resultados cargados) o **Download all results** (Descargar todos los resultados).

    ![Captura de pantalla de la opción Exportar resultados con Descargar todos los resultados destacado.](media/service-admin-auditing/export-auditing-results.png)

### <a name="use-powershell-to-search-audit-logs"></a>Uso de PowerShell para buscar registros de auditoría

También puede usar PowerShell para acceder a los registros de auditoría mediante el inicio de sesión. En el ejemplo siguiente se muestra cómo conectarse a Exchange Online PowerShell y usar luego el comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para extraer las entradas de registro de auditoría de Power BI. Para ejecutar el script, un administrador debe asignarle los permisos adecuados, como se describe en la sección [Requisitos del registro de auditoría](#audit-log-requirements).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

### <a name="use-powershell-to-export-audit-logs"></a>Uso de PowerShell para exportar registros de auditoría

También puede usar PowerShell para exportar los resultados de la búsqueda de registros de auditoría. En el ejemplo siguiente se muestra cómo enviar desde el comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) y exportar los resultados con el cmdlet [Export-Csv](/powershell/module/microsoft.powershell.utility/export-csv). Para ejecutar el script, un administrador debe asignarle los permisos adecuados, como se describe en la sección [Requisitos del registro de auditoría](#audit-log-requirements).

```powershell
$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2019 -EndDate 9/15/2019 -RecordType PowerBI -ResultSize 5000 |
Export-Csv -Path "c:\temp\PowerBIAuditLog.csv" -NoTypeInformation

Remove-PSSession $Session
```

Para obtener más información sobre cómo conectarse a Exchange Online, vea [Conexión a Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Para consultar otro ejemplo del uso de PowerShell con los registros de auditoría, vea [Using Power BI audit log and PowerShell to assign Power BI Pro licenses](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) (Uso del registro de auditoría de Power BI y PowerShell para asignar licencias de Power BI Pro).

## <a name="operations-available-in-the-audit-and-activity-logs"></a>Operaciones disponibles en los registros de actividad y auditoría

Las operaciones siguientes están disponibles en los registros de auditoría y de actividad.

| Nombre descriptivo                                     | Nombre de operación                              | Notas                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Tablas destacadas de Power BI a las que se ha accedido en Excel | AnalyzedByExternalApplication |    |
| Origen de datos agregado a la puerta de enlace de Power BI             | AddDatasourceToGateway                      |                                          |
| Acceso a la carpeta de Power BI agregado                      | AddFolderAccess                             | No se usa actualmente                       |
| Miembros del grupo de Power BI agregados                      | AddGroupMembers                             |                                          |
| Cuenta de almacenamiento del flujo de datos adjuntado al inquilino por el administrador | AdminAttachedDataflowStorageAccountToTenant | No se usa actualmente                       |
| Se ha analizado un conjunto de datos de Power BI                         | AnalyzedByExternalApplication               | Se genera cuando los usuarios interactúan con el servicio                                         |
| Informe de Power BI analizado                          | AnalyzeInExcel                              |                                          |
| Asignado un área de trabajo a una canalización de implementación                          | AssignWorkspaceToPipeline                              |                                          |
| Cuenta de almacenamiento del flujo de datos asociada                 | AttachedDataflowStorageAccount              |                                          |
| Conjunto de datos de Power BI enlazado a la puerta de enlace                | BindToGateway                               |                                          |
| Actualización de flujo de datos cancelada                        | CancelDataflowRefresh                       |                                          |
| Estado de capacidad cambiado                            | ChangeCapacityState                         |                                          |
| Asignación de usuarios de la capacidad cambiada                  | UpdateCapacityUsersAssignment               |                                          |
| Conexiones de datos de Power BI cambiadas              | SetAllConnections                           |                                          |
| Se han cambiado los administradores de la puerta de enlace de Power BI                   | ChangeGatewayAdministrators                 |                                          |
| Se han cambiado los usuarios de los orígenes de datos de la puerta de enlace de Power BI        | ChangeGatewayDatasourceUsers                |                                          |
| Se creó un objeto visual personalizado de organización                          | InsertOrganizationalGalleryItem                                |                                          |
| Paquete de contenido organizativo de Power BI creado      | CreateOrgApp                                |                                          |
| Se creó una canalización de implementación      | CreateAlmPipeline                                |                                          |
| Aplicación de Power BI creada                              | CreateApp                                   |                                          |
| Panel de Power BI creado                        | CreateDashboard                             |                                          |
| Flujo de datos de Power BI creado                         | CreateDataflow                              |                                          |
| Conjunto de datos de Power BI creado                          | CreateDataset                               |                                          |
| Suscripción de correo electrónico de Power BI creada               | CreateEmailSubscription                     |                                          |
| Carpeta de Power BI creada                           | CreateFolder                                |                                          |
| Se ha creado una puerta de enlace de Power BI                          | CreateGateway                               |                                          |
| Grupo de Power BI creado                            | CreateGroup                                 |                                          |
| Informe de Power BI creado                           | CreateReport <sup>1</sup>                                |                                          |
| El objeto visual personalizado solicitó un token de acceso a Azure AD                           | GenerateCustomVisualAADAccessToken                                |                                          |
| El objeto visual personalizado solicitó un token de acceso a Office Web Apps                           | GenerateCustomVisualWACAccessToken                                |                                          |
| Flujo de datos migrado a la cuenta de almacenamiento externa     | DataflowMigratedToExternalStorageAccount    | No se usa actualmente                       |
| Permisos de flujo de datos agregados                        | DataflowPermissionsAdded                    | No se usa actualmente                       |
| Permisos de flujo de datos eliminados                      | DataflowPermissionsRemoved                  | No se usa actualmente                       |
| Se eliminó un objeto visual personalizado de organización     | DeleteOrganizationalGalleryItem                                |                                          |
| Se eliminó una canalización de implementación      | DeleteAlmPipeline                                |                                          |
| Paquete de contenido organizativo de Power BI eliminado      | DeleteOrgApp                                |                                          |
| Comentario de Power BI eliminado                          | DeleteComment                               |                                          |
| Panel de Power BI eliminado                        | DeleteDashboard                             | No se usa actualmente                       |
| Flujo de datos de Power BI eliminado                         | DeleteDataflow                              | No se usa actualmente                       |
| Conjunto de datos de Power BI eliminado                          | DeleteDataset                               |                                          |
| Suscripción de correo electrónico de Power BI eliminada               | DeleteEmailSubscription                     |                                          |
| Carpeta de Power BI eliminada                           | DeleteFolder                                |                                          |
| Acceso a la carpeta de Power BI eliminado                    | DeleteFolderAccess                          | No se usa actualmente                       |
| Se ha eliminado una puerta de enlace de Power BI                          | DeleteGateway                               |                                          |
| Grupo de Power BI eliminado                            | DeleteGroup                                 |                                          |
| Informe de Power BI eliminado                           | DeleteReport                                |                                          |
| Implementado en una fase de canalización                           | DeployAlmPipeline                                |                                          |
| Orígenes de datos de conjunto de datos de Power BI detectados          | GetDatasources                              |                                          |
| Informe de Power BI descargado                        | DownloadReport                              |                                          |
| Propiedades del flujo de datos editadas                        | EditDataflowProperties                      |                                          |
| Permiso de certificación de Power BI editado          | EditCertificationPermission                 | No se usa actualmente                       |
| Panel de Power BI editado                         | EditDashboard                               | No se usa actualmente                       |
| Conjunto de datos de Power BI editado                           | EditDataset                                 |                                          |
| Propiedades de conjunto de datos de Power BI editadas                | EditDatasetProperties                       | No se usa actualmente                       |
| Informe de Power BI editado                            | EditReport                                  |                                          |
| Flujo de datos de Power BI exportado                        | ExportDataflow                              |                                          |
| Datos de objetos visuales de informe de Power BI exportados              | ExportReport                                |                                          |
| Datos de iconos de Power BI exportados                       | ExportTile                                  |                                          |
| No se pudieron agregar permisos de flujo de datos                | FailedToAddDataflowPermissions              | No se usa actualmente                       |
| No se pudieron eliminar permisos de flujo de datos             | FailedToRemoveDataflowPermissions           | No se usa actualmente                       |
| Token SAS de flujo de datos de Power BI generado             | GenerateDataflowSasToken                    |                                          |
| Token de inserción Power BI generado                    | GenerateEmbedToken                          |                                          |
| Archivo a Power BI importado                         | Importación                                      |                                          |
| Aplicación de Power BI instalada                            | InstallApp                                  |                                          |
| Área de trabajo a una capacidad migrada                  | MigrateWorkspaceIntoCapacity                |                                          |
| Comentario de Power BI publicado                           | PostComment                                 |                                          |
| Panel de Power BI imprimido                        | PrintDashboard                              |                                          |
| Página de informe de Power BI imprimida                      | PrintReport                                 |                                          |
| Informe de Power BI publicado en la Web                  | PublishToWebReport <sup>2</sup>                         |                                          |
| Tablas destacadas publicadas o actualizadas | UpdateFeaturedTables <sup>3</sup>   | |
| Flujo de datos de Power BI secreto recibido de Key Vault  | ReceiveDataflowSecretFromKeyVault           |                                          |
| Se quitó un área de trabajo de una canalización de implementación         | UnassignWorkspaceFromPipeline                 |                                          |
| Se ha eliminado un origen de datos de la puerta de enlace de Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Miembros del grupo de Power BI eliminados                    | DeleteGroupMembers                          |                                          |
| Área de trabajo de una capacidad eliminada                 | RemoveWorkspacesFromCapacity                |                                          |
| Nombre de un panel de Power BI cambiado                        | RenameDashboard                             |                                          |
| Actualización del flujo de datos de Power BI solicitada               | RequestDataflowRefresh                      | No se usa actualmente                       |
| Actualización del conjunto de datos de Power BI solicitada                | RefreshDataset                              |                                          |
| Áreas de trabajo de Power BI recuperadas                     | GetWorkspaces                               |                                          |
| Etiqueta de confidencialidad aplicada                         | SensitivityLabelApplied                     |                                          |
| Etiqueta de confidencialidad modificada                         | SensitivityLabelChanged                     |                                          |
| Etiqueta de confidencialidad quitada                         | SensitivityLabelRemoved                     |                                          |
| Establecer la ubicación de almacenamiento del flujo de datos para un área de trabajo     | SetDataflowStorageLocationForWorkspace      |                                          |
| Actualización programada en un flujo de datos de Power BI establecida        | SetScheduledRefreshOnDataflow               |                                          |
| Actualización programada en un conjunto de datos de Power BI establecida         | SetScheduledRefresh                         |                                          |
| Panel de Power BI compartido                         | ShareDashboard                              |                                          |
| Informe de Power BI compartido                            | ShareReport                                 |                                          |
| Se ha iniciado la versión de prueba extendida de Power BI                   | OptInForExtendedProTrial                    | No se usa actualmente                       |
| Versión de prueba de Power BI iniciada                            | OptInForProTrial                            |                                          |
| Control tomado sobre un origen de datos de Power BI                   | TakeOverDatasource                          |                                          |
| Control tomado sobre un conjunto de datos de Power BI                        | TakeOverDataset                             |                                          |
| Control tomado sobre un flujo de datos de Power BI                     | TookOverDataflow                             |                                          |
| Publicación de una aplicación de Power BI anulada                          | UnpublishApp                                |                                          |
| Configuración de gobernanza de recursos de capacidad actualizada      | UpdateCapacityResourceGovernanceSettings    | No se encuentra en el Centro de administración de Microsoft 365 |
| Se actualizó un objeto visual personalizado de organización                     | UpdateOrganizationalGalleryItem                   |                                          |
| Administración de capacidad actualizada                            | UpdateCapacityAdmins                        |                                          |
| Nombre para mostrar de la capacidad actualizado                     | UpdateCapacityDisplayName                   |                                          |
| Permisos de asignación de almacenamiento del flujo de datos actualizados   | UpdatedDataflowStorageAssignmentPermissions |                                          |
| Se actualizó el acceso a una canalización de implementación   | UpdateAlmPipelineAccess |                                          |
| Se actualizó la configuración de una canalización de implementación   | SetConfigurationAlmPipeline |                                          |
| Configuración de Power BI de la organización actualizada          | UpdatedAdminFeatureSwitch                   |                                          |
| Aplicación de Power BI actualizada                              | UpdateApp                                   |                                          |
| Flujo de datos de Power BI actualizados                         | UpdateDataflow                              |                                          |
| Orígenes de datos de conjunto de datos de Power BI actualizados             | UpdateDatasources                           |                                          |
| Parámetros de conjunto de datos de Power BI actualizados               | UpdateDatasetParameters                     |                                          |
| Suscripción de correo electrónico de Power BI actualizada               | UpdateEmailSubscription                     |                                          |
| Carpeta de Power BI actualizada                           | UpdateFolder                                |                                          |
| Acceso a la carpeta de Power BI actualizado                    | UpdateFolderAccess                          |                                          |
| Credenciales de los orígenes de datos de la puerta de enlace de Power BI actualizadas  | UpdateDatasourceCredentials                 |                                          |
| Panel de Power BI visualizado                         | ViewDashboard                               |                                          |
| Flujo de datos de Power BI visualizado                          | ViewDataflow                                |                                          |
| Informe de Power BI visualizado                            | ViewReport                                  |                                          |
| Conjunto de datos de Power BI visualizado                              | ViewTile                                    |                                          |
| Métricas de uso de Power BI visualizadas                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

<sup>1</sup> La publicación desde Power BI Desktop en el servicio es un evento CreateReport en el servicio.

<sup>2</sup> PublishtoWebReport hace referencia a la característica [Publicar en la web](../collaborate-share/service-publish-to-web.md).

<sup>3</sup> UpdateFeaturedTables hace referencia a [Tablas destacadas de Power BI en Excel](../collaborate-share/service-excel-featured-tables.md).

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué es la administración de Power BI?](service-admin-administering-power-bi-in-your-organization.md)
- [Portal de administración de Power BI](service-admin-portal.md)
- [Acceso al registro de actividad de Power BI](../guidance/admin-activity-log.md)
- ¿Tiene preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)