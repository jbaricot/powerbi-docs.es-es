---
title: Conjuntos de datos grandes en Power BI Premium
description: El formato de almacenamiento de conjuntos de datos grandes posibilita que los conjuntos de datos de Power BI Premium tengan más de 10 GB de tamaño.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 12/04/2020
ms.custom: references_regions
LocalizationGroup: Premium
ms.openlocfilehash: 1f9a34b68f465eda5b8921e48576c9bef5d17f36
ms.sourcegitcommit: 0bf42b6393cab7a37d21a52b934539cf300a08e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2020
ms.locfileid: "96781715"
---
# <a name="large-datasets-in-power-bi-premium"></a>Conjuntos de datos grandes en Power BI Premium

Los conjuntos de datos de Power BI pueden almacenar datos en una memoria caché en memoria muy comprimida para optimizar el rendimiento de las consultas, a fin de permitir una rápida interactividad del usuario. Gracias a las capacidades Premium, se pueden habilitar conjuntos de datos grandes que superen el límite predeterminado de 10 GB por medio de la opción **Formato de almacenamiento de conjunto de datos de gran tamaño**. Si esta opción se habilita, el tamaño de los conjuntos de datos estará limitado por el tamaño de la *capacidad* Premium.

Los conjuntos de datos grandes se pueden habilitar para todas las SKU P de la versión Premium y las SKU A de la versión Embedded. El límite de tamaño de los conjuntos de datos grandes en Premium es comparable al de Azure Analysis Services en cuanto a la limitación del tamaño del modelo de datos.

Aunque es necesario que los conjuntos de datos tengan más de 10 GB, habilitar la opción Formato de almacenamiento de conjunto de datos de gran tamaño reporta más ventajas. Si tiene previsto usar herramientas basadas en puntos de conexión XMLA para realizar operaciones de escritura en el conjunto de datos, procure habilitar esta opción, incluso en el caso de aquellos conjuntos de datos que no se caractericen necesariamente por ser un conjunto de datos *grande*. Si se habilita, el formato de almacenamiento de conjuntos de datos grandes puede mejorar el rendimiento de las operaciones de escritura de XMLA.

Los conjuntos de datos grandes del servicio no afectan al tamaño de carga de modelos de Power BI Desktop, que sigue estando restringido a 10 GB. En su lugar, los conjuntos de datos pueden crecer más de 10 GB en el servicio al actualizarse.

## <a name="enable-large-datasets"></a>Habilitar conjuntos de datos grandes

Con estos pasos se explica cómo habilitar conjuntos de datos grandes para un modelo nuevo publicado en el servicio. Respecto a los conjuntos de datos existentes, solo es necesario el paso tres.

1. Cree un modelo en Power BI Desktop. Si el conjunto de datos va a ir creciendo y consumiendo más memoria progresivamente, asegúrese de configurar la opción [Actualización incremental](service-premium-incremental-refresh.md).

1. Publique el modelo como un conjunto de datos en el servicio.

1. En servicio > conjunto de datos > **Configuración**, expanda **Formato de almacenamiento de conjunto de datos de gran tamaño**, haga clic en el control deslizante para **activarlo** y, después, haga clic en **Aplicar**.

    :::image type="content" source="media/service-premium-large-models/enable-large-dataset.png" alt-text="Habilitar el control deslizante de conjuntos de datos grandes":::

1. Invoque una actualización para cargar los datos históricos basada en la directiva de actualización incremental. La primera actualización podría tardar bastante tiempo en cargar el historial. Las actualizaciones posteriores deberían ser más rápidas, dependiendo de cómo sea su directiva de actualización incremental.

## <a name="set-default-storage-format"></a>Establecer el formato de almacenamiento predeterminado

Todos los conjuntos de datos nuevos que se creen en un área de trabajo asignada a una capacidad Premium pueden tener habilitado el formato de almacenamiento de conjuntos de datos grandes de forma predeterminada.

1. En el área de trabajo, haga clic en **Configuración** > **Premium**.

1. En **Formato de almacenamiento predeterminado**,seleccione **Formato de almacenamiento de conjunto de datos de gran tamaño** y, después, haga clic en **Guardar**.

    :::image type="content" source="media/service-premium-large-models/default-storage-format.png" alt-text="Habilitar el formato de almacenamiento predeterminado":::

### <a name="enable-with-powershell"></a>Habilitar con PowerShell

El formato de almacenamiento de los conjuntos de datos grandes también se puede habilitar con PowerShell. Debe tener privilegios de administrador de áreas de trabajo y de la capacidad para ejecutar los cmdlets de PowerShell.

1. Busque el identificador del conjunto de datos (GUID). En la pestaña **Conjuntos de datos** del área de trabajo, en la configuración del conjunto de datos, puede ver el identificador en la dirección URL.

    ![GUID del conjunto de datos](media/service-premium-large-models/dataset-guid.png)

1. En un símbolo del sistema de administrador de PowerShell, instale el módulo [MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/).

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. Ejecute los siguientes cmdlets para iniciar sesión y comprobar el modo de almacenamiento del conjunto de datos.

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    La respuesta será la siguiente. El modo de almacenamiento es ABF (archivo de copia de seguridad de Analysis Services), que es el valor predeterminado.

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. Ejecute los siguientes cmdlets para establecer el modo de almacenamiento. La conversión a Azure Files Premium puede tardar unos segundos.

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    La respuesta será la siguiente. El modo de almacenamiento ahora está establecido en Azure Files Premium.

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

Puede comprobar el estado de las conversiones del conjunto de datos hacia y desde Azure Files Premium con el cmdlet [Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus).

## <a name="dataset-eviction"></a>Expulsión del conjunto de datos

Power BI usa la administración dinámica de la memoria para expulsar los conjuntos de datos inactivos de la memoria. Power BI expulsa los conjuntos de datos para poder cargar otros conjuntos de datos para direccionar las consultas de los usuarios. La administración dinámica de la memoria permite que la suma de los tamaños de los conjunto de datos sea bastante mayor que la memoria disponible en la capacidad, pero debe caber un solo conjunto de datos en la memoria. Para más información sobre la administración dinámica de la memoria, consulte [Funcionamiento de las capacidades](service-premium-what-is.md#how-capacities-function).

Tenga en cuenta el impacto de la expulsión en los modelos grandes. A pesar de los tiempos de carga de conjuntos de datos relativamente rápidos, los usuarios podrían notar un retraso considerable si tienen que esperar a que se recarguen los conjuntos de datos grandes expulsados. Por esta razón, en su forma actual, se recomienda usar la característica de modelos grandes principalmente para las capacidades dedicadas a los requisitos de inteligencia empresarial en lugar de a capacidades mixtas con requisitos de inteligencia empresarial con características de autoservicio. Las capacidades dedicadas a los requisitos de inteligencia empresarial son menos propensas a desencadenar expulsiones y por lo que no necesitan volver a cargar los conjuntos de datos con tanta frecuencia. Por otro lado, las capacidades de inteligencia empresarial con características de autoservicio pueden tener muchos conjuntos de datos pequeños que se cargan con más frecuencia dentro y fuera de la memoria.

## <a name="checking-dataset-size"></a>Comprobación del tamaño del conjunto de datos

Después de cargar los datos históricos, puede usar [SSMS](/sql/ssms/download-sql-server-management-studio-ssms) a través del [punto de conexión de XMLA](service-premium-connect-tools.md) para comprobar el tamaño estimado del conjunto de datos en la ventana de propiedades del modelo.

![Tamaño estimado del conjunto de datos](media/service-premium-large-models/estimated-dataset-size.png)

Para comprobar el tamaño del conjunto de datos, también puede ejecutar las siguientes consultas DMV desde SSMS. Sume las columnas DICTIONARY\_SIZE y USED\_SIZE de la salida para ver el tamaño del conjunto de datos en bytes.

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Tenga en cuenta las siguientes restricciones cuando use conjuntos de datos grandes:

- **Se necesitan áreas de trabajo nuevas**: los conjuntos de datos grandes solo funcionan con [áreas de trabajo nuevas](../collaborate-share/service-create-the-new-workspaces.md).

- **Descarga en Power BI Desktop**: si un conjunto de datos se almacena en Files Premium, se producirá un error al [descargar como archivo .pbix](../create-reports/service-export-to-pbix.md).
- **Regiones admitidas**: los conjuntos de datos grandes se pueden usar en todas las regiones de Azure que admitan el almacenamiento de archivos Premium. Para más información, vea [Productos disponibles por región](https://azure.microsoft.com/global-infrastructure/services/?products=storage) y consulte la tabla de la siguiente sección.

## <a name="region-availability"></a>Disponibilidad en regiones

Los conjuntos de datos grandes de Power BI solo están disponibles en determinadas regiones de Azure que admiten [Azure Premium Files Storage](/azure/storage/files/storage-files-planning#storage-tiers).

En la siguiente lista se indican las regiones en las que hay disponibles conjuntos de datos grandes en Power BI. Las regiones que no están en la lista siguiente no se admiten para los modelos grandes:

|Región de Azure  |Abreviatura de la región de Azure  |
|---------|---------|
|Este de Australia     | australiaeast        |
|Sudeste de Australia     | australiasoutheast        |
|Centro de EE. UU.     | centralus        |
|Este de Asia     | eastasia        |
|Este de EE. UU.     | estado        |
|Este de EE. UU. 2     | eastus2        |
|Japón Oriental     | japaneast        |
|Japón Occidental     | japanwest        |
|Centro de Corea del Sur     | koreacentral        |
|Corea del Sur     | koreasouth        |
|Centro-Norte de EE. UU     | northcentralus        |
|Norte de Europa     | northeurope        |
|Centro-sur de EE. UU.     | southcentralus        |
|Sudeste de Asia     | southeastasia        |
|Sur de Reino Unido     | uksouth        |
|Oeste de Reino Unido     | ukwest        |
|Oeste de Europa     | westeurope        |
|Oeste de EE. UU.     | westus        |
|Oeste de EE. UU. 2     | westus2        |

## <a name="next-steps"></a>Pasos siguientes

Los vínculos siguientes proporcionan información que puede ser útil para trabajar con modelos grandes:

* [Azure Premium Files Storage](/azure/storage/files/storage-files-planning#storage-tiers)
* [Configuración de compatibilidad con Multi-Geo en Power BI Premium](service-admin-premium-multi-geo.md)
* [Sus propias claves de cifrado para Power BI](service-encryption-byok.md)
* [Cómo funcionan las capacidades](service-premium-what-is.md#how-capacities-function)
* [Actualización incremental](service-premium-incremental-refresh.md)

Power BI ha introducido Power BI Premium Gen2 como una oferta en versión preliminar, lo que mejora la experiencia con Power BI Premium mediante mejoras en los siguientes aspectos:
* Rendimiento
* Concesión de licencias por usuario
* Mayor escala
* Métricas mejoradas
* Escalado automático
* Menor sobrecarga de administración

Para más información sobre Power BI Premium Gen2, vea [Power BI Premium Generation 2 (versión preliminar)](service-premium-what-is.md#power-bi-premium-generation-2-preview).
