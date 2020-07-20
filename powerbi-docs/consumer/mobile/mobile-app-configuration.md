---
title: Opciones de configuración de la aplicación de Power BI
description: Personalización del comportamiento de Power BI mediante una herramienta de MDM
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 07/14/2020
ms.author: painbar
ms.openlocfilehash: f9b6efd07aad3d2058e49f81ae21095b618123ee
ms.sourcegitcommit: d8acf2fb0318708a3e8e1e259cb3747b0312b312
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2020
ms.locfileid: "86385938"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Configuración remota de la aplicación de Power BI mediante la herramienta de administración de dispositivos móviles (MDM)

La aplicación Power BI Mobile para iOS y Android admite la configuración de la aplicación que permite a los administradores de los servicios de administración de dispositivos móviles (MDM), como Intune, personalizar el comportamiento de la aplicación.

La aplicación de Power BI Mobile admite los escenarios de configuración siguientes:

* Configuración del servidor de informes (iOS y Android)
* Configuración de la protección de datos (iOS y Android)
* Deshabilitación del inicio de sesión único (iOS y Android)
* Configuración de la interacción (iOS y Android)

## <a name="report-server-configuration-ios-and-android"></a>Configuración del servidor de informes (iOS y Android)

La aplicación Power BI para iOS y Android permite a los administradores "insertar" de manera remota la configuración del servidor de informes en los dispositivos inscritos.

| Clave | Tipo | Descripción |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Cadena | Dirección URL del servidor de informes.<br><br>Debe comenzar por http o https.|
| com.microsoft.powerbi.mobile.ServerUsername | Cadena | (opcional)<br><br>El nombre de usuario que se usará para conectar el servidor.<br><br>Si no existe, la aplicación pide al usuario que escriba el nombre de usuario para la conexión.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Cadena | (opcional)<br><br>El valor predeterminado es “Servidor de informes”<br><br>Nombre descriptivo que se usa en la aplicación para representar al servidor. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Booleano | (opcional)<br><br>El valor predeterminado es True. Si se establece en True, invalida cualquier definición del servidor de informes que ya esté disponible en el dispositivo móvil. Los servidores existentes ya configurados se eliminan. Al establecer Reemplazar en True también se evita que el usuario quite esa configuración.<br><br>Si se establece en False, se agregan los valores insertados, dejando cualquier configuración existente. Si la misma dirección URL del servidor ya está configurada en la aplicación móvil, esta deja dicha configuración tal cual. La aplicación no pide al usuario que vuelva a autenticarse para el mismo servidor. |

## <a name="data-protection-settings-ios-and-android"></a>Configuración de la protección de datos (iOS y Android)

La aplicación móvil de Power BI para iOS y Android ofrece a los administradores la capacidad de personalizar la configuración predeterminada para las opciones de seguridad y privacidad. En iOS, puede exigir que los usuarios proporcionen su identificación Face ID, Touch ID o un código de acceso al acceder a la aplicación móvil de Power BI. En Android, puede exigir que los usuarios usen la autenticación biométrica (Fingerprint ID).

| Clave | Tipo | Descripción |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Booleano | El valor predeterminado es False. <br><br>Se puede requerir la identificación biométrica, como Touch ID o Face ID (iOS), o Fingerprint ID (Android), para que los usuarios puedan acceder a la aplicación en su dispositivo. Cuando es requerida, la identificación biométrica se usa además de la autenticación.<br><br>Si usa directivas de protección de aplicaciones, Microsoft recomienda deshabilitar esta opción para impedir solicitudes de acceso dobles. |

>[!NOTE]
>La configuración de la protección de datos solo se aplicará en dispositivos Android que admitan la autenticación biométrica.

## <a name="disable-single-sign-on-ios-and-android"></a>Deshabilitación del inicio de sesión único (iOS y Android)

De forma predeterminada, la aplicación móvil de Power BI proporciona una experiencia práctica de inicio de sesión único para un solo usuario al minimizar el número de veces que el usuario tiene que proporcionar un nombre de usuario y una contraseña. Este comportamiento de inicio de sesión único se basa en la suposición de que el dispositivo es el dispositivo personal del usuario y que solo hay un usuario que utiliza el dispositivo y las aplicaciones que contiene.

Los administradores pueden activar el valor **DisableSingleSignOn** en el archivo de configuración de la aplicación para configurar de forma remota la aplicación y deshabilitar el inicio de sesión único y solicitar de forma explícita la contraseña del usuario cuando inicie sesión.

Se trata de un valor exclusivo del administrador que se configura a través de la configuración remota. El usuario final no puede cambiar esta configuración.

| Clave | Tipo | Descripción |
|---|---|---|
| com.microsoft.powerbi.mobile.DisableSingleSignOn | Booleano | El valor predeterminado es False.<br><br>Una vez que un usuario cierra la sesión, la aplicación no volverá a usar las credenciales existentes, pero le pedirá al siguiente usuario que proporcione una contraseña para autenticarse y conectarse al servicio Power BI.
 |

## <a name="interaction-settings-ios-and-android"></a>Configuración de la interacción (iOS y Android)

La aplicación de Power BI para iOS y Android ofrece a los administradores la posibilidad de configurar las opciones de interacción, en el caso de que se opte por cambiar la configuración de la interacción predeterminada entre grupos de usuarios de una organización.

>[!NOTE]
>Actualmente, no todas las interacciones se admiten en todos los dispositivos. Consulte [Configuración de las opciones de interacción de los informes](mobile-app-interaction-settings.md) para ver un gráfico que muestra la disponibilidad actual en todos los dispositivos.

| Clave | Tipo | Valores | Descripción |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Cadena |  <nobr>pulsación única</nobr><br><nobr>pulsar dos veces</nobr> | Configure si la acción de pulsar un objeto visual también realiza la selección de un punto de datos. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Booleano |  <nobr>True</nobr><br><nobr>False</nobr> | Configure si la acción de pulsar un punto de datos reemplazará la selección actual o agregará el elemento seleccionado a la selección actual. |
| com.microsoft.powerbi.mobile.RefreshAction | Cadena |  <nobr>deslizar para actualizar</nobr><br>Nuevo… | Configure si el usuario dispondrá de un botón para actualizar el informe, o bien deberá usar la acción de deslizar para actualizar. |
| com.microsoft.powerbi.mobile.FooterAppearance | Cadena |  acoplado<br>dinámico | Permite configurar si el pie de página del informe se acoplará a la parte inferior del informe o se ocultará de forma automática. |

## <a name="deploying-app-configuration-settings"></a>Implementación de los valores de configuración de la aplicación

A continuación se indican los pasos necesarios para crear una directiva de configuración de aplicación. Una vez creada la directiva de configuración, puede asignar su configuración a grupos de usuarios.

1. Conecte la herramienta MDM.
2. Cree una nueva directiva de configuración de aplicaciones y asígnele un nombre.
3. Elija los usuarios a los que quiere distribuir esta directiva de configuración de aplicación.
4. Cree pares de clave y valor para la configuración que desea insertar a los usuarios.

El portal de Intune permite a los administradores implementar fácilmente esta configuración a la aplicación de Power BI mediante directivas de configuración de aplicación. No obstante, se admite cualquier proveedor de MDM. Si no usa Intune, deberá consultar la documentación de MDM sobre cómo implementar esta configuración.

## <a name="next-steps"></a>Pasos siguientes

* Obtenga la aplicación Power BI Mobile en la [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) y en [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Siga [@MSPowerBI en Twitter](https://twitter.com/MSPowerBI)
* Únase a la conversación en la [comunidad de Power BI](https://community.powerbi.com/)