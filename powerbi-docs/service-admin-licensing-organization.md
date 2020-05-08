---
title: Licencias de Power BI en la organización
description: Información general sobre los diferentes tipos de licencia disponibles en Power BI y sobre cómo los administradores adquieren y administran las licencias de su organización.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: a41e9453158c38a208fe7f4ac937b4e86a515f4b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "81436331"
---
# <a name="power-bi-licensing-in-your-organization"></a>Licencias de Power BI en la organización

En el servicio Power BI, los usuarios pueden hacer diferentes cosas en función del tipo de licencia por usuario que tienen y de si el contenido sobre el que actúan se encuentra en un área de trabajo asignada a una capacidad de Power BI Premium. Todos los usuarios del servicio Power BI deben tener una licencia.

Hay dos maneras para que los usuarios obtengan una licencia. Con las funcionalidades de registro de autoservicio y su cuenta profesional o educativa, los usuarios pueden obtener su propia licencia gratuita o Pro. O bien, los administradores pueden obtener una suscripción de Power BI y asignar licencias a los usuarios.

Este artículo se centra en la compra de servicios y licencias por usuario desde una perspectiva de administrador. Para obtener más información sobre cómo los usuarios pueden obtener su propia licencia, consulte el artículo [Registro en Power BI como usuario individual](service-self-service-signup-for-power-bi.md).

## <a name="who-can-purchase-and-assign-licenses"></a>¿Quién puede comprar y asignar licencias?

Debe tener asignado un rol de administrador para poder comprar o asignar licencias para su organización. Los roles de administrador se asignan mediante el centro de administración de Azure Active Directory o de Microsoft 365. En la tabla siguiente se muestra qué rol es necesario para realizar tareas relacionadas con la adquisición y la concesión de licencias. Para obtener más información sobre los roles de administrador en Azure Active Directory, consulte [Visualización y asignación de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal). Si lo que quiere es obtener información sobre los roles de administrador en Microsoft 365, incluidos los procedimientos recomendados, vea el artículo [Acerca de los roles de administrador](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

| ¿Quién puede adquirir servicios y licencias? | ¿Quién puede administrar licencias de usuario? |
| --------------- | --------------- |
| Administrador de facturación | Administrador de licencias |
| Administrador global | Administrador de usuarios |
|  | Administrador global |

Estos roles administran la organización. Para obtener información sobre los roles de administrador del servicio Power BI, consulte [Descripción de los roles de administrador del servicio Power BI](service-admin-role.md).

## <a name="get-power-bi-for-your-organization"></a>Obtención de Power BI para su organización

Un administrador global o un administrador de facturación puede suscribirse al servicio Power BI y comprar licencias para los usuarios de su organización. Si no está a punto para realizar la compra, seleccione la prueba de Power BI Pro. Obtendrá 25 licencias que podrá usar durante un mes. Para obtener instrucciones paso a paso sobre cómo suscribirse, consulte cómo [obtener una suscripción de Power BI para su organización](admin/service-admin-org-subscription.md).

## <a name="about-self-service-sign-up"></a>Acerca del registro de autoservicio

Los usuarios individuales pueden obtener sus propias licencias de Power BI registrándose con su cuenta profesional o educativa. Con una licencia gratuita, los usuarios pueden explorar Power BI para analizar y visualizar datos personales desde la sección Mi área de trabajo, pero no pueden colaborar con otros usuarios. Se requiere una licencia de Power BI Pro para compartir contenido. Los usuarios pueden actualizar su tipo de licencia a Pro, o registrarse directamente en Pro, si su organización usa la nube comercial. La compra directa o la actualización a Pro no está disponible para las organizaciones educativas ni para las implementadas en la Administración Pública o en instancias de la nube soberana.

Si no quiere que el registro de autoservicio esté disponible para los usuarios de su organización, consulte el artículo [Activación o desactivación del registro de autoservicio](admin/service-admin-disable-self-service.md) para obtener información sobre cómo desactivarlo.

Si quiere ver qué usuarios de su organización puede que ya dispongan de una licencia, consulte el artículo sobre cómo [ver y administrar licencias de usuario](admin/service-admin-manage-licenses.md).

## <a name="license-types-and-capabilities"></a>Tipos de licencia y funcionalidades

Hay dos tipos de licencias de Power BI por usuario: gratuita y Pro. El tipo de licencia que necesita un usuario depende de dónde almacene el contenido y de cómo interactuará con ese contenido. El lugar donde se puede almacenar el contenido viene determinado por el [tipo de suscripción](#subscription-types) de su organización.

El tipo de suscripción [Power BI Premium](service-admin-premium-purchase.md) permite a los usuarios con una licencia gratuita actuar en el contenido de las áreas de trabajo que se asignan a la capacidad Premium. Fuera de la capacidad Premium, un usuario con una licencia gratuita solo puede usar el servicio Power BI para conectarse a los datos y crear informes y paneles en un área de trabajo personal. No puede compartir contenido con otros usuarios ni publicar contenido en áreas de trabajo de las aplicaciones.

Las suscripciones estándar de Power BI usan una capacidad compartida. Cuando el contenido se almacena en capacidad compartida, los usuarios a los que se les asigna una licencia de Power BI Pro solo pueden colaborar con otros usuarios de Power BI Pro. Pueden consumir contenido compartido por otros usuarios, publicar contenido en áreas de trabajo de las aplicaciones, compartir paneles y suscribirse a paneles e informes.  Cuando las áreas de trabajo están en una capacidad Premium, los usuarios de Pro pueden distribuir contenido a usuarios que no tienen una licencia de Power BI Pro.

En la tabla siguiente se resumen las funcionalidades básicas de cada tipo de licencia. Para obtener un desglose detallado de la disponibilidad de características según el tipo de licencia, consulte el artículo [Características del servicio Power BI por tipo de licencia](service-features-license-type.md).

| Tipo de licencia | Funcionalidades cuando el área de trabajo está en capacidad compartida | Funcionalidades adicionales cuando el área de trabajo está en una capacidad Premium |
| --------- | ----------- | ----------- |
| Power BI (gratis) | Acceso al contenido de Mi área de trabajo | Consumo de contenido compartido con ellos |
| Power BI Pro | Publicación de contenido en áreas de trabajo de las aplicaciones, uso compartido paneles, suscripción a paneles e informes y uso compartido de contenido con usuarios que tienen una licencia Pro | Distribución de contenido a usuarios con licencias gratuitas |

## <a name="subscription-types"></a>Tipos de suscripción

Todas las suscripciones de licencias comerciales de Microsoft para usuarios se basan en identidades de Azure Active Directory. Esto significa que debe iniciar sesión con una identidad que admita Azure Active Directory para obtener licencias comerciales. Puede agregar una suscripción de Power BI a cualquier suscripción de Microsoft que use Azure Active Directory para servicios de identidad. Algunas suscripciones, como Office 365 E5, incluyen una licencia de Power BI Pro, por lo que no se necesita ningún registro independiente para Power BI.

Hay dos tipos de suscripciones de Power BI para las organizaciones: BI de autoservicio con Power BI Pro y análisis avanzado con Power BI Premium.

Con una suscripción estándar de autoservicio a Power BI Pro, los administradores asignan licencias por usuario. Se cobra una cuota mensual por usuario por las licencias de Power BI Pro, lo que permite la colaboración, la publicación, el uso compartido y el análisis ad hoc. El contenido se guarda en una capacidad de almacenamiento compartido totalmente administrada por Microsoft.

Una suscripción de Power BI Premium asigna capacidad dedicada a una organización. Las licencias Premium proporcionan controles avanzados de administración e implementación, muy adecuados para BI empresarial, el análisis de macrodatos y la creación de informes locales y en la nube. Los administradores de capacidad de la organización se encargan de administrar los recursos dedicados de almacenamiento y de proceso. Este entorno dedicado tiene un costo mensual. Además de otras ventajas, los usuarios que no tienen licencias de Power BI Pro pueden acceder al contenido almacenado en una capacidad Premium y distribuirlo. Al menos un usuario debe tener una licencia de Power BI Pro asignada para usar Premium, y los creadores del contenido y los desarrolladores siguen necesitando una licencia de Power BI Pro.

Los dos tipos de suscripciones no son mutuamente excluyentes. Puede tener Power BI Premium y Power BI Pro. En esta configuración, el contenido almacenado en la capacidad Premium se puede compartir con todos los usuarios, y la capacidad compartida también está disponible. Para obtener información acerca de los límites de capacidad, consulte el artículo [Administración del almacenamiento de datos en las áreas de trabajo de Power BI](service-admin-manage-your-data-storage-in-power-bi.md).

Para comparar las características y los precios de los productos, vea [Precios de Power BI](https://powerbi.microsoft.com/pricing).

## <a name="guest-user-access"></a>Acceso de usuarios invitados

Es posible que quiera distribuir contenido a usuarios de fuera de la organización. Es posible compartir contenido con usuarios externos invitándolos a ver el contenido como invitados. Azure AD B2B (Azure Active Directory de negocio a negocio) permite compartir contenido con usuarios invitados externos. Para poder compartir contenido con usuarios externos, se deben cumplir los siguientes requisitos previos:

- La capacidad de compartir contenido con usuarios externos debe estar habilitada.

- El usuario invitado debe tener la licencia adecuada para ver el contenido compartido.

Para obtener más información sobre el acceso de usuarios invitados, consulte [Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="purchase-power-bi-pro-licenses"></a>Adquisición de licencias de Power BI Pro

Como administrador, puede adquirir licencias de Power BI Pro mediante Microsoft 365 o a través de un partner de Microsoft. Después de comprar las licencias, deberá asignarlas a usuarios individuales. Para obtener más información, vea [Adquirir y asignar licencias de Power BI Pro](service-admin-purchasing-power-bi-pro.md).

### <a name="power-bi-pro-license-expiration"></a>Expiración de la licencia de Power BI Pro

Hay un período de gracia después de que expire una licencia de Power BI Pro. Las licencias que forman parte de una compra de licencia por volumen disponen de un período de gracia de 90 días. Si compró la licencia directamente, el período de gracia es de 30 días.

Power BI Pro tiene el mismo ciclo de vida de suscripción que Office 365. Para más información, consulte [¿Qué pasa con mis datos y mi acceso cuando termina mi suscripción de Office 365 para empresas?](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3)


## <a name="next-steps"></a>Pasos siguientes

- [Adquirir y asignar licencias de Power BI Pro](service-admin-purchasing-power-bi-pro.md)
- [Suscripciones de empresa y documentación de facturación de Microsoft 365](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [Find Power BI users that have signed in](service-admin-access-usage.md) (Búsqueda de usuarios de Power BI que hayan iniciado sesión)
- ¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
