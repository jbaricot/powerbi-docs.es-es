---
title: Orígenes de datos insertados para informes paginados en el servicio Power BI
description: En este artículo, obtendrá información sobre cómo crear y modificar un origen de datos insertado en un informe paginado en el servicio Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 03/02/2020
ms.openlocfilehash: 29ed0a764773c2252989aa05bfcabe5976472d11
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297826"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Creación de un origen de datos insertado para informes paginados en el servicio Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

En este artículo, obtendrá información sobre cómo crear y modificar un origen de datos insertado en un informe paginado en el servicio Power BI. Defina un origen de datos insertado en un único informe y úselo solo en dicho informe. Actualmente, los informes paginados que se publican en el servicio Power BI necesitan conjuntos de datos insertados y orígenes de datos insertados, y se pueden conectar a estos orígenes de datos:

- Azure Analysis Services
- Azure SQL Database y 
- Azure SQL Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

Para los siguientes orígenes de datos, use la opción [Conexión de SQL Server Analysis Services](../admin/service-premium-connect-tools.md):

- Conjuntos de datos de Power BI Premium

Los informes paginados se conectan a los orígenes de datos locales mediante una [puerta de enlace de Power BI](../connect-data/service-gateway-onprem.md). Configure la puerta de enlace después de publicar el informe en el servicio Power BI.

Consulte [Datos del informe en el Generador de informes de Power BI](report-builder-data.md) para más información.

## <a name="create-an-embedded-data-source"></a>Creación de un origen de datos insertados
  
1. Abra el Generador de informes de Power BI.

1. En la barra de herramientas del panel Datos de informe, seleccione **Nuevo** > **Orígenes de datos**. Se abre el cuadro de diálogo **Propiedades del origen de datos** .

   ![Nuevo origen de datos](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
1. En el cuadro de texto **Nombre** , escriba un nombre para el origen de datos o acepte el valor predeterminado.  
  
1. Seleccione **Usar una conexión incrustada en el informe**.  
  
1. En la lista **Seleccionar el tipo de conexión** , seleccione un tipo de origen de datos. 

1. Especifique una cadena de conexión con el uso de alguno de estos métodos:  
  
   - Escriba la cadena de conexión directamente en el cuadro de texto **Cadena de conexión** . 
  
   - Seleccione **Compilar** para abrir el cuadro de diálogo **Propiedades de conexión** para el origen de datos elegido en el paso 2.  
  
     Rellene los campos del cuadro de diálogo **Propiedades de conexión** según corresponda para el tipo de origen de datos. Las propiedades de conexión incluyen el tipo de origen de datos, el nombre del origen de datos, y las credenciales que se deben usar. Después de especificar los valores de este cuadro de diálogo, seleccione **Probar conexión** para comprobar que el origen de datos está disponible y que las credenciales que especificó son correctas.  
  
1. Seleccione **Credenciales**.  
  
   Especifique las credenciales que se deben usar para este origen de datos. El propietario del origen de datos elige el tipo de credenciales que se admiten. Para más información, consulte [Especificar información de credenciales y conexión para los orígenes de datos de informes](/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
1. Seleccione **Aceptar**.  
  
   El origen de datos aparece en el panel Datos de informe.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Los informes paginados que se conectan a los conjuntos de datos de Power BI siguen las reglas para los conjuntos de datos compartidos en Power BI con algunos cambios menores.  Para que los usuarios puedan ver correctamente los informes paginados con conjuntos de datos de Power BI, así como para garantizar que la seguridad en el nivel de fila (RLS) esté habilitada y que se aplique a los usuarios, asegúrese de que sigue estas reglas:

### <a name="classic-apps-and-workspaces"></a>Aplicaciones y áreas de trabajo clásicas

- .rdl en la misma área de trabajo que el conjunto de datos (mismo propietario): Admitido
- .rdl en una área de trabajo distinta a la del conjunto de datos (mismo propietario): Admitido
- .rdl compartido: necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos.
- Aplicación compartida: necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos.
- .rdl en la misma área de trabajo que el conjunto de datos (usuario distinto): Admitido
- .rdl en una área de trabajo distinta a la del conjunto de datos (otro usuario): necesita permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos.
- Seguridad en el nivel de rol: necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos para aplicarla.

### <a name="new-experience-apps-and-workspaces"></a>Nueva experiencia de aplicaciones y áreas de trabajo

- .rdl en la misma área de trabajo que el conjunto de datos: Admitido
- .rdl en una área de trabajo distinta a la del conjunto de datos (mismo propietario): Admitido
- .rdl compartido: necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos.
- Aplicación compartida: necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos.
- .rdl en la misma área de trabajo que el conjunto de datos (usuario distinto): se admite.
- .rdl en una área de trabajo distinta a la del conjunto de datos (usuario distinto): necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos.
- Seguridad en el nivel de rol: necesita un permiso de lectura asignado a cada usuario que esté viendo el informe en el nivel de conjunto de datos para aplicarla.

## <a name="next-steps"></a>Pasos siguientes

- [Creación de un conjunto de datos insertado para un informe paginado en el servicio Power BI](paginated-reports-create-embedded-dataset.md)
- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)