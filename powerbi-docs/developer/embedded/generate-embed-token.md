---
title: Consideraciones para generar un token de inserción en los análisis insertados de Power BI
description: Obtenga información sobre las consideraciones, las limitaciones y los permisos necesarios para generar un token de inserción.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 45a88d93e7ac5a63b269350451f39991ba153dd5
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098039"
---
# <a name="considerations-when-generating-an-embed-token"></a>Consideraciones para generar un token de inserción

[Generar token](/rest/api/power-bi/embedtoken) es una API REST que le permite generar un token para insertar un elemento de Power BI en una aplicación web o un portal. El token se usa para autorizar la solicitud en el servicio Power BI.

La API de generación de tokens usa una única identidad (una entidad de servicio o usuario maestro) para generar un token para un usuario individual, en función de las credenciales de ese usuario en la aplicación (identidad efectiva).

Después de la autenticación correcta, se concede el acceso a los datos pertinentes.

>[!NOTE]
>Generar token solo es aplicable cuando esté [*insertando para los clientes*](embed-sample-for-customers.md) (escenario conocido también como *La aplicación posee los datos*).

Puede usar las siguientes API para generar un token:

* [Paneles](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [Conjuntos de datos](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [Generar token para varios informes](/rest/api/power-bi/embedtoken/generatetoken)


* [Creación de informes](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [Informes](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [Iconos](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>Versiones del área de trabajo

Power BI tiene dos versiones del área de trabajo, un área de trabajo *clásica* y un área de trabajo *nueva*. Puede obtener más información sobre las diferencias entre estas áreas de trabajo en [Diferencias entre áreas de trabajo nuevas y clásicas](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences).

Al crear un token de inserción, distintas áreas de trabajo tienen distintas consideraciones y requieren permisos diferentes.

|                  |Área de trabajo *clásica* |Área de trabajo *nueva*|
|------------------|---------|--------|
|**Consideraciones**|<li>El conjunto de datos y el elemento deben estar en la misma área de trabajo.</li><li>No se puede usar la entidad de servicio.</li>  |El conjunto de datos y el elemento pueden estar en dos áreas de trabajo *nuevas*. |
|**Permisos de área de trabajo**|El usuario maestro debe ser un administrador del área de trabajo.  |La entidad de servicio o el usuario maestro debe ser al menos miembro de ambas áreas de trabajo. |

>[!NOTE]
>* No se puede crear un token de inserción para [Mi área de trabajo](../../consumer/end-user-workspaces.md#types-of-workspaces).
>* La palabra *elemento* hace referencia a un elemento de Power BI, como un panel, un icono, preguntas y respuestas o un informe.

## <a name="securing-your-data"></a>Protección de los datos

Al crear la solución, tenga en cuenta estos dos enfoques para proteger los datos:

* [Aislamiento basado en el área de trabajo](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [Aislamiento basado en seguridad de nivel de fila](embed-multi-tenancy.md#row-level-security-based-isolation)

Si va a usar el enfoque de nivel de fila, revise las [consideraciones y limitaciones de RLS](generate-embed-token.md#row-level-security) al final de este artículo.

## <a name="token-permissions"></a>Permisos de token

En las API de generación de tokens, la sección *GenerateTokenRequest* describe los permisos de token.

>[!NOTE]
>Los permisos de token que se enumeran en esta sección no son aplicables a la API de [generación de token para varios informes](/rest/api/power-bi/embedtoken/generatetoken).

### <a name="access-level"></a>Nivel de acceso

Use el parámetro *accessLevel* para determinar el nivel de acceso del usuario.

* **Ver**: conceda permisos de visualización al usuario.

* **Editar**: conceda permisos de visualización y edición al usuario (solo se aplica al generar un token de inserción para un informe).

    Si utiliza la API de [generación de token para varios informes](/rest/api/power-bi/embedtoken/generatetoken), use el parámetro *allowEdit* para conceder permisos de visualización y edición al usuario.

* **Crear**: conceda al usuario permisos para crear un informe (solo se aplica al generar un token de inserción para crear un informe).

    Para la creación de informes, también debe proporcionar el parámetro *datasetId*.

### <a name="saving-a-copy-of-the-report"></a>Guardado de una copia del informe

Use el valor booleano *allowSaveAs* para permitir que los usuarios guarden el informe como un nuevo informe. De forma predeterminada, esta opción está establecida en *false*.

Este parámetro solo es aplicable al generar un token de inserción para un informe.

### <a name="row-level-security"></a>Seguridad de nivel de fila

Con [Seguridad de nivel de fila (RLS)](embedded-row-level-security.md), puede elegir usar una identidad diferente de la identidad de la entidad de servicio o el usuario maestro con el que está generando el token. Con esta opción, puede mostrar información insertada según el usuario al que está destinada. Por ejemplo, en la aplicación puede pedir a los usuarios que inicien sesión y, a continuación, mostrar un informe que solo contenga información de ventas si el usuario que inició sesión es un empleado de ventas.

Si utiliza RLS, en algunos casos puede omitir la identidad del usuario (el parámetro *EffectiveIdentity*). Esto permite que el token tenga acceso a toda la base de datos. Este método se puede usar para conceder acceso a usuarios como administradores y directivos, que tienen permisos para ver el conjunto de datos completo. Sin embargo, no puede usar este método en todos los escenarios. En la tabla siguiente se enumeran los distintos tipos de RLS y se muestra el método de autenticación que se puede usar sin especificar la identidad de un usuario.

En la tabla también se muestran las consideraciones y limitaciones aplicables a cada tipo de RLS.

|Tipo de RLS  |¿Se puede generar un token de inserción sin especificar el identificador de usuario efectivo?  |Consideraciones y limitaciones  |
|---------|---------|---------|
|Seguridad de nivel de fila en la nube (RLS en la nube)      |✔ Usuario maestro<br/>✖ Entidad de servicio          |         |
|RDL (informes paginados)     |✖ Usuario maestro<br/>✔ Entidad de servicio        |No se puede usar un usuario maestro para generar un token de inserción para RDL.         |
|Conexión dinámica local de Analysis Services (AS)    |✔ Usuario maestro<br/>✖ Entidad de servicio         |El usuario que genera el token de inserción también necesita uno de los siguientes permisos:<li>Permisos de administrador de puerta de enlace</li><li>Permiso de suplantación de origen de datos (*ReadOverrideEffectiveIdentity*)</li>         |
|Conexión dinámica de Azure de Analysis Services (AS)    |✔ Usuario maestro<br/>✖ Entidad de servicio         |No se puede reemplazar la identidad del usuario que genera el token de inserción. Los datos personalizados se pueden utilizar para implementar RLS dinámico o filtrado seguro.<br/><br/>**Nota**: La entidad de servicio debe proporcionar su identificador de objeto como identidad efectiva (el nombre de usuario de RLS).         |
|Inicio de sesión único (SSO)     |✔ Usuario maestro<br/>✖ Entidad de servicio         |Se puede proporcionar una identidad explícita (SSO) mediante la propiedad de blob de identidad en un objeto de identidad efectiva.         |
|SSO y RLS en la nube     |✔ Usuario maestro<br/>✖ Entidad de servicio         |Debe proporcionar lo siguiente:<li>Identidad explícita (SSO) en la propiedad de blob de identidad en un objeto de identidad efectivo</li><li>Identidad efectiva (RLS) (nombre de usuario)</li>         |

>[!NOTE]
>La entidad de servicio siempre debe proporcionar lo siguiente:
>* Una identidad para cualquier elemento con un conjunto de datos de RLS.
>* Para un conjunto de datos de SSO, una identidad de RLS efectiva con la propiedad de nombre de usuario definida.

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Registro de una aplicación](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded para los clientes](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objetos de aplicación y de entidad de servicio de Azure Active Directory](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Seguridad de nivel de fila mediante puerta de enlace de datos local con entidad de servicio](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Inserción de contenido de Power BI con entidades de servicio](embed-service-principal.md)