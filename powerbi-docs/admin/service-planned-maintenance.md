---
title: Mantenimiento planeado de Power BI
description: Información para administradores sobre el modo en que el mantenimiento planeado de Power BI afecta a su organización y a los siguientes pasos que pueden tener que realizar.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/19/2020
ms.author: kfollis
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: 13bbf23c075fb1f58c2af71ae0a082d4e539d023
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537697"
---
# <a name="power-bi-planned-maintenance"></a>Mantenimiento planeado de Power BI

El mantenimiento planeado para el servicio Power BI es una parte necesaria de nuestro compromiso de proporcionar un producto confiable a nuestros clientes. Cuando se está realizando el mantenimiento planeado, el servicio Power BI no estará disponible para su organización durante un tiempo. Es posible que los usuarios no puedan tener acceso al servicio Power BI y que las operaciones en segundo plano no se realicen correctamente. Después de la ventana de mantenimiento, esperamos que el servicio funcione normalmente y que las operaciones interactivas y en segundo plano se realicen correctamente.  

Se prevé que el mantenimiento se lleve a cabo fuera del horario comercial normal para minimizar cualquier impacto en la organización. En el caso de las organizaciones que tienen usuarios en todo el mundo, reconocemos que "fuera del horario comercial normal" puede afectar de manera diferente. Lamentamos cualquier repercusión sobre los usuarios. Estamos trabajando para mejorar Power BI y minimizar estas ventanas de mantenimiento.

Si la organización se ve afectada, le proporcionaremos un aviso previo. Los administradores de Microsoft 365 verán un aviso con antelación en el Centro de mensajes de Microsoft 365 y recibirán un correo electrónico. Además, los clientes con contratos de soporte técnico Premier recibirán una notificación a través de su equipo de la cuenta Microsoft.

## <a name="actions-to-take-now"></a>Acciones que se deben realizar ahora

* Los administradores de Microsoft 365 deben [comprobar el Centro de mensajes](https://admin.microsoft.com/Adminportal/Home#/MessageCenter) para ver si hay información sobre el mantenimiento planeado de Power BI. Comparta el mensaje con personas que deben tenerlo en cuenta pero que pueden no tener acceso al Centro de mensajes.
* Si no es administrador de Microsoft 365, póngase en contacto con su departamento de TI o con los equipos de soporte técnico internos para preguntar sobre los próximos mantenimientos.

## <a name="actions-to-take-when-maintenance-is-complete"></a>Acciones que deben realizarse cuando el mantenimiento se completa

* Los usuarios deben actualizar las ventanas abiertas del explorador.
* Los usuarios de la aplicación Power BI Mobile deberán comprobar que están usando la versión más reciente y luego iniciar sesión de nuevo en la aplicación. Compruebe la tienda de aplicaciones de su teléfono o consulte nuestra página de [Power BI Mobile](https://powerbi.microsoft.com/mobile/).
* Los clientes que estaban editando o publicando activamente informes que usan objetos visuales de la organización, ya sea de forma local o desde ubicaciones de OneDrive y SharePoint, deberán volver a importar el archivo visual a través de la tienda de objetos visuales de la organización o descargar un archivo PBIX actualizado antes de volver a publicar. Para obtener más información sobre los objetos visuales de la organización, vea [Objetos visuales de la organización](organizational-visuals.md).
* Si los libros de Excel que usan la característica Analizar en Excel no se actualizan, puede que tenga que actualizar la cadena de conexión o volver a descargar la conexión ODC para ese conjunto de datos. Para más información, vea [Analizar en Excel](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data).
* Los vínculos a Power BI insertados en el contenido podrían no conectarse cuando haya finalizado el mantenimiento. Por ejemplo, un vínculo insertado en SharePoint o Teams puede producir un error de usuario. Para resolver este problema, tiene que volver a generar el vínculo insertado en Power BI y, a continuación, actualizar las ubicaciones en las que se usan. Para obtener más información sobre los vínculos insertados, vea [Insertar un elemento web de informes en SharePoint Online](../collaborate-share/service-embed-report-spo.md) y [Colaboración en Microsoft Teams con Power BI](../collaborate-share/service-collaborate-microsoft-teams.md).

## <a name="next-steps"></a>Pasos siguientes

* [Habilitación de las notificaciones de interrupción del servicio](service-interruption-notifications.md)
* [Seguimiento del próximo cambio en el Centro de mensajes](https://docs.microsoft.com/microsoft-365/admin/manage/message-center?view=o365-worldwide)
