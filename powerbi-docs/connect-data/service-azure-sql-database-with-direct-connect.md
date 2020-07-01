---
title: Azure SQL Database con DirectQuery
description: Azure SQL Database con DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.date: 04/28/2020
LocalizationGroup: Data from databases
ms.openlocfilehash: ffdb18927d5b92ecd10eb4b9e3a3b8fcd921dea2
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230578"
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database con DirectQuery

Obtenga información sobre cómo puede conectarse directamente a Azure SQL Database y crear informes que usan datos activos. Puede mantener los datos en el origen y no en Power BI.

Con DirectQuery, las consultas se envían a Azure SQL Database a medida que explora los datos en la vista de informe. Se sugiere esta experiencia para los usuarios que están familiarizados con las bases de datos y entidades a las que se conectan.

> [!Important]
> En esta descripción se supone que la base de datos de Azure SQL no está detrás de una red virtual ni tiene habilitado el punto de conexión de vínculo privado.

**Notas:**

* Especifique el nombre completo del servidor cuando se conecte (consulte a continuación para obtener más detalles).
* Asegúrese de que las reglas de firewall de la base de datos están configuradas en "[Permitir el acceso a servicios de Azure](https://docs.microsoft.com/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services)".
* Cada acción, como seleccionar una columna o agregar un filtro, enviará una consulta a la base de datos.
* Los iconos se actualizan cada hora (no es necesario programar la actualización). Puede ajustar la frecuencia de actualización en la configuración avanzada al conectarse.
* Preguntas y respuestas no está disponible para conjuntos de datos de DirectQuery.
* Los cambios de esquema no se capturan automáticamente.

Estas restricciones y notas pueden cambiar mientras seguimos mejorando las experiencias. A continuación, se detallan los pasos para conectarse.

> [!Important]
> Hemos mejorado la conectividad con Azure SQL Database.  Use Power BI Desktop para disfrutar de la mejor experiencia de conexión al origen de datos de Azure SQL Database.  Una vez creados el modelo y el informe, puede publicarlos en el servicio Power BI.  El conector directo de Azure SQL Database en el servicio Power BI se encuentra en desuso.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop y DirectQuery

Para conectarse a Azure SQL Database mediante DirectQuery, debe usar Power BI Desktop. Este enfoque proporciona más flexibilidad y capacidades. Los informes creados mediante Power BI Desktop se pueden publicar en el servicio Power BI. Puede obtener más información sobre cómo conectarse a [Azure SQL Database mediante DirectQuery](desktop-use-directquery.md) en Power BI Desktop.

## <a name="find-parameter-values"></a>Búsqueda de valores de parámetro

Puede encontrar el nombre completo del servidor y el nombre de la base de datos en Azure Portal.

![Nueva actualización de Azure Portal](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Actualización de Azure Portal](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](../includes/direct-query-sso.md)]

## <a name="next-steps"></a>Pasos siguientes

* [Usar DirectQuery en Power BI Desktop](desktop-use-directquery.md)  
* [¿Qué es Power BI?](../fundamentals/power-bi-overview.md)  
* [Obtener datos para Power BI](service-get-data.md)  

¿Tiene más preguntas? [Consulte la comunidad de Power BI](https://community.powerbi.com/)
