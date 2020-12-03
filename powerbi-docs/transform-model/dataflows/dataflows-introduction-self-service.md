---
title: Introducción a los flujos de datos y la preparación de datos de autoservicio
description: Información general sobre los flujos de datos de Power BI y cuándo usarlos
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 5dde70b9834d990987e42c6aa945940a7f110949
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416080"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>Introducción a los flujos de datos y la preparación de datos de autoservicio

A medida que aumenta el volumen de datos, también se complica el desafío de limpiar y transformar dichos datos en información accionable y con un formato correcto. Queremos datos que estén listos para análisis, para rellenar objetos viduales, informes y paneles, a fin de que podamos convertir los volúmenes de datos rápidamente en información procesable. Con la preparación de datos de autoservicio para macrodatos en Power BI, puede convertir los datos en información de Power BI con tan solo unos clics.

![Flujo de datos](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>Cuándo usar los flujos de datos

Los flujos de datos están diseñados para admitir los siguientes escenarios:

* Crear una lógica de transformación reutilizable que puedan compartir muchos conjuntos de datos e informes en Power BI. Los flujos de datos promocionan la reutilización de los elementos de datos subyacentes, lo que evita la necesidad de crear conexiones independientes con los orígenes de datos locales o en la nube.

* Exponer los datos de su propio almacenamiento de Azure Data Lake Gen 2, lo que le permite conectar otros servicios de Azure a los datos subyacentes sin procesar.

* Crear una única fuente de confianza al obligar a los analistas a conectarse a los flujos de datos, en lugar de conectarse a los sistemas subyacentes, lo que le proporciona control sobre los datos a los que se accede y sobre la forma en que se exponen los datos a los creadores de informes. También puede asignar los datos a definiciones estándar del sector, lo que le permite crear vistas organizadas y ordenadas, que pueden funcionar con otros servicios y productos de Power Platform.

* Si quiere trabajar con grandes volúmenes de datos y realizar ETL a escala, los flujos de datos con Power BI Premium se escalan de forma más eficaz y proporcionan más flexibilidad. Los flujos de datos admiten una amplia variedad de orígenes en la nube y locales. 

* Impedir que los analistas tengan acceso directo al origen de datos subyacente. Dado que los creadores de informes pueden basarse en flujos de datos, puede ser más conveniente permitir el acceso a los orígenes de datos subyacentes solo a algunas personas y, después, proporcionar acceso a los flujos de datos para que los analistas se basen en ellos. Este enfoque reduce la carga en los sistemas subyacentes y ofrece a los administradores un mayor control sobre cuándo se cargan los sistemas desde las actualizaciones.

Una vez que ha creado un flujo de datos, puede usar Power BI Desktop y el servicio Power BI para crear conjuntos de datos, informes, paneles y aplicaciones que aprovechan Common Data Model para integrar información detallada en las actividades empresariales. La programación de actualizaciones de los flujos de datos se administra directamente desde el área de trabajo en la que se creó el flujo de datos, al igual que los conjuntos de datos.

## <a name="next-steps"></a>Pasos siguientes
En este artículo se proporciona información general sobre la preparación de datos de autoservicio para macrodatos en Power BI y las numerosas formas en que puede usarse. 

En los artículos siguientes encontrará más información sobre los flujos de datos y Power BI:

* [Creación de un flujo de datos](dataflows-create.md)
* [Configurar y consumir un flujo de datos](dataflows-configure-consume.md)
* [Configuración del almacenamiento de flujo de datos para usar Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Características prémium de flujos de datos](dataflows-premium-features.md)
* [IA con flujos de datos](dataflows-machine-learning-integration.md)
* [Limitaciones y consideraciones de flujos de datos](dataflows-features-limitations.md)
* [Procedimientos recomendados para flujos de datos](dataflows-best-practices.md)


Para más información sobre Common Data Service, puede leer su artículo de introducción:
* [Introducción a Common Data Model](/powerapps/common-data-model/overview)