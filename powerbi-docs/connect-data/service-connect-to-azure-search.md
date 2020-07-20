---
title: Conexión a Azure Search con Power BI
description: Azure Search para Power BI
author: SarinaJoan
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 11389b5986d0dd627b0077808a74db5ab2769a65
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216304"
---
# <a name="connect-to-azure-search-with-power-bi"></a>Conexión a Azure Search con Power BI
Azure Search Traffic Analytics permite supervisar y comprender el tráfico al servicio Azure Search. El paquete de contenido de Azure Search para Power BI proporciona información detallada sobre los datos de búsqueda, que incluye la búsqueda, la indexación, las estadísticas del servicio y la latencia de los últimos 30 días. Puede encontrar más detalles en la [entrada de blog de Azure](https://azure.microsoft.com/blog/analyzing-your-azure-search-traffic/).

[!INCLUDE [include-short-name](../includes/service-deprecate-content-packs.md)]

Conéctese al [paquete de contenido de Azure Search](https://app.powerbi.com/getdata/services/azure-search) para Power BI.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación.
   
   ![Captura de pantalla de Obtener datos de Power BI Desktop, donde se muestra el botón del panel de navegación.](media/service-connect-to-azure-search/pbi_getdata.png) 
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Servicios, en el que se muestra el botón Obtener.](media/service-connect-to-azure-search/pbi_getservices.png) 
3. Seleccione **Azure Search** \> **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Servicios de Azure, en el que se muestra el vínculo Obtener.](media/service-connect-to-azure-search/azuresearch.png)
4. Proporcione el nombre de la cuenta de Table Storage donde está almacenado el análisis de Azure Search.
   
   ![Captura de pantalla del cuadro de diálogo Conectar con Azure Search, donde se muestra el campo Nombre de la cuenta de almacenamiento de Azure.](media/service-connect-to-azure-search/params.png)
5. Seleccione **Clave** como mecanismo de autenticación y proporcione la clave de cuenta de almacenamiento. Haga clic en **Iniciar sesión** e inicie el proceso de carga.
   
   ![Captura de pantalla del cuadro de diálogo Conectar con Azure Search, en el que se muestra que se ha escrito Clave en el campo Método de autenticación.](media/service-connect-to-azure-search/creds.png)
6. Cuando se complete la carga, aparecerán un nuevo panel, un informe y un modelo en el panel de navegación. Seleccione el panel para ver los datos importados.
   
    ![Captura de pantalla del panel de navegación, en la que muestran el panel, el informe y el modelo.](media/service-connect-to-azure-search/dashboard2.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](../consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](../create-reports/service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](../consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="system-requirements"></a>Requisitos del sistema
El paquete de contenido de Azure Search requiere que Azure Search Traffic Analytics esté habilitado en la cuenta.

## <a name="troubleshooting"></a>Solución de problemas
Asegúrese de que el nombre de la cuenta de almacenamiento esté correctamente indicada junto con la clave de acceso completa. El nombre de la cuenta de almacenamiento debe corresponder a la cuenta configurada con Azure Search Traffic Analytics.

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](../fundamentals/power-bi-overview.md)

[Conceptos básicos para diseñadores en el servicio Power BI](../fundamentals/service-basic-concepts.md)
