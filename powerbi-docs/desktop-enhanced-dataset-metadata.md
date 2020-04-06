---
title: Uso de metadatos de conjuntos de datos mejorados en Power BI Desktop (versión preliminar)
description: En este artículo se describe cómo usar metadatos de conjunto de datos mejorado en Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 54c3622b0a4dd6c690c2f22a0b93aed39e9d2799
ms.sourcegitcommit: 3c51431d85793b71f378c4b0b74483dfdd8411b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2020
ms.locfileid: "80464635"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>Uso de metadatos de conjunto de datos mejorado (versión preliminar)

Cuando Power BI Desktop crea informes, también crea metadatos de conjunto de datos en los archivos PBIX y PBIT correspondientes. Anteriormente, los metadatos se almacenaban en un formato específico de Power BI Desktop. Se usaban expresiones de M codificadas con Base 64 y orígenes de datos, y se formulaban suposiciones sobre cómo se almacenaban los metadatos.

Con el lanzamiento de la característica **Metadatos del conjunto de datos mejorado**, se quitan muchas de estas limitaciones. Con la característica **Metadatos del conjunto de datos mejorado** habilitada, los metadatos creados por Power BI Desktop usan un formato similar al de los tabulares de Analysis Services, que se basa en el [Modelo de objetos tabulares](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo).


La característica **Metadatos del conjunto de datos mejorado** es estratégica y fundamental, ya que la futura funcionalidad de Power BI se generará en función de sus metadatos. Algunas de las funcionalidades adicionales que se benefician de la característica Metadatos del conjunto de datos mejorado incluyen la [lectura y escritura de XMLA](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite) para la administración de conjuntos de datos de Power BI y la migración de cargas de trabajo de Analysis Services a Power BI para aprovechar las características de próxima generación.



## <a name="enable-enhanced-dataset-metadata"></a>Habilitación de los metadatos de conjuntos de datos mejorados

La característica **Metadatos del conjunto de datos mejorado** se encuentra actualmente en versión preliminar. Para habilitar los metadatos de conjuntos de datos mejorados, en Power BI Desktop, seleccione **Archivo > Opciones y configuración > Opciones > Características en versión preliminar** y, después, active la casilla **Permite almacenar los conjuntos de datos con el formato de metadatos mejorado**, como se muestra en la imagen siguiente. 

![Habilitación de la característica en versión preliminar](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Se le pedirá que reinicie Power BI Desktop.

![Solicitud de reinicio](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

Una vez habilitada la característica de versión preliminar, Power BI Desktop intentará actualizar los archivos PBIX y PBIT que usan el formato de metadatos anterior. 

> [!IMPORTANT]
> La habilitación de la característica de **metadatos mejorados del conjunto de datos** se traduce en una actualización irreversible de los informes. Cualquier informe de Power BI cargado o creado con Power BI Desktop, una vez habilitados los **metadatos mejorados del conjunto de datos**, se convierten de forma irreversible al formato de metadatos mejorados del conjunto de datos.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

En la versión preliminar, se aplican las siguientes limitaciones cuando está habilitada la característica en versión preliminar.

Al abrir un archivo PBIX o PBIT existente que no se ha actualizado, se producirá un error en la actualización si el conjunto de datos contiene cualquiera de las siguientes características o conectores. Si se produce este error, no debería haber ningún impacto inmediato en la experiencia del usuario y Power BI Desktop seguirá usando el formato de metadatos anterior.

* Scripts de Python
* Conectores personalizados
* Azure DevOps Server
* Conector de BI
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* Expresiones M que contienen determinadas combinaciones de caracteres como "\\n" en nombres de columna
* Cuando se usan conjuntos de datos con la característica **Metadatos del conjunto de datos mejorado** habilitada, los orígenes de datos de inicio de sesión único (SSO) no se pueden configurar en el servicio Power BI

Además, los archivos PBIX y PBIT que ya se han actualizado correctamente para usar **Metadatos del conjunto de datos mejorado** *no pueden* usar las características ni los conectores anteriores en la versión actual.


## <a name="next-steps"></a>Pasos siguientes

Puede hacer todo tipo de cosas con Power BI Desktop. Para obtener más información sobre sus capacidades, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](desktop-what-is-desktop.md)
* [Novedades de Power BI Desktop](desktop-latest-update.md)
* [Información general sobre consultas con Power BI Desktop](desktop-query-overview.md)
* [Tipos de datos en Power BI Desktop](desktop-data-types.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tareas de consultas comunes en Power BI Desktop](desktop-common-query-tasks.md)

