---
title: Adquirir y asignar licencias de Power BI Pro
description: Aprenda a adquirir y asignar licencias de Power BI Pro para los usuarios para que puedan acceder a contenido y colaborar con otros en el servicio Power BI.
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 0184e549911afb784e06b1ee829bf113ff97e067
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086312"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Compra y asignación de licencias de usuario de Power BI Pro

>[!IMPORTANT]
>Este artículo es para administradores. ¿Está a punto para realizar la actualización a una licencia de Power BI Pro? Vaya directamente a [Introducción a Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) para configurar su cuenta.

Power BI Pro es una licencia de usuario individual que permite a los usuarios leer e interactuar con los informes y paneles que otros usuarios han publicado en el servicio Power BI. Los usuarios con este tipo de licencia pueden compartir contenido y colaborar con otros usuarios de Power BI Pro. Solo los usuarios de Power BI Pro pueden publicar o compartir contenido con otros usuarios o consumir contenido creado por otros, salvo que la capacidad de una instancia Power BI Premium hospede dicho contenido. Para obtener más información sobre los tipos de licencias y suscripciones disponibles, consulte [Licencias de Power BI en la organización](service-admin-licensing-organization.md).

## <a name="purchase-power-bi-pro-user-licenses"></a>Adquisición de licencias de usuario de Power BI Pro

En este artículo se explica cómo adquirir licencias de usuario de Power BI Pro en el centro de administración de Microsoft 365. Después de comprar las licencias, puede asignarlas a los usuarios en el centro de administración de Microsoft 365 o en Azure Portal.

> [!NOTE]
> A partir del 14 de enero de 2020, las funcionalidades de compra, suscripción y administración de licencias de autoservicio para los productos de Power Platform (Power BI, Power Apps y Power Automate) están disponibles para los clientes de la nube comercial. Para obtener más información, vea las [preguntas más frecuentes sobre las compras de autoservicio](/microsoft-365/commerce/subscriptions/self-service-purchase-faq). Para habilitar o deshabilitar las funcionalidades de compra de autoservicio, consulte cómo [habilitar o deshabilitar el registro y la compra de autoservicio](./service-admin-disable-self-service.md).

### <a name="prerequisites"></a>Requisitos previos

Para comprar y asignar licencias en el centro de administración de Microsoft 365, debe ser miembro del rol [Administrador global o Administrador de facturación](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) en Microsoft 365.

Para asignar licencias en Azure Portal, debe ser propietario de la suscripción a Azure que se usa en Power BI para las búsquedas de Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Compra de licencias en Microsoft 365

> [!NOTE]
> Si normalmente compra licencias a través de un contrato de licencias por volumen, como un Contrato Enterprise, y quiere recibir una factura en lugar de comprar con una tarjeta de crédito o una cuenta bancaria, tendrá que enviar el pedido de otra manera. Trabaje con el revendedor de Microsoft o el Centro de servicios de licencias por volumen para agregar o quitar licencias. Para obtener más información, vea [Administración de licencias de suscripción](/microsoft-365/commerce/licenses/buy-licenses).

Siga estos pasos para comprar licencias de Power BI Pro en el Centro de administración de Microsoft 365:

1. Inicie sesión en el [Centro de administración de Microsoft 365](https://admin.microsoft.com).

2. En el menú de navegación, seleccione **Facturación** > **Servicios de compra**.

3. Busque la suscripción que desea comprar. Encontrará **Power BI** en **Other categories that might interest you** (Otras categorías que pueden interesarle) cerca de la parte inferior de la página. Seleccione el vínculo para ver las suscripciones de Power BI disponibles para su organización.

4. Seleccione **Power BI Pro**.

5. En la página **Servicios de compra**, seleccione **Comprar**.

6. Elija **Pagar mensualmente** o **Pagar un año completo**, según cómo desee pagar.

7. En **How many users do you want?** (¿Cuántos usuarios quiere?), escriba el número de licencias que quiere comprar y seleccione **Check out now** (Comprar ahora) para completar la transacción.

8. Para comprobar la compra, vaya a **Facturación** > **Productos y servicios** y busque **Power BI Pro**.

9. Para agregar más licencias más adelante, busque **Power BI Pro** en la página **Productos y servicios** y, a continuación, seleccione **Agregar o quitar licencias**.


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Asignación de licencias en el Centro de administración de Microsoft 365

Para más información sobre la asignación de licencias en el Centro de administración de Microsoft 365, vea [Asignación de licencias a usuarios](/office365/admin/manage/assign-licenses-to-users).

Para los usuarios invitados, vea [Asignación de licencias a usuarios en la página Licencias](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Antes de asignar licencias Pro a usuarios invitados, póngase en contacto con el representante de la cuenta de Microsoft para asegurarse de que cumple con los términos del contrato con Microsoft.

## <a name="assign-licenses-in-the-azure-portal"></a>Asignación de licencias en Azure Portal

Siga estos pasos para asignar licencias de Power BI Pro a cuentas de usuario individuales:

1. Inicie sesión en [Azure Portal](https://portal.azure.com/).

2. Busque y seleccione **Azure Active Directory**.

3. En **Administrar** en el menú de recursos **Azure Active Directory**, seleccione **Licencias**.

4. Seleccione **Todos los productos** en el menú **Licencias: Información general** y, a continuación, seleccione **Power BI Pro** para ver la lista de usuarios con licencia.

5. En la barra de comandos, seleccione **+ Asignar**. En la página **Asignar licencia**, elija primero un usuario y, después, seleccione **Opciones de asignación** para activar una licencia de Power BI Pro para la cuenta de usuario seleccionada.

## <a name="next-steps"></a>Pasos siguientes

- [Licencias de Power BI en la organización](service-admin-licensing-organization.md)

 - [Encontrar usuarios de Power BI que hayan iniciado sesión](service-admin-access-usage.md)

 - [Registro en Power BI como usuario individual](../fundamentals/service-self-service-signup-for-power-bi.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)