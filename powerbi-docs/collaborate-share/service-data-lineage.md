---
title: Linaje de datos
description: En los proyectos de inteligencia empresarial (BI) modernos, comprender el flujo de datos desde el origen de datos hasta su destino es un desafío clave para muchos clientes.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: 76dd059d59daed5916e9d28692ef018dd7465749
ms.sourcegitcommit: 5bbe7725918a72919ba069c5f8a59e95453ec14c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94946987"
---
# <a name="data-lineage"></a>Linaje de datos
En los proyectos de inteligencia empresarial (BI) modernos, comprender el flujo de datos desde el origen de datos hasta su destino puede ser un desafío. El desafío es incluso mayor si se han creado proyectos analíticos avanzados que abarcan varios orígenes de datos, artefactos y dependencias. Preguntas como "¿Qué ocurre si cambio estos datos?" o bien, "¿Por qué no se ha actualizado este informe?" pueden ser difíciles de responder. Es posible que para entenderlas se necesite un equipo de expertos o una investigación en profundidad. Para ayudarle a responder a estas preguntas se ha diseñado una vista de linaje.

![Vista de linaje de Power BI](media/service-data-lineage/service-data-lineage-view.png)
 
Power BI tiene varios tipos de artefactos, como paneles, informes, conjuntos de datos y flujos de datos. Muchos conjuntos y flujos de datos se conectan a orígenes de datos externos, como SQL Server, y a conjuntos de datos externos en otras áreas de trabajo. Cuando un conjunto de datos es externo a un área de trabajo de su propiedad, puede estar en un área de trabajo que pertenezca a un miembro del departamento de TI o a otro analista. Los orígenes de datos y los conjuntos de datos externos hacen que sea más difícil saber de dónde proceden los datos, en última instancia. Para los proyectos complejos y los más sencillos, se presenta la vista de linaje.

En la vista de linaje, puede ver las relaciones de linaje entre todos los artefactos de un área de trabajo y todas sus dependencias externas. Muestra las conexiones entre todos los artefactos del área de trabajo, incluidas las conexiones a los flujos de datos de entrada, tanto ascendentes como descendentes.    

<iframe width="560" height="315" src="https://www.youtube.com/embed/rUj06dqB98g" frameborder="0" allowfullscreen></iframe>



> [!VIDEO https://youtu.be/rUj06dqB98g]

## <a name="explore-lineage-view"></a>Exploración de la vista de linaje

Todas las áreas de trabajo, ya sean nuevas o clásicas, tienen una vista de linaje. Para verla, necesita al menos un rol de colaborador en el área de trabajo. Para más información, vea [Permisos](#permissions) en este artículo.

* Para acceder a la vista de linaje, vaya a la vista de lista de áreas de trabajo. Pulse la flecha situada junto a **Vista de lista** y seleccione **Vista de linaje**.

   ![Cambio a la vista de linaje](media/service-data-lineage/service-data-lineage-view-select.png)

En esta vista, verá todos los artefactos del área de trabajo y cómo los datos fluyen de un artefacto a otro.

**Orígenes de datos**

Verá los orígenes de datos de los que obtienen sus datos los conjuntos de datos y los flujos de datos. En las tarjetas de origen de datos, verá más información que puede ayudar a identificar el origen. Por ejemplo, para Azure SQL Server, también verá el nombre de la base de datos.

![Origen de datos de vista de linaje sin puerta de enlace](media/service-data-lineage/service-data-lineage-data-source-card.png)
 
**Puertas de enlace**

Si un origen de datos se conecta a través de una puerta de enlace local, la información de la puerta de enlace se agrega a la tarjeta del origen de datos. Si tiene permisos, ya sea como administrador de puerta de enlace o como usuario de origen de datos, verá más información, como el nombre de la puerta de enlace.

![Origen de datos de vista de linaje con puerta de enlace](media/service-data-lineage/service-data-lineage-data-gateway-card.png)

**Conjuntos de datos y flujos de datos**
 
En los conjuntos de datos y flujos de datos, verá la hora de la última actualización, así como si se ha certificado o promovido el conjunto de datos o el flujo de datos.

![Conjuntos de datos promovidos y certificados en la vista de linaje](media/service-data-lineage/service-data-lineage-promoted-certified.png)
 
Si un informe del área de trabajo se basa en un conjunto de datos o flujo de datos ubicado en otra área de trabajo, verá el nombre del área de trabajo de origen en la tarjeta de dicho conjunto de datos o flujo de datos. Seleccione el nombre del área de trabajo de origen para ir hasta esa área de trabajo.

* Para cualquier artefacto, seleccione **Más opciones (...)** para ver el menú de opciones. Incluye en una vista de lista todas las acciones disponibles.

Para ver más metadatos en cualquier artefacto, seleccione la propia tarjeta de artefacto. En un panel lateral se muestra información adicional sobre el artefacto. En la imagen siguiente, el panel lateral muestra los metadatos de un conjunto de datos seleccionado.

![Panel lateral con más información](media/service-data-lineage/service-data-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Representación del linaje de cualquier artefacto 

Imagine que quiere ver el linaje de un artefacto específico.

* Seleccione las flechas dobles situadas debajo del artefacto.

   ![Resaltado del linaje de un artefacto específico](media/service-data-lineage/service-data-lineage-specific-artifact.png)

   Power BI resalta todos los artefactos relacionados con ese artefacto y atenúa el resto. 

## <a name="navigation-and-full-screen"></a>Navegación y pantalla completa 

La vista de linaje es un lienzo interactivo. Puede usar el mouse y el panel táctil para navegar por el lienzo, así como para acercar o alejar la vista.

* Para acercar y alejar la vista, use el menú de la esquina inferior derecha, o bien el mouse o el panel táctil.
* Para tener más espacio para el propio gráfico, use la opción de pantalla completa en la esquina inferior derecha. 

    ![Acercar o alejar, o pantalla completa](media/service-data-lineage/service-data-lineage-zoom.png)

## <a name="permissions"></a>Permisos

* Necesita una licencia de Power BI Pro para ver la vista de linaje.
* La vista de linaje solo está disponible para los usuarios con acceso al área de trabajo.
* Los usuarios deben tener un rol de Administrador, Miembro o Colaborador en el área de trabajo. Los usuarios con un rol de Visor no pueden cambiar a la vista de linaje.


## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

- La vista de linaje no está disponible en Internet Explorer. Vea [Exploradores compatibles con Power BI](../fundamentals/power-bi-browsers.md) para más información.

## <a name="next-steps"></a>Pasos siguientes

* [Introducción a los conjuntos de datos de áreas de trabajo (versión preliminar)](../connect-data/service-datasets-across-workspaces.md)
* [Análisis de impacto para conjuntos de datos](service-dataset-impact-analysis.md)
