---
title: Clasificación de datos del panel
description: Obtenga información acerca de la clasificación de datos de panel, incluido cómo un administrador debe configurarla y cómo los propietarios de un panel pueden cambiar la clasificación.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/10/2017
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: d8c7a8532122487bdf3bcd718eb4089cb7c67008
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2020
ms.locfileid: "86262794"
---
# <a name="dashboard-data-classification"></a>Clasificación de datos del panel
Cada panel es diferente y, según el origen de datos al que se conecte, probablemente encontrará que usted y los compañeros con los que lo comparte deberán tomar diferentes precauciones en función de la confidencialidad de los datos. Algunos paneles nunca deberían compartirse con personas de fuera de su empresa o imprimirse, mientras que otros pueden compartirse libremente. Si usa la clasificación de los datos del panel, podrá informar a los usuarios que ven los paneles sobre el nivel de seguridad que debe utilizarse. Puede etiquetar sus paneles con clasificaciones definidas por el departamento informático de su empresa para que todos los usuarios que vean el contenido tengan el mismo nivel de conocimiento acerca de la confidencialidad de los datos.

![Captura de pantalla de un panel, en la que se muestra la clasificación de datos de un ejemplo.](media/service-data-classification/dashboard_tagged_as_hbi.png)

## <a name="data-classification-tags"></a>Etiquetas de clasificación de datos
Las etiquetas de clasificación de los datos aparecen junto al nombre del panel, lo que permite a cualquiera que lo vea conocer el nivel de seguridad que se debe aplicar en el panel y los datos que contiene.

![Captura de pantalla de un panel, en la que se muestra una etiqueta de clasificación de datos junto al nombre del panel.](media/service-data-classification/tag_next_to_title.png)

También se mostrará junto al icono del panel en su lista de favoritos.

![Captura de pantalla de la lista Favoritos, en la que se muestra una etiqueta de clasificación de datos junto al icono del panel en la lista Favoritos.](media/service-data-classification/tag_on_dashboard_tile.png)

Al mantener el ratón sobre la etiqueta, verá el nombre completo de la clasificación.

![Captura de pantalla de la etiqueta HBI, en la que se muestra el nombre completo de la clasificación al mantener el puntero sobre la etiqueta. ](media/service-data-classification/tag_tooltip.png)

Los administradores también pueden establecer la dirección URL de una etiqueta para proporcionar información adicional.

> [!NOTE]
> Según la configuración de la clasificación establecida por el administrador, puede que algunos tipos de clasificación no se muestren como una etiqueta en el panel. Si es propietario de un panel, siempre puede comprobar el tipo de clasificación de panel en la configuración del panel.
> 
> 

## <a name="setting-a-dashboards-classification"></a>Configurar la clasificación de un panel
Si la clasificación de datos está activada para su empresa, todos los paneles se inician con un tipo de clasificación predeterminado; no obstante, como propietario de un panel, puede cambiar la clasificación para que coincida con el nivel de seguridad que quiera para los paneles.

Para cambiar el tipo de clasificación, siga este procedimiento:

1. Vaya a la configuración del panel seleccionando los **puntos suspensivos** junto al nombre del panel y seleccione **Configuración**.
   
    ![Captura de pantalla de un panel, en la que se muestra la selección de Configuración.](media/service-data-classification/dashboard_settings.png)
2. En la configuración del panel, podrá ver la clasificación actual del panel y usar la lista desplegable para cambiar el tipo de clasificación.
   
    ![Captura de pantalla de la configuración del panel, en la que se muestra una clasificación actual y la selección de la lista desplegable Clasificación de datos.](media/service-data-classification/classification_setting_dropdown.png)
3. Seleccione **Aplicar** cuando haya terminado.

Después de aplicar el cambio, cualquier persona con quien haya compartido el panel verá la actualización la próxima vez que lo vuelva a cargar.

## <a name="working-with-data-classification-tags-as-an-admin"></a>Trabajar con etiquetas de clasificación de datos como administrador
El administrador global de una organización configura su clasificación de datos. Para activar la clasificación de datos, siga este procedimiento:

1. Seleccione el icono de engranaje de configuración y seleccione **Portal de administración**.
   
    ![Captura de pantalla del engranaje Configuración, con la selección de Portal de administración.](media/service-data-classification/admin_portal_in_settings.png)
2. En la pestaña **Configuración de inquilinos**, *active* la opción **Clasificación de datos para paneles e informes**.
   
    ![Captura de pantalla del Portal de administración, en la que se muestra la selección de Configuración de inquilinos y Clasificación de datos para paneles e informes.](media/service-data-classification/data_classification_switch_location.png)

Una vez activada, aparecerá un formulario para crear las diversas clasificaciones en su organización.

![Captura de pantalla de un formulario. en el que se muestran entradas de campos para distintas clasificaciones de la organización.](media/service-data-classification/blank_classification_form.png)

Cada clasificación tiene un **nombre** y una **abreviatura** que aparecerá en el panel. Para cada clasificación, puede decidir si la etiqueta de forma abreviada aparecerá en el panel o no seleccionando **Mostrar etiqueta**. Si no desea mostrar el tipo de clasificación en el panel, el propietario podrá ver el tipo en la configuración del panel. Además, puede agregar opcionalmente una dirección **URL** que contenga más información sobre las directrices de clasificación y los requisitos de uso de su organización.  

Lo último que debe decidir es qué tipo de clasificación será la predeterminada.  

Una vez que rellene el formulario con los tipos de clasificación, seleccione **Aplicar** para guardar los cambios.

![Captura de pantalla de un formulario, en la que se muestran entradas rellenas con los tipos de clasificación que se van a aplicar.](media/service-data-classification/filled_in_classification_form.png)

En este momento, se asignará la clasificación predeterminada a todos los paneles. Los propietarios de los paneles ya pueden cambiar el tipo de clasificación al más adecuado para su contenido. Puede volver a este punto en el futuro para agregar o quitar tipos de clasificación o para cambiar el valor predeterminado.  

> [!NOTE]
> Debe recordar algunas cuestiones importantes cuando vuelva a realizar cambios:
> 
> * Si desactiva la clasificación de datos, no se recordará ninguna de las etiquetas. Deberá empezar de cero si decide activarlo de nuevo más adelante.  
> * Si quita un tipo de clasificación, cualquier panel asignado a dicho tipo de clasificación se reasignará al tipo de clasificación predeterminado hasta que el propietario lo vuelva a asignar.  
> * Si cambia el valor predeterminado, todos los paneles a los que el propietario no haya asignado ningún tipo de clasificación cambiarán al nuevo valor predeterminado.
> 
> 

