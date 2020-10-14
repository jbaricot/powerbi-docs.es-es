---
title: Configurar aplicaciones móviles con Microsoft Intune
description: Cómo configurar aplicaciones móviles de Power BI con Microsoft Intune Incluye cómo agregar e implementar la aplicación. También incluye cómo crear la directiva de aplicación móvil para controlar la seguridad.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a7a3e0382b80d46ddb41b3f5677763a1a08bf26d
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/13/2020
ms.locfileid: "91981559"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Configurar aplicaciones móviles con Microsoft Intune

Microsoft Intune permite a las organizaciones administrar dispositivos y aplicaciones. Las aplicaciones móviles de Power BI para iOS y Android se integran con Intune. Esta integración le permite administrar la aplicación en los dispositivos y controlar la seguridad. Mediante las directivas de configuración, puede controlar elementos como requerir un PIN de acceso, la forma en que la aplicación controla los datos e incluso cifrar los datos de la aplicación cuando la aplicación no está en uso.

La aplicación móvil de Microsoft Power BI permite obtener acceso a la información empresarial importante. Puede ver e interactuar con los paneles e informes para todos los datos empresariales de los dispositivos administrados y las aplicaciones de la organización. Para obtener más información sobre las aplicaciones de Intune compatibles, vea [Aplicaciones protegidas de Microsoft Intune](/intune/apps/apps-supported-intune-apps).

## <a name="general-mobile-device-management-configuration"></a>Configuración general de administración de dispositivos móviles

En este artículo se supone que Intune está configurado correctamente y que tiene dispositivos inscritos con Intune. Este artículo no está pensado como una guía de configuración completa de Microsoft Intune. Para obtener más información sobre Intune, vea [¿Qué es Intune?](/intune/introduction-intune/)

Microsoft Intune puede coexistir con administración de dispositivos móviles (MDM) en Microsoft 365. Si usa MDM, el dispositivo se mostrará como inscrito en MDM, pero está disponible para administrarlo en Intune.

Antes de que los usuarios finales puedan usar la aplicación de Power BI en sus dispositivos, un administrador de Intune debe agregarla a Intune y también asignarla a los usuarios finales.

> [!NOTE]
> Después de configurar Intune, la actualización de datos en segundo plano se desactiva para la aplicación móvil de Power BI en su dispositivo iOS o Android. Power BI actualizará los datos desde el servicio Power BI en la web cuando se acceda a la aplicación.

## <a name="step-1-add-the-power-bi-app-to-intune"></a>Paso 1: Adición de la aplicación de Power BI a Intune

Para agregar la aplicación de Power BI a Intune, siga los pasos que se indican en los temas siguientes:
- [Incorporación de aplicaciones de la tienda iOS a Microsoft Intune](/intune/apps/store-apps-ios)
- [Agregar aplicaciones de la Tienda Android a Microsoft Intune](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>Paso 2: Asignación de la aplicación a los usuarios finales

Después de agregar la aplicación de Power BI a Microsoft Intune, puede asignarla a usuarios y dispositivos. Es importante tener en cuenta que puede asignar una aplicación a un dispositivo independientemente de si el dispositivo está administrado por Intune o no.

Para asignar la aplicación de Power BI a usuarios y dispositivos, siga los pasos proporcionados en [Asignación de aplicaciones a grupos con Microsoft Intune](/intune/apps/apps-deploy).

## <a name="step-3-create-and-assign-app-protection-policies"></a>Paso 3: Creación y asignación de directivas de protección de aplicaciones

Las directivas de protección de aplicaciones (APP) que garantizan los datos de la organización siguen siendo seguras o se encuentran en una aplicación administrada. Una directiva puede ser una regla que se aplica cuando el usuario intenta obtener acceso o mover datos "corporativos" o un conjunto de acciones que están prohibidas o que se supervisan cuando el usuario está dentro de la aplicación. Una aplicación administrada es aquella que tiene las directivas de protección de aplicaciones aplicadas y puede administrarse mediante Intune.

Las directivas de protección de aplicaciones de Administración de aplicaciones móviles (MAM) le permiten administrar y proteger los datos de su organización dentro de una aplicación. Con MAM sin inscripción (MAM-WE), una aplicación profesional o educativa que contiene información confidencial puede administrarse en casi cualquier dispositivo, incluidos los dispositivos personales en escenarios de Bring Your Own Device (BYOD). Para obtener más información, consulte [Introducción a las directivas de protección de aplicaciones](/intune/apps/app-protection-policy).

Para crear y asignar una directiva de protección de aplicaciones para la aplicación de Power BI, siga los pasos proporcionados en [Procedimiento para crear y asignar directivas de protección de aplicaciones](/intune/apps/app-protection-policies).

## <a name="step-4-use-the-application-on-a-device"></a>Paso 4: Uso de la aplicación en un dispositivo

Las aplicaciones administradas son aplicaciones que el equipo de soporte técnico de su empresa puede configurar para ayudar a proteger los datos de la empresa a los que se puede obtener acceso en esa aplicación. Al acceder a los datos de la empresa en una aplicación administrada en el dispositivo, puede observar que la aplicación funciona de forma ligeramente diferente a lo esperado. Por ejemplo, es posible que no pueda copiar y pegar los datos protegidos de la compañía o no pueda guardar dichos datos en determinadas ubicaciones.

Para entender cómo los usuarios finales pueden usar la aplicación de Power BI en su dispositivo, revise los pasos proporcionados en los artículos siguientes:
- [Usar aplicaciones administradas en el dispositivo iOS](/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [Usar aplicaciones administradas en el dispositivo Android](/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>Pasos siguientes

[Creación y asignación de directivas de protección de aplicaciones](/intune/app-protection-policies) 

[Aplicaciones de Power BI para dispositivos móviles](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)