---
title: Referencia de datos de supervisión de Power BI Embedded
description: Material de referencia importante necesario al supervisar Power BI Embedded
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: fc6b9dd4d50d665211324d1b6c05e62468fc034d
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690808"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>Referencia de datos de supervisión de Power BI Embedded

Vea [Supervisión de Power BI Embedded](monitor-power-bi-embedded.md) para obtener más información sobre la recopilación y el análisis de los datos de supervisión para Power BI Embedded.

## <a name="metrics"></a>Métricas

En esta sección se enumeran todas las métricas de plataforma recopiladas automáticamente para Power BI Embedded.  

|Tipo de métrica | Espacio de nombres de proveedor de recursos/tipo<br/> y vínculo a métricas individuales |
|-------|-----|
| Capacities | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>Capacities

Proveedor de recursos y tipo: [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| Nombre | Métrica | Unidad | Descripción |
|:---|:-------|:-----|:------------|
|Memoria (Gen1) |memory_metric               |Bytes        |Memoria. Intervalo de 0-3 GB para A1, 0-5 GB para A2, 0-10 GB para A3, 0-25 GB para A4, 0-50 GB para A5 y 0-100 GB para A6. Solo se admite para recursos de Power BI Embedded Generation 1. |
|Hiperpaginación de memoria (conjuntos de datos) (Gen1) |memory_thrashing_metric     |Percent      |Paginación excesiva media de memoria. Solo se admite para recursos de Power BI Embedded Generation 1. |
|Uso alto de QPU (Gen1) |qpu_high_utilization_metric |Count        |Uso alto de QPU en el último minuto, 1 para un uso elevado de QPU; de lo contrario, 0. Solo se admite para recursos de Power BI Embedded Generation 1. |
|Duración de consulta (conjuntos de datos) (Gen1) |QueryDuration               |Milisegundos |Duración de la consulta DAX en el último intervalo. Solo se admite para recursos de Power BI Embedded Generation 1. |
|Longitud de la cola de trabajos del grupo de consultas (conjuntos de datos) (Gen1) |QueryPoolJobQueueLength     |Count        |Número de trabajos en la cola del grupo de subprocesos de consultas. Solo se admite para recursos de Power BI Embedded Generation 1. |

## <a name="metric-dimensions"></a>Dimensiones de métricas

Para obtener más información sobre las dimensiones de métricas, consulte [Métricas multidimensionales](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics).

Power BI Embedded no tiene ninguna métrica que contenga dimensiones.

## <a name="resource-logs"></a>Registros del recurso

En esta sección se enumeran los tipos de registros de recursos que se pueden recopilar para Power BI Embedded.

Como referencia, vea una lista de [todos los tipos de categorías de registros de recursos admitidos en Azure Monitor](/azure/azure-monitor/platform/resource-logs-schema).

En esta sección se enumeran todos los tipos de categorías de registros de recursos recopilados para Power BI Embedded.  

|Tipo de registro de recursos | Espacio de nombres de proveedor de recursos/tipo<br/> y vínculo a métricas individuales |
|-------|-----|
| Capacities | [Microsoft.PowerBIDedicated/capacities](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Tablas de registros de Azure Monitor

En esta sección se hace referencia a todas las tablas Kusto de los registros de Azure Monitor relevantes para Power BI Embedded y disponibles para las consultas realizadas por Log Analytics.

|Tipo de recurso | Notas |
|-------|-----|
| [¿Qué es Power BI Embedded de Azure?](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |Vea una lista de tablas a continuación. |

### <a name="power-bi-embedded"></a>Power BI Embedded

| Tabla |  Descripción |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Entradas del registro de actividad de Azure que proporcionan información detallada sobre los eventos a nivel de suscripción o a nivel de grupo de administración que se han producido en Azure.    |                             |                                                   | 
| [AzureDiagnostics](/azure/azure-monitor/reference/tables/azurediagnostics)   | Almacena los registros de recursos de los servicios de Azure que usan el modo de Azure Diagnostics. Los registros de recursos describen el funcionamiento interno de los recursos de Azure. |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | Datos de métricas emitidos por los servicios de Azure que miden su estado y rendimiento. |

Puede encontrar una referencia de todas las tablas de registros de Azure Monitor o de Log Analytics en [Referencia de la tabla de registros de Azure Monitor](/azure/azure-monitor/reference/tables/tables-resourcetype).

## <a name="activity-log"></a>Registro de actividades

Puede seleccionar las categorías **Engine** o **AllMetrics**.

### <a name="engine"></a>Motor

La categoría Motor indica al recurso que registre los eventos siguientes. Y cada evento tiene sus propiedades.

|     Nombre del evento     |     Descripción del evento     |
|----------------------------|----------------------------------------------------------------------------------|
|    Auditoría de inicio de sesión    |    Registra todas las conexiones nuevas a los eventos de motor desde que empezó el seguimiento.    |
|    Inicialización de sesión    |    Registra todos los eventos de inicialización de sesión desde que empezó el seguimiento.    |
|    Inicio de consulta de Vertipaq    |    Registra todos los eventos de inicio de consulta de VertiPaq SE desde que empezó el seguimiento.    |
|    Inicio de consulta    |    Registra todos los eventos de inicio de consulta desde que empezó el seguimiento.    |
|    Fin de consulta    |    Registra todos los eventos de fin de consulta desde que empezó el seguimiento.    |
|    Fin de consulta de Vertipaq    |    Registra todos los eventos de fin de consulta de VertiPaq SE desde que empezó el seguimiento.    |
|    Auditoría de cierre de sesión    |    Registra todos los eventos de desconexión del motor desde que empezó el seguimiento.    |
|    Error    |    Registra todos los eventos de error del motor desde que empezó el seguimiento.    |

#### <a name="event-example"></a>Ejemplo de evento

En la tabla siguiente se muestra un ejemplo de evento.

| Nombre de la propiedad | Ejemplo de fin de consulta Vertipaq | Descripción de la propiedad |
|---|---|---|
| EventClass (Clase de evento) | XM_SEQUERY_END | Clase de evento se usa para categorizar los eventos. |
| EventSubclass (Subclase de evento) | 0 | Subclase de evento proporciona información adicional sobre cada clase de evento. (por ejemplo, 0: examen de VertiPaq) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | Identificador de actividad raíz. |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | Hora de inicio del evento, si está disponible. |
| StartTime | 2018-04-06T18:30:11.9137358Z | Hora de inicio del evento, si está disponible. |
| JobID | 0 | Id. de trabajo para el progreso. |
| ObjectID | 464 | Identificador de objeto |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | Hora de finalización del evento. |
| Duration | 0 | Cantidad de tiempo (en milisegundos) que tarda el evento. |
| SessionType | User (Usuario) | Tipo de sesión (entidad que ha provocado la operación). |
| ProgressTotal | 0 | Progreso total. |
| IntegerData | 0 | Datos enteros. |
| Severity | 0 | Nivel de gravedad de una excepción. |
| Operación completada correctamente | 1 | 1 = operación completada correctamente. 0 = error (por ejemplo, 1 significa que una comprobación de permisos se realizó correctamente y 0 significa error en dicha comprobación). |
| Error | 0 | Número de error de un evento determinado. |
| ConnectionID | 3 | Id. de conexión única. |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | Identificador del conjunto de datos en el que se ejecuta la instrucción del usuario. |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | GUID de la sesión. |
| SPID | 180 | Id. de proceso de servidor. Identifica una sesión de usuario de manera única. Corresponde directamente al GUID de la sesión que XML/A usa. |
| ClientProcessID | null | El identificador de proceso de la aplicación cliente. |
| ApplicationName | null | Nombre de la aplicación cliente que creó la conexión al servidor. |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | Nombre del recurso de capacidad de Power BI Embedded. |

### <a name="allmetrics"></a>AllMetrics

Al activar la opción **AllMetrics** se registran los datos de todas las métricas que puede usar con un recurso de Power BI Embedded.

En la tabla siguiente se enumeran las operaciones relacionadas con Power BI Embedded que se pueden crear en el registro de actividad.

## <a name="schemas"></a>Esquemas

Power BI Embedded usa el esquema **dedicado de Power BI**.

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Supervisión de Azure Power BI Embedded](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Registros de diagnóstico de recursos de Azure](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting)