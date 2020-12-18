---
title: Detección de conjuntos de datos mediante el centro de conectividad de conjuntos de datos
description: Obtenga información sobre cómo puede buscar, explorar y usar los conjuntos de datos de su organización y sus informes relacionados.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Share your work
ms.openlocfilehash: c6b7170df78b6d544f7eb97ec62516577f9267b6
ms.sourcegitcommit: b5365df7fc32b7c49f8a2bf2cf75b5edd6bda9b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513813"
---
# <a name="datasets-discovery-using-the-datasets-hub"></a>Detección de conjuntos de datos mediante el centro de conectividad de conjuntos de datos

El centro de conectividad de conjuntos de datos facilita la búsqueda, exploración y uso de los conjuntos de datos de la organización. Proporciona información sobre los conjuntos de datos, así como puntos de entrada para crear informes sobre esos conjuntos de datos o para usar esos conjuntos de datos con Analizar en Excel.

El centro de conectividad de conjuntos de datos puede ser útil en numerosos escenarios:
* Los propietarios de los conjuntos de datos pueden ver las métricas de uso, el estado de actualización y el linaje de dichos conjuntos de datos, así como informes relacionados con los mismos, para supervisarlos y administrarlos.
* Los creadores de informes pueden usar el centro de conectividad para buscar conjuntos de datos adecuados en los que crear sus informes y usar vínculos para crear fácilmente informes basados en el conjunto de datos, ya sea desde cero o a partir de plantillas.
* Los consumidores de informes pueden utilizar esta página para buscar informes basados en conjuntos de datos de confianza.

Al facilitar la búsqueda de conjuntos de datos de calidad y sus informes relacionados, el centro de conectividad de los conjuntos de datos ayuda a evitar la creación de informes redundantes. También facilita la búsqueda de buenos informes para usarlos como puntos de partida para crear nuevos informes.

En este artículo se explica lo que se ve en el centro de conectividad de conjuntos de datos y se describe cómo usarlo. En el caso de los propietarios de conjuntos de datos, también incluye una serie de sugerencias sobre cómo [mejorar la capacidad de detección y uso de sus conjuntos de datos](#make-your-dataset-discoverable).

**¿Qué conjuntos de datos veo en el centro de conectividad de conjuntos de datos?**
* Para que un conjunto de valores aparezca en el concentrador de conjuntos de valores, debe encontrarse en una [nueva experiencia de área de trabajo](../collaborate-share/service-new-workspaces.md).
* Los conjuntos de datos que puede ver en el centro de conectividad de conjuntos de datos son aquellos para los que tiene al menos [permisos de compilación](service-datasets-build-permissions.md).
* Si es un usuario gratuito, solo verá los conjuntos de datos de *Mi área de trabajo*, o bien los conjuntos de datos para los que tiene [permisos de compilación](service-datasets-build-permissions.md) que se encuentran en áreas de trabajo de la capacidad Premium.

## <a name="find-the-dataset-you-need"></a>Búsqueda del conjunto de datos que necesita

La experiencia de detección de conjuntos de datos se inicia en la página del centro de conectividad de conjuntos de datos. Para llegar a la página del centro de conectividad de conjuntos de datos:
* En el servicio Power BI: Seleccione **Conjunto de datos** en el panel de navegación.
* En la aplicación Power BI en Teams: Seleccione la pestaña **Conjuntos de datos** o **Conjuntos de datos** en el panel de navegación.

En la imagen siguiente se muestra el centro de conectividad de conjuntos de datos en el servicio Power BI.

![Captura de pantalla de la página del centro de conectividad conjuntos de datos](media/service-datasets-hub/datasets-hub-main-page.png)

El centro de conectividad de conjuntos de datos muestra una selección de conjuntos de datos recomendados y una lista de todos los conjuntos de datos de la organización para los que tiene permisos de acceso.

En los apartados siguientes se describen estas secciones y las acciones que puede realizar.

### <a name="recommended-datasets"></a>Conjuntos de datos recomendados

Los conjuntos de datos recomendados son conjuntos de datos aprobados (promocionados o certificados) que se presentan en función de un cálculo que tiene en cuenta la frecuencia con que se han actualizado y el momento en que ha visitado los informes o los paneles que están relacionados con ellos.

### <a name="dataset-list"></a>Lista de conjuntos de datos

La lista de conjuntos de datos muestra los conjuntos de datos de la organización para los que tiene al menos [permisos de compilación](service-datasets-build-permissions.md). La lista tiene tres pestañas para filtrar la lista de conjuntos de datos.
* **Todos los conjuntos de datos**: muestra todos los conjuntos de datos de la organización para los que tiene al menos [permisos de compilación](service-datasets-build-permissions.md).
* **Recientes**: muestra los conjuntos de datos a cuyos informes relacionados ha accedido recientemente. Al acceder a un informe, puede haber un retraso de varios minutos hasta que el conjunto de datos relacionado aparece en la columna Recientes.
* **Mis conjuntos de datos**: muestra los conjuntos de datos de los que es propietario. 

Utilice el cuadro de búsqueda para filtrar aún más los elementos de la pestaña actual.

A continuación se describen las columnas de la lista. Haga clic en el encabezado de columna para ordenar por esa columna. 
* **Nombre**: el nombre del conjunto de datos. Haga clic en el nombre del conjunto de datos para explorar los informes que se han creado con este conjunto de datos.
* **Promoción**: estado de la aprobación.
* **Propietario**: propietario del conjunto de datos.
* **Área de trabajo**: área de trabajo en la que se encuentra el conjunto de datos.
* **Actualizado**: última hora de actualización (redondeado a hora, día, mes y año. Vea la información del conjunto de datos en la página de detalles del conjunto de datos para ver la hora exacta de la última actualización).
* **Sensibilidad**: sensibilidad, si se establece. Haga clic en el icono de información para ver la descripción de la etiqueta de sensibilidad.

### <a name="create-new-reports-or-pull-data-into-excel-via-analyze-in-excel"></a>Creación de nuevos informes o extracción de datos en Excel mediante Analizar en Excel

Para crear un nuevo informe basado en un conjunto de datos, o para extraer los datos en Excel con [Analizar en Excel](../collaborate-share/service-analyze-in-excel.md), seleccione **Más opciones (...)** en la esquina inferior derecha de un icono de conjunto de datos recomendado o en la línea de un conjunto de datos en la lista de conjuntos de datos. Pueden aparecer otras acciones en el menú desplegable, en función de los permisos que tenga en el conjunto de datos.

Al crear un nuevo informe basado en el conjunto de cambios, se abre el lienzo de edición del informe. Al guardar el nuevo informe, se guardará en el área de trabajo que contiene el conjunto de datos si tiene permisos de escritura en esa área de trabajo. Si no tiene permisos de escritura en esa área de trabajo, o si es un usuario gratuito y el conjunto de datos se encuentra en un área de trabajo de capacidad Premium, el nuevo informe se guardará en *Mi área de trabajo*.

## <a name="view-dataset-details-and-explore-related-reports"></a>Visualización de detalles del conjunto de datos y exploración de informes relacionados

Para obtener más información sobre el conjunto de datos, para explorar informes relacionados o para crear un nuevo informe basado en el conjunto de datos, ya sea desde cero o a partir de una plantilla, seleccione un conjunto de datos de los conjuntos de datos recomendados o de la lista de conjuntos de datos. Se abrirá una página que muestra información sobre el conjunto de datos, enumera los informes que se basan en el conjunto de datos y proporciona puntos de entrada para crear nuevos informes basados en el conjunto de datos o para extraer los datos en Excel a través de [Analizar en Excel](../collaborate-share/service-analyze-in-excel.md).

![Captura de pantalla de la página de exploración de informes relacionados del centro de conectividad de conjuntos de datos](media/service-datasets-hub/datasets-hub-explore-related-reports.png)

El encabezado de página muestra el nombre del conjunto de datos, la aprobación, si existe, y el propietario del conjunto de datos. Para enviar un correo electrónico al propietario del conjunto de datos o al certificador del conjunto de datos (si existe), haga clic en el encabezado y luego haga clic en el nombre del propietario.

### <a name="dataset-details"></a>Detalles del conjunto de datos

En la sección Detalles del conjunto de datos se muestra el nombre del área de trabajo donde se encuentra el conjunto de datos, la hora exacta de la última actualización, la sensibilidad (si se ha establecido), la descripción del conjunto de datos (si existe) y el nombre del certificador (si se ha certificado). También puede abrir el linaje del conjunto de datos desde aquí.

### <a name="related-reports"></a>Informes relacionados

La sección Explorar informes relacionados muestra todos los informes que se basan en el conjunto de datos seleccionado. Puede crear una copia de un informe. Para ello, seleccione la línea del informe en la lista y haga clic en el icono Guardar una copia de este informe.

Las columnas de la lista de informes relacionados son:
* **Nombre**: nombre del informe. Si el nombre termina con (plantilla), significa que este informe se ha construido especialmente para usarse como plantilla.
* **Promoción**: estado de la aprobación.
* **Área de trabajo**: nombre del área de trabajo donde se encuentra el informe.

### <a name="create-a-report-built-on-the-dataset"></a>Creación de un informe basado en el conjunto de datos

En la sección Crear un informe, haga clic en el botón **Crear**. Si hay una plantilla de informe para el conjunto de datos, un menú desplegable ofrecerá dos opciones:
* **From template** (Desde una plantilla): crea una copia de la plantilla en *Mi área de trabajo*.
* **From scratch** (Desde cero): abre el lienzo de edición del informe en un nuevo informe basado en el conjunto de cambios. Al guardar el nuevo informe, se guardará en el área de trabajo que contiene el conjunto de datos si tiene permisos de escritura en esa área de trabajo. Si no tiene permisos de escritura en el área de trabajo, o si es un usuario gratuito y el conjunto de datos se encuentra en un área de trabajo de capacidad Premium, el nuevo informe se guardará en *Mi área de trabajo*.

Si no hay ninguna plantilla de informe, al hacer clic en **Crear** se abrirá el lienzo de edición del informe directamente.

>[!NOTE]
> En el menú desplegable Crear informe solo se mostrará una plantilla, aunque exista más de una plantilla de informe para este conjunto de datos. 

### <a name="pull-the-dataset-into-excel-via-analyze-in-excel"></a>Extracción del conjunto de datos en Excel mediante Analizar en Excel

En la sección Analizar en Excel, seleccione **Analizar** para extraer el conjunto de datos en Excel mediante Analizar en Excel.

## <a name="make-your-dataset-discoverable"></a>Hacer que el conjunto de datos sea reconocible

Hay varias maneras de mejorar la capacidad de detección de los conjuntos de datos:
* **Aprobar el conjunto de datos**: puede promocionar o certificar el conjunto de datos para facilitar a los usuarios la búsqueda y el conocimiento de que es un origen de datos de confianza. Los conjuntos de datos aprobados se etiquetan con notificaciones y se pueden identificar fácilmente en Power BI. En el centro de conectividad de conjuntos de datos, solo se muestran los conjuntos de datos aprobados en la sección de conjuntos de datos recomendados, y la lista de conjuntos de datos enumera en primer lugar, y de forma predeterminada, los conjuntos de datos aprobados.

    [Obtenga información sobre cómo aprobar los conjuntos de datos](../collaborate-share/service-endorse-content.md). 
* **Proporcionar una descripción significativa del conjunto de datos**: puede ayudar a los usuarios a detectar el conjunto de datos adecuado para ellos proporcionando descripciones útiles y significativas de los conjuntos de datos. [La descripción se proporciona como parte del proceso de aprobación del conjunto de datos](../collaborate-share/service-endorse-content.md#promote-content). 
* **Proporcionar al conjunto de datos una imagen memorable**: Puede facilitar a los usuarios la búsqueda y memorización del conjunto de datos proporcionándolo imágenes memorables. Esto hace que el conjunto de datos destaque en la página del centro de conectividad de conjuntos de datos y en cualquier otra parte que admita la visualización de imágenes de conjuntos de datos. Para asignar una imagen a un conjunto de datos, abra la configuración de dicho conjunto de datos y expanda la sección de imagen del conjunto de datos.
* **Crear una plantilla de informe basada en el conjunto de datos**: Puede crear una plantilla de informe que los usuarios puedan usar para empezar a crear sus propios informes basados en el conjunto de datos. Esta plantilla es simplemente un informe normal que se diseña teniendo en cuenta que se va a utilizar como plantilla. Al guardarlo, debe agregar el sufijo "(plantilla)" al nombre del informe, por ejemplo *Ventas mensuales (plantilla)* .

    Cuando un usuario selecciona **Crear > From template** (Desde una plantilla) en la sección Crear un informe en la vista de detalles del conjunto de datos del centro de conectividad del centro de datos, se creará una copia de la plantilla en *Mi área de trabajo* del usuario y luego se abrirá en el lienzo de edición del informe.

    Las plantillas de informe también se pueden identificar fácilmente en la lista de informes relacionados en la vista Detalles del conjunto de datos del centro de conectividad de conjuntos de datos.
  
## <a name="next-steps"></a>Pasos siguientes
* [Uso de conjuntos de datos entre áreas de trabajo](service-datasets-across-workspaces.md)
* [Creación de informes basados en conjuntos de datos de diferentes áreas de trabajo](service-datasets-discover-across-workspaces.md)
* [Aprobación del contenido](../collaborate-share/service-endorse-content.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
