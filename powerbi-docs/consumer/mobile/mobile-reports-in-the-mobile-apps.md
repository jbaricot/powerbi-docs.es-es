---
title: Exploración de informes en las aplicaciones móviles de Power BI
description: Aprenda a ver informes e interactuar con ellos en las aplicaciones móviles de Power BI del teléfono o la tableta. Cree informes en el servicio Power BI o en Power BI Desktop y, luego, interactúe con ellos en las aplicaciones móviles.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 08/12/2020
ms.author: painbar
ms.openlocfilehash: 47f1db75eb3923c1c4195a319323c3a37d17484e
ms.sourcegitcommit: 383d87841d2509131fac7cc02c5c37c6a868144f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92026099"
---
# <a name="explore-reports-in-the-power-bi-mobile-apps"></a>Exploración de informes en las aplicaciones móviles de Power BI
Se aplica a:

| ![iPhone](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![iPad](././media/mobile-reports-in-the-mobile-apps/ios-logo-40-px.png) | ![Teléfono Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Tableta Android](././media/mobile-reports-in-the-mobile-apps/android-logo-40-px.png) | ![Dispositivos de Windows 10](./media/mobile-reports-in-the-mobile-apps/win-10-logo-40-px.png) |
|:---: |:---: |:---: |:---: |:---: |
| iPhone |iPad |Teléfonos Android |Tabletas Android |Dispositivos de Windows 10 |

>[!NOTE]
>El soporte técnico de la aplicación móvil de Power BI con **teléfonos con Windows 10 Mobile** finalizará el 16 de marzo de 2021. [Más información](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

Un informe de Power BI es una vista interactiva de los datos, con objetos visuales que describen distintas conclusiones e información de dichos datos. Ver informes en las aplicaciones móviles de Power BI es el tercer paso de un proceso de tres pasos:

1. [Crear informes en Power BI Desktop](../../create-reports/desktop-report-view.md). Puede incluso [optimizar un informe para teléfonos](mobile-apps-view-phone-report.md) en Power BI Desktop.
2. Publique esos informes en el servicio Power BI [(https://powerbi.com)](https://powerbi.com) o [Power BI Report Server](../../report-server/get-started.md).  
3. Interactuar con los informes en las aplicaciones móviles de Power BI.

## <a name="open-a-power-bi-report-in-the-mobile-app"></a>Apertura de un informe de Power BI en la aplicación móvil
Los informes de Power BI se almacenan en distintos lugares de la aplicación móvil, en función de su procedencia. Pueden estar en Aplicaciones, Compartido conmigo, Áreas de trabajo (incluidos Mi área de trabajo) o en un servidor de informes. A veces, se desplaza por un panel relacionado para llegar a un informe y a veces aparecen en una lista.

En listas y menús, encontrará un icono junto al nombre de un informe, lo que ayuda a entender que este elemento es un informe:

![Informes en Mi área de trabajo](./media/mobile-reports-in-the-mobile-apps/reports-my-workspace.png)

En las aplicaciones móviles de Power BI Mobile hay dos iconos para los informes:

* ![Icono de informe](./media/mobile-reports-in-the-mobile-apps/report-default-icon.png) indica un informe que se presentará en orientación horizontal en la aplicación. Tendrá el mismo aspecto que en un explorador.

* ![Icono de informe de teléfono](./media/mobile-reports-in-the-mobile-apps/report-phone-icon.png) indica un informe que tiene al menos una página optimizada para teléfono, que se presentará en orientación vertical.

> [!NOTE]
> Al sujetar el teléfono en horizontal, siempre obtendrá el diseño horizontal, aunque la página del informe esté en diseño para dispositivos móviles.

Para obtener un informe desde un panel, pulse **Más opciones** (...) en la esquina superior derecha de un icono y, después, pulse **Abrir informe** :
  
  ![Abrir informe](./media/mobile-reports-in-the-mobile-apps/power-bi-android-open-report-tile.png)
  
  No todos los iconos se pueden abrir como informes. Por ejemplo, los iconos que se crean cuando hace una pregunta en el cuadro de Preguntas y respuestas no abren informes al pulsarlos.
  
## <a name="zoom-in-on-your-data"></a>Acercar los datos   
Use el gesto de acercar los dedos para acercar los informes y examinarlos con mayor detalle. Separe los dedos para reducir el zoom. El gesto de acercar los dedos para hacer zoom se admite en teléfonos y tabletas iOS y Android.

## <a name="interact-with-reports"></a>Interacción con informes
Una vez que haya abierto un informe en la aplicación, puede empezar a trabajar con él. Con el informe y los datos puede hacer muchas cosas. En el pie de página del informe, encontrará acciones que puede realizar en el informe. También puede segmentar los datos mediante pulsaciones y pulsaciones largas en los datos mostrados en el informe.

### <a name="single-tap-versus-double-tap-interaction"></a>Interacción de pulsación única frente a pulsar dos veces
Al descargar la aplicación móvil de Power BI, está establecida para la interacción de pulsación única. Esto significa que, al pulsar un objeto visual para realizar una acción, como seleccionar un elemento de segmentación, resaltado cruzado, hacer clic en un vínculo o botón, etc., la pulsación selecciona el objeto visual y realiza la acción deseada.

Si lo prefiere, puede cambiar a la interacción de pulsar dos veces. Con la interacción de pulsar dos veces, primero debe pulsar un objeto visual para seleccionarlo y, después, volver a pulsarlo para realizar la acción deseada.

Para cambiar a la interacción de pulsar dos veces, o bien para recuperar la de pulsación única, vaya a la [configuración de las interacciones de la aplicación](./mobile-app-interaction-settings.md).

### <a name="single-select-versus-multi-select-mode-for-data-point-selection"></a>Modo de selección única frente al modo de selección múltiple para la selección de puntos de datos

En un informe, debe pulsar un punto de datos para seleccionarlo. Puede elegir si desea usar el modo de selección única o de selección múltiple. En el modo de selección única, al pulsar un punto de datos para seleccionarlo, la selección reemplazará cualquier selección anterior que haya realizado. En el modo de selección múltiple, al pulsar un punto de datos para seleccionarlo, la selección se *agregará* a cualquier selección que tenga actualmente y el resultado combinado de todas las selecciones se resaltará en todos los objetos visuales del informe.

Para anular la selección de un punto de datos seleccionado, simplemente púlselo de nuevo.

Para cambiar entre el modo de selección única y el de selección múltiple, vaya a la [configuración de interacción de la aplicación](./mobile-app-interaction-settings.md).

### <a name="using-tap-and-long-tap"></a>Uso de pulsaciones y pulsaciones largas
Una pulsación es como un clic del mouse. Por tanto, si quiere resaltar el informe en función de un punto de datos, pulse ese punto de datos.
Al pulsar un valor de segmentación, se selecciona el valor y el resto del informe se segmenta por ese valor.
Al pulsar un vínculo, un botón o un marcador, se producirá la acción definida por el autor del informe.

Probablemente haya observado que al pulsar un objeto visual aparece un borde. En la esquina superior derecha del borde, verá **Más opciones** (...). Si pulsa los puntos suspensivos, verá un menú de acciones que puede realizar en ese objeto visual:

![Objeto visual y menú](./media/mobile-reports-in-the-mobile-apps/report-visual-menu.png)

### <a name="tooltip-and-drill-actions"></a>Acciones relativas a la información en pantalla y la obtención de detalles
Al realizar una pulsación larga (pulsar y mantener presionado) en un punto de datos, se mostrará una información en pantalla con los valores que representa este punto de datos:

![Información sobre herramientas](./media/mobile-reports-in-the-mobile-apps/report-tooltip.png)

Si el autor del informe ha configurado la información en pantalla de la página del informe, la información en pantalla predeterminada se reemplazará por la de la página del informe:

![Información en pantalla de la página de informes](./media/mobile-reports-in-the-mobile-apps/report-page-tooltip.png)

> [!NOTE]
> La información en pantalla para informes se admite para los dispositivos de al menos 640 píxeles y 320 puntos de ventanilla de píxeles. Si el dispositivo es más pequeño, la aplicación muestra la información en pantalla predeterminada.

Los autores de informes pueden definir jerarquías en los datos y las relaciones entre las páginas del informe. Las jerarquías permiten explorar en profundidad, rastrear agrupando datos y obtener detalles de otra página de informe desde un objeto visual y un valor. Por tanto, al realizar una pulsación larga en un valor, además de la información en pantalla, en el pie de página aparecen las opciones de exploración pertinentes:

![Acciones de obtención de detalles](./media/mobile-reports-in-the-mobile-apps/report-drill-actions.png)


Al pulsar una parte específica de un objeto visual y la opción de *obtención de detalles* , Power BI le mostrará otra página del informe y la filtrará según el valor que haya pulsado. El autor de un informe puede definir una o más opciones de exploración de varias páginas, de modo que cada opción dirija a una página diferente. En ese caso, podrá elegir en qué opción quiere obtener detalles. El botón Atrás le dirigirá de vuelta a la página anterior.


Para obtener más información, consulte el artículo sobre cómo [agregar la obtención de detalles en Power BI Desktop](../../create-reports/desktop-drillthrough.md).
   
   > [!IMPORTANT]
   > En las aplicaciones móviles de Power BI, las acciones de obtención de detalles de los objetos visuales de matriz y tabla se habilitan solamente a través de los valores de celda, no a través de los encabezados de columna o de fila.
   
   
   
### <a name="using-the-actions-in-the-report-footer"></a>Uso de las acciones en el pie de página del informe
Desde el pie de página del informe, puede realizar varias acciones en la página del informe actual o en todo el informe. El pie de página proporciona acceso rápido a las acciones que se usan con más frecuencia. Para tener acceso a otras acciones, pulse el botón **Más opciones** (...):

![Pie de página del informe](./media/mobile-reports-in-the-mobile-apps/report-footer.png)

Puede realizar las siguientes acciones desde el pie de página:
* Restablecer el filtro de informe y las selecciones de resaltado cruzado a su estado original.
* Abrir el panel de conversación para ver o agregar comentarios en el informe.
* Abrir el panel de filtro para ver o modificar el filtro aplicado actualmente en el informe.
* Enumerar todas las páginas del informe. Al pulsar el nombre de la página se cargará y presentará esa página.
Puede desplazarse entre las páginas del informe si desliza el dedo desde el borde de la pantalla hasta el centro.
* Ver todas las acciones del informe.

#### <a name="all-report-actions"></a>Todas las acciones del informe
Al pulsar el botón **Más opciones** (...) en el pie de página del informe, verá todas las acciones que puede realizar en un informe:


![Todas las acciones del informe](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-all-actions.png)

Es posible que algunas de las acciones estén deshabilitadas, ya que dependen de las funciones específicas del informe.
Por ejemplo:

**Marcadores** solo aparece si se han establecido [marcadores](mobile-reports-in-the-mobile-apps.md#bookmarks) en el informe. Se muestran tanto los marcadores personales que puede definir en el servicio Power BI como los definidos por el creador del informe. Si uno de los marcadores se ha definido como el marcador predeterminado, el informe se abrirá en esa vista cuando se cargue.

Es posible que **Anotar y compartir** esté desactivado si hay una [directiva de protección de Intune](/intune/app-protection-policies) en la organización que prohíba el uso compartido desde la aplicación Power BI Mobile.

La opción **Invitar** solo está habilitada si tiene permiso para compartir el informe con otros usuarios. Solo tendrá permiso si es el propietario del informe o si el propietario le ha proporcionado permiso para volver a compartirlo.

**Filtrar por la ubicación actual** está habilitado si el autor del informe lo ha clasificado con datos geográficos. Para obtener más información, consulte el artículo sobre la [identificación de datos geográficos en un informe](../../transform-model/desktop-mobile-geofiltering.md).

**Examinar para filtrar el informe por código de barras** solo está habilitado si el conjunto de datos del informe se ha etiquetado como **Código de barras** . Para obtener más información, consulte el artículo sobre el [etiquetado de códigos de barra en Power BI Desktop](../../transform-model/desktop-mobile-barcodes.md).

### <a name="bookmarks"></a>Marcadores

La aplicación móvil de Power BI admite los marcadores de informe que haya definido el creador del informe y los marcadores personales que puede definir en el servicio Power BI. Puede encontrar el menú de marcadores en **Más opciones** (...), en la [barra de herramientas de acciones del informe](mobile-reports-in-the-mobile-apps.md#all-report-actions).

Los marcadores predeterminados se indican mediante un icono especial. En el caso de los marcadores personales, puede establecer, desactivar o cambiar la configuración predeterminada pulsando **Más opciones (...)** junto al marcador que quiera cambiar y seleccionando **Establecer como valor predeterminado** o **Borrar valor predeterminado** .

![Menú de marcadores](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-bookmark-menu.png)

Cuando se abre una vista de marcador de un informe, el nombre del marcador aparece en la parte superior del informe.

![Vista de marcadores](./media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-bookmark-title.png)

[Obtenga más información sobre los marcadores en el servicio Power BI](../end-user-bookmarks.md).

## <a name="refresh-your-data"></a>Actualización de los datos

Si no está seguro de estar viendo los datos más actualizados, puede extraer nuevos datos para su informe desde el servicio Power BI:

* En dispositivos iOS y tabletas Android, desplace el dedo ligeramente de arriba a abajo en la página del informe.
* En los teléfonos Android, puede usar la acción de mover hacia abajo o un botón de actualización, según cómo lo haya establecido en la [configuración de la interacción](mobile-app-interaction-settings.md).
* En los dispositivos Windows, use el botón de actualizar situado en la parte superior derecha de la pantalla.

    Las páginas de informe que tienen [actualización automática de página](../../create-reports/desktop-automatic-page-refresh.md) se actualizarán automáticamente en función de su configuración (solo aplicación de Windows).

>[!NOTE]
>Los métodos de actualización anteriores no actualizan el conjunto de datos subyacente. En su lugar, actualizan el informe que está viendo en la aplicación móvil con los datos nuevos que puedan existir en Power BI.

### <a name="how-do-i-know-when-my-report-was-last-refreshed"></a>¿Cómo se sabe cuándo se actualizó el informe por última vez?

Para averiguar cuándo se actualizó el informe por última vez, pulse el encabezado del informe. Se mostrará el árbol de navegación del informe, incluida la fecha y hora de la última actualización. 

![Captura de pantalla de la información de actualización del informe en la aplicación móvil.](media/mobile-reports-in-the-mobile-apps/power-bi-mobile-report-refresh-info.png)
 
## <a name="configure-your-experience-with-reports"></a>Configuración de la experiencia con los informes
La aplicación móvil de Power BI tiene una serie de valores que le permiten controlar la experiencia con los informes. Actualmente, puede configurar lo siguiente:
* **Interacción con los objetos visuales** : puede optar por usar la interacción de pulsación única o de pulsar dos veces.
* **Método de actualización de datos** : puede elegir entre un botón de actualización o una acción de deslizar para actualizar los datos del informe.
* **Visibilidad del pie de página del informe** : puede elegir entre un pie de página acoplado siempre visible, o bien un pie de página dinámico que se oculte y se vuelva a mostrar en función de las acciones (desplazamiento, por ejemplo).

Vea la [configuración de las interacciones de la aplicación](./mobile-app-interaction-settings.md) para obtener información sobre cómo cambiar esta configuración.


## <a name="next-steps"></a>Pasos siguientes
* [Ver e interactuar con informes de Power BI optimizados para el teléfono](mobile-apps-view-phone-report.md)
* [Creación de versiones de informes optimizadas para teléfonos](../../create-reports/desktop-create-phone-report.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)