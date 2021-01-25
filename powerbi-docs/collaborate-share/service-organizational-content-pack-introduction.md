---
title: 'Paquetes de contenido organizativos en Power BI: introducción'
description: Obtenga más información sobre cómo empaquetar sus paneles, informes, libros de Excel y conjuntos de datos en paquetes de contenido organizativos para compartirlos con sus compañeros.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/12/2021
LocalizationGroup: Share your work
ms.openlocfilehash: 038a0c57fe5994b2b15b64dfe67f3eda77ef86f2
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2021
ms.locfileid: "98227109"
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Paquetes de contenido organizativos en Power BI: introducción

> [!NOTE]
> Los paquetes de contenido organizativos se están poniendo en desuso. Ahora es un buen momento para actualizar los paquetes de contenido a aplicaciones, si todavía no ha empezado. Vea la sección de hoja de ruta sobre la actualización de áreas de trabajo de esta entrada de blog [Announcing Power BI admins can upgrade classic workspaces](https://powerbi.microsoft.com/blog/announcing-power-bi-admins-can-upgrade-classic-workspaces-and-roadmap-update/) (Anuncio de que los administradores de Power BI pueden actualizar las áreas de trabajo clásicas) para obtener la escala de tiempo.
> 

¿Distribuye informes periódicamente por correo electrónico a su equipo? En su lugar, pruebe lo siguiente: empaquete los paneles, informes, libros de Excel y conjuntos de datos, y publíquelos en el equipo como *paquete de contenido organizativo*. Su equipo encontrará con facilidad los paquetes de contenido que cree, ya que todos ellos están en AppSource. Dado que son parte de Power BI, aprovechan todas las características de Power BI, como la exploración interactiva de datos, los nuevos objetos visuales, las preguntas y respuestas, la integración con otros orígenes de datos, la actualización de datos y mucho más.

![Captura de pantalla de un panel que muestra paquetes de contenido de la organización.](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

Es distinto crear paquetes de contenido que compartir paneles o colaborar en ellos en un área de trabajo. Lea [¿Cómo debo compartir paneles, informes e iconos?](service-how-to-collaborate-distribute-dashboards-reports.md) para decidir cuál es la mejor opción en su caso. 

En AppSource, puede explorar o buscar paquetes de contenido publicados en toda la organización o en los grupos de distribución o de seguridad, y en los [grupos de Microsoft 365 a los que pertenece](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Si no es miembro de un grupo específico, no verá los paquetes de contenido compartidos con ese grupo. Todos los miembros del grupo tienen el mismo permiso de solo lectura para tener acceso a los datos del paquete de contenido, los informes y los paneles (a menos que sea un origen de datos de SQL Server Analysis Services, también denominado SSAS, en cuyo caso los privilegios se heredan con el origen de datos).

Los paneles, informes y libros de Excel son de solo lectura, aunque puede copiar y usar los paneles e informes como punto de partida para crear su propia versión personalizada del paquete de contenido.

> [!NOTE]
> Los paquetes de contenido organizativos solo están disponibles si usted y sus compañeros tienen [licencias de Power BI Pro](../fundamentals/service-features-license-type.md).
> 
> 

## <a name="what-is-appsource"></a>¿Qué es *AppSource*?
Al publicar un paquete de contenido de la organización, se agrega a AppSource.  Este repositorio centralizado facilita a los miembros que exploren y descubran paneles, informes y conjuntos de datos publicados para ellos.  

* Para ver AppSource, seleccione **Obtener datos** > **Mi organización** > **Obtener**.

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>El ciclo de vida de un paquete de contenido organizativo
Cualquier usuario de Power BI Pro puede crear, publicar y acceder a los paquetes de contenido organizativos. Solo el creador del paquete de contenido puede modificar el libro y el conjunto de datos, programar la actualización y eliminarlo.

El ciclo de vida tiene un aspecto similar al siguiente:

1. En Power BI Pro, Nate crea un paquete de contenido y lo publica en el grupo de distribución Marketing. La configuración de actualización se hereda con el conjunto de datos y solo Nate puede cambiarla.
   
   > [!NOTE]
   > Si crea el paquete de contenido desde un [área de trabajo de Power BI](service-create-distribute-apps.md) al que pertenece, aunque salga de dicha área de trabajo, el resto de los usuarios podrán asumir su propiedad.
   > 
   > 
2. Nate envía un correo electrónico al grupo de distribución, informándoles acerca del nuevo paquete de contenido.
3. En Power BI Pro, Jane (que pertenece al grupo Distribución de marketing), busca este paquete de contenido en AppSource y se conecta a él. Ahora, tiene una copia de solo lectura. Sabe que es de solo lectura porque en el panel de navegación se muestra un icono de uso compartido a la izquierda del nombre del panel y el nombre del informe. Y, cuando Jane seleccione el panel, un icono de candado le permite saber que busca un panel de paquete de contenido. 
4. Digamos que Jane decide personalizarlo. Ahora, tendrá su propia copia del panel y los informes. Su trabajo no afectará al origen, al paquete de contenido original ni a otros miembros del grupo de distribución. Ahora, cada uno trabaja en su propia copia del panel y el informe.
5. Nate realiza cambios en el panel y, cuando está listo, publica una nueva versión del paquete de contenido.
   
   * Julio, otro miembro del grupo de distribución, no personalizó el paquete de contenido original. Los cambios nuevos se aplican automáticamente en su versión del paquete de contenido.  
   * Jane personalizó el paquete de contenido. Jane recibe una notificación de que hay una nueva versión.  Puede ir a AppSource y obtener el paquete de contenido actualizado sin perder su versión personalizada. Jane tiene ahora dos versiones: la versión personalizada y el paquete de contenido actualizado.
6. Imaginemos que Nate cambia la configuración de seguridad. Julio y Jane ya no tienen acceso al contenido. Digamos que se les ha eliminado del grupo de distribución Marketing.
   
   * Julio no personalizó el paquete de contenido original, por lo que el contenido se quita automáticamente. 
   * Jane personalizó el paquete de contenido. La próxima vez que abra el panel, todos los iconos del paquete de contenido original habrán desaparecido, pero aún se mostrarán los iconos que ancló desde otros informes (que todavía tiene permiso para usar). Los informes y el conjunto de datos asociados ya no están disponibles (y no aparecen en el panel de navegación).
7. O bien, Nate elimina el paquete de contenido.
   
   * Julio no personalizó el paquete de contenido original, por lo que el contenido se quita automáticamente. 
   * Jane personalizó el paquete de contenido. La próxima vez que abra el panel, todos los iconos del paquete de contenido original habrán desaparecido, pero aún se mostrarán los iconos que ancló desde otros informes. Los informes y el conjunto de datos asociados ya no están disponibles (y no aparecen en el panel de navegación).

## <a name="data-security"></a>Seguridad de los datos
Todos los miembros del grupo de distribución tienen los mismos permisos con respecto a los datos que el creador del paquete de contenido. La única excepción son los conjuntos de datos tabulares de instancias locales de SQL Server Analysis Services (SSAS). Como los informes y paneles se conectan de forma dinámica al modelo de SSAS local, se usan las credenciales de cada miembro del grupo de distribución para determinar a qué datos pueden acceder.

## <a name="next-steps"></a>Pasos siguientes
* [Creación y publicación de un paquete de contenido organizativo](service-organizational-content-pack-create-and-publish.md)
* [Creación y distribución de una aplicación en Power BI](service-create-distribute-apps.md) 
* [Conceptos básicos para los diseñadores en el servicio Power BI](../fundamentals/service-basic-concepts.md)
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
