---
title: Cómo se organiza el contenido en las áreas de trabajo
description: Obtenga información sobre las áreas de trabajo y los roles de área de trabajo.
author: mihart
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 801b5cf5400bbe1cc0487eef596ea3d1cdc5fb1e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82120205"
---
# <a name="collaborate-in-workspaces"></a>Colaboración en áreas de trabajo

 Las *áreas de trabajo* son lugares de colaboración con compañeros en contenido específico. Los *diseñadores* de Power BI crean las áreas de trabajo para incluir colecciones de paneles e informes. Después, estas colecciones se pueden agrupar en *aplicaciones* y distribuirse por toda la organización o a grupos o usuarios específicos. 

 Todos los usuarios que usan el servicio Power BI tienen también un espacio denominado **Mi área de trabajo**.  Mi área de trabajo es su espacio aislado personal donde se puede crear contenido.

 Puede ver las áreas de trabajo desde el **Inicio** de Power BI, o bien si selecciona **Área de trabajo** o **Mi área de trabajo** en el panel de navegación izquierdo.

 ![Panel de navegación en el que se muestran dos tipos de áreas de trabajo](media/end-user-workspaces/power-bi-home.png)

## <a name="types-of-workspaces"></a>Tipos de áreas de trabajo
En **Mi área de trabajo** se almacena todo el contenido que se crea y del que se es propietario. Puede considerarla como su espacio aislado o área de trabajo para su propio contenido. Para muchos *consumidores* de Power BI, la sección **Mi área de trabajo** estará vacía porque su trabajo no conlleva la creación de contenido. Los *consumidores*, por definición, consumen datos creados por otros usuarios y usan esos datos para tomar decisiones empresariales. En el caso de que también se dedique a crear contenido, le recomendamos que lea [los artículos de Power BI para diseñadores](../create-reports/index.yml).

Las **áreas de trabajo de aplicación** incluyen todo el contenido de una aplicación específica. Cuando un *diseñador* crea una aplicación, agrupa todo el contenido necesario para que esta se pueda usar. El contenido puede incluir paneles, informes y conjuntos de datos. No todas las aplicaciones contendrán estos tres elementos de contenido. Una aplicación puede contener solo un panel, tres elementos de cada tipo o incluso veinte informes. Todo ello depende de lo que el *diseñador* incluya en la aplicación. Las áreas de trabajo de aplicaciones para *consumidores* normalmente no incluyen los conjuntos de datos.

La siguiente área de trabajo de la aplicación de cifras de ventas contiene tres informes y un panel. 

![Panel de navegación en el que se muestran dos tipos de áreas de trabajo](media/end-user-workspaces/power-bi-app-workspace.png)

## <a name="roles-in-the-workspaces"></a>Roles en las áreas de trabajo

Los roles determinan qué puede hacer en un área de trabajo, para que los equipos puedan colaborar.  Al conceder acceso a una nueva área de trabajo, los *diseñadores* agregan personas o grupos a uno de los roles de área de trabajo: **Visor**, **Miembro**, **Colaborador** o **Administrador**. 


Como *consumidor* de Power BI, normalmente interactuará en las áreas de trabajo mediante el rol de **Visor**. Aun así, un *diseñador* podría asignarle también el rol de **Miembro** o **Colaborador**. El rol de Visor le permite no solo ver el contenido (paneles, informes y aplicaciones) que otros usuarios han creado y compartido con usted, sino interactuar con él. Dado que el rol de Visor no puede acceder al conjunto de datos subyacente, es una forma segura de interactuar con el contenido sin preocuparse de "perjudicar" los datos subyacentes.


Para obtener una lista detallada de lo que puede hacer como *consumidor* con el rol de Visor, consulte [Características de Power BI para consumidores](end-user-features.md).


### <a name="workspace-roles"></a>Roles de área de trabajo
Estas son las funciones de los cuatro roles: administradores, miembros, colaboradores y visores. Todas estas funciones, excepto las de visualización e interacción, requieren una licencia de Power BI Pro.

|Funcionalidad   | Administrador  | Miembro  | Colaborador  | Visor |
|---|---|---|---|---|
| Actualizar y eliminar el área de trabajo.  | X  |   |   |   | 
| Agregar o quitar usuarios, incluidos otros administradores.  | X  |   |   |   |
| Agregar miembros u otros usuarios con permisos inferiores.  |  X | X  |   |   |
| Publicar y actualizar una aplicación. |  X | X  |   |   |
| Compartir un elemento o una aplicación.<sup>1</sup> |  X | X  |   |   |
| Permitir que otros usuarios vuelvan a compartir elementos.<sup>1</sup> |  X | X  |   |   |
| Destacar aplicaciones en la página principal de los compañeros |  X | X  |   |   |
| Destacar paneles e informes en la página principal de los compañeros |  X | X  | X |   |
| Crear, editar y eliminar contenido en el área de trabajo.  |  X | X  | X  |   |
| Publicar informes en el área de trabajo, eliminar contenido.  |  X | X  | X  |   |
| Crear un informe en otra área de trabajo en función de un conjunto de datos de esta área de trabajo<sup>1</sup>. |  X | X  | X  |   |
| Copiar un informe. | X | X | X |  |
| Ver un elemento e interactuar con él<sup>2</sup>. |  X | X  | X  | X  |
| Leer los datos almacenados en los flujos de trabajo del área de trabajo | X | X | X | X |

1. Los usuarios con los roles de Colaborador y Miembro pueden compartir elementos en un área de trabajo si tienen permisos para volver a compartir.

2. Incluso aunque no tenga una licencia de Power BI Pro, puede ver los elementos e interactuar con ellos en el servicio Power BI si los elementos están en un área de trabajo de una capacidad Premium.

## <a name="licensing-workspaces-and-capacity"></a>Licencias, áreas de trabajo y capacidad
Las licencias también desempeñan un papel importante al determinar lo que puede hacer y lo que no en un área de trabajo. Muchas características requieren que el usuario tenga una licencia de Power BI *Pro*. La mayoría de los *consumidores* trabajan con una licencia *gratuita*. 

Si tiene una licencia gratuita y el área de trabajo se almacena en una *capacidad Premium*, podrá ver el contenido de esa área de trabajo e interactuar con él. Las áreas de trabajo y las aplicaciones que se almacenan en la capacidad Premium se identifican con un icono de rombo.

![Áreas de trabajo seleccionadas](media/end-user-workspaces/power-bi-diamond.png) Para obtener más información, consulte [Información sobre las licencias disponibles](end-user-license.md).



## <a name="next-steps"></a>Pasos siguientes
* [Aplicaciones de Power BI](end-user-apps.md)    

* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

