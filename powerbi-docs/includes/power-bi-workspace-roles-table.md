---
title: Roles de área de trabajo de Power BI
description: Tabla de roles de área de trabajo de Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 5ed3a65f1ef65640c76ada765931a85714aad3af
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781368"
---
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
| Copiar un informe.<sup>2</sup> | X | X | X |  |
| Programar las actualizaciones de datos a través de la puerta de enlace local.<sup>3</sup> | X | X | X |  |
| Modificar la configuración de la conexión de la puerta de enlace.<sup>3</sup> | X | X | X |  |
| Ver un elemento e interactuar con él.<sup>4</sup> |  X | X  | X  | X  |
| Leer los datos almacenados en los flujos de trabajo del área de trabajo | X | X | X | X |

1. Los usuarios con los roles Colaborador y Visor pueden compartir elementos en un área de trabajo si tienen permisos para volver a compartir.
2. Para copiar un informe y crear un informe en otra área de trabajo en función de un conjunto de datos de esta área de trabajo, debe tener el permiso de compilación para el conjunto de datos. Para los conjuntos de datos de esta área de trabajo, los usuarios con los roles de Administrador, Miembro y Colaborador tienen permiso de compilación en su rol de área de trabajo.
3. Tenga en cuenta que también necesita permisos en la puerta de enlace. Estos permisos se administran en otro lugar, independientemente de los roles y los permisos del área de trabajo. Vea [Administración de una puerta de enlace local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para más información.
4. Incluso aunque no tenga una licencia de Power BI Pro, puede ver los elementos e interactuar con ellos en el servicio Power BI si los elementos están en un área de trabajo de una capacidad Premium.

