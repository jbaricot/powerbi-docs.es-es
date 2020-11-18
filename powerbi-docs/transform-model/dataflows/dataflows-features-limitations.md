---
title: Limitaciones, restricciones, conectores admitidos y características de los flujos de datos
description: Información general de todas las funcionalidades de los flujos de datos
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 2d58fe71b7ceb27afe5d52a55ed57ae162622b06
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668175"
---
# <a name="dataflows-limitations-and-considerations"></a>Limitaciones y consideraciones de flujos de datos

Existen algunas limitaciones en los flujos de entrada en cuanto a la creación, las actualizaciones y la administración de capacidades que los usuarios deben tener en cuenta, como se describe en las secciones siguientes.

## <a name="dataflow-authoring"></a>Creación de flujos de entrada

Al crear flujos de datos, los usuarios deben tener en cuenta lo siguiente:

* La creación de flujos de datos se realiza en el entorno de Power Query Online (PQO); consulte las limitaciones que se describen en [Límites de Power Query](/power-query/power-query-online-limits).
Dado que la creación de flujos de datos se realiza en el entorno de Power Query Online (PQO), las actualizaciones realizadas en las configuraciones de la carga de trabajo de flujos de datos solo afectan a las actualizaciones, y no a la experiencia de creación.

* Los flujos de datos solo pueden ser modificarlos sus propietarios.

* Los flujos de datos no están disponibles en *Mi área de trabajo*.

* Los flujos de datos que usan orígenes de datos de puerta de enlace no admiten varias credenciales para el mismo origen de datos.

* Para usar el conector Web.Page, se requiere una puerta de enlace.

## <a name="api-considerations"></a>Consideraciones sobre las API

Se puede encontrar más información sobre las API REST de flujos de datos en la [referencia de la API REST](/rest/api/power-bi/dataflows). Estas son algunos aspectos que se deben tener en cuenta:

* Al exportar e importar un flujo de datos, ese flujo de datos recibe un nuevo identificador.

* La importación de flujos de datos que contienen entidades vinculadas no corregirá las referencias existentes en el flujo de datos (estas consultas deben corregirse manualmente antes de importar el flujo de datos).

* Los flujos de datos se pueden sobrescribir con el parámetro *CreateOrOverwrite*, si se han creado inicialmente mediante la API de importación.

## <a name="dataflows-in-shared"></a>Flujos de datos en uso compartido

Existen limitaciones para los flujos de datos con capacidades compartidas:

* Al actualizar los flujos de datos, los tiempos de espera en uso compartido son de 2 horas por entidad y de 3 horas por flujo de datos.
* No se pueden crear entidades vinculadas en flujos de datos compartidos, si bien pueden existir en ellos mientras la propiedad *Load Enabled* (Carga habilitada) de la consulta esté deshabilitada
* No se pueden crear entidades calculadas en flujos de datos compartidos.
* Los servicios AutoML y Cognitive no están disponibles en los flujos de datos compartidos.
* La actualización incremental no funciona en los flujos de datos compartidos.

## <a name="dataflows-in-premium"></a>Flujos de datos de la versión Premium

Los flujos de datos que existen en la versión Premium presentan las siguientes limitaciones y consideraciones.

**Actualizaciones y consideraciones sobre los datos:**

* Al actualizar los flujos de datos, los tiempos de espera son de 24 horas (no hay distinción entre entidades o flujos de datos).

* Al cambiar un flujo de datos de una directiva de actualización incremental a una actualización normal, o viceversa, se descartarán todos los datos.

* Al modificar el esquema de un flujo de datos, se descartarán todos los datos.

**Entidades vinculadas y calculadas:**

* las entidades vinculadas pueden descender hasta una profundidad de 32 referencias.

* No se permiten dependencias cíclicas de entidades vinculadas.

* Una entidad vinculada no se puede combinar con una entidad estándar que obtenga sus datos de un origen de datos local.

* Cuando se usa una consulta (consulta *A*, por ejemplo) en el cálculo de otra (consulta *B*) en los flujos de datos, la consulta *B* se convierte en una entidad calculada. Las entidades calculadas no pueden hacer referencia a orígenes locales.


**Motor de proceso:**

* al usar el motor de proceso, existe un aumento inicial aproximado del 10 % al 20 % en el tiempo de ingesta de datos.

  1. Este aumento solo se aplica al primer flujo de datos que se encuentra en el motor de proceso y lee los datos del origen de datos.
  2. Los flujos de entrada subsiguientes, que usan el origen, no incurrirán en la misma penalización

* Solo determinadas operaciones hacen uso del motor de proceso y solo cuando se utiliza mediante una entidad vinculada o como entidad calculada. Puede encontrar una lista completa de las operaciones disponibles en [esta entrada de blog](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html).


**Administración de la capacidad:**

* por diseño, las capacidades de Power BI Premium tienen un administrador de recursos interno que limita las cargas de trabajo de distintas formas cuando la capacidad se ejecuta con memoria insuficiente.

  1. En el caso de los flujos de datos, esta presión limitante reduce el número de contenedores M disponibles.
  2. La memoria de los flujos de datos se puede establecer en 100 % con un contenedor de tamaño adecuado para los tamaños de datos, y la carga de trabajo administrará el número de contenedores de forma adecuada.

* El número aproximado de contenedores se puede averiguar dividiendo la memoria total asignada a la carga de trabajo entre la cantidad de memoria asignada a un contenedor.

## <a name="dataflow-usage-in-datasets"></a>Uso de flujos de datos en conjuntos de datos

* Al crear un conjunto de datos en Power BI Desktop y, luego, publicarlo en el servicio Power BI, asegúrese de que las credenciales que se usan en Power BI Desktop para el origen de datos de flujos de datos sean iguales que las que se usan cuando el conjunto de datos se publica en el servicio.
  1. Si no se puede garantizar que esas credenciales sean las mismas, se producirá el error de *clave no encontrada* al actualizar el conjunto de datos.

## <a name="next-steps"></a>Pasos siguientes
En los artículos siguientes encontrará más información sobre los flujos de datos y Power BI:

* [Introducción a los flujos de datos y la preparación de datos de autoservicio](dataflows-introduction-self-service.md)
* [Creación de un flujo de datos](dataflows-create.md)
* [Configurar y consumir un flujo de datos](dataflows-configure-consume.md)
* [Configuración del almacenamiento de flujo de datos para usar Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Características prémium de flujos de datos](dataflows-premium-features.md)
* [IA con flujos de datos](dataflows-machine-learning-integration.md)
* [Procedimientos recomendados para flujos de datos](dataflows-best-practices.md)