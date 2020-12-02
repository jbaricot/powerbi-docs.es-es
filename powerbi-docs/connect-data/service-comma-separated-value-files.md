---
title: Obtención de datos de archivos .CSV (valores separados por comas)
description: Aprenda cómo obtener datos de archivos CSV en Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 01bef505d48f28df869bf2be705dcda963b3d0f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403338"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>Obtención de datos de archivos .CSV (valores separados por comas)
![Icono de CSV](media/service-comma-separated-value-files/csv_icon.png)

Los archivo de valores separados por coma, conocidos como .CSV, son archivos de texto simples con filas de datos donde cada valor se separa por una coma. Estos tipos de archivos pueden contener grandes cantidades de datos con un tamaño de archivo relativamente pequeño, por lo que son un origen de datos ideal para Power BI. Puede descargar un archivo .CSV de ejemplo [aquí](https://go.microsoft.com/fwlink/?LinkID=619356).

Si tiene un archivo .CSV, es el momento de consultarlo en el sitio de Power BI como un conjunto de datos para poder empezar a explorar los datos, crear algunos paneles y compartir sus conocimientos con otros usuarios.

>[!TIP]
>Muchas organizaciones generan un archivo .CSV con datos actualizados cada día. Para asegurarse de que el conjunto de datos en Power BI permanece sincronizado con el archivo actualizado, asegúrese de que el archivo se guarda en OneDrive con el mismo nombre.

## <a name="where-your-file-is-saved-makes-a-difference"></a>La ubicación donde guarda el archivo marca la diferencia
**Local**: si guarda el archivo .CSV en una unidad local en el equipo o en otra ubicación de su organización, desde Power BI puede *importar* el archivo en Power BI. El archivo sigue estando en la unidad local, no se ha importado realmente a Power BI. Lo que sucede en realidad es que se crea un nuevo conjunto de datos en Power BI y los datos del archivo .CSV se cargan en el conjunto de datos.

**OneDrive para la Empresa**: si dispone de OneDrive para la Empresa, la manera más eficaz de mantener su archivo .CSV y de mantener sincronizados el conjunto de datos, los informes y los paneles en Power BI es iniciar sesión en OneDrive con la misma cuenta que inicia sesión en Power BI. Dado que tanto Power BI como OneDrive están en la nube, Power BI se *conecta* al archivo en OneDrive cada hora aproximadamente. Si se detectan cambios, se actualizarán automáticamente el conjunto de datos, los informes y los paneles en Power BI.

**OneDrive - Personal**: si guarda los archivos en su propia cuenta de OneDrive, conseguirá muchas ventajas idénticas a las que obtendría con OneDrive para la Empresa. La principal diferencia estriba en que cuando se conecta al archivo por primera vez (mediante Obtener datos > Archivos > OneDrive – Personal) debe iniciar sesión en OneDrive con la cuenta de Microsoft, que normalmente es distinta de la que usa para iniciar sesión en Power BI. Al iniciar sesión en OneDrive con la cuenta de Microsoft, asegúrese de seleccionar la opción Mantener la sesión iniciada. De este modo, Power BI podrá conectarse al archivo cada hora aproximadamente y asegurarse de que el conjunto de datos está sincronizado.

**SharePoint: sitios de grupo**: guardar los archivos de Power BI Desktop en SharePoint: sitios de grupo, es prácticamente igual a guardarlos en OneDrive para la Empresa. La diferencia más importante es cómo se conecta al archivo desde Power BI. Puede especificar una dirección URL o conectarse a la carpeta raíz.

## <a name="import-or-connect-to-a-csv-file"></a>Importación de un archivo .CSV o conexión a él
>[!IMPORTANT]
>El tamaño máximo de archivo que se puede importar en Power BI es 1 gigabyte.

1. En Power BI, en el panel del navegador, haga clic en **Obtener datos**.
   
   ![Captura de pantalla de Obtener datos de Power BI Desktop, donde se muestra el botón del panel de navegación.](media/service-comma-separated-value-files/csv_get_data_button.png)
2. En **Archivos**, haga clic en **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Archivos, en el que se muestra el botón Obtener.](media/service-comma-separated-value-files/csv_files_get.png)
3. Busque el archivo.
   
   ![Captura de pantalla de cuatro iconos para buscar el archivo, en la que se muestra la selección de Archivo local, OneDrive para la Empresa, OneDrive personal y SharePoint.](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>Pasos siguientes
**Exploración de los datos**: cuando obtenga datos del archivo en Power BI, será el momento de explorarlos. Simplemente haga clic con el botón derecho en el nuevo conjunto de datos y, a continuación, haga clic en **Explorar**.

**Programar actualización**: si el archivo se guarda en una unidad local, puede configurar la actualización programada para mantener al día el conjunto de datos y los informes de Power BI. Para más información, consulte [Actualizar datos en Power BI](refresh-data.md). Si el archivo está guardado en OneDrive, Power BI se sincronizará automáticamente con él cada hora aproximadamente.

