---
title: 'Paquetes de contenido organizativo: Administrar y actualizar'
description: Obtenga más información sobre cómo administrar, actualizar y eliminar paquetes de contenido organizativos en Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/02/2018
LocalizationGroup: Share your work
ms.openlocfilehash: fb47df4f81225d8e55fbc637331f85f36337aade
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406443"
---
# <a name="manage-update-and-delete-organizational-content-packs"></a>Administración, actualización y eliminación de paquetes de contenido organizativos
> [!NOTE]
> No se pueden crear paquetes de contenido de la organización ni instalarlos en las nuevas experiencias de áreas de trabajo. Ahora es un buen momento para actualizar los paquetes de contenido a aplicaciones, si todavía no ha empezado. Obtenga [más información sobre la nueva experiencia de áreas de trabajo](service-create-the-new-workspaces.md).
> 

Puede empaquetar y compartir sus paneles, informes, libros de Excel y conjuntos de datos con sus compañeros como [paquetes de contenido de la organización](service-organizational-content-pack-introduction.md). Sus compañeros pueden usarlos tal cual o crear sus propias copias.

Es distinto crear paquetes de contenido que compartir paneles o colaborar en ellos en un grupo. Lea [¿Cómo debo compartir paneles, informes e iconos?](service-how-to-collaborate-distribute-dashboards-reports.md) para decidir cuál es la mejor opción en su caso.

Algunas tareas del paquete de contenido de la organización solo puede realizarlas el creador del paquete de contenido:

* Publicar de nuevo.
* Restringir o ampliar el acceso al paquete de contenido.
* Establecer y cambiar la actualización programada.
* Eliminar el paquete de contenido.

## <a name="modify-and-re-publish-an-organizational-content-pack"></a>Modificación y nueva publicación de un paquete de contenido organizativo
Si realiza cambios en el panel del paquete de contenido original, el informe o el libro de Excel, Power BI le solicitará que vuelva a publicarlo. Además, como creador del paquete de contenido, puede actualizar cualquiera de las opciones seleccionadas en la ventana Crear paquete de contenido al crear el paquete de contenido original. 

## <a name="republish-with-new-content"></a>Nueva publicación con nuevo contenido
Cuando realiza y guarda un cambio en el panel que ha incluido en un paquete de contenido, Power BI le recuerda que lo actualice para que los demás puedan ver los cambios. Por ejemplo, si ancla un nuevo icono o simplemente cambia el nombre del panel.

1. Seleccione **Ver paquetes de contenido** en el mensaje.
   
   ![Captura de pantalla de un cuadro de diálogo de mensaje para seleccionar Ver paquetes de contenido.](media/service-organizational-content-pack-manage-update-delete/pbi_contpkchangesmessage.png)
2. O bien seleccione el icono de engranaje de la esquina superior derecha ![Captura de pantalla del icono de engranaje.](media/service-organizational-content-pack-manage-update-delete/cog.png) y seleccione **Ver paquete de contenido**.
   
   ![Captura de pantalla del icono de engranaje de la esquina superior derecha.](media/service-organizational-content-pack-manage-update-delete/pbi_contpkview.png)
   
   Observe el icono de advertencia. ![Captura de pantalla del icono de advertencia.](media/service-organizational-content-pack-manage-update-delete/pbi_contpkwarningicon.png).  Esto le permite saber que ha modificado de alguna manera el paquete de contenido y ya no coincide con el que publicó.
3. Seleccione **Editar**.  
4. Realice los cambios necesarios en la ventana **Actualizar paquete de contenido** y seleccione **Actualizar**. Aparece un mensaje de operación **correcta** .
   
   * Para los miembros de grupo que no personalizaron el paquete de contenido, la actualización se aplicará automáticamente.
   * Los miembros del grupo que personalizaron el paquete de contenido recibirán una notificación de la existencia de una nueva versión.  Pueden ir a AppSource y obtener el paquete de contenido actualizado sin perder su versión personalizada.  Ahora tendrán dos versiones: la versión personalizada y el paquete de contenido actualizado.  En la versión personalizada, todos los iconos del paquete de contenido original se habrán eliminado.  Pero los iconos que ancló desde otros informes seguirán apareciendo. Sin embargo, si el propietario del paquete de contenido elimina el conjunto de datos en que se basa el paquete de contenido, se eliminará todo el informe.  

## <a name="update-the-audience-expand-or-restrict-access"></a>Actualice el público: amplíe o restrinja el acceso
Otra modificación disponible para creadores de los paquetes de contenido es ampliar y restringir el acceso al paquete de contenido.  Quizás publicó un paquete de contenido para un público amplio y decidió restringir el acceso a un grupo más reducido.  

1. Seleccione el icono de engranaje ![Captura de pantalla del icono de engranaje.](media/service-organizational-content-pack-manage-update-delete/cog.png) y elija **Ver paquetes de contenido**.
2. Seleccione **Editar**. 
3. Realice los cambios necesarios en la ventana **Actualizar paquete de contenido** y seleccione **Actualizar**. Por ejemplo, elimine el grupo de distribución original en el campo **Grupos específicos** y reemplácelo por otro grupo de distribución (que tenga menos miembros).
   
   Aparece un mensaje de operación correcta.
   
   Para cualquier compañero de trabajo que no forme parte del nuevo alias:
   
   * Para los miembro del grupo que no personalizaron el paquete de contenido, el panel y los informes asociados a ese paquete de contenido ya no estarán disponibles, y el paquete de contenido no aparecerá en el panel de navegación.
   * Para los miembros del grupo que personalizaron el paquete de contenido, la próxima vez que abran el panel personalizado, todos los iconos del paquete de contenido original habrán desaparecido.  Pero los iconos que ancló desde otros informes seguirán apareciendo. Los informes y los conjuntos de datos del paquete de contenido original ya no están disponibles, y el paquete de contenido no aparece en el panel de navegación.   

## <a name="refresh-an-organizational-content-pack"></a>Actualización de un paquete de contenido organizativo
Como creador del paquete de contenido puede [programar la actualización de los conjunto de datos](../connect-data/refresh-data.md).  Al crear y cargar el paquete de contenido, dicha programación de actualización se carga con los conjuntos de datos. Si cambia la programación de actualización, debe volver a publicar el paquete de contenido (consulte más arriba).

## <a name="delete-an-organizational-content-pack-from-appsource"></a>Eliminación de un paquete de contenido de la organización de AppSource
Solo puede eliminar de AppSource aquellos paquetes de contenido si lo ha creado. Si ha creado un paquete de contenido organizativo en un área de trabajo y, después, decide eliminar esa área de trabajo, asegúrese de eliminar primero el paquete de contenido. Si elimina el área de trabajo sin eliminar primero el paquete de contenido, se perderá todo el acceso a estos paquetes de contenido y tendrá que ponerse en contacto con Soporte técnico de Microsoft para pedir ayuda. 

> [!TIP]
> Puede [eliminar la conexión a un paquete de contenido](service-organizational-content-pack-disconnect.md) que no ha creado. Eso no elimina el paquete de contenido de AppSource.
> 
> 

1. Para eliminar un paquete de contenido de AppSource, vaya al área de trabajo en la que creó el paquete de contenido, seleccione el icono del engranaje ![Captura de pantalla del icono de engranaje.](media/service-organizational-content-pack-manage-update-delete/cog.png) y elija **Ver paquetes de contenido**.
2. Seleccione **Eliminar \> Eliminar**. 
   
   * Para los miembros del grupo que no personalizaron el paquete de contenido, se quitan automáticamente el panel y los informes asociados a ese paquete de contenido. Ya no están disponibles y el paquete de contenido no aparece en el panel de navegación.
   * Para los miembros del grupo que personalizaron el paquete de contenido, la próxima vez que abran el panel personalizado, todos los iconos del paquete de contenido original habrán desaparecido.  Pero los iconos que ancló desde otros informes seguirán apareciendo. Los informes y los conjuntos de datos del paquete de contenido original ya no están disponibles, y el paquete de contenido no aparece en el panel de navegación.   

## <a name="next-steps"></a>Pasos siguientes
* [Introducción a los paquetes de contenido organizativos](service-organizational-content-pack-introduction.md)
* [Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md) 
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

