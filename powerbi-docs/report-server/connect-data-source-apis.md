---
title: Cambio de cadenas de conexión de origen de datos con PowerShell
description: 'Cambio de cadenas de conexión de origen de datos mediante API en PowerShell: Power BI Report Server.'
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: 4e1947abe0fa0f17e1db92619f0aa7fba5df5575
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415482"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>Cambio de cadenas de conexión de origen de datos en informes de Power BI con PowerShell: Power BI Report Server


A partir de la versión de octubre de 2020 de Power BI Report Server, se habilita la capacidad de actualizar las conexiones para informes de Power BI para DirectQuery y actualización.

> [!IMPORTANT]
> Esto también es un cambio importante sobre cómo se podía configurar en versiones anteriores. Si usa una versión de Power BI Report Server anterior a la de octubre de 2020, vea [Cambio de cadenas de conexión de origen de datos en informes de Power BI con PowerShell: Power BI Report Server anterior a octubre de 2020](connect-data-source-apis-pre-oct-2020.md).

## <a name="prerequisites"></a>Requisitos previos:
- Descargue la versión de octubre de 2020 de [Power BI Report Server y Power BI Desktop optimizado para Power BI Report Server](https://powerbi.microsoft.com/report-server/).
- Un informe guardado con la versión de octubre de 2020 de Power BI Desktop optimizado para Report Server, con **Metadatos de conjuntos de datos mejorados** habilitado.
- Un informe en el que se usen conexiones parametrizadas. Después de la publicación solo se pueden actualizar los informes con conexiones parametrizadas y las bases de datos.
- En este ejemplo se usan las herramientas de PowerShell de Reporting Services. Puede lograr lo mismo mediante las nuevas API REST.

## <a name="create-a-report-with-parameterized-connections"></a>Creación de un informe con conexiones parametrizadas
    
1. Cree una conexión de SQL Server a un servidor. En el ejemplo siguiente, se va a conectar al host local a una base de datos denominada ReportServer y a extraer datos de ExecutionLog.

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="Conexión a una base de datos de SQL Server":::

    Este es el aspecto de la consulta de M hasta el momento:

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. Seleccione **Administrar parámetros** en la cinta del Editor de Power Query.

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="Selección de Administrar parámetros":::

1.  Cree parámetros para el nombre del servidor y la base de datos.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="Administración de parámetros, y establecimiento del nombre del servidor y la base de datos.":::


3. Edite la consulta para la primera conexión y asigne el nombre del servidor y la base de datos.

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="Asignación del nombre del servidor y la base de datos":::

    Ahora la consulta tiene este aspecto:

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. Publique el informe en el servidor. En este ejemplo, el nombre del informe es executionlogparameter. La imagen siguiente es un ejemplo de una página de administración de orígenes de datos.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="Página de administración de orígenes de datos.":::

## <a name="update-parameters-using-the-powershell-tools"></a>Actualización de parámetros con las herramientas de PowerShell

1. Abra PowerShell e instale las herramientas de Reporting Services más recientes mediante las instrucciones que se indican en [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools).
    
2.  A fin de obtener el parámetro para el informe, use la nueva API REST DataModelParameters con la siguiente llamada de PowerShell:

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. El resultado de esta llamada se guarda en una variable:

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. Esta variable se actualiza con los valores que se deben cambiar.
5. El resultado de esta llamada se guarda en una variable:

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. Con los valores actualizados, se puede usar el commandlet `Set-RsRestItemDataModelParameters` para actualizar los valores del servidor:

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. Una vez que se han actualizado los parámetros, el servidor actualiza los orígenes de datos que estaban enlazados a los parámetros. De nuevo en el cuadro de diálogo **Editar origen de datos**, debería poder establecer las credenciales para el servidor y la base de datos actualizados.

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="Establezca las credenciales para el servidor y la base de datos actualizados.":::

## <a name="next-steps"></a>Pasos siguientes

[Orígenes de datos de informes paginados en Power BI Report Server](connect-data-sources.md) 

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
