---
title: Conexión a datos creados por flujos de datos de Power Platform en Power BI Desktop
description: Conéctese fácilmente a flujos de datos y úselos en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 24635df4a07f0f73a701fcb9d30b5db3ef678666
ms.sourcegitcommit: 7e99e8af9caf9340958c4607a94728d43e8c3811
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2020
ms.locfileid: "91668468"
---
# <a name="connect-to-data-created-by-power-platform-dataflows-in-power-bi-desktop"></a>Conexión a datos creados por flujos de datos de Power Platform en Power BI Desktop
En **Power BI Desktop**, puede conectarse a datos creados por **flujos de datos de Power Platform** al igual que con cualquier otro origen de datos en Power BI Desktop.

![Conectarse a datos](media/desktop-connect-dataflows/connect-dataflows_01.png)

El conector de **flujos de datos de Power Platform** permite conectarse a las entidades creadas por flujos de datos en el servicio Power BI. 

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Para usar el conector de flujos d **Power Platform**, debe ejecutar una versión reciente de **Power BI Desktop**. Siempre puede [descargar Power BI Desktop](../fundamentals/desktop-get-the-desktop.md) e instalarlo en su equipo para asegurarse de que dispone de la versión más reciente.  

> [!NOTE]
> La versión anterior del conector de flujos de datos de Power Platform requiere que descargue un archivo .MEZ y que lo coloque en una carpeta. Las versiones actuales de **Power BI Desktop** incluyen el conector de flujos de datos de Power Platform, de manera que ya no se requiere el archivo y puede causar conflictos con la versión incluida del conector. Si colocó manualmente el archivo .MEZ en la carpeta, *debe* eliminar ese archivo .MEZ descargado de la carpeta **Documentos > Power BI Desktop > Conectores personalizados** para evitar conflictos. 

## <a name="desktop-performance"></a>Rendimiento de Desktop
**Power BI Desktop** se ejecuta localmente en el equipo donde está instalado. El rendimiento de la ingesta de los flujos de datos se determina según una serie de factores. Dichos factores incluyen el tamaño de los datos, la CPU y la RAM del equipo, el ancho de banda de red, la distancia desde el centro de datos y otros factores.

Puede mejorar el rendimiento de la ingesta de datos para los flujos de datos. Por ejemplo, si el tamaño de los datos ingeridos es demasiado grande como para que **Power BI Desktop** los administre en el equipo, puede usar entidades vinculadas y calculadas en los flujos de datos para agregar los datos (dentro de los flujos de datos) e ingerir solo los datos agregados preparados previamente. 

De esa forma, el procesamiento de datos grandes se realiza en línea en los flujos de datos, en lugar de realizarse localmente en la instancia en ejecución de **Power BI Desktop**. Este enfoque permite que Power BI Desktop ingiera cantidades de datos más pequeñas y mantiene la experiencia con los flujos de datos rápida y con capacidad de respuesta.

## <a name="additional-considerations"></a>Consideraciones adicionales

La mayoría de los flujos de datos residen en el inquilino del servicio Power BI. Sin embargo, los usuarios de **Power BI Desktop** no pueden acceder a los flujos de datos almacenados en la cuenta de Azure Data Lake Storage Gen2, a menos que sean propietarios del flujo de datos o que tengan autorización explícita para la carpeta de CDS del flujo de datos. Considere la siguiente situación:

1.  Anna crea un área de trabajo y la configura para almacenar flujos de datos en la instancia de Data Lake de la organización.
2.  Ben, que también es miembro del área de trabajo que ha creado Anna, quiere usar Power BI Desktop y el conector de flujo de datos para obtener datos del flujo de datos que ha creado su compañera.
3.  Ben recibe un error porque no se le ha agregado como usuario autorizado en la carpeta CDM del flujo de datos de la instancia de Data Lake.

Para resolver este problema, Ben debe tener permisos de lector para la carpeta de CDS y sus archivos. Puede aprender más sobre cómo conceder acceso a la carpeta de CDM en [Configuración y consumo de un flujo de datos](dataflows/dataflows-configure-consume.md).




## <a name="next-steps"></a>Pasos siguientes
Hay muchas cosas interesantes que puede hacer con los flujos de datos. Para más información, consulte los siguientes recursos:

* [Introducción a los flujos de datos y la preparación de datos de autoservicio](dataflows/dataflows-introduction-self-service.md)
* [Creación de un flujo de datos](dataflows/dataflows-create.md)
* [Configurar y consumir un flujo de datos](dataflows/dataflows-configure-consume.md)
* [Configuración del almacenamiento de flujo de datos para usar Azure Data Lake Gen 2](dataflows/dataflows-azure-data-lake-storage-integration.md)
* [Características prémium de flujos de datos](dataflows/dataflows-premium-features.md)
* [IA con flujos de datos](dataflows/dataflows-machine-learning-integration.md)


También hay artículos sobre **Power BI Desktop** que pueden resultarle útiles:

* [Orígenes de datos en Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Especificar datos directamente en Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md)