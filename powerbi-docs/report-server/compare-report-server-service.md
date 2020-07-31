---
title: Comparación de Power BI Report Server y el servicio Power BI
description: En este artículo se comparan las características de Power BI Report Server y del servicio Power BI.
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 07/27/2020
ms.openlocfilehash: c91642a08642a52b333ccba14078068eaa9ba616
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "87252875"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Comparación de Power BI Report Server y el servicio Power BI

Power BI Report Server y el servicio Power BI tienen muchas similitudes y algunas diferencias clave. En esta tabla se explican cuáles son.

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Características de Power BI Report Server y el servicio Power BI

| Características | Power BI Report Server | Servicio Power BI | Notas |
|---------|---------|---------|---------|
| Implementación | Local u hospedada en la nube | Nube | Power BI Report Server se puede implementar en máquinas virtuales de Azure (implementación hospedada en la nube) si tiene licencia de Power BI Premium o SQL Server Enterprise con Software Assurance.|
| Datos de origen | Nube o local | Nube o local |  |
| Licencia | Power BI Premium o SQL Server EE con Software Assurance (SA) | Power BI Pro o Power BI Premium | |  
| Ciclo de vida | Directiva de ciclo de vida moderna | Servicio totalmente administrado |  |
| Ciclo de versiones | Tres veces al año (enero, mayo, septiembre) | Una vez al mes | Las últimas características y correcciones primero se incorporan en el servicio Power BI. Un paquete acumulativo de características de las versiones de Power BI Desktop para el servicio llega a Power BI Report Server en cada versión; la mayoría de las otras características solo están destinadas al servicio Power BI. |
| Crear informes de Power BI en Power BI Desktop | Sí | Sí |  |
| Crear informes de Power BI en el explorador | No | Sí |  |
| Hospedar y conectarse a conjuntos de datos compartidos de Power BI | No | Sí | [Introducción a los conjuntos de datos de áreas de trabajo](../connect-data/service-datasets-across-workspaces.md) |
| Se requiere una puerta de enlace | No | Sí para orígenes de datos locales |  |
| Streaming en directo | No | Sí | [Streaming en directo en Power BI](../connect-data/service-real-time-streaming.md) |
| Paneles | No | Sí | [Paneles en el servicio Power BI](../consumer/end-user-dashboards.md) |
| Distribuir grupos de informes con aplicaciones | No | Sí | [Crear y publicar aplicaciones con los paneles e informes](../collaborate-share/service-create-distribute-apps.md) |
| Paquetes de contenido | No | Sí | [Paquetes de contenido organizativo: Introducción](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Conectarse a servicios como Salesforce | Sí | Sí | [Conéctese a los servicios que usa](../connect-data/service-connect-to-services.md) con paquetes de contenido en el servicio Power BI. En Power BI Report Server, use conectores certificados para conectarse a los servicios. Vea [Orígenes de datos de los informes de Power BI en Power BI Report Server](data-sources.md) para obtener más información. |
| Preguntas y respuestas | No | Sí | [Preguntas y respuestas en el servicio Power BI y Power BI Desktop](../create-reports/power-bi-tutorial-q-and-a.md) 
| Información rápida | No | Sí | [Generación automática de información sobre los datos con Power BI](../consumer/end-user-insights.md) |
| Analizar en Excel | No | Sí | [Analizar en Excel](../collaborate-share/service-analyze-in-excel.md) 
| Informes paginados | Sí | Sí | Los [informes paginados están disponibles en el servicio Power BI](../paginated-reports/paginated-reports-report-builder-power-bi.md), en la versión preliminar en una capacidad Premium. |
| Aplicaciones móviles de Power BI | Sí | Sí | [Información general sobre aplicaciones móviles de Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| Mapas de ArcGIS | No | Sí | [Tutorial de mapas de ArcGIS de Esri en el servicio Power BI y Power BI Desktop](../visuals/power-bi-visualization-arcgis.md) |
| Suscripciones de correo electrónico para los informes de Power BI | No | Sí | [Suscripción personal o de otros usuarios](../collaborate-share/service-report-subscribe.md) a un informe o panel en el servicio Power BI |
| Suscripciones de correo electrónico para informes paginados | Sí | Sí | [Suscripción personal y de otros usuarios a informes paginados en el servicio Power BI](../consumer/paginated-reports-subscriptions.md)<br><br>[Entrega de correo electrónico en Reporting Services](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal)  |
| Alertas de datos | No | Sí | [Alertas de datos](../create-reports/service-set-data-alerts.md) en el servicio Power BI
| Seguridad de nivel de fila (RLS) | Sí | Sí | Disponible en DirectQuery (origen de datos) y en el modo de importación <br><br>Seguridad de nivel de fila (RLS) en el [servicio Power BI](../admin/service-admin-rls.md) <br><br>Seguridad de nivel de fila (RLS) en [Power BI Report Server](row-level-security-report-server.md) |
| Obtención de detalles de varios informes | No | Sí | [Uso de la obtención de detalles de varios informes](../create-reports/desktop-cross-report-drill-through.md) |
| Modo de pantalla completa | No | Sí | [Modo de pantalla completa](../consumer/end-user-focus.md) en el servicio Power BI |
| Colaboración de Microsoft 365 avanzada | No | Sí | [Colaboración en un área de trabajo](../collaborate-share/service-collaborate-power-bi-workspace.md) con Microsoft 365 |
| Scripts y objetos visuales de R | No | Sí | [Cree objetos visuales de R](../create-reports/desktop-r-visuals.md) y ejecute scripts de R en Power BI Desktop, y publíquelos en el servicio Power BI. No se pueden guardar los informes de Power BI con objetos visuales o scripts de R en Power BI Report Server.  |
| Scripts y objetos visuales de Python | No | Sí | [Cree scripts de Python](../connect-data/desktop-python-scripts.md) y objetos visuales en Power BI Desktop y publíquelos en el servicio Power BI. No se pueden guardar los informes de Power BI con objetos visuales o scripts de Python en Power BI Report Server. |
| Características en vista previa | No | Sí | [Participación en las características de versión preliminar del servicio Power BI](../consumer/end-user-preview-features.md) |
| Objetos visuales de Power BI | Sí | Sí | [Objetos visuales de Power BI](../developer/visuals/power-bi-custom-visuals.md) |
| Modelos compuestos | No | Sí |
| Power BI Desktop | Versión optimizada para Report Server, disponible para su descarga con Report Server | Versión optimizada para el servicio Power BI, disponible desde Microsoft Store | [Power BI Desktop para Report Server](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI Desktop para el servicio Power BI](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>Pasos siguientes

[Instalar un servidor de informes de Power BI](install-report-server.md)






