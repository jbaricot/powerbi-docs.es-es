---
title: Paso de una aplicación de análisis integrados de Power BI a producción para obtener una mejor información de BI insertada
description: Información sobre cuáles son los pasos necesarios para pasar su aplicación de Power BI a la fase de producción Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 71eff0f09c0e34ffd8789f1b56347d754b6589bc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886681"
---
# <a name="move-your-embedded-app-to-production"></a>Paso de una aplicación insertada a producción

Tras terminar de desarrollar la aplicación, para pasarla a producción hay que hacer una copia de seguridad del área de trabajo con una capacidad.

> [!Important]
> Todas las áreas de trabajo (las que contienen los informes o paneles y las que contienen los conjuntos de datos) deben asignarse a una capacidad.

## <a name="create-a-capacity"></a>Creación de una capacidad

Al crear una capacidad, puede aprovechar las ventajas de disponer de un recurso para su cliente. Puede elegir entre dos tipos de capacidades:

* **Power BI Premium**: suscripción de Microsoft 365 de nivel de inquilino disponible en dos familias de SKU, *EM* y *P*. Al insertar contenido de Power BI, se hace referencia a esta solución como *Inserción de Power BI*. Para más información acerca de esta suscripción, consulte [¿Qué es Power BI Premium?](../../admin/service-premium-what-is.md)

* **Azure Power BI Embedded**: puede adquirir una capacidad en [Microsoft Azure Portal](https://portal.azure.com). Esta suscripción utiliza las SKU de tipo *A*. Para obtener más información sobre cómo crear la capacidad de Power BI Embedded, consulte [Creación de una capacidad de Power BI Embedded en Azure Portal](azure-pbie-create-capacity.md).

    > [!NOTE]
    > Con las SKU de tipo A no puede acceder al contenido de Power BI con una licencia gratuita de Power BI.

### <a name="capacity-specifications"></a>Especificaciones de capacidad

En la tabla siguiente se describen los recursos y los límites de cada SKU. Para determinar cuál es la capacidad que mejor se adapta a sus necesidades, consulte la tabla [Qué SKU debo comprar para mi escenario](./embedded-faq.md#which-solution-should-i-choose).

| Nodos de capacidad | Total de núcleos virtuales | Núcleos virtuales de back-end | RAM (GB) | Núcleos virtuales de front-end | Límites de conexiones dinámicas/DirectQuery (por segundo) | Paralelismo de actualización de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>Pruebas de desarrollo

En el caso de las pruebas de desarrollo, puede usar tokens de prueba de inserción con una licencia de Pro. Para realizar inserciones en un entorno de producción, use una capacidad.

El número de tokens de prueba de inserción que puede generar una *entidad de seguridad* o *usuario maestro* (cuenta maestra) del servicio Power BI es limitado. Use la API [Características disponibles](/rest/api/power-bi/availablefeatures/getavailablefeatures) para comprobar el porcentaje del uso insertado actual. La cantidad de uso se muestra por entidad de servicio o por cuenta maestra.

Si se queda sin tokens de inserción durante las pruebas, debe adquirir una [capacidad](embedded-capacity.md) de Power BI Embedded o Premium. No hay ningún límite en cuanto a la cantidad de tokens de inserción que puede generar con una capacidad.

## <a name="assign-a-workspace-to-a-capacity"></a>Asignación de un área de trabajo a una capacidad

Una vez que cree una capacidad, puede asignarle su área de trabajo.

Todas las áreas de trabajo que contengan recursos de Power BI relacionados con contenido insertado (incluidos conjuntos de datos, informes y paneles) deben tener asignadas capacidades. Por ejemplo, si un informe insertado y el conjunto de datos a él enlazado se encuentran en áreas de trabajo diferentes, se deben asignar capacidades a las dos áreas de trabajo.

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>Asignación de un área de trabajo a una capacidad por medio de una entidad de servicio

Para asignar una capacidad a un área de trabajo por medio de una [entidad de servicio](embed-service-principal.md), use la [API REST de Power BI](/rest/api/power-bi/capacities/groups_assigntocapacity). Cuando use las API REST de Power BI, asegúrese de usar el [identificador de objeto de entidad de servicio](embed-service-principal.md).

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>Asignación de un área de trabajo a una capacidad por medio de un usuario maestro

Siga estos pasos para asignar una capacidad a un área de trabajo por medio de un **usuario maestro**.

1. Abra el área de trabajo en el **servicio Power BI**. 

1. En el **servicio Power BI**, expanda las áreas de trabajo y seleccione el botón de puntos suspensivos del área de trabajo en la que quiera insertar contenido. A continuación, seleccione **Editar áreas de trabajo**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="Captura de pantalla que muestra el menú de configuración del área de trabajo en el portal del servicio Power BI":::

2. Seleccione la pestaña **Premium** y haga lo siguiente:

    * Habilite **Capacidad**.

    * Seleccione la capacidad que ha creado.

    * Seleccione **Guardar**.

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="Captura de pantalla que muestra la pestaña de configuración Premium del área de trabajo en el portal del servicio Power BI":::

    Cuando asigne el área de trabajo a una capacidad, aparecerá un diamante junto a ella. 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="Captura de pantalla que muestra el diamante junto a un área de trabajo con una capacidad Premium en el portal del servicio Power BI":::

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Capacidad y SKU de los análisis incrustados de Power BI](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Planeamiento de la capacidad de análisis insertado de Power BI](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[Consideraciones para generar un token de inserción](generate-embed-token.md)