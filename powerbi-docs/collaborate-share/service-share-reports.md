---
title: Filtrado y uso compartido de un informe de Power BI
description: Aprenda a filtrar un informe de Power BI y a compartirlo con los compañeros de la organización.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/29/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 0e086b6ab5ce3411697607bfbda25bb0b82c6dca
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406627"
---
# <a name="filter-and-share-a-power-bi-report"></a>Filtrado y uso compartido de un informe de Power BI
*Compartir* es una buena manera de permitir que otros usuarios tengan acceso a sus paneles e informes. ¿Qué sucede si quiere compartir una versión filtrada de un informe? Es posible que desee que el informe muestre únicamente los datos de una ciudad, un vendedor o un año específicos. En este artículo se explica cómo filtrar un informe y compartir la versión filtrada. Otra manera de compartir un informe filtrado es [agregar parámetros de consulta a la dirección URL del informe](service-url-filters.md). En ambos casos, el informe se filtra cuando los destinatarios lo abren por primera vez. Estos pueden borrar las selecciones de filtro del informe.

![Informe filtrado](media/service-share-reports/power-bi-share-filter-pane-report.png)

Power BI ofrece también [otras maneras de colaborar y distribuir sus informes](service-how-to-collaborate-distribute-dashboards-reports.md). Con el uso compartido, usted y sus destinatarios necesitarán una [licencia de Power BI Pro](../fundamentals/service-features-license-type.md) o que el contenido esté en una [capacidad premium](../admin/service-premium-what-is.md). 

## <a name="follow-along-with-sample-data"></a>Seguir adelante con los datos de ejemplo

En este artículo se usa la aplicación de plantilla de ejemplo Marketing y ventas. ¿Quiere probarlo? 

1. Instale la [aplicación de plantilla Marketing y ventas](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample?tab=Overview).
2. Seleccione la aplicación y, luego, **Explorar aplicación**.

   ![Exploración de los datos de ejemplo](media/service-share-reports/power-bi-sample-explore-data.png)

3. Seleccione el icono de lápiz para abrir el área de trabajo que instaló con la aplicación.

    ![Lápiz de edición de la aplicación](media/service-share-reports/power-bi-edit-pencil-app.png)

4. En la lista de contenido del área de trabajo, seleccione **Informes** y, después, seleccione el informe **PBIX del ejemplo de ventas y marketing**.

    ![Abrir el informe de ejemplo](media/service-share-reports/power-bi-open-sample-report.png)

    Ya está listo para continuar.

## <a name="set-a-filter-in-the-report"></a>Establecimiento de un filtro en el informe

Abra un informe en [Vista de edición](../consumer/end-user-reading-view.md) y aplique un filtro.

En este ejemplo, vamos a filtrar la página YTD Category (Categoría hasta la fecha) de la aplicación de plantilla Ejemplo de marketing y ventas para mostrar solo los valores donde **Región** es igual a **Central**. 
 
![Panel de filtro de informe](media/service-share-reports/power-bi-share-report-filter.png)

Guarde el informe.

## <a name="share-the-filtered-report"></a>Compartir el informe filtrado

1. Seleccione **Compartir**.

   ![Seleccionar Compartir](media/service-share-reports/power-bi-share.png)

2. Desactive **Enviar notificación por correo electrónico a los destinatarios**, de modo que pueda enviar un vínculo filtrado en su lugar, seleccione **Compartir informe con los filtros y las segmentaciones actuales** y, luego, seleccione **Compartir**.

    ![Informe compartido con filtros](media/service-share-reports/power-bi-share-with-filters.png)

4. Seleccione de nuevo **Compartir**.

   ![Seleccionar Compartir](media/service-share-reports/power-bi-share.png)

5. Seleccione la pestaña **Acceso** y, luego, **Administrar vistas de informe compartidas**.

    ![Administración de vistas de informe compartidas](media/service-share-reports/power-bi-manage-shared-report-views.png)

6. Haga clic con el botón derecho en la dirección URL que desee y seleccione **Copiar vínculo**.

    ![Copia del vínculo filtrado](media/service-share-reports/power-bi-copy-filtered-link.png)

7. Cuando comparta este vínculo, los destinatarios verán el informe filtrado. 

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones
Aspectos que se deben tener en cuenta sobre el uso compartido de los informes:

* Al compartir un conjunto de datos mediante la administración de permisos, el uso compartido de informes o paneles, o bien la publicación de una aplicación, se le concede acceso a todo el conjunto de datos a menos que se limite mediante la [seguridad de nivel de fila (RLS)](../admin/service-admin-rls.md). Los autores de informes pueden usar funciones que personalicen las experiencias del usuario al ver o interactuar con los informes, por ejemplo ocultar columnas, limitar las acciones en objetos visuales y otras. Esta experiencia de usuario personalizada no restringe los datos a los que los usuarios pueden acceder en el conjunto de datos. Use la [seguridad de nivel de fila (RLS)](../admin/service-admin-rls.md) en el conjunto de datos para que las credenciales de cada usuario determinen los datos a los que puede acceder.

## <a name="next-steps"></a>Pasos siguientes
* [Formas de compartir el trabajo en Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartir un panel](service-share-dashboards.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/).
* ¿Quiere hacer algún comentario? Vaya al [sitio de la comunidad de Power BI](https://community.powerbi.com/) para efectuar sus sugerencias.
