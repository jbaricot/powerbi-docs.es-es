---
title: Seguridad de nivel de fila (RLS) con Power BI
description: Cómo configurar la seguridad de nivel de fila para conjuntos de datos importados, y DirectQuery, dentro del servicio Power BI.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/17/2020
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: f1358cbafa08c0dbb3790322c414d7a746386f0f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408582"
---
# <a name="row-level-security-rls-with-power-bi"></a>Seguridad de nivel de fila (RLS) con Power BI

La seguridad de nivel de fila (RLS) con Power BI puede usarse para restringir el acceso a los datos a determinados usuarios. Los filtros restringen el acceso a los datos en el nivel de fila y se pueden definir en roles. En el servicio Power BI, los miembros de un área de trabajo tienen acceso a conjuntos de datos del área de trabajo. RLS no restringe este acceso a datos.

Puede configurar RLS para los modelos de datos que se han importado en Power BI con Power BI Desktop. También puede configurar RLS en conjuntos de datos que utilizan DirectQuery, como SQL Server. En el caso de las conexiones dinámicas de Analysis Services o Azure Analysis Services, puede configurar la seguridad de nivel de fila en el modelo, no en Power BI Desktop. La opción de seguridad no se mostrará para conjuntos de datos de conexión dinámica.

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

De forma predeterminada, el filtrado de la seguridad de nivel de fila utiliza filtros unidireccionales, independientemente de si las relaciones se establecen de forma unidireccional o bidireccional. Para habilitar manualmente un filtro cruzado bidireccional con seguridad de nivel de fila, seleccione la relación y marque la casilla de verificación **Aplicar filtro de seguridad en ambas direcciones**. Active esta opción al implementar también la seguridad de nivel de fila dinámica en el nivel del servidor, donde la seguridad de nivel de fila se basa en el nombre de usuario o el identificador de inicio de sesión.

Para más información, consulte los artículos técnicos [Filtrado cruzado bidireccional con DirectQuery en Power BI Desktop](../transform-model/desktop-bidirectional-filtering.md) y [Protección del modelo semántico tabular de BI](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx).

![Aplicar filtro de seguridad](media/service-admin-rls/rls-apply-security-filter.png)


[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

## <a name="manage-security-on-your-model"></a>Administración de la seguridad en el modelo

Para administrar la seguridad en el modelo de datos, siga estos pasos:

1. En el servicio Power BI, seleccione el menú **Más opciones** para un conjunto de datos. Este menú aparece cuando se mantiene el puntero sobre el nombre de un conjunto de los mismos, tanto si se selecciona desde el menú de navegación como desde la página del área de trabajo.

    ![Menú Más opciones del área de trabajo](media/service-admin-rls/dataset-leftnav-more-options.png)

    ![Menú Más opciones en el menú de navegación](media/service-admin-rls/dataset-canvas-more-options.png)

1. Seleccione **Seguridad**.

   ![Selección de Seguridad en el menú Más opciones](media/service-admin-rls/dataset-more-options-menu.png)

Esto le llevará a la página RLS para agregar miembros a un rol creado en Power BI Desktop. Solo los propietarios del conjunto de datos verán la opción Seguridad. Si el conjunto de datos está en un grupo, solo los administradores del grupo verán la opción de seguridad.

Solo puede crear o modificar roles dentro de Power BI Desktop.

## <a name="working-with-members"></a>Miembros

### <a name="add-members"></a>Agregar miembros

Agregue un miembro al rol escribiendo la dirección de correo electrónico o el nombre del usuario o el grupo de seguridad. No se pueden agregar grupos creados en Power BI. Puede agregar miembros [externos a la organización](../guidance/whitepaper-azure-b2b-power-bi.md#data-security-for-external-partners).

![Agregar un miembro](media/service-admin-rls/rls-add-member.png)

También puede ver cuántos miembros forman parte del rol por el número entre paréntesis junto al nombre del rol o junto a Miembros.

![Miembros de rol](media/service-admin-rls/rls-member-count.png)

### <a name="remove-members"></a>Quitar miembros

Puede quitar miembros seleccionando la X junto a su nombre. 

![Quitar miembro](media/service-admin-rls/rls-remove-member.png)

## <a name="validating-the-role-within-the-power-bi-service"></a>Validación del rol en el servicio Power BI

Puede validar que el rol definido funciona correctamente probándolo.

1. Seleccione **Más opciones** (...) junto al rol.
2. Seleccione **Probar datos como rol**.

![Probar como rol](media/service-admin-rls/rls-test-role.png)

Verá los informes que están disponibles para este rol. Los paneles no se muestran en esta vista. En el encabezado de la página, se muestra el rol que se está aplicando.

![Ahora se muestra como <role>](media/service-admin-rls/rls-test-role2.png)

Pruebe otros roles, o una combinación de roles, seleccionando **Ahora se muestra como**.

![Probar otros roles](media/service-admin-rls/rls-test-role3.png)

Puede optar por ver los datos como una persona específica o puede seleccionar una combinación de roles disponibles para validar que funcionan.

Para volver a la vista normal, seleccione **Volver a seguridad de nivel de fila**.

[!INCLUDE [include-short-name](../includes/rls-usernames.md)]

## <a name="using-rls-with-workspaces-in-power-bi"></a>Uso de RLS con áreas de trabajo en Power BI

Si publica un informe de Power BI Desktop en un área de trabajo dentro del servicio Power BI, los roles se aplican a los miembros de solo lectura. Debe indicar que los miembros solo pueden ver contenido de Power BI dentro de la configuración del área de trabajo.

> [!WARNING]
> Si ha configurado el área de trabajo para que los miembros tengan permisos de edición, los roles de RLS no se aplicarán a ellos. Los usuarios pueden ver todos los datos.

![Configuración de grupo](media/service-admin-rls/rls-group-settings.png)

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>Pasos siguientes

- [Restricción del acceso a datos con seguridad de nivel de fila (RLS) en Power BI Desktop](../create-reports/desktop-rls.md)
- [Instrucciones de seguridad de nivel de fila (RLS) en Power BI Desktop](../guidance/rls-guidance.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)
