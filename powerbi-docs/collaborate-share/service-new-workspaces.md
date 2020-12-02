---
title: Organización del trabajo en las nuevas áreas de trabajo en Power BI
description: Obtenga información sobre las nuevas áreas de trabajo, que son colecciones de paneles e informes creadas para proporcionar métricas clave a su organización.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
ms.date: 10/21/2020
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 43af5a2ea924ababdba7b328b814045b75be5316
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411756"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organización del trabajo en las nuevas áreas de trabajo en Power BI

Las *áreas de trabajo* son lugares donde se colabora con compañeros para crear colecciones de paneles, informes, conjuntos de datos e informes paginados. La nueva experiencia de áreas de trabajo le ayuda a administrar mejor el acceso al contenido. En este artículo se describen las nuevas áreas de trabajo y cómo se diferencian de las áreas de trabajo clásicas.  Al igual que con las áreas de trabajo clásicas, se siguen utilizando para crear y distribuir aplicaciones. 

¿Listo para crear un área de trabajo? Lea [Creación de una nueva experiencia de áreas de trabajo](service-create-the-new-workspaces.md).

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Nueva experiencia de área de trabajo de Power BI":::

Las áreas de trabajo nuevas y actualizadas pueden coexistir en paralelo con las áreas de trabajo clásicas existentes. La nueva experiencia de áreas de trabajo es el tipo de área de trabajo predeterminado. Sin embargo, puede crear y utilizar [áreas de trabajo clásicas](service-create-workspaces.md) basadas en grupos de Microsoft 365, si lo necesita. ¿Está listo para migrar el área de trabajo clásica? Para más información, consulte [Actualización de las áreas de trabajo clásicas a las nuevas áreas de trabajo de Power BI](service-upgrade-workspaces.md).

## <a name="new-and-classic-workspace-differences"></a>Diferencias entre áreas de trabajo nuevas y clásicas

Con las nuevas áreas de trabajo, se han rediseñado algunas características. Estas son las diferencias principales.

- **Al crear las nuevas áreas de trabajo no se crean grupos de Microsoft 365**, como sí ocurría con las áreas de trabajo clásicas. Toda la administración de la nueva área de trabajo se realiza en Power BI, no en Office 365. Puede seguir administrando el acceso del usuario al contenido a través de los grupos de Microsoft 365, si así lo desea. Solo tiene que agregar un grupo de Microsoft 365 en la lista de acceso al área de trabajo.
- **Uso de roles de área de trabajo más pormenorizados** para flexibilizar la administración de permisos en las nuevas áreas de trabajo.  En las áreas de trabajo clásicas solo puede agregar usuarios individuales a las listas de miembros y administradores. 
- **Asignación de roles de área de trabajo a grupos de usuarios**: en las nuevas áreas de trabajo, puede agregar estos roles a varios grupos de seguridad de Active Directory, listas de distribución o grupos de Microsoft 365 para facilitar la administración de usuarios. 
- **Lista de contactos**: en las nuevas áreas de trabajo, puede especificar quién recibe notificaciones sobre la actividad del área de trabajo.
- **Creación de aplicaciones de plantilla**: solo puede crear *aplicaciones de plantilla* en las nuevas áreas de trabajo. Las aplicaciones de plantilla son aplicaciones que se pueden distribuir a los clientes de fuera de la organización. Después, esos clientes pueden conectarse a sus propios datos con la aplicación de plantilla. Más información sobre las [aplicaciones de plantilla](../connect-data/service-template-apps-overview.md).
- **Uso compartido de conjuntos de datos**: para compartir un conjunto de datos fuera de un área de trabajo específica, debe guardar el informe que contiene el conjunto de datos en una de las nuevas áreas de trabajo. No se pueden compartir conjuntos de datos de áreas de trabajo clásicas. Más información sobre los [conjuntos de datos compartidos](../connect-data/service-datasets-across-workspaces.md).
- **Paquetes de contenido organizativo**: cree y consuma paquetes de contenido organizativos en áreas de trabajo clásicas. Esto no puede hacerlo en las nuevas áreas de trabajo. Las aplicaciones y las aplicaciones de plantilla reemplazan a los paquetes de contenido organizativos en las nuevas áreas de trabajo.

En este artículo se explican estas características con más detalle.

> [!NOTE]
> Power BI continúa mostrando todos los grupos de Microsoft 365 de los que se es miembro. De esta forma, se evita tener que cambiar los flujos de trabajo existentes.

### <a name="features-that-work-differently"></a>Características que funcionan de forma diferente

En las nuevas áreas de trabajo, algunas características funcionan de manera diferente. Estas diferencias son intencionales, en función de los comentarios que hemos recibido de los clientes, y permiten un enfoque más flexible hacia la colaboración en las áreas de trabajo.

- **Cumplimiento de licencias**: al publicar informes en una nueva experiencia de área de trabajo se aplican las reglas de licencia existentes. Los usuarios que colaboran en las nuevas áreas de trabajo o que comparten contenido con otras personas en el servicio Power BI necesitan una licencia de Power BI Pro. Los usuarios sin una licencia Pro ven el error "Solo los usuarios con licencias de Power BI Pro pueden publicar en esta área de trabajo".
- **Opción "Members can reshare" (Los miembros pueden volver a compartir)** : el rol de colaborador de las nuevas áreas de trabajo reemplaza a la opción "Members can reshare" (Los miembros pueden volver a compartir) de las áreas de trabajo clásicas.
- **Áreas de trabajo de solo lectura**: el rol de espectador de las nuevas áreas de trabajo reemplaza a la concesión de acceso de solo lectura a los usuarios a un área de trabajo clásica. El rol de espectador permite acceso de solo lectura similar al contenido de las nuevas áreas de trabajo.
- Los **usuarios sin una licencia Pro** pueden acceder a la nueva área de trabajo cuando esta se encuentra en una capacidad Power BI Premium, pero solo si tienen el rol de espectador.
- **Permitir que los usuarios exporten datos**: incluso los usuarios con un rol de espectador en la nueva área de trabajo pueden exportar datos si tienen permiso de compilación sobre los conjuntos de datos de esa área de trabajo. Obtenga más información sobre [Permiso de compilación para conjuntos de datos](../connect-data/service-datasets-build-permissions.md).
- No hay botón **Abandonar área de trabajo** en las nuevas áreas de trabajo.

### <a name="workspace-contact-list"></a>Lista de contactos del área de trabajo

La nueva característica **Lista de contactos** le permite especificar qué usuarios reciben una notificación sobre los problemas que se producen en las nuevas áreas de trabajo. De forma predeterminada, reciben notificaciones los usuarios o grupos especificados como administradores de áreas de trabajo en la nueva área de trabajo. Puede agregar otros a esa lista. Los usuarios o grupos de la lista de contactos también se enumeran en la interfaz de usuario (UI) de las nuevas áreas de trabajo, por lo que los usuarios finales del área de trabajo saben con quién ponerse en contacto. 

Lea acerca de [cómo crear la lista de contactos del área de trabajo](service-create-the-new-workspaces.md#create-a-contact-list).

### <a name="workspace-onedrive"></a>Área de trabajo: OneDrive

Como se ha indicado, Power BI no crea un grupo de Microsoft 365 en segundo plano al crear una de las nuevas áreas de trabajo. Aun así, puede que le resulte útil tener una instancia de OneDrive asociada a la nueva área de trabajo. La característica de área de trabajo OneDrive de las nuevas áreas de trabajo permite configurar un grupo de Microsoft 365 cuyo almacenamiento de archivos de la biblioteca de documentos de SharePoint está disponible para los usuarios del área de trabajo. Primero se crea el grupo fuera de Power BI.
 
Power BI no realiza la sincronización entre la pertenencia a grupos de Microsoft 365 y los permisos de usuarios o grupos con acceso a la nueva área de trabajo. Puede sincronizarlos de la siguiente manera: Administre el acceso al área de trabajo a través del mismo grupo de Microsoft 365 cuyo almacenamiento de archivos se define en esta opción. 

Lea sobre cómo [establecer el área de trabajo OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive).  

## <a name="roles-in-the-new-workspaces"></a>Roles en las nuevas áreas de trabajo

Los roles le permiten administrar quién puede hacer qué en las nuevas áreas de trabajo, para que los equipos puedan colaborar. Las nuevas áreas de trabajo le permiten asignar roles a usuarios y grupos de usuarios: grupos de seguridad, grupos de Microsoft 365 y listas de distribución. 

Para conceder acceso a una nueva área de trabajo, asigne a esos usuarios o grupos de usuarios uno de los roles del área de trabajo: administrador, miembro, colaborador o espectador. Todos los miembros de un grupo de usuarios obtienen el rol que haya definido. Si algún usuario está en varios grupos de usuarios, obtiene el nivel de permiso mayor proporcionado por los roles que se le asignan. Si anida grupos de usuarios, todos los usuarios contenidos tienen permiso. Todas estas funciones, excepto las de visualización e interacción, requieren una licencia de Power BI Pro. Más información sobre las [licencias](#licenses) en este artículo.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - Puede asignar roles a los usuarios, ya sea de forma individual o en grupo, incluso si no pueden usar el rol. En otras palabras, puede asignar a los usuarios que no tengan licencias de Power BI Pro un rol que requiera una licencia. Consulte [Licencias](#licenses) en este artículo para más información.
> - Para imponer [seguridad de nivel de fila (RLS)](../admin/service-admin-rls.md) a los usuarios que exploran el contenido de un área de trabajo, use el rol de espectador. También puede aplicar RLS sin ofrecer acceso a la nueva área de trabajo. [Publique una aplicación](service-create-distribute-apps.md) y distribúyala a esos usuarios, o utilice el [uso compartido para distribuirles contenido](service-share-dashboards.md).

## <a name="licensing-and-administering"></a>Licencias y administración

### <a name="licenses"></a>Licencias
Si una de las nuevas áreas de trabajo está en una capacidad compartida, todos los usuarios que agregue a ella necesitarán una licencia de Power BI Pro. Estos usuarios pueden colaborar en los paneles e informes de la nueva área de trabajo. Si quiere distribuir contenido a otros usuarios dentro de la organización, asigne licencias de Power BI Pro a esos usuarios o coloque el área de trabajo en una capacidad Power BI Premium.

Cuando la nueva área de trabajo está en una capacidad Power BI Premium, los usuarios con el rol de espectador pueden acceder al área de trabajo incluso si no tienen una licencia de Power BI Pro. Sin embargo, si asigna a estos usuarios un rol superior, como administrador, miembro o colaborador, se les pedirá que inicien una evaluación Pro al intentar acceder al área de trabajo. Si quiere que los usuarios sin licencias Pro usen el rol de espectador, asegúrese de que no tengan también otros roles de área de trabajo, ya sea como individuos o como parte de un grupo de usuarios.

La publicación de informes en la nueva experiencia de área de trabajo tiene el cumplimiento más estricto de las reglas de licencia existentes. Si intenta publicar desde Power BI Desktop u otras herramientas cliente sin una licencia de Pro, verá el error "Solo los usuarios con licencias de Power BI Pro pueden publicar en esta área de trabajo.".

> [!NOTE]
> Power BI para la Administración Pública no está disponible como licencia gratuita. Para más información sobre las licencias, consulte [Power BI para clientes de la Administración pública de EE. UU.](../admin/service-govus-overview.md)

### <a name="guest-users"></a>Usuarios invitados

De forma predeterminada, los [usuarios invitados de Azure AD B2B](../admin/service-admin-azure-ad-b2b.md) no pueden tener acceso a las áreas de trabajo. El administrador de Power BI puede [permitir a los usuarios invitados externos editar y administrar el contenido de la organización](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Los usuarios invitados habilitados pueden acceder a las áreas de trabajo para las que tienen permiso.

### <a name="administering-new-workspace-experience-workspaces"></a>Administración de áreas de trabajo de la nueva experiencia de áreas de trabajo

La administración de las áreas de trabajo de la nueva experiencia está en el portal de administración de Power BI. Los administradores de Power BI deciden qué usuarios de una organización pueden crear áreas de trabajo y distribuir aplicaciones. Lea sobre la [administración de la capacidad de los usuarios para crear áreas de trabajo](../admin/service-admin-portal.md#create-the-new-workspaces) en el artículo "Portal de administración". 

Los administradores pueden ver también el estado de todas las áreas de trabajo de su organización. Pueden administrar, recuperar e incluso eliminar áreas de trabajo. Lea sobre la [administración de las áreas de trabajo por sí mismos](../admin/service-admin-portal.md#workspaces) en el artículo "Portal de administración".

### <a name="auditing"></a>Auditoría

Power BI audita las siguientes actividades en las áreas de trabajo de la nueva experiencia.

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

**¿Afecta la nueva experiencia de área de trabajo a los vínculos a contenido existentes?**

No. Los vínculos a los elementos existentes de las áreas de trabajo clásicas no se ven afectados por la nueva experiencia de áreas de trabajo. La disponibilidad general (GA) de la nueva experiencia de áreas de trabajo cambia el área de trabajo predeterminada que se crea, pero no cambia las áreas de trabajo existentes. 

**¿Se actualizan las áreas de trabajo existentes a la nueva experiencia de área de trabajo con disponibilidad general?**

No. La disponibilidad general de la nueva experiencia de áreas de trabajo solo cambia el tipo de área de trabajo predeterminado a la nueva experiencia de áreas de trabajo. Las áreas de trabajo clásicas existentes que se basan en grupos de Microsoft 365 permanecen sin cambios.

**¿Las áreas de trabajo siguen creándose automáticamente para los grupos de Microsoft 365?**

Sí. Dado que se admiten ambos tipos de áreas de trabajo en paralelo, seguimos mostrando todos los grupos de Microsoft 365 a los que el usuario tiene acceso en la lista de áreas de trabajo.

## <a name="next-steps"></a>Pasos siguientes

* [Crear las nuevas áreas de trabajo en Power BI](service-create-the-new-workspaces.md)
* [Crear las áreas de trabajo clásicas](service-create-workspaces.md)
* [Instalar y usar aplicaciones en Power BI](service-create-distribute-apps.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

