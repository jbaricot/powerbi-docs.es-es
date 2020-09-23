---
title: Configuración de la actualización programada de informes de Power BI
description: Para actualizar los datos en el informe de Power BI, debe crear un plan de actualización programada.
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
ms.openlocfilehash: 7bc3b77a8badafe1c9660af347a74214176690ac
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859046"
---
# <a name="how-to-configure-power-bi-report-scheduled-refresh"></a>Configuración de la actualización programada de informes de Power BI
Para actualizar los datos del informe de Power BI en Power BI Report Server, debe crear un plan de actualización programado. Este plan se crea en el área *Administrar* de un informe de Power BI en el servidor de informes.

![Actualización programada correcta de un informe de Power BI](media/configure-scheduled-refresh/scheduled-refresh-success.png)

## <a name="configure-data-source-credentials"></a>Configuración de las credenciales del origen de datos
Necesita los permisos requeridos para crear un plan de actualización programado. Los permisos se definen en las definiciones de roles para el servidor de informes. Consulte [Definiciones de roles: roles predefinidos](/sql/reporting-services/security/role-definitions-predefined-roles) en la documentación de SQL Server Reporting Services para obtener más información.

Antes de crear un plan de actualización programada de datos, debe establecer las credenciales para **cada origen de datos** usado en el informe de Power BI.

1. En el portal web, haga clic con el botón derecho en el informe de Power BI y seleccione **Administrar**.
   
    ![Selección de Administrar en el menú contextual del informe de Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. En el menú de la izquierda, seleccione la pestaña **Orígenes de datos**.
3. Para cada origen de datos que aparece, elija el tipo de autenticación que se utilizará al conectarse a ese origen de datos. Escriba las credenciales adecuadas.
   
    ![Credenciales del origen de datos en la pantalla de administración del informe](media/configure-scheduled-refresh/data-source-credentials.png)

## <a name="creating-a-schedule-refresh-plan"></a>Creación de un plan de actualización programada
Siga estos pasos para crear un plan de actualización programada.

1. En el portal web, haga clic con el botón derecho en el informe de Power BI y seleccione **Administrar**.
   
    ![Selección de Administrar en el menú contextual del informe de Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. En el menú de la izquierda, seleccione la pestaña **Actualización programada**.
3. En la página **Actualización programada**, seleccione **Nuevo plan de actualización programada**.
   
    ![Nuevo plan de actualización programada](media/configure-scheduled-refresh/new-scheduled-refresh-plan.png)
4. En la página **Nuevo plan de actualización programada**, escriba una descripción y establezca una programación con la que desea que se actualice el modelo de datos.
5. Seleccione **Crear plan de actualización programada** cuando haya finalizado.
   
    ![Creación del plan de actualización programada](media/configure-scheduled-refresh/create-scheduled-refresh-plan.png)

## <a name="modifying-a-schedule-refresh-plan"></a>Modificación de un plan de actualización programada
Modificar un plan de actualización programada es similar a crear uno.

1. En el portal web, haga clic con el botón derecho en el informe de Power BI y seleccione **Administrar**.
   
    ![Selección de Administrar en el menú contextual del informe de Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. En el menú de la izquierda, seleccione la pestaña **Actualización programada**.
3. En la página **Actualización programada**, seleccione **Editar** junto al plan de actualización que desea administrar.
   
    ![Selección de Editar junto al plan que desea editar](media/configure-scheduled-refresh/edit-scheduled-refresh-plan.png)
4. En la página **Editar plan de actualización programada**, escriba una descripción y establezca una programación con la que desea que se actualice el modelo de datos.
5. Seleccione **Aplicar** cuando haya terminado.
   
    ![La página de edición de un plan de actualización programada es similar a la pantalla de creación](media/configure-scheduled-refresh/edit-scheduled-refresh-plan-page.png)

## <a name="viewing-the-status-of-schedule-refresh-plan"></a>Visualización del estado del plan de actualización programada
Puede ver el estado de un plan de actualización programada en el portal web.

1. En el portal web, haga clic con el botón derecho en el informe de Power BI y seleccione **Administrar**.
   
    ![Selección de Administrar en el menú contextual del informe de Power BI](media/configure-scheduled-refresh/manage-power-bi-report.png)
2. En el menú de la izquierda, seleccione la pestaña **Actualización programada**.
3. En la página **Actualización programada**, la columna del extremo derecho muestra el estado de un plan.
   
   | **Estado** | **Descripción** |
   | --- | --- |
   | Nuevo plan de actualización programada |El plan se ha creado pero no se ejecutó. |
   | Actualizando |Se ha iniciado el proceso de actualización. |
   | Transmitiendo el modelo a Analysis Server |Copiando el modelo desde la base de datos del catálogo del servidor de informes a la instancia de Analysis Services hospedada. |
   | Actualizando datos |Actualizando los datos del modelo. |
   | Eliminando las credenciales del modelo |Eliminadas las credenciales utilizadas para conectar al origen de datos desde el modelo. |
   | Guardando el modelo en el catálogo |La actualización de datos ha finalizado y se guarda el modelo actualizado en la base de datos del catálogo del servidor de informes. |
   | Completado: Actualización de datos |La actualización se ha realizado. |
   | Error: |Un error se produjo durante la actualización y se muestra. |

Es necesario actualizar la página web para ver el estado actual. El estado no cambiará automáticamente.

## <a name="next-steps"></a>Pasos siguientes
Para más información sobre la creación y modificación de programaciones, consulte [Creación, modificación y eliminación de programaciones](/sql/reporting-services/subscriptions/create-modify-and-delete-schedules).

Para obtener información acerca de cómo solucionar problemas de actualización programada, consulte [Solución de problemas de actualización programada en Power BI Report Server](scheduled-refresh-troubleshoot.md).

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)