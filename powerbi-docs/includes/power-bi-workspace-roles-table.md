---
title: Roles de área de trabajo de Power BI
description: Tabla de roles de área de trabajo de Power BI
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 06/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 9ddf9df0feaed2a2a0177d11e9b36f34135801c6
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365207"
---
|Funcionalidad   | Administrador  | Miembro  | Colaborador  | Visor |
|---|---|---|---|---|
| Actualizar y eliminar el área de trabajo.  |  |   |   |   | 
| Agregar o quitar usuarios, incluidos otros administradores.  |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Permitir que los colaboradores actualicen la aplicación para esta área de trabajo  |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Agregar miembros u otros usuarios con permisos inferiores.  |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publicar y cambiar permisos para una aplicación. |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Actualizar una aplicación. |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |  Si se permite <sup>1</sup>  |   |
| Compartir un elemento o una aplicación.<sup>2</sup> |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Permitir que otros usuarios vuelvan a compartir elementos.<sup>2</sup> |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar aplicaciones en la página principal de los compañeros |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Destacar paneles e informes en la página principal de los compañeros |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Crear, editar y eliminar contenido en el área de trabajo.  |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publicar informes en el área de trabajo, eliminar contenido.  |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Crear un informe en otra área de trabajo en función de un conjunto de datos de esta área de trabajo.<sup>2</sup> |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Copiar un informe.<sup>3</sup> | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Programar las actualizaciones de datos a través de la puerta de enlace local.<sup>4</sup> | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modificar la configuración de la conexión de la puerta de enlace.<sup>4</sup> | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Ver un elemento e interactuar con él.<sup>5</sup> |  ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Leer los datos almacenados en los flujos de trabajo del área de trabajo | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Marca de verificación Sí](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Los usuarios con el rol Colaborador pueden actualizar los metadatos de la aplicación, pero no publicar una nueva aplicación o cambiar quién tiene permiso para la aplicación, si el [administrador del área de trabajo delega este permiso a los colaboradores](../collaborate-share/service-create-the-new-workspaces.md#security-settings).

<sup>2</sup> Los usuarios con los roles Colaborador y Visor también pueden compartir elementos en un área de trabajo si tienen permisos para volver a compartir.

<sup>3</sup> Para copiar un informe y crear un informe en otra área de trabajo en función de un conjunto de datos de esta área de trabajo, debe tener el [permiso de compilación para el conjunto de datos](../connect-data/service-datasets-build-permissions.md). Para los conjuntos de datos de esta área de trabajo, los usuarios con los roles de Administrador, Miembro y Colaborador tienen automáticamente permiso de compilación en su rol de área de trabajo.

<sup>4</sup> Tenga en cuenta que también necesita permisos en la puerta de enlace. Estos permisos se administran en otro lugar, independientemente de los roles y los permisos del área de trabajo. Vea [Administración de una puerta de enlace local](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) para más información.

<sup>5</sup> Incluso aunque no tenga una licencia de Power BI Pro, puede ver los elementos e interactuar con ellos en el servicio Power BI si los elementos están en un área de trabajo de una capacidad Premium.
