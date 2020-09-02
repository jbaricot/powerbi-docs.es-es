---
title: Integración de Azure Machine Learning en Power BI
description: Obtenga información sobre cómo usar Machine Learning con Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/01/2020
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: b24663acf2a3a3fd76953413c298580041afc4ab
ms.sourcegitcommit: 89ce1777a85b9fc476f077cbe22978c6cf923603
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89286852"
---
# <a name="azure-machine-learning-integration-in-power-bi"></a>Integración de Azure Machine Learning en Power BI

Numerosas organizaciones usan modelos de **Machine Learning** para obtener mejores conclusiones y predicciones sobre sus negocios. La capacidad de visualizar e invocar conclusiones de estos modelos en sus informes, paneles y otros análisis puede ayudar a divulgar estas conclusiones a los usuarios profesionales que más lo necesiten.  Ahora Power BI facilita la incorporación de las conclusiones de modelos hospedados en Azure Machine Learning, mediante movimientos sencillos de apuntar y hacer clic.

Para usar esta funcionalidad, un científico de datos puede conceder acceso al modelo de Azure ML al analista de BI simplemente mediante Azure Portal.  A continuación, al inicio de cada sesión, Power Query detecta todos los modelos de Azure ML a los que tiene acceso el usuario y los expone como funciones de Power Query dinámicas.  Después, el usuario puede invocar esas funciones obteniendo acceso a ellas desde la cinta de opciones del Editor de Power Query o invocando la función M directamente. Power BI también procesa por lotes las solicitudes de acceso de forma automática al invocar el modelo de Azure ML para que un conjunto de filas logre un mejor rendimiento.

Actualmente, esta funcionalidad solo es compatible con los flujos de datos de Power BI y con Power Query en línea en el servicio Power BI.

Para más información sobre los flujos de datos, consulte [Preparación de datos de autoservicio en Power BI](service-dataflows-overview.md).

Para obtener más información sobre Azure Machine Learning, consulte:

- Información general:  [¿Qué es Azure Machine Learning?](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml)
- Guías de inicio rápido y tutoriales de Azure Machine Learning:  [Documentación de Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/)

> [!NOTE]
> Se requiere una suscripción de Power BI Premium para usar la integración de Azure Machine Learning.

## <a name="granting-access-to-the-azure-ml-model-to-a-power-bi-user"></a>Concesión de acceso al modelo de Azure ML a un usuario de Power BI

Para obtener acceso a un modelo de Azure ML desde Power BI, el usuario debe tener acceso de **lectura** a la suscripción a Azure.  Asimismo:

- En los modelos de Machine Learning Studio (clásico), acceso de **lectura** al servicio web Machine Learning Studio (clásico)
- En los modelos de Machine Learning, acceso de **lectura** al área de trabajo de Machine Learning

En los pasos de este artículo se describe cómo conceder un acceso de usuario de Power BI a un modelo hospedado en el servicio Azure ML de modo que pueda tener acceso a este modelo como función de Power Query.  Para más detalles, consulte [Manage access using RBAC and the Azure portal](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal) (Administrar el acceso mediante RBAC y Azure Portal).

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Vaya a la página **Suscripciones**. Encontrará la página **Suscripciones** mediante la lista **Todos los servicios** del menú del panel de navegación de Azure Portal.

    ![Página de suscripciones a Azure](media/service-machine-learning-integration/machine-learning-integration_01.png)

3. Seleccione su suscripción.

    ![Seleccionar su suscripción](media/service-machine-learning-integration/machine-learning-integration_02.png)

4. Seleccione **Control de acceso (IAM)** y, a continuación, seleccione el botón **Agregar**.

    ![Control de acceso (IAM)](media/service-machine-learning-integration/machine-learning-integration_03.png)

5. Seleccione **Lector** como rol. Seleccione el usuario de Power BI a quien desea conceder acceso al modelo de Azure ML.

    ![Seleccionar Lector como rol](media/service-machine-learning-integration/machine-learning-integration_04.png)

6. Seleccione **Guardar**.

7. Repita los pasos del tres al seis para conceder acceso de **lectura** al usuario para el servicio web Machine Learning Studio (clásico) específico, *o bien* al área de trabajo de Machine Learning que hospeda el modelo.


## <a name="schema-discovery-for-machine-learning-models"></a>Detección de esquema para modelos de Machine Learning

Los científicos de datos usan principalmente Python para desarrollar e incluso implementar sus modelos de aprendizaje automático para Machine Learning.  A diferencia de Machine Learning Studio (clásico), que ayuda a automatizar la tarea de creación de un archivo de esquema para el modelo, en el caso de Machine Learning, el científico de datos debe generar de forma explícita el archivo de esquema mediante Python.

Este archivo de esquema se debe incluir en el servicio web implementado para los modelos de Machine Learning. Para generar de forma automática el esquema para el servicio web, debe proporcionar un ejemplo de la entrada y salida en el script de entrada para el modelo implementado. Consulte la subsección sobre [Generación automática de esquemas de Swagger (opcional) en los modelos de implementación con la documentación del servicio Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/how-to-deploy-advanced-entry-script#power-bi-compatible-endpoint). El vínculo incluye el script de entrada de ejemplo con las instrucciones para la generación de esquemas. 

En concreto, las funciones *input_sample\@* y *output_sample\@* del script de entrada hacen referencia a los formatos de ejemplo de entrada y salida de las variables *input_sample* y *output_sample*, y usan estos ejemplos para generar una especificación OpenAPI (Swagger) para el servicio web durante la implementación.

Estas instrucciones para la generación de esquemas mediante la actualización del script de entrada también se deben aplicar a los modelos creados mediante experimentos automatizados de aprendizaje automático con el SDK de Azure Machine Learning.

## <a name="invoking-the-azure-ml-model-in-power-bi"></a>Invocación del modelo de Azure ML en Power BI

Puede invocar cualquier modelo de Azure ML al que se le haya concedido acceso directamente desde el Editor de Power Query de su flujo de datos. Para obtener acceso a los modelos de Azure ML, seleccione el botón **Editar** para la entidad que quiera enriquecer con conclusiones de su modelo de Azure ML, como se muestra en la siguiente imagen.

![Servicio Power BI: editar la entidad](media/service-machine-learning-integration/machine-learning-integration_05.png)

Al seleccionar el botón **Editar** se abre el Editor de Power Query para las entidades de su flujo de datos.

![Editor de Power Query](media/service-machine-learning-integration/machine-learning-integration_06.png)

Seleccione el botón **Conclusiones de AI** de la cinta de opciones y, a continuación, seleccione la carpeta _Modelos de Azure Machine Learning_ en el menú del panel de navegación. Todos los modelos de Azure ML a los que tiene acceso se recogen aquí como funciones de Power Query. Asimismo, los parámetros de entrada para el modelo de Azure ML se asignan automáticamente como parámetros de la función de Power Query correspondiente.

Para invocar un modelo de Azure ML, puede especificar cualquiera de las columnas de la entidad seleccionadas como entrada del menú desplegable. También puede especificar un valor constante que se va a usar como entrada cambiando el icono de la columna a la izquierda del cuadro de diálogo de entrada.

![seleccionar la columna](media/service-machine-learning-integration/machine-learning-integration_07.png)

Seleccione **Invocar** para ver la versión preliminar del resultado del modelo de Azure ML como nueva columna en la tabla de entidades. También verá la invocación de modelos como paso aplicado para la consulta.

![Seleccionar Invocar](media/service-machine-learning-integration/machine-learning-integration_08.png)

Si el modelo devuelve varios parámetros de salida, se agrupan como registro en la columna de salida. Puede expandir la columna para producir parámetros de salida individuales en columnas independientes.

![expandir la columna](media/service-machine-learning-integration/machine-learning-integration_09.png)

Una vez que guarde su flujo de datos, el modelo se invocará automáticamente al actualizarse el flujo de datos, para cualquier fila nueva o actualizada de la tabla de entidades.

## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporcionaba información general de la integración de Machine Learning en el servicio Power BI. Los siguientes artículos también podrían ser interesantes y útiles. 

* [Tutorial: Invocación de un modelo de Machine Learning Studio (clásico) en Power BI](../connect-data/service-tutorial-invoke-machine-learning-model.md)
* [Tutorial: Uso de Cognitive Services en Power BI](../connect-data/service-tutorial-use-cognitive-services.md)
* [Cognitive Services en Power BI](service-cognitive-services.md)

Para más información sobre los flujos de datos, puede leer estos artículos:
* [Creación y uso de flujos de datos en Power BI](service-dataflows-create-use.md)
* [Uso de entidades calculadas en Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Uso de flujos de datos con orígenes de datos locales](service-dataflows-on-premises-gateways.md)
* [Recursos para desarrolladores sobre flujos de datos de Power BI](service-dataflows-developer-resources.md)
* [Integración de flujos de datos y Azure Data Lake (versión preliminar)](service-dataflows-azure-data-lake-integration.md)
