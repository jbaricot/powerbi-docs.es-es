---
title: ¿Qué es Power BI Report Server?
description: Obtenga información general de Power BI Report Server para saber cómo se adapta a SQL Server Reporting Services (SSRS) y al resto de servicios de Power BI.
author: maggiesMSFT
ms.author: maggies
keywords: ''
ms.date: 05/28/2020
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: eba3038e654192ca0ae0ec381323762f80cf711a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96397818"
---
# <a name="what-is-power-bi-report-server"></a>¿Qué es Power BI Report Server?

Power BI Report Server es un servidor de informes local con un portal web en el que muestra y administra informes y KPI. Junto con él, se incluyen herramientas para crear informes de Power BI, informes paginados, informes móviles y KPI. Los usuarios pueden acceder a los informes de maneras diferentes: verlos en un explorador web o en un dispositivo móvil, o como un correo electrónico en su bandeja de entrada.

![La captura de pantalla muestra el portal web de Power BI Report Server.](media/get-started/power-bi-report-server-overview.png)

## <a name="comparing-power-bi-report-server"></a>Comparación de Power BI Report Server 
Power BI Report Server es similar a SQL Server Reporting Services y al servicio en línea Power BI, pero con algunas diferencias. Al igual que el servicio Power BI, Power BI Report Server hospeda informes de Power BI (.pbix), archivos de Excel e informes paginados (.rdl). Al igual que Reporting Services, Power BI Report Server se encuentra en el entorno local. Las características de Power BI Report Server son un superconjunto de Reporting Services: todo lo que puede hacer en Reporting Services, puede hacerlo con Power BI Report Server, además de tener compatibilidad con los informes de Power BI. Vea [Comparación de Power BI Report Server y el servicio Power BI](compare-report-server-service.md) para obtener información detallada.

## <a name="licensing-power-bi-report-server"></a>Licencias de Power BI Report Server
Microsoft Power BI Report Server está disponible en dos licencias diferentes: [Power BI Premium](../admin/service-premium-what-is.md) y SQL Server Enterprise Edition con Software Assurance. Consulte [Licencias por Volumen de Microsoft](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=1&ShowArchived=True) para más información. Con una licencia de Power BI Premium, puede crear una implementación híbrida en la que se combine la nube y un entorno local.

Si publica informes de Power BI en Power BI Report Server, también necesitará una licencia de Power BI Pro. Para ver e interactuar con informes de Power BI en Power BI Report Server no necesita una licencia de Power BI Pro.

> [!NOTE]
> Para Power BI Premium, Power BI Report Server solo se incluye con las SKU P. No se incluye con las SKU EM.

## <a name="web-portal"></a>Portal web
El punto de entrada de Power BI Report Server es un portal web seguro que puede ver en cualquier explorador moderno. Aquí, accede a todos los informes y KPI. El contenido del portal web se organiza en una jerarquía de carpetas tradicional. En las carpetas, el contenido se agrupa por tipo: informes de Power BI, informes móviles, informes paginados, KPI y libros de Excel. Los conjuntos de datos y orígenes de datos compartidos se encuentran en sus propias carpetas, que usará como bloques de creación de informes. Etiquete favoritos para verlos en una sola carpeta y cree los KPI directamente en el portal web. 

![La fotografía muestra un equipo portátil que muestra el portal web de Power BI Report Server.](media/get-started/web-portal.png)

Dependiendo de sus permisos, puede administrar el contenido en el portal web. Puede programar el procesamiento de informes, acceder a informes a petición y suscribirse a los informes publicados. Puede aplicar también su propia [marca](/sql/reporting-services/branding-the-web-portal) personalizada al portal web. 

Obtenga más información sobre el [portal web de Power BI Report Server](/sql/reporting-services/web-portal-ssrs-native-mode).

## <a name="power-bi-reports"></a>Informes de Power BI
Cree informes de Power BI (.pbix) con la versión de Power BI Desktop optimizada para el servidor de informes. Después, publíquelos y véalos en el portal web en su propio entorno.

![Informes de Power BI en Power BI Report Server](media/get-started/powerbi-reports.png)

Un informe de Power BI es una vista de varias perspectivas de un modelo de datos, con visualizaciones que representan diferentes hallazgos e información detallada de ese modelo de datos.  Un informe puede tener una sola visualización o páginas enteras de visualizaciones. Dependiendo de su rol, puede leer y explorar los informes, o puede crearlos para otras personas.

Lea sobre la [instalación de Microsoft Power BI Desktop](install-powerbi-desktop.md).

## <a name="paginated-reports"></a>Informes paginados
Los informes paginados (.rdl) son informes con estilo de documento con visualizaciones, en los que las tablas se expanden horizontalmente y verticalmente para mostrar todos sus datos, avanzando de una página a otra según sea necesario. Son excelentes para generar documentos de diseño fijo y apariencia perfecta, optimizados para la impresión, como los archivos PDF y de Word. 

![Informes paginados en Power BI Report Server](media/get-started/paginated-reports.png)

Puede crear informes paginados mediante el [Generador de informes](/sql/reporting-services/report-builder/report-builder-in-sql-server-2016) o el Diseñador de informes en [SQL Server Data Tools (SSDT)](/sql/reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt).

## <a name="reporting-services-mobile-reports"></a>Informes móviles de Reporting Services
Los informes móviles se conectan a datos locales y tienen un diseño dinámico que se adapta a diferentes dispositivos y distintas maneras de contenerlos. Puede crearlos con el Publicador de informes móviles de Microsoft SQL Server.

Obtenga más información sobre los [Informes móviles de Reporting Services](/sql/reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher). 

## <a name="report-server-programming-features"></a>Características de programación del servidor de informes
Saque provecho de las características de programación de Power BI Report Server para que pueda extender y personalizar los informes, con API para integrar o extender el procesamiento de datos e informes en aplicaciones personalizadas.

Más [documentación para desarrolladores del servidor de informes](/sql/reporting-services/reporting-services-developer-documentation).

## <a name="next-steps"></a>Pasos siguientes
[Instalar un servidor de informes de Power BI](install-report-server.md)  
[Descarga del Generador de informes](https://www.microsoft.com/download/details.aspx?id=53613)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)