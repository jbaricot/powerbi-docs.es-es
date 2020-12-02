---
title: Actualización de un conjunto de datos desde OneDrive o SharePoint Online
description: Actualización de un conjunto de datos creado a partir de un archivo de Power BI Desktop en OneDrive o SharePoint Online
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: 317b879e8e9d70019aa60b60a6586ac747dcc185
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410836"
---
# <a name="refresh-a-dataset-stored-on-onedrive-or-sharepoint-online"></a>Actualización de un conjunto de datos almacenado en OneDrive o SharePoint Online
Importar archivos desde OneDrive o SharePoint Online en el servicio Power BI es una excelente manera de asegurarse de que el trabajo que está realizando en Power BI Desktop permanece sincronizado con el servicio Power BI.

## <a name="advantages-of-storing-a-power-bi-desktop-file-on-onedrive-or-sharepoint-online"></a>Ventajas de almacenar un archivo de Power BI Desktop en OneDrive o SharePoint Online
Cuando almacena un archivo de Power BI Desktop en OneDrive o SharePoint Online, todos los datos cargados en el modelo del archivo se importan en el conjunto de datos. Los informes creados en el archivo se cargan en **Informes** en el servicio Power BI. Supongamos que realiza cambios en el archivo en OneDrive o SharePoint Online. Estos cambios pueden incluir la adición de nuevas medidas, el cambio de los nombres de columnas o la edición de visualizaciones. Una vez que guarde el archivo, el servicio Power BI sincroniza también esos cambios, por lo general en una hora.

Para realizar una actualización manual única directamente en Power BI Desktop, seleccione **Actualizar** en la cinta de opciones **Inicio**. Cuando se selecciona **Actualizar**, se actualiza el modelo del archivo con los datos actualizados del origen de datos original. Este tipo de actualización ocurre por completo dentro de la propia aplicación de Power BI Desktop. Es diferente de una actualización programada o manual en Power BI, y es importante comprender la diferencia.

![Captura de pantalla de la cinta Inicio de Power BI Desktop, donde se muestra la selección de Actualizar.](media/refresh-desktop-file-onedrive/pbix-refresh.png)

Al importar el archivo de Power BI Desktop desde OneDrive o SharePoint Online, los datos y otra información acerca del modelo se cargan en un conjunto de datos en Power BI. Desea actualizar el conjunto de datos en el servicio Power BI porque eso es en lo que se basan los informes. Dado que los orígenes de datos son externos, puede actualizar manualmente el conjunto de datos mediante **Actualizar ahora** o bien puede configurar una programación de actualización mediante **Programar actualización**. 

![Captura de pantalla del conjunto de datos en Power BI Desktop, donde se muestra la selección de Programar actualización.](media/refresh-desktop-file-onedrive/powerbi-service-refresh.png)

Al actualizar el conjunto de datos, Power BI no se conecta al archivo en OneDrive o SharePoint Online para consultar los datos actualizados. Utiliza la información del conjunto de datos para conectarse directamente a los orígenes de datos y consultar los datos actualizados. A continuación, carga datos en el conjunto de datos. Estos datos actualizados en el conjunto de datos no se vuelven a sincronizar con el archivo en OneDrive o SharePoint Online.

## <a name="whats-supported"></a>¿Qué es compatible?
Power BI admite las opciones **Actualizar** y **Programar actualización** para los conjuntos de datos creados a partir de archivos de Power BI Desktop importados desde una unidad local donde usa **Obtener datos** o el **Editor de consultas** para conectarse a cualquiera de los siguientes orígenes de datos y cargar datos de ellos.

> [!NOTE]
> Se admite la actualización de OneDrive para conjuntos de datos de conexión dinámica. Sin embargo, en el escenario de actualización de OneDrive no se admite el cambio del conjunto de datos de conexión dinámica, de un conjunto de datos a otro en un informe ya publicado.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
* Todos los orígenes de datos en línea que se muestran en **Obtener datos** y en el **Editor de consultas** de Power BI Desktop.
* Todos los orígenes de datos locales que se muestran en **Obtener datos** y en el **Editor de consultas** de Power BI Desktop, excepto el archivo Hadoop (HDFS) y Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](../includes/refresh-datasources.md)]

> [!NOTE]
> Es necesario tener una puerta de enlace instalada y en ejecución para que Power BI se pueda conectar a orígenes de datos locales y actualizar el conjunto de datos.
> 
> 

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive o OneDrive para la Empresa. ¿Cuál es la diferencia?
Si tiene OneDrive personal y OneDrive para la Empresa, debería mantener los archivos que quiere importar en Power BI en OneDrive para la Empresa. Esta es la razón: es probable que use dos cuentas diferentes para iniciar sesión en ambos.

La conexión a OneDrive para la Empresa en Power BI es fácil porque su cuenta de Power BI suele coincidir con su cuenta de OneDrive para la Empresa. Con OneDrive personal, normalmente inicia sesión con otra [cuenta Microsoft](https://account.microsoft.com).

Si inicia sesión con su cuenta Microsoft, asegúrese de seleccionar **Mantener la sesión iniciada**. Posteriormente, Power BI podrá sincronizar todas las actualizaciones que realice en el archivo en Power BI Desktop con los conjuntos de datos de Power BI.

![Captura de pantalla del cuadro de diálogo Iniciar sesión, con la casilla Mantener la sesión iniciada activada.](media/refresh-desktop-file-onedrive/refresh_signin_keepmesignedin.png)

Si ha cambiado sus credenciales de Microsoft, no puede sincronizar los cambios entre el archivo en OneDrive y el conjunto de datos en Power BI. Tendrá que conectarse a OneDrive e importar el archivo de nuevo desde ahí.

## <a name="how-do-i-schedule-refresh"></a>¿Cómo se programa una actualización?
Al configurar una programación de actualización, Power BI se conecta directamente a los orígenes de datos. Power BI usa la información de conexión y las credenciales del conjunto de datos para consultar los datos actualizados. A continuación, Power BI carga los datos actualizados en el conjunto de datos. Luego actualiza las visualizaciones de informes y los paneles basados en ese conjunto de datos en el servicio Power BI.

Para más información sobre cómo configurar la actualización programada, consulte [Configuración de actualización programada](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Si se produce algún problema
Si se produce algún problema, suele ser porque Power BI no puede iniciar sesión en los orígenes de datos. Es posible que también se produzcan problemas si el conjunto de datos intenta conectarse a un origen de datos local pero la puerta de enlace está sin conexión. Para evitar estos problemas, asegúrese de que Power BI puede iniciar sesión en los orígenes de datos. Intente iniciar sesión en los orígenes de datos en **Credenciales del origen de datos**. A veces, cambia la contraseña que usa para iniciar sesión en un origen de datos o Power BI cierra la sesión desde un origen de datos.

Si guarda los cambios en el archivo de Power BI Desktop en OneDrive y no los ve en Power BI en un plazo aproximado de una hora, podría ser porque Power BI no puede conectarse a OneDrive. Intente conectarse de nuevo al archivo en OneDrive. Si se le pide que inicie sesión, asegúrese de seleccionar **Mantener la sesión iniciada**. Dado que Power BI no pudo conectarse a OneDrive para la sincronización con el archivo, deberá volver a importar el archivo.

Asegúrese de dejar seleccionada la opción **Enviar un correo con los errores de actualización** . Si no se puede realizar una actualización programada, deseará saberlo inmediatamente.

## <a name="troubleshooting"></a>Solución de problemas
A veces, la actualización de datos no funciona según lo previsto. Normalmente encontrará problemas con la actualización de datos cuando esté conectado con una puerta de enlace. Consulte en los artículos de solución de problemas relacionados con la puerta de enlace las herramientas y los problemas conocidos.

[Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md)

[Solución de problemas de Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

¿Tiene más preguntas? Pruebe a preguntar a la [comunidad de Power BI](https://community.powerbi.com/).
