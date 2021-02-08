---
title: 'Cambio de cadenas de conexión de origen de datos con PowerShell: Power BI Report Server anterior a octubre de 2020'
description: 'Cambie cadenas de conexión de origen de datos mediante API en PowerShell: Power BI Report Server anterior a octubre de 2020.'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: f0dd30e721d8325fdbfd8b562083fbedef2af9c0
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044204"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server-pre-october-2020"></a>Cambio de cadenas de conexión de origen de datos en informes de Power BI con PowerShell: Power BI Report Server anterior a octubre de 2020


Puede cambiar las cadenas de conexión de origen de datos de los informes de Power B hospedados en Power BI Report Server usando PowerShell para interactuar con las API necesarias. 

> [!IMPORTANT]
> Si usa la versión más reciente de Power BI Report Server, consulte [Cambio de cadenas de conexión de origen de datos en informes de Power BI con PowerShell: Power BI Report Server](connect-data-source-apis.md).

> [!NOTE]
> Actualmente, esta funcionalidad solo funciona para DirectQuery. La compatibilidad con la importación y la actualización de datos estará disponible próximamente.

1. Instale los commandlets de PowerShell de Power BI Report Server. Busque los commandlets y las instrucciones de instalación en [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools). 

    Instale el módulo `ReportingServicesTools` directamente desde la [Galería de PowerShell](https://www.powershellgallery.com/packages/ReportingServicesTools/) usando el siguiente comando.

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. Capture la información del origen de datos existente para el archivo de Power BI a través de commandlets de PowerShell:

    ```powershell
    $dataSources = Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    Para ver información del primer origen de datos contenido en el informe de Power BI: 

    ```powershell
    $dataSources[0]
    ```

3. Actualice la información de conexión y las credenciales según sea necesario. Si al actualizar la cadena de conexión y el origen de datos se usan las credenciales almacenadas, debe proporcionar la contraseña de la cuenta. 

    Para actualizar una cadena de conexión de origen de datos:

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    Para cambiar el tipo de credencial del origen de datos:

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    Para cambiar el nombre de usuario y la contraseña del origen de datos:

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. Vuelva a guardar las credenciales actualizadas en el servidor.

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>Pasos siguientes

[Orígenes de datos de informes paginados en Power BI Report Server](connect-data-sources.md) 

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
