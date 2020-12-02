---
title: Conexión a una base de datos de Google BigQuery en Power BI Desktop
description: Conéctese fácilmente a Google BigQuery y úselo en Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 7cffba9178d4eec0bfd468040b7551768aab7f1d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405891"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Conexión a una base de datos de Google BigQuery en Power BI Desktop
En Power BI Desktop, puede conectarse a una base de datos de Google **BigQuery** y usar los datos subyacentes como con cualquier otro origen de datos en Power BI Desktop.

## <a name="connect-to-google-bigquery"></a>Conectarse a Google BigQuery
Para conectarse a una base de datos de Google **BigQuery**, seleccione **Obtener datos** en la cinta **Inicio** de Power BI Desktop. Seleccione **Base de datos** en las categorías de la izquierda para que se muestre **Google BigQuery**.

![Cuadro de diálogo Obtener datos para Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_01.png)

En la ventana de **Google BigQuery** que aparece, inicie sesión en su cuenta de Google BigQuery y seleccione **Conectar**.

![Iniciar sesión en Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

Cuando haya iniciado sesión, verá la ventana siguiente que indica que se ha autenticado. 

![Sesión iniciada en Google](media/desktop-connect-bigquery/connect_bigquery_02b.png)

Una vez que se haya conectado correctamente, aparece la ventana **Navegador**, en la que se muestran los datos disponibles en el servidor, desde donde puede seleccionar uno o varios elementos para importar y usar en **Power BI Desktop**.

![Datos de Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones
Hay algunos límites y consideraciones que se deben tener en cuenta con el conector de Google **BigQuery**:

* El conector de Google BigQuery está disponible en Power BI Desktop y en el servicio Power BI. En el servicio Power BI, se puede acceder al conector mediante la conexión de nube a nube de Power BI a Google BigQuery.

* Puede usar Power BI con el **proyecto de facturación** de Google BigQuery. De forma predeterminada, Power BI usa el primer proyecto de la lista que se devuelve para el usuario. 

  Para personalizar el comportamiento del proyecto de facturación cuando se usa con Power BI, especifique la siguiente opción en la M subyacente del paso de origen, que se puede personalizar mediante el **editor de Power Query** en Power BI Desktop:

  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])
  ```

  A partir de la versión de septiembre de 2020, se ha habilitado la compatibilidad con la [API de almacenamiento de Google BigQuery](https://cloud.google.com/bigquery/docs/reference/storage). Esta característica está habilitada de forma predeterminada y se controla mediante el argumento booleano opcional denominado "UseStorageApi". Puede que algunos clientes encuentren problemas con esta característica si usan permisos exhaustivos. En este escenario, es posible que vea el siguiente mensaje de error:

  `ERROR [HY000] [Microsoft][BigQuery] (131) Unable to authenticate with Google BigQuery Storage API. Check your account permissions`

  Para resolver este problema, ajuste los permisos de usuario de la API de almacenamiento. Asigne estos permisos de la API de almacenamiento:

  - `bigquery.readsessions.create`: crea una sesión de lectura a través de la API de almacenamiento de BigQuery.
  - `bigquery.readsessions.getData`: lee datos de una sesión de lectura a través de la API de almacenamiento de BigQuery.
  - `bigquery.readsessions.update`: actualiza una sesión de lectura a través de la API de almacenamiento de BigQuery.

  Estos permisos se proporcionan normalmente en el rol BigQuery.User. Para más información, consulte [Roles y permisos predefinidos de Google BigQuery](https://cloud.google.com/bigquery/docs/access-control).
  
  Si los pasos anteriores no resuelven el problema o si quiere deshabilitar la compatibilidad con la API de almacenamiento, cambie la consulta a lo siguiente:
  ```
  Source = GoogleBigQuery.Database([UseStorageApi=false])
  ```
  También puede cambiar la consulta a lo siguiente, si ya usa un proyecto de facturación:
  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here", UseStorageApi=false])
  ```

## <a name="next-steps"></a>Pasos siguientes
Hay todo tipo de datos a los que puede conectarse con Power BI Desktop. Para obtener más información sobre orígenes de datos, consulte los siguientes recursos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   
