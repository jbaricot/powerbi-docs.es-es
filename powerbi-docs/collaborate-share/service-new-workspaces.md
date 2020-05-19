---
title: Organización del trabajo en las nuevas áreas de trabajo en Power BI
description: Obtenga información sobre las nuevas áreas de trabajo, que son colecciones de paneles e informes creadas para proporcionar métricas clave a su organización.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c534a72594692c5cf404b095492e7d6425f23329
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83273670"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organización del trabajo en las nuevas áreas de trabajo en Power BI

Las *áreas de trabajo* son lugares donde se colabora con compañeros para crear colecciones de paneles, informes, conjuntos de datos e informes paginados. La nueva experiencia de áreas de trabajo le ayuda a administrar mejor el acceso al contenido. En este artículo se describen las nuevas áreas de trabajo y cómo se diferencian de las áreas de trabajo clásicas.  Al igual que con las áreas de trabajo clásicas, se siguen utilizando para crear y distribuir aplicaciones. ¿Está preparado para crear una nueva área de trabajo? Lea [Creación de una nueva experiencia de áreas de trabajo](service-create-the-new-workspaces.md).

Las áreas de trabajo nuevas y actualizadas pueden coexistir en paralelo con las áreas de trabajo existentes. La nueva experiencia de áreas de trabajo es el tipo de área de trabajo predeterminado. Aún puede crear y utilizar [áreas de trabajo clásicas](service-create-workspaces.md) en función de los grupos de Office 365, si lo necesita. ¿Está listo para migrar el área de trabajo clásica? Para más información, consulte [Actualización de las áreas de trabajo clásicas a las nuevas áreas de trabajo de Power BI](service-upgrade-workspaces.md).

Con las nuevas áreas de trabajo puede hacer lo siguiente:

- Asignar roles de área de trabajo a grupos de usuarios: grupos de seguridad, listas de distribución, grupos de Office 365 y usuarios.
- Crear un área de trabajo en Power BI sin crear un grupo de Office 365 subyacente asociado. Toda la administración del área de trabajo se realiza en Power BI, no en Office 365.
- Seguir administrando el acceso del usuario al contenido a través de los grupos de Office 365, si lo desea. Solo tiene que agregar un grupo de Office 365 en la lista de acceso al área de trabajo.
- Usar roles de las áreas de trabajo más granulares para flexibilizar la administración de permisos en un área de trabajo.

Power BI continúa enumerando todos los grupos de Office 365 de los que es miembro. Esto evita cambiar los flujos de trabajo existentes.

## <a name="new-and-classic-workspace-differences"></a>Diferencias entre áreas de trabajo nuevas y clásicas

Con las nuevas áreas de trabajo, se han rediseñado algunas características. Estas son la diferencias principales.

* La creación de estas áreas de trabajo no crea grupos de Office 365, como sí hacen las áreas de trabajo clásicas. Sin embargo, ahora puede usar un grupo de Office 365 para proporcionar a los usuarios acceso al área de trabajo mediante la asignación de un rol. 
* En las áreas de trabajo clásicas solo puede agregar usuarios individuales a las listas de miembros y administradores. En las áreas de trabajo nuevas, puede agregar varios grupos de seguridad de Active Directory, listas de distribución o grupos de Office 365 a estas listas para facilitar la administración de usuarios. 
- Puede crear un paquete de contenido de la organización desde un área de trabajo clásica, pero no desde las áreas de trabajo nuevas.
- Puede consumir un paquete de contenido de la organización desde un área de trabajo clásica. Pero no puede hacerlo desde las áreas de trabajo nuevas.

### <a name="workspace-features-that-work-differently"></a>Características del área de trabajo que funcionan otra forma

Algunas características funcionan de manera diferente en las áreas de trabajo actuales y en las áreas de trabajo nuevas. Estas diferencias son intencionadas, en función de los comentarios que hemos recibido de los clientes. Permiten un enfoque más flexible para la colaboración con áreas de trabajo.

- **Cumplimiento de licencias**: la publicación de informes en la nueva experiencia de áreas de trabajo exige el cumplimiento de las reglas de licencia existentes. Los usuarios que colaboran en áreas de trabajo o comparten contenido con otras personas en el servicio Power BI, necesitan una licencia de Power BI Pro. Los usuarios sin una licencia Pro ven el error "Solo los usuarios con licencias de Power BI Pro pueden publicar en esta área de trabajo".
- **Los miembros pueden o no pueden volver a compartir**: el rol Colaborador sustituye esta configuración.
- **Áreas de trabajo de solo lectura**: en lugar de conceder a los usuarios acceso de solo lectura a un área de trabajo, asígnelos al rol Visor. Permite el acceso de solo lectura similar al contenido de un área de trabajo.
- Los **usuarios sin una licencia de Pro** pueden acceder al área de trabajo si esta tiene una capacidad de Power BI Premium, incluso si los usuarios solo tienen el rol Visor.
- **Permitir a los usuarios exportar datos**: los usuarios con el rol Visor pueden exportar datos si tienen permiso de compilación en los conjuntos de datos en el área de trabajo. Obtenga más información sobre [Permiso de compilación para conjuntos de datos](../connect-data/service-datasets-build-permissions.md).
- Ausencia del botón **Abandonar área de trabajo**.

### <a name="workspace-contact-list"></a>Lista de contactos del área de trabajo

La nueva característica **Lista de contactos** le permite especificar qué usuarios reciben una notificación sobre los problemas que se producen en el área de trabajo. De forma predeterminada, se notifica a cualquier usuario o grupo especificado como administrador del área de trabajo, pero puede personalizar la lista. Los usuarios o grupos que aparecen en la lista de contactos se mostrarán en la interfaz de usuario (IU) para ayudar a los usuarios a obtener ayuda relacionada con el área de trabajo. 

Lea más sobre la [configuración de la lista de contactos del área de trabajo](service-create-the-new-workspaces.md#workspace-contact-list).

### <a name="workspace-onedrive"></a>Área de trabajo: OneDrive

La característica Área de trabajo: OneDrive permite configurar un grupo de Office 365 cuyo almacenamiento de archivos de la biblioteca de documentos de SharePoint esté disponible para los usuarios del área de trabajo. Se crea el grupo fuera de Power BI.

Power BI no sincroniza los permisos de los usuarios o grupos que están configurados para tener acceso al área de trabajo con la pertenencia al grupo de Office 365. El procedimiento recomendado es administrar el acceso al área de trabajo a través del mismo grupo de Office 365 cuyo almacenamiento de archivos se define en esta configuración. 

Obtenga información sobre cómo [establecer Área de trabajo: OneDrive y acceder a esta característica](service-create-the-new-workspaces.md#workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Roles en las nuevas áreas de trabajo

Para conceder acceso a una nueva área de trabajo, agregue grupos de usuarios o individuos a uno de los roles de área de trabajo: administradores, miembros, colaboradores o visores. Todos los miembros de un grupo de usuarios obtienen el rol que haya definido. Si un usuario está en varios grupos de usuarios, obtiene el nivel de permiso mayor proporcionado por los roles que se les asignan.

Los roles le permiten administrar quién puede hacer qué en un área de trabajo, para que los equipos puedan colaborar. Las nuevas áreas de trabajo le permiten asignar roles a usuarios y grupos de usuarios: grupos de seguridad, grupos de Office 365 y listas de distribución. 

Al asignar roles a un grupo de usuarios, cada uno de ellos tiene acceso al contenido. Si anida grupos de usuarios, todos los usuarios contenidos tienen permiso.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> Para imponer la seguridad de nivel de fila (RLS) para los usuarios que exploran el contenido en un área de trabajo, use el rol Visor. Para aplicar RLS sin permitir el acceso al área de trabajo, publique una aplicación Power BI en esos usuarios, o bien utilice el uso compartido para distribuir el contenido.

## <a name="licensing"></a>Licencias
Todos los usuarios que agregue a un área de trabajo en la capacidad compartida necesitan una licencia de Power BI Pro. En el área de trabajo, estos usuarios pueden colaborar en paneles e informes que planee publicar para un público más amplio, o incluso para toda la organización. 

Si quiere distribuir contenido a otros usuarios dentro de la organización, puede asignar licencias de Power BI Pro a los usuarios o colocar el área de trabajo en una capacidad de Power BI Premium.

Cuando el área de trabajo está en una capacidad de Power BI Premium, los usuarios con el rol Visor pueden acceder al área de trabajo incluso si no tienen una licencia de Power BI Pro. Pero si asigna un rol superior a estos usuarios, como Administrador, Miembro o Colaborador, se les solicitará que inicien una Prueba de Pro al intentar acceder al área de trabajo. Para usar el rol Visor para usuarios sin licencias Pro, asegúrese de que no tienen otros roles de área de trabajo, ya sea individualmente o a través de un grupo de usuarios.

> [!NOTE]
> La publicación de informes en la nueva experiencia de áreas de trabajo tiene el cumplimiento más estricto de las reglas de licencia existentes. Si intenta publicar desde Power BI Desktop u otras herramientas cliente sin una licencia de Pro, verá el error "Solo los usuarios con licencias de Power BI Pro pueden publicar en esta área de trabajo.".

## <a name="administering-new-workspace-experience-workspaces"></a>Administración de áreas de trabajo de la nueva experiencia de áreas de trabajo

La administración de la nueva experiencia de áreas de trabajo está ahora en el portal de administración de Power BI. Los administradores de Power BI deciden qué usuarios de una organización pueden crear áreas de trabajo y distribuir aplicaciones. Los administradores pueden ver el estado de todas las áreas de trabajo de su organización. También pueden administrar y recuperar áreas de trabajo. Obtenga más información sobre la [creación de nuevas áreas de trabajo](../admin/service-admin-portal.md#create-the-new-workspaces) en el artículo del portal de administración.

## <a name="guest-users"></a>Usuarios invitados

De forma predeterminada, los [usuarios invitados de Azure AD B2B](../admin/service-admin-azure-ad-b2b.md) no pueden tener acceso a las áreas de trabajo. El administrador de Power BI puede [permitir a los usuarios invitados externos editar y administrar el contenido de la organización](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Los usuarios invitados habilitados pueden acceder a las áreas de trabajo para las que tienen permiso.

## <a name="auditing"></a>Auditoría

Power BI audita las siguientes actividades para nuevas áreas de trabajo de experiencia de áreas de trabajo.

| Nombre descriptivo | Nombre de operación |
|---|---|
| Carpeta de Power BI creada | CreateFolder |
| Carpeta de Power BI eliminada | DeleteFolder |
| Carpeta de Power BI actualizada | UpdateFolder |
| Acceso a la carpeta de Power BI actualizado| UpdateFolderAccess |

Lea más sobre la [auditoría de Power BI](../admin/service-admin-auditing.md).

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

Limitaciones que se deben tener en cuenta:

- Las áreas de trabajo pueden contener un máximo de 1000 conjuntos de datos o 1000 informes por cada conjunto de datos. 
- Una persona con una licencia de Power BI Pro puede ser miembro de 1000 áreas de trabajo como máximo.
- Power BI Publisher para Excel no se admite.

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

**¿Afecta la nueva experiencia de áreas de trabajo a los vínculos a contenido existente?**

No. Los vínculos a los elementos existentes de las áreas de trabajo clásicas no se ven afectados por la nueva experiencia de áreas de trabajo. La disponibilidad general (GA) de la nueva experiencia de áreas de trabajo cambia el área de trabajo predeterminada que se crea, pero no cambia las áreas de trabajo existentes. 

**¿Se actualizan las áreas de trabajo existentes a la nueva experiencia de áreas de trabajo con disponibilidad general?**

No. La disponibilidad general de la nueva experiencia de áreas de trabajo solo cambia el tipo de área de trabajo predeterminado a la nueva experiencia de áreas de trabajo. Las áreas de trabajo clásicas existentes que se basan en grupos de Office 365 permanecen sin cambios.

**¿Las áreas de trabajo siguen creándose automáticamente para los grupos de Office 365?**

Sí. Dado que se admiten ambos tipos de áreas de trabajo en paralelo, seguimos enumerando todos los grupos de Office 365 a los que tiene acceso en la lista de áreas de trabajo.

## <a name="next-steps"></a>Pasos siguientes

* [Crear las nuevas áreas de trabajo en Power BI](service-create-the-new-workspaces.md)
* [Crear las áreas de trabajo clásicas](service-create-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](service-create-distribute-apps.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

