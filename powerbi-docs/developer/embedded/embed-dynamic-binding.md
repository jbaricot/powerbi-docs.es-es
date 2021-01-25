---
title: Conexión de un informe de Power BI a un conjunto de datos mediante el enlace dinámico
description: Aprenda a insertar un informe de Power BI mediante el enlace dinámico de los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 01/17/2021
ms.openlocfilehash: 0bc33ed37e389b42f5c27f8271cc461eb99e229a
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565824"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Conexión de un informe a un conjunto de datos mediante el enlace dinámico 

Cuando un informe está conectado a un conjunto de datos puede usar el enlace dinámico. La conexión entre el informe y el conjunto de datos se conoce como *enlace*. Cuando se determina el enlace en el momento de la inserción, en lugar de hacerlo con anterioridad, este se conoce como enlace dinámico.

Al insertar un informe de Power BI con el *enlace dinámico*, puede conectar el mismo informe a otros conjuntos de datos en función de las credenciales del usuario.

Esto significa que puede usar un informe para mostrar otra información, en función del conjunto de datos al que esté conectado. Por ejemplo, un informe que muestre valores de ventas al por menor puede estar conectado a distintos conjuntos de datos del minorista y producir resultados diferentes en función del conjunto de datos del minorista al que esté conectado.

No es preciso que el informe y el conjunto de datos se encuentren en la misma área de trabajo. Las dos áreas de trabajo (la que contiene el informe y la que contiene el conjuntos de datos) deben asignarse a una [capacidad](azure-pbie-create-capacity.md).

Como parte del proceso de inserción, asegúrese de *generar un token con los permisos suficientes* y *ajustar el objeto de configuración*.

## <a name="generating-a-token-with-sufficient-permissions"></a>Generación de un token con permisos suficientes

El enlace dinámico se admite en los dos escenarios de inserción: *Inserción de contenido para la organización* e *Inserción de contenido para los clientes*. En la tabla siguiente, se describen las consideraciones para cada escenario.

|Escenario  |Propiedad de los datos  |Token  |Requisitos  |
|---------|---------|---------|---------|
|*Inserción de contenido para la organización*    |El usuario posee los datos         |Token de acceso para usuarios de Power BI         |Se usa el usuario que es el token de Azure AD, debe tener los permisos adecuados para todos los artefactos.         |
|*Inserción de contenido para los clientes*     |La aplicación posee los datos         |Token de acceso para usuarios que no usen Power BI         |Se deben incluir permisos tanto para el informe como para el conjunto de datos enlazado dinámicamente. Use la [API para generar un token de inserción para varios elementos](/rest/api/power-bi/embedtoken/generatetoken) con el fin de admitir varios artefactos.         |

## <a name="adjusting-the-config-object"></a>Ajuste del objeto de configuración

Para que el enlace dinámico funcione, debe agregar `datasetBinding` al objeto de configuración. Para obtener información sobre cómo hacerlo, vea [Enlace dinámico de conjuntos de datos a un informe](/javascript/api/overview/powerbi/bind-report-datasets). 

## <a name="next-steps"></a>Pasos siguientes

Si es la primera vez que inserta en Power BI, vea estos tutoriales para aprender a insertar el contenido de Power BI.

>[!div class="nextstepaction"]
>[Inserción del contenido de Power BI en una aplicación para los clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Insertar contenido de Power BI en una aplicación para la organización](embed-sample-for-your-organization.md)