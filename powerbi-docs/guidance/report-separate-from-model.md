---
title: Informes independientes de los modelos en Power BI Desktop
description: Instrucciones para separar los informes de los modelos en Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/11/2020
ms.author: v-pemyer
ms.openlocfilehash: f2b9ee2093889fc9a60d621ad09b3b52d2e90474
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2020
ms.locfileid: "91525947"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>Informes independientes de los modelos en Power BI Desktop

Al crear una nueva solución de Power BI Desktop, una de las primeras tareas que debe hacer es obtener los datos. La obtención de los datos puede dar lugar a dos resultados distintos. Podría:

- Crear una [conexión dinámica](../connect-data/desktop-report-lifecycle-datasets.md) a un modelo ya publicado, que puede ser un conjunto de datos de Power BI o un modelo de Analysis Services hospedado de forma remota.
- Iniciar el desarrollo de un nuevo modelo, que puede ser un modelo de importación, DirectQuery o compuesto.

Este artículo está relacionado con el segundo escenario. En él se proporcionan instrucciones sobre si un informe y un modelo deben combinarse en un único archivo de Power BI Desktop.

## <a name="single-file-solution"></a>Solución de un solo archivo

Una _solución de un solo archivo_ funciona bien cuando solo hay un informe basado en el modelo. En este caso, es probable que tanto el modelo como el informe sean producto del esfuerzo de la misma persona. Se define como una solución de _BI personal_, aunque el informe podría compartirse con otros usuarios. Estas soluciones pueden representar informes de ámbito de rol o evaluaciones únicas de un desafío empresarial, que a menudo se describen como _informes ad hoc_.

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="Un único archivo contiene un modelo y un informe, desarrollados por la misma persona." border="true":::

## <a name="separate-report-files"></a>Archivos de informes independientes

Tiene sentido separar el desarrollo del modelo y el informe en archivos de Power BI Desktop independientes cuando:

- Los modeladores de datos y los autores del informe son personas diferentes.
- Se entiende que un modelo será el origen de varios informes, ahora o en el futuro.

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="Un único archivo contiene un modelo y un informe, desarrollados por la misma persona." border="true":::

Los modeladores de datos pueden seguir usando la experiencia de creación de informes de Power BI Desktop para probar y validar sus diseños de modelo. Pero solo después de publicar su archivo en el servicio Power BI podrán quitar el informe del área de trabajo. Además, deben acordarse de quitar el informe cada vez que vuelvan a publicar y sobrescribir el conjunto de datos.

### <a name="preserve-the-model-interface"></a>Conservación de la interfaz de modelo

A veces, los cambios en el modelo son inevitables. Los modeladores de datos deben tener cuidado de no interrumpir la interfaz de modelo. Si lo hacen, es posible que se interrumpan los objetos visuales del informe o los iconos del panel relacionados. Los objetos visuales interrumpidos aparecen como errores y pueden causar frustración a los autores y consumidores de informes. Y, lo que es peor, pueden reducir la confianza en los datos.

Por lo tanto, administre los cambios del modelo con cuidado. Si es posible, evite los cambios siguientes:

- Cambiar el nombre de tablas, columnas, jerarquías, niveles de jerarquía o medidas.
- Modificar tipos de datos de columna.
- Modificar expresiones de medida para que devuelvan un tipo de datos diferente.
- Mover medidas a una tabla inicial diferente. Se debe a que mover una medida podría interrumpir las medidas de ámbito de informe que califican totalmente las medidas con el nombre de la tabla inicial. No se recomienda escribir expresiones DAX mediante nombres de medidas completos. Para obtener más información, consulte [DAX: Referencias de columnas y medidas](dax-column-measure-references.md).

Agregar nuevas tablas, columnas, jerarquías, niveles de jerarquía o medidas es seguro, con una excepción: es posible que un nuevo nombre de medida pueda entrar en conflicto con un nombre de medida de ámbito de informe. Para evitar colisiones, recomendamos que los autores de informes adopten una convención de nomenclatura al definir medidas en sus informes. Pueden prefijar nombres de medidas de ámbito de informe con un guion bajo u otros caracteres.

Si debe realizar cambios importantes en los modelos, se recomienda lo siguiente:

- [Consulte el contenido relacionado con el conjunto de datos](../consumer/end-user-related.md) en el servicio Power BI.
- Explore la vista de [linaje de datos](../collaborate-share/service-data-lineage.md) en el servicio Power BI.

Ambas opciones permiten identificar rápidamente los informes y paneles relacionados. La vista de linaje de datos es probablemente la mejor opción, ya que es fácil ver la persona de contacto para cada artefacto relacionado. De hecho, es un hipervínculo que abre un mensaje de correo electrónico dirigido al contacto en cuestión.

Se recomienda que se ponga en contacto con el propietario de cada artefacto relacionado para informarle de los cambios importantes planeados. De este modo, puede prepararse para corregir y volver a publicar sus informes, lo que ayuda a minimizar el tiempo de inactividad y la frustración.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Conexión a conjuntos de datos del servicio Power BI desde Power BI Desktop](../connect-data/desktop-report-lifecycle-datasets.md)
- [Visualización del contenido relacionado en el servicio Power BI](../consumer/end-user-related.md)
- [Linaje de datos](../collaborate-share/service-data-lineage.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
