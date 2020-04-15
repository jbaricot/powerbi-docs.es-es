---
title: Tipos de licencias para consumidores de Power BI
description: Obtenga información sobre los diferentes tipos de licencias y cómo averiguar cuál tiene.
author: mihart
ms.reviewer: lukasz
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/27/2020
ms.author: mihart
LocalizationGroup: consumers
ms.openlocfilehash: 4615bae84ddeb3d3e0b3c471a6b9d6bcf7eda406
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267305"
---
# <a name="types-of-power-bi-licenses"></a>Tipos de licencias de Power BI

[!INCLUDE[consumer-appliesto-ynnn](../includes/consumer-appliesto-ynnn.md)]

Como *consumidor*, usa el servicio Power BI para explorar informes y paneles con el fin de tomar decisiones empresariales. Si ha estado usando Power BI durante un tiempo o ha estado conversando con sus compañeros *diseñadores*, probablemente haya descubierto que hay algunas características que solo funcionan si tiene un determinado tipo de licencia o suscripción. 

En este artículo se explican las diferencias entre las licencias de usuario y las suscripciones de la organización, y cómo funcionan conjuntamente en sus versiones gratuita, Pro, Premium y capacidad Premium. También verá cómo averiguar la combinación de licencia y suscripción que está usando.  

![Diagrama que muestra cómo se conectan las licencias](media/end-user-license/power-bi-venn.png)

Para comenzar, nos centraremos en las dos categorías de licencias: suscripción de usuario y suscripción de organización. Nuestro punto de partida será la funcionalidad predeterminada disponible con cada una de ellas. A continuación, veremos cómo su administrador de Power BI y los propietarios de contenido pueden usar roles y permisos para modificar las capacidades predeterminadas de las licencias y las suscripciones. 

Por ejemplo, incluso si una licencia lo permite, el administrador puede limitar la capacidad de hacer cosas, como exportar datos, usar consultas con lenguaje natural en Preguntas y respuestas o publicar en la Web. Y, cuando un *diseñador* de informes asigna contenido a un [área de trabajo](end-user-workspaces.md), puede asignarlo a usted a un rol de área de trabajo. Los roles determinan lo que puede y no puede hacer en esa área de trabajo. El *diseñador* puede ajustar aún más los límites de la licencia mediante la configuración de permisos. En otras palabras... es complicado. Espero que este artículo aclare toda o casi toda la confusión.

## <a name="per-user-licenses"></a>Licencias por usuario
El primer tipo de licencia es una licencia **por usuario**. Cada usuario del servicio Power BI tiene una licencia gratuita o una licencia Pro. Ciertas características están reservadas para los usuarios con licencias Pro.  

- Una **licencia de Power BI Pro (sin suscripción Premium)** permite a un usuario colaborar con otros usuarios de Pro creando y compartiendo contenido. Solo los usuarios con una licencia Pro pueden publicar informes, suscribirse a paneles e informes y colaborar con compañeros en áreas de trabajo. 

    ![Imagen de usuarios de Pro](media/end-user-license/power-bi-pro.jpg)

    Power BI Pro es una licencia de usuario individual que permite a los usuarios leer e interactuar con los informes y paneles que otros usuarios han publicado en el servicio Power BI. Los usuarios con este tipo de licencia pueden compartir contenido y colaborar con otros usuarios de Power BI Pro. Solo los usuarios de Power BI Pro pueden publicar o compartir contenido con otros usuarios o consumir contenido que han creado otros usuarios. La excepción a esto es el contenido que se hospeda en [capacidad Premium de Power BI](#understanding-premium-and-premium-capacity). (Para obtener más información, vea la sección sobre la [capacidad Premium de Power BI](#understanding-premium-and-premium-capacity) a continuación). Las licencias de Pro suelen utilizarlas los *diseñadores* de informes y los desarrolladores. 


- **Una licencia gratuita de Power BI independiente (sin una suscripción Premium)** , aunque es práctica, es la que utilizan los usuarios que empiezan a usar Power BI o que crean contenido para ellos mismos. Vea [Registro en Power BI como usuario individual](../service-self-service-signup-for-power-bi.md).   

    Una licencia de usuario independiente gratuita es perfecta para alguien que utilice los ejemplos de Microsoft para aprender a usar Power BI. Los usuarios con licencias gratuitas independientes no pueden ver el contenido compartido por otras personas ni compartir su propio contenido con otros usuarios de Power BI. 

    ![Imagen de usuarios independientes](media/end-user-license/power-bi-free-license.jpg)

    Todos los clientes con una licencia independiente gratuita pueden registrarse para disfrutar de una [licencia de prueba gratuita de Power BI Pro](../service-self-service-signup-for-power-bi.md). La versión de prueba le proporciona toda la eficacia y la funcionalidad de un usuario de Power BI Pro.

    ![invitación a la prueba de Pro](media/end-user-license/power-bi-pro-trial.png)

- **Una licencia gratuita de Power BI con una suscripción Premium** Cuando una organización tiene una suscripción Premium, los administradores y los usuarios de Pro pueden asignar áreas de trabajo a la *capacidad Premium* y conceder a los usuarios con licencia gratuita acceso a esas áreas de trabajo. Un área de trabajo en una capacidad Premium es un espacio en el que los usuarios de Pro pueden compartir y colaborar con usuarios que tienen una licencia gratuita, sin necesidad de que estos últimos tengan cuentas de Pro. Dentro de esas áreas de trabajo, los usuarios con licencia gratuita tienen permisos elevados; pueden colaborar y compartir, exportar datos, suscribirse, interactuar con filtros y mucho más. 

¿Todo claro hasta el momento?  Aceptar. Echemos un vistazo más de cerca a la **capacidad Premium**.

## <a name="understanding-premium-and-premium-capacity"></a>Descripción de las licencias Premium y capacidad Premium
Premium es una suscripción de **organización**. Se puede decir que es como agregar una capa de características y funcionalidad encima de todas las licencias **por usuario** de Power BI de una organización. 

Cuando una organización adquiere una licencia Premium, el administrador suele asignar licencias de Pro a los empleados que van a crear y compartir contenido. Además, el administrador asigna licencias gratuitas a todos los usuarios que vayan a consumir ese contenido. Los usuarios de Pro crean [áreas de trabajo de aplicaciones](end-user-workspaces.md) y agregan contenido (paneles, informes, aplicaciones) a esas áreas de trabajo. Para permitir que los usuarios con licencias gratuitas colaboren en esas áreas de trabajo, el administrador o el usuario Pro guarda las áreas de trabajo en la *capacidad Premium*. 

Cuando una organización adquiere una licencia de capacidad Premium, obtiene capacidad en el servicio Power BI asignada exclusivamente a ella. No se comparte con otras organizaciones. La capacidad es compatible con hardware dedicado totalmente administrado por Microsoft. Las organizaciones pueden aplicar la capacidad que tienen dedicada de forma global o asignarla a áreas de trabajo específicas. Una organización puede tener todas las áreas de trabajo en su capacidad o solo algunas de ellas. Puede identificar un área de trabajo en la capacidad Premium por su icono de rombo. ![icono de rombo](media/end-user-license/power-bi-diamond.png).  Un área de trabajo en una capacidad Premium es un espacio en el que los usuarios de Pro pueden compartir y colaborar con usuarios que tienen una licencia gratuita, sin necesidad de que estos últimos tengan cuentas de Pro. 

En la capacidad Premium, las licencias de Pro siguen siendo necesarias para los diseñadores de contenido. Los diseñadores crean áreas de trabajo de aplicaciones, se conectan a orígenes de datos, modelan los datos y crean paneles e informes que se comparten directamente o se empaquetan y comparten como aplicaciones. Los usuarios que no tienen una licencia de Pro pueden acceder a un área de trabajo de aplicación que se encuentre en Power BI Premium, siempre que esa área de trabajo esté en una *capacidad* Premium y que el propietario del área de trabajo les dé permiso.

En el diagrama siguiente, el lado izquierdo representa a los usuarios de Pro que crean y comparten contenido en áreas de trabajo de aplicaciones. 

- El **área de trabajo A** se creó en una organización que no tiene una suscripción Premium. 

- El **área de trabajo B** se creó en una organización que tiene una suscripción Premium, pero esta área de trabajo en particular no se guardó en la capacidad Premium. El área de trabajo no tiene el icono de diamante.

- El **área de trabajo C** se creó en una organización que tiene una suscripción Premium y se guardó en la capacidad Premium. Esta área de trabajo tiene un icono de diamante.  

![Imagen de usuarios de Pro](media/end-user-license/power-bi-sharing-scenarios.jpg)

El *diseñador* de Power BI Pro puede compartir y colaborar con otros usuarios de Pro en cualquiera de las tres áreas de trabajo, siempre que el diseñador comparta el área de trabajo con toda la organización o asigne roles de área de trabajo a los usuarios de Pro. 

El usuario de Power BI Pro solo puede compartir y colaborar con usuarios que tengan una licencia gratuita en el área de trabajo C. El área de trabajo debe estar asignada a la capacidad Premium para que los usuarios con una licencia gratuita puedan tener acceso al área de trabajo. En el área de trabajo, el diseñador asigna roles a los colaboradores: *Administrador*, *Miembro*, *Colaborador* o *Visor*. El rol determina qué acciones puede realizar en el área de trabajo. A los *consumidores* de Power BI se les suele asignar el rol *Visor*. Para obtener más información, vea [Colaboración en áreas de trabajo](end-user-workspaces.md).

## <a name="find-out-which-license-and-subscription-you-have"></a>¿Qué licencia y suscripción tiene?
Hay varias maneras de encontrar información sobre su suscripción y licencia de Power BI. 

En primer lugar, averigüe qué licencia de **usuario** posee.

- Algunas versiones de Microsoft Office incluyen una licencia Power BI Pro.  Para ver si su versión de Office incluye Power BI, visite el [portal de Office](https://portal.office.com/account) y seleccione **Suscripciones**.

    Nuestro primer usuario, Pradtanna, tiene Office 365 E5, que incluye una licencia Power BI Pro.

    ![Pestaña Suscripciones del portal de Office](media/end-user-license/power-bi-license-office.png)

    Nuestro segundo usuario, Zalan, tiene una licencia gratuita de Power BI. 

    ![Pestaña Suscripciones del portal de Office](media/end-user-license/power-bi-license-free.png)

A continuación, compruebe si su cuenta también forma parte de una suscripción Premium. Cualquiera de los usuarios anteriores, con licencia de Pro o gratuita, puede pertenecer a una organización que tenga una licencia Premium.  Vamos a comprobarlo con nuestro segundo usuario, Zalan.  

- En el servicio Power BI, seleccione **Mi área de trabajo** y, después, el icono de engranaje en la esquina superior derecha. Seleccione **Administrar almacenamiento personal**.

    ![Vista del menú de configuración de engranaje](media/end-user-license/power-bi-license-personal.png)

    Las licencias **por usuario**, tanto de Pro como gratuitas, proporcionan 10 GB de almacenamiento en la nube que se pueden usar para hospedar informes de Power BI o libros de Excel. Si ve más de 10 GB, significa que es miembro de una cuenta profesional con una licencia Premium.

    ![Vista de Administrar almacenamiento con 100 GB](media/end-user-license/power-bi-free-capacity.png)

    Recordemos que, en la página del portal de Office, la licencia de usuario de Zalan era para Power BI (gratis). Sin embargo, dado que su organización adquirió una suscripción Premium, en el servicio Power BI, Zalan no está limitado a 10 GB de almacenamiento, tiene 100 GB disponibles. Como *consumidor* en una organización con una licencia Premium, siempre y cuando el *diseñador* ponga el área de trabajo en una capacidad Premium, Zalan puede ver el contenido compartido, colaborar con compañeros, trabajar con aplicaciones, etc. La ampliación de sus permisos la establecen su administrador de Power BI y el diseñador del contenido. Tenga en cuenta que un usuario de Pro ya ha compartido un área de trabajo con Zalan. El icono de diamante le permite saber que esta área de trabajo está almacenada en una capacidad Premium. 

   
## <a name="understanding-workspace-roles"></a>Descripción de los roles de un área de trabajo
Hasta ahora, hemos revisado las licencias por usuario, las suscripciones Premium, las áreas de trabajo de la aplicación y la capacidad Premium. Echemos un vistazo ahora a los *roles* de un área de trabajo.

Puesto que este es un artículo para *consumidores* de Power BI, tenemos el siguiente escenario:

-  Usted es un usuario con una licencia *gratuita* de una organización que tiene una suscripción de Power BI Premium. 
- Un usuario de Power BI Pro ha creado una colección de paneles e informes y la ha publicado como una *aplicación* para toda la organización.  
- Las aplicaciones están en *áreas de trabajo* y el área de trabajo está en una capacidad Premium.    
- El área de trabajo de esta aplicación tiene un panel y dos informes.
- El usuario de Pro nos ha asignado el rol **Visor**.

### <a name="the-viewer-role"></a>Rol Visor
Los roles permiten a los *diseñadores* de Power BI determinar quién puede hacer qué en un área de trabajo para que los equipos puedan colaborar. Uno de estos roles es **Visor**. 

Cuando el área de trabajo está en una capacidad de Power BI Premium, los usuarios con el rol Visor pueden acceder al área de trabajo incluso si no tienen una licencia de Power BI Pro. Y dado que el rol Visor no puede tener acceso a los datos subyacentes ni exportarlos, es una forma segura de interactuar con los paneles, los informes y las aplicaciones.

> [!TIP]
> Para obtener información sobre los demás roles (Administrador, Miembro y Colaborador), consulte [Organización del trabajo en las nuevas áreas de trabajo en Power BI](../service-new-workspaces.md).

## <a name="next-steps"></a>Pasos siguientes
[¿Soy consumidor de *Power BI*?](end-user-consumer.md)    
[Más información sobre las áreas de trabajo](end-user-workspaces.md)    
<!--[View Power BI features by license type](end-user-features.md) -->

