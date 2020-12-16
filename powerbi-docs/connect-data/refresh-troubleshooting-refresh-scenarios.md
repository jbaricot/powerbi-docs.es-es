---
title: Solución de problemas de escenarios de actualización
description: Solución de problemas de escenarios de actualización
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 12/14/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: eba044de4918ad3cc62ce8b47144eab25c34702a
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491814"
---
# <a name="troubleshooting-refresh-scenarios"></a>Solución de problemas de escenarios de actualización

Aquí puede encontrar información sobre distintos escenarios que pueden darse al actualizar datos en el servicio Power BI.

> [!NOTE]
> Si se encuentra con un escenario que no se menciona a continuación y está causando incidencias, puede pedir ayuda adicional en el [sitio de la comunidad](https://community.powerbi.com/) o crear una [incidencia de soporte técnico](https://powerbi.microsoft.com/support/).
>

Siempre debe asegurarse de que se cumplen y se comprueban los requisitos básicos para la actualización. Estos requisitos básicos incluyen lo siguiente:

* Comprobar que la versión de la puerta de enlace está actualizada
* Comprobar que el informe tiene una puerta de enlace seleccionada; de lo contrario, es posible que el origen de datos haya cambiado o falte

Una vez que haya confirmado que se cumplen estos requisitos, consulte las secciones siguientes para obtener más información. 


## <a name="email-notifications"></a>Notificaciones por correo electrónico

Si ha llegado a este artículo a partir de una notificación por correo electrónico, y ya no desea recibir correos electrónicos acerca de los problemas de actualización, póngase en contacto con el administrador de Power BI. Pídales que quiten directamente su dirección de correo electrónico, o que la eliminen de una lista de correo electrónico a la que se esté suscrito de los conjuntos de datos correspondientes en Power BI. Pueden hacerlo desde la siguiente área del portal de administración de Power BI.

![Correo electrónico para notificaciones de actualización](media/refresh-troubleshooting-refresh-scenarios/refresh-email.png)

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>La actualización mediante el conector web no funciona correctamente

Si tiene un script de conector web que usa la función [**Web.Page**](/powerquery-m/web-page) y ha actualizado el conjunto de datos o el informe después del 18 de noviembre de 2016, debe usar una puerta de enlace para que la actualización funcione correctamente.

## <a name="unsupported-data-source-for-refresh"></a>Origen de datos no admitido para la actualización

Al configurar un conjunto de datos, puede que reciba un error que indica que el conjunto de datos utiliza un origen de datos no admitido para la actualización. Para más detalles, consulte [Solución de problemas de origen de datos no admitido para la actualización](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>El panel no refleja los cambios tras la actualización

Espere entre 10 y 15 minutos aproximadamente para que la actualización se refleje en los iconos del panel. Si sigue sin aparecer, ancle de nuevo la visualización al panel.

## <a name="gatewaynotreachable-when-setting-credentials"></a>GatewayNotReachable al establecer las credenciales

Puede que aparezca el error `GatewayNotReachable` al intentar establecer las credenciales para un origen de datos. Esto podría deberse a que la puerta de enlace no está actualizada. Instale la última versión de Gateway y vuelva a intentarlo.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Error de procesamiento: Se produjo el siguiente error del sistema: no coinciden los tipos

Puede tratarse de una incidencia con el script M en el libro de Excel o el archivo de Power BI Desktop. También puede deberse a que la versión de Power BI Desktop esté obsoleta.

## <a name="tile-refresh-errors"></a>Errores de actualización de iconos

Para ver una lista de errores que pueden producirse con los iconos de panel y explicaciones, consulte [Solución de problemas de errores de icono](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>Error de actualización al actualizar datos de orígenes que usan OAuth de AAD

El token de OAuth de Azure Active Directory (**AAD**) que utilizan muchos orígenes de datos diferentes expira en aproximadamente una hora. Pueden surgir situaciones en las que la carga de datos tarda más tiempo que la expiración del token (más de una hora), ya que el servicio de Power BI espera hasta dos horas al cargar datos. En esa situación, el proceso de carga de datos se puede interrumpir debido a un error en las credenciales.

Entre los orígenes de datos que usan AAD OAuth se incluyen **Microsoft Dynamics CRM Online**, **SharePoint Online** (SPO) y otros. Si se va a conectar a dichos orígenes de datos y recibe un error de credenciales cuando la carga de datos tarda más de una hora, este puede ser el motivo.

Microsoft investiga una solución que permita que el proceso de carga de datos actualice el token de actualización y continúe. Sin embargo, si la instancia de Dynamics CRM Online o SharePoint Online (o cualquier otro origen de datos de OAuth de AAD) es tan grande que puede llegar al umbral de dos horas de carga de datos, también puede aparecer un error que indique que se ha superado el tiempo de espera de la carga de datos desde el servicio Power BI.

Tenga en cuenta también que, para que la actualización funcione correctamente, al conectarse a un origen de datos de **SharePoint Online** con OAuth de AAD, debe utilizar la misma cuenta que usa para iniciar sesión en el **servicio Power BI**.

## <a name="uncompressed-data-limits-for-refresh"></a>Límites de datos sin comprimir para la actualización

El tamaño máximo de los conjuntos de datos importados en el **servicio Power BI** es de 1 GB. Estos conjuntos de datos están muy comprimidos para garantizar un alto rendimiento. Además, en la capacidad compartida, el servicio establece un límite en la cantidad de datos sin comprimir que se procesan durante la actualización de 10 GB. Este límite tiene en cuenta la compresión y, por tanto, es mucho mayor que 1 GB. Los conjuntos de datos de Power BI Premium no están sujetos a este límite. Si se produce un error en la actualización en el servicio Power BI por este motivo, reduzca la cantidad de datos importados en Power BI y vuelva a intentarlo.

## <a name="scheduled-refresh-timeout"></a>Tiempo de espera de la actualización programada

El tiempo de espera de la actualización programada de los conjuntos de datos importados se agotó después de dos horas. Este tiempo de espera se puede aumentar a cinco horas para los conjuntos de datos de las áreas de trabajo **Premium**. Si alcanza este límite, puede que deba considerar la posibilidad de reducir el tamaño o la complejidad del conjunto de datos o la posibilidad de dividirlo en conjuntos más pequeños.

## <a name="scheduled-refresh-failures"></a>Errores de actualización programada

Si se produce un error en una actualización programada en cuatro ocasiones en una fila, Power BI deshabilita la actualización. Solucione el problema subyacente y, a continuación, vuelva a habilitar la actualización programada.

## <a name="access-to-the-resource-is-forbidden"></a>El acceso al recurso queda prohibido  

Este error puede producirse debido a que las credenciales almacenadas en caché han expirado. Para borrar la memoria caché del explorador web, inicie sesión en Power BI y vaya a `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true`. De esta manera se fuerza la actualización de las credenciales.

## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>Error al actualizar los datos debido a que ha cambiado la contraseña o las credenciales han expirado

Otro posible error en la actualización de datos podría deberse a que la credencial almacenada en caché ha expirado. Para borrar la memoria caché del explorador web, inicie sesión en Power BI y vaya a `https://app.powerbi.com?alwaysPromptForContentProviderCreds=true`. De esta manera se fuerza la actualización de las credenciales.

## <a name="next-steps"></a>Pasos siguientes

- [Actualizar datos en Power BI](refresh-data.md)  
- [Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md)  
- [Solución de problemas de Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la Comunidad de Microsoft Power BI](https://community.powerbi.com/)
