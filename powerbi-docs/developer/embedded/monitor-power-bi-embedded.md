---
title: Supervisión de Power BI Embedded
description: Comience aquí para obtener información sobre cómo supervisar Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: subject-monitoring
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 5cea43f4be9a3fee7c2fb0f99ef0acef99bb8364
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617005"
---
# <a name="monitor-power-bi-embedded"></a>Supervisión de Power BI Embedded

Si tiene aplicaciones y procesos empresariales críticos que dependen de recursos de Azure, querrá supervisar esos recursos para su disponibilidad, rendimiento y funcionamiento. En este artículo se describen los datos de supervisión generados por Power BI Embedded y cómo puede usar las características de Azure Monitor para analizar estos datos y crear alertas sobre ellos.

## <a name="monitor-overview"></a>Información general de supervisión

La página **Información general** de Azure Portal para cada instancia de *Power BI Embedded* incluye la siguiente información:

* **Grupo de recursos**: el [grupo de recursos](/azure/azure-resource-manager/management/overview#resource-groups) al que pertenece la instancia.
* **Estado**: el estado de la instancia de Power BI Embedded.
* **Ubicación**: la ubicación de la instancia de Power BI Embedded.
* **Nombre de recurso**: el nombre de la instancia de Power BI Embedded.
* **SKU**: la SKU que la instancia de Power BI Embedded utiliza.
* **Nombre de suscripción**: el nombre de la suscripción de la instancia de Power BI Embedded.
* **Id. de suscripción**: el identificador de la suscripción de la instancia de Power BI Embedded.

## <a name="what-is-azure-monitor"></a>¿Qué es Azure Monitor?

*Power BI Embedded* crea los datos de supervisión mediante [Azure Monitor](/azure/azure-monitor/overview), que es un servicio de supervisión de pila completo en Azure, que proporciona un abanico completo de características para supervisar los recursos de Azure, además de los recursos de otras nubes y entornos locales.

Comience leyendo el artículo [Supervisión de recursos de Azure con Azure Monitor](/azure/azure-monitor/insights/monitor-azure-resource), en el que se describen los conceptos siguientes:

- ¿Qué es Azure Monitor?
- Costos asociados con la supervisión
- Datos de supervisión recopilados en Azure
- Configuración de la recolección de datos
- Herramientas estándar en Azure para analizar datos de supervisión y alertar sobre ellos

Las secciones siguientes complementan este artículo mediante la descripción de los datos recopilados para Power BI Embedded. También se proporcionan ejemplos para configurar la recopilación y el análisis de datos con las herramientas de Azure.

## <a name="monitoring-data"></a>Supervisión de datos

Power BI Embedded recopila los mismos tipos de datos de supervisión que otros recursos de Azure que se describen en [Supervisión de datos de recursos de Azure](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources).

Vea [Referencia de datos de supervisión de *Power BI Embedded*](monitor-power-bi-embedded-reference.md) para obtener una referencia detallada de los registros y las métricas creados por Power BI Embedded.

## <a name="collection-and-routing"></a>Recopilación y enrutamiento

Las métricas de la plataforma y el registro de actividad se recopilan y almacenan de forma automática, pero se pueden enrutar a otras ubicaciones mediante una configuración de diagnóstico.  

Los registros de recursos no se recopilan ni almacenan hasta que se crea una configuración de diagnóstico y se enrutan a una o varias ubicaciones.

Consulte [Creación de una configuración de diagnóstico para recopilar registros de plataforma y métricas en Azure](/azure/azure-monitor/platform/diagnostic-settings) para ver el proceso detallado para crear una configuración de diagnóstico mediante el Azure Portal, la CLI o PowerShell. Cuando se crea una configuración de diagnóstico, se especifican las categorías de registros que se van a recopilar. Las categorías de *Power BI Embedded* se muestran en la [Referencia de datos de supervisión de Power BI Embedded](monitor-power-bi-embedded-reference.md#resource-logs).

### <a name="using-powershell-to-enable-diagnostics"></a>Uso de PowerShell para habilitar los diagnósticos

Para habilitar las métricas y el registro de diagnóstico mediante PowerShell, use los comandos mostrados a continuación. Para obtener más información sobre el uso de PowerShell para habilitar el diagnóstico, vea [Crear y configurar el área de trabajo de Log Analytics en Azure Monitor con PowerShell](/azure/azure-monitor/platform/powershell-workspace-configuration).

* Para habilitar el almacenamiento de registros de diagnóstico en una cuenta de almacenamiento, use este comando:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    El identificador de la cuenta de almacenamiento es el identificador de recurso para la cuenta de almacenamiento donde desea enviar los registros.

* Para habilitar el streaming de los registros de diagnóstico a un centro de eventos, use este comando:

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* El identificador de regla de Azure Service Bus es una cadena con este formato:

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* Para habilitar el envío de registros de diagnóstico a un área de trabajo de Log Analytics, use este comando:

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* Puede obtener el identificador de recurso del área de trabajo de Log Analytics con el comando siguiente:

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

Puede combinar estos parámetros para habilitar varias opciones de salida.

En las secciones siguientes se describen las métricas y los registros que se pueden recopilar.

## <a name="analyzing-metrics"></a>Análisis de métricas

Puede analizar las métricas de *Power BI Embedded* con métricas de otros servicios de Azure mediante el explorador de métricas; para ello, abra **Métricas** en el menú de **Azure Monitor**. Consulte [Introducción al explorador de métricas de Azure](/azure/azure-monitor/platform/metrics-getting-started) para más información sobre esta herramienta.

Para obtener una lista de las métricas de la plataforma recopiladas para Power BI Embedded, vea [Métricas de referencia de los datos de supervisión de *Power BI Embedded*](monitor-power-bi-embedded-reference.md#metrics).  

Como referencia, puede ver una lista de [todas las métricas de recursos que se admiten en Azure Monitor](/azure/azure-monitor/platform/metrics-supported).

## <a name="analyzing-logs"></a>Análisis de datos

Los datos de los registros de Azure Monitor se almacenan en tablas, cada una con un conjunto propio de propiedades únicas.  

Todos los registros de recursos de Azure Monitor tienen los mismos campos seguidos de campos específicos del servicio. El esquema común se describe en el [esquema de registros de recursos de Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema). El esquema de los registros de recursos de Power BI Embedded se basa en la [Referencia de datos de Power BI Embedded](monitor-power-bi-embedded-reference.md#schemas).

El [registro de actividad](/azure/azure-monitor/platform/activity-log) es un registro de plataforma de Azure que proporciona conclusiones sobre los eventos del nivel de suscripción. Puede verlo de forma independiente o enrutarlo a registros de Azure Monitor, donde puede realizar consultas mucho más complejas mediante Log Analytics.  

Para obtener una lista de los tipos de registros de recursos recopilados para Power BI Embedded, vea [Referencia de datos de supervisión de Power BI Embedded](monitor-power-bi-embedded-reference.md#resource-logs).  

Para obtener una lista de las tablas utilizadas por los registros de Azure Monitor y en la que Log Analytics puede realizar consultas, vea [Referencia de datos de supervisión de Power BI Embedded](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables).  

### <a name="sample-kusto-queries"></a>Ejemplos de consultas de Kusto

> [!IMPORTANT]
> Al seleccionar **Registros** en el menú de Power BI Embedded, Log Analytics se abre con el ámbito de la consulta establecido en el recurso de Power BI Embedded actual. Esto significa que las consultas de registro solo incluirán datos de ese recurso. Si desea ejecutar una consulta que incluya datos de otro recurso de Power BI Embedded o de otros servicios de Azure, seleccione **Registros** en el menú de **Azure Monitor**. Consulte [Ámbito e intervalo de tiempo de una consulta de registro en Log Analytics de Azure Monitor](/azure/azure-monitor/log-query/scope/) para obtener más información.

A continuación, se muestran ejemplos de consultas para la supervisión de Power BI Embedded.

* Se trata de una consulta que se completa en menos de 5 minutos (300 000 milisegundos).

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* Identifique los nombres de capacidad.

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>Alertas

Las alertas de Azure Monitor le informan de forma proactiva cuando se detectan condiciones importantes en los datos que se supervisan. Permiten identificar y solucionar las incidencias en el sistema antes de que los clientes puedan verlos. Puede establecer alertas en [métricas](/azure/azure-monitor/platform/alerts-metric-overview), [registros](/azure/azure-monitor/platform/alerts-unified-log) y el [registro de actividad](/azure/azure-monitor/platform/activity-log-alerts).

## <a name="next-steps"></a>Pasos siguientes

Puede obtener más información sobre el registro de diagnóstico de recursos de Azure.

>[!div class="nextstepaction"]
>[Referencia de datos de supervisión de Power BI Embedded](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[Supervisión de recursos de Azure con Azure Monitor](/azure/azure-monitor/insights/monitor-azure-resource)
