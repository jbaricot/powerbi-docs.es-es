---
title: Conectarse a una fuente OData en Power BI Desktop
description: Puede conectarse a una fuente OData en Power BI Desktop y usarla fácilmente
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 5c7d9464e8d14354ba893dd80d11a46b8ea170cc
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405845"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Conectarse a fuentes OData en Power BI Desktop
En Power BI Desktop, puede conectarse a una **fuente OData** y usar los datos subyacentes igual que cualquier otro origen de datos en Power BI Desktop.

Para conectarse a una fuente OData, seleccione **Obtener datos > Fuente OData** en la cinta **Inicio** en Power BI Desktop.

![Captura de pantalla de la cinta Obtener datos de Power BI Desktop, donde se muestra la selección de Fuente OData.](media/desktop-connect-odata/connect-to-odata_1.png)

En la ventana **Fuente OData** que aparece, escriba o pegue la URL de la fuente OData en el cuadro y seleccione **Aceptar**.

![Captura de pantalla del cuadro de diálogo Fuente OData, en el que se muestra el campo Dirección URL.](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop se conecta a la fuente OData y muestra las tablas disponibles y otros elementos de datos en la ventana **Navegador**. Al seleccionar un elemento, el panel derecho de la ventana **Navegador** muestra una vista previa de los datos. Puede seleccionar tantas tablas como quiera importar. La ventana **Navegador** muestra una vista previa de la tabla seleccionada actualmente.

![Captura de pantalla del cuadro de diálogo Navegador en la que se muestra una vista previa de los datos de la tabla seleccionada.](media/desktop-connect-odata/connect-to-odata_3.png)

Puede elegir el botón **Editar**, que inicia el **Editor de consultas**, donde puede dar forma y transformar los datos de la fuente OData antes de importarla en Power BI Desktop. O puede seleccionar el botón **Cargar** e importar todos los elementos de datos que ha seleccionado en el panel izquierdo.

Al seleccionar **Cargar**, Power BI Desktop importa los elementos seleccionados y muestra la ventana **Carga** del progreso de la importación.

![Captura de pantalla del cuadro de diálogo Cargar, en el que se muestra el progreso de la importación.](media/desktop-connect-odata/connect-to-odata_4.png)

Una vez que haya finalizado, Power BI Desktop hace que las tablas seleccionadas y otros elementos de datos estén disponibles en el panel **Campos**, que se encuentra en el lado derecho de la vista *Informes* en Power BI Desktop.

![Captura de pantalla del panel Campos, en el que se muestra la lista de tablas seleccionadas.](media/desktop-connect-odata/connect-to-odata_5.png)

¡Eso es todo!

Ahora está preparado para usar los datos importados de la fuente OData en Power BI Desktop para crear objetos visuales, informes, o para interactuar con cualquier otro dato con el que quiera conectarse e importar, como otros libros de Excel, bases de datos o cualquier otro origen de datos.

## <a name="next-steps"></a>Pasos siguientes
Hay todo tipo de datos a los que puede conectarse con Power BI Desktop. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
