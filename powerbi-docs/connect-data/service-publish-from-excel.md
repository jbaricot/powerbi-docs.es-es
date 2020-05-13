---
title: Publicación en Power BI desde Microsoft Excel
description: Obtenga información sobre cómo publicar un libro de Excel en su sitio de Power BI.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/05/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ca3e954f64665798c439fba47c3135e93fe51ac0
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83305620"
---
# <a name="publish-to-power-bi-from-microsoft-excel"></a>Publicación en Power BI desde Microsoft Excel
Con Microsoft Excel 2016 y versiones posteriores, puede publicar libros de Excel directamente en el área de trabajo de [Power BI](https://powerbi.microsoft.com) y, una vez allí, crear informes y paneles sumamente interactivos basados en los datos del libro. Luego, puede compartir sus recomendaciones con otras personas de la organización.

![Publicación de un libro en Power BI](media/service-publish-from-excel/pbi_uploadexport2.png)

Al publicar un libro en Power BI, hay algunas cosas que debe tener en cuenta:

* La cuenta que use para iniciar sesión en Office, OneDrive para la Empresa (si usa libros guardados ahí) y Power BI debe ser la misma.
* No se puede publicar un libro vacío ni un libro que no tenga contenido de Power BI compatible.
* No se pueden publicar libros cifrados ni protegidos con contraseña, ni libros con Information Rights Management.
* La publicación en Power BI requiere que la autenticación moderna esté habilitada (de forma predeterminada). En caso contrario, la opción Publicar no estará disponible en el menú Archivo.

## <a name="publish-your-excel-workbook"></a>Publicación del libro de Excel
Para publicar el libro de Excel, en Excel, seleccione **Archivo** > **Publicar** y seleccione **Cargar** o **Exportar**.

Si **carga** el libro en Power BI, puede interactuar con el libro tal como lo haría con Excel Online. También puede anclar las selecciones del libro en paneles de Power BI y compartir el libro, o los elementos seleccionados, a través de Power BI.

Si selecciona **Exportar**, puede exportar los datos de la tabla y su modelo de datos en un conjunto de datos de Power BI, que puede usar para crear informes y paneles de Power BI.

### <a name="local-file-publishing"></a>Publicación de archivos locales
Excel admite la publicación de archivos de Excel locales. Ya no hace falta guardarlos en OneDrive para la Empresa o SharePoint Online.

> [!IMPORTANT]
> Solo puede publicar archivos locales si usa Excel 2016 (o posterior) con una suscripción a Office 365. Las instalaciones independientes de Excel 2016 pueden publicar en Power BI, pero solo cuando el libro se guarda en OneDrive para la Empresa o SharePoint Online.
> 

Al seleccionar **Publicar**, puede seleccionar el área de trabajo en la que desea publicar. Si el archivo de Excel reside en OneDrive para la Empresa, solo se puede publicar en *Mi área de trabajo*. Si el archivo de Excel reside en una unidad local, puede publicar en *Mi área de trabajo* o en un área de trabajo compartida a la que tenga acceso.

![Publicar en Power BI](media/service-publish-from-excel/pbi_choose_workspace.png)

Dos opciones para colocar el libro en Power BI.

![Publicar en Power BI](media/service-publish-from-excel/pbi_uploadexport3.png)

Una vez publicado, el contenido del libro que publique se importa en Power BI, aparte del archivo local. Si desea actualizar el archivo en Power BI, debe volver a publicar la versión actualizada, o bien puede actualizar los datos mediante la configuración de una actualización programada, en el libro o en el conjunto de datos de Power BI.

### <a name="publishing-from-a-standalone-excel-installation"></a>Publicación desde una instalación de Excel independiente
Al publicar desde una instalación independiente de Excel, se debe guardar el libro en OneDrive para la Empresa. Seleccione **Guardar en la nube** y elija una ubicación en OneDrive para la Empresa.

![Guardado en OneDrive para la Empresa](media/service-publish-from-excel/pbi_savetoonedrive2.png)

Una vez guardado el libro en OneDrive para la Empresa, al seleccionar **Publicar**, tiene dos opciones para colocar el libro en Power BI, **cargar** o **exportar**:

![Opciones para Power BI](media/service-publish-from-excel/pbi_uploadexport2.png)

#### <a name="upload-your-workbook-to-power-bi"></a>Cargar el libro en Power BI
Si elige la opción **Cargar**, aparecerá el libro en Power BI tal como lo haría en Excel Online. Sin embargo, a diferencia de Excel Online, podrá disfrutar de opciones que le permiten anclar elementos de las hojas de cálculo en los paneles.

No puede editar el libro en Power BI, pero si necesita realizar algunos cambios en los datos, puede seleccionar **Editar** y, a continuación, edite el libro en Excel Online o ábralo en Excel en el equipo. Todos los cambios que realice se guardarán en el libro en OneDrive para la Empresa.

Cuando **carga**, no se crea ningún conjunto de datos en Power BI. El libro aparecerá en Informes, en el panel de navegación del área de trabajo. Los libros cargados en Power BI tienen un icono especial que los identifica como libros de Excel que se han cargado.

Elija la opción de **cargar** si solo tiene datos en hojas de cálculo o si tiene tablas dinámicas y gráficos que desea consultar en Power BI.

En Excel, el uso de la carga con la opción Publicar en Power BI es una experiencia similar a utilizar las opciones **Obtener datos > Archivo > OneDrive para la Empresa > Conectar, administrar y ver Excel en Power BI desde Power BI** en el explorador.

#### <a name="export-workbook-data-to-power-bi"></a>Exportar datos del libro a Power BI
Si elige la opción **Exportar**, se exportarán todos los datos admitidos en las tablas o los modelos de datos a un nuevo conjunto de datos en Power BI. Las hojas de Power View del libro se vuelven a crear en Power BI como informes.

Puede continuar la edición del libro. Al guardar los cambios, estos se sincronizan con el conjunto de datos en Power BI, normalmente en el plazo de una hora aproximadamente. Si necesita actualizaciones más inmediatas, puede seleccionar **Publicar** de nuevo desde Excel y los cambios se exportan inmediatamente. También se actualizan las visualizaciones de los informes y los paneles.

Elija la opción de **Publicar** si ha usado las opciones Obtener y Transformar datos o Power Pivot para cargar datos en un modelo de datos, o si el libro tiene hojas de Power View con visualizaciones que desea ver en Power BI.

En Excel, el uso de la **exportación** es muy similar a utilizar las opciones **Obtener datos > Archivo > OneDrive para la Empresa > Exportar datos de Excel en Power BI** desde Power BI en el explorador.

## <a name="publishing"></a>Publicación
Cuando se elige cualquiera de estas opciones, Excel inicia sesión en Power BI con la cuenta actual y, a continuación, publica el libro en el área de trabajo de Power BI. Puede supervisar la barra de estado en Excel para ver cómo progresa el proceso de publicación.

![barra de estado para la publicación en Power BI](media/service-publish-from-excel/pbi_publishingstatus.png)

Cuando haya terminado, puede ir a Power BI directamente desde Excel.

![ir a Power BI](media/service-publish-from-excel/pbi_gotopbi.png)

## <a name="next-steps"></a>Pasos siguientes
[Datos de Excel en Power BI](service-excel-workbook-files.md)  
¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

