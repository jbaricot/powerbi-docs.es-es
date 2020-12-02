---
title: Notificaciones de interrupción del servicio
description: Obtenga información sobre cómo recibir notificaciones por correo electrónico cuando se produzca una interrupción del servicio Power BI.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/25/2020
ms.openlocfilehash: e5d8f43a8edb6dc05b58cb62836e98cf209c8b5c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407823"
---
# <a name="service-interruption-notifications"></a>Notificaciones de interrupción del servicio

Es importante tener información sobre la disponibilidad de las aplicaciones empresariales críticas. Power BI proporciona una notificación de incidentes para que pueda recibir mensajes de correo electrónico si se produce una interrupción o degradación del servicio. Aunque el Acuerdo de Nivel de Servicio (SLA) del 99,9 % de Power BI hace que esto sea poco frecuente, queremos asegurarnos de que esté informado. En la captura de pantalla siguiente se muestra el tipo de correo electrónico que recibirá si habilita las notificaciones:

![Correo electrónico de notificación de actualización](media/service-interruption-notifications/refresh-notification-email.png)

En este momento, se envían mensajes de correo electrónico para los siguientes _escenarios de confiabilidad_:

- Confiabilidad de apertura del informe
- Confiabilidad de actualización del modelo
- Confiabilidad de actualización de consultas

Las notificaciones se envían cuando se produce un _retraso prolongado_ en las operaciones (por ejemplo, al abrir un informe, actualizar conjuntos de datos o ejecutar consultas). Una vez que se ha resuelto un incidente, recibirá un correo electrónico de seguimiento.

> [!NOTE]
> En la actualidad, esta característica solo está disponible para las capacidades en Power BI Premium. No está disponible para la capacidad compartida o insertada.

## <a name="capacity-and-reliability-notifications"></a>Notificaciones de capacidad y fiabilidad

Cuando una capacidad de Power BI Premium está experimentando periodos largos de uso elevado de recursos que pueden afectar a la fiabilidad, se envía un correo electrónico de notificación. Entre los ejemplos de estos efectos se incluyen retrasos prolongados en operaciones como, por ejemplo, abrir un informe, actualización del conjunto de datos y ejecuciones de consultas. 

En el correo electrónico de notificación se proporciona información sobre el motivo del uso elevado de recursos, incluida la siguiente:

* Id. del conjunto de datos del responsable
* Tipo de operación
* Tiempo de CPU asociado al uso elevado de recursos. Esta es la [definición de tiempo de CPU](https://wikipedia.org/wiki/CPU_time) en Wikipedia.

Power BI también envía notificaciones por correo electrónico cuando se detecta una sobrecarga en una capacidad de Power BI Premium. El correo electrónico explica el motivo más probable de la sobrecarga, las operaciones que han generado la carga en los 10 minutos anteriores y la carga de cada operación generada.

Si tiene más de una capacidad Premium, el correo electrónico incluye información sobre esas capacidades durante el período sobrecargado. Esta información le ayuda a considerar la posibilidad de mover las áreas de trabajo que contienen elementos con un uso intensivo de recursos a capacidades con la carga mínima.

Las notificaciones correos electrónicos de sobrecarga solo se envían cuando se desencadena un umbral de sobrecarga. No recibirá un segundo correo electrónico cuando la carga en esa capacidad Premium vuelva a los niveles no sobrecargados.

En la imagen siguiente se muestra un ejemplo de correo electrónico de notificación:

![correo electrónico de notificación de capacidad sobrecargada](media/service-interruption-notifications/refresh-notification-email-2.png)


## <a name="enable-notifications"></a>Habilitación de notificaciones

Un administrador de Power BI habilita las notificaciones en el portal de administración:

1. Identifique o cree un grupo de seguridad habilitado para correo electrónico que deba recibir notificaciones.

1. En el portal de administración, seleccione **Configuración de inquilinos**. En **Configuración de ayuda y soporte técnico**, expanda **Recepción de notificaciones por correo electrónico sobre interrupciones o incidentes en el servicio**.

1. Habilite las notificaciones, escriba un grupo de seguridad y seleccione **Aplicar**.

    ![Habilitación de notificaciones del servicio](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI envía notificaciones desde la cuenta no-reply-powerbi@microsoft.com. Asegúrese de que esta cuenta se agregue a la lista de remitentes seguros para que las notificaciones no vayan a una carpeta de correo no deseado.

## <a name="service-health-in-microsoft-365"></a>Estado del servicio en Microsoft 365

En este artículo se describe cómo recibir notificaciones de servicio mediante Power BI. También puede supervisar el estado del servicio Power BI mediante Microsoft 365. Participe para recibir notificaciones por correo electrónico sobre el estado del servicio desde Microsoft 365. Obtenga más información en [Cómo comprobar el estado del servicio de Microsoft 365](/microsoft-365/enterprise/view-service-health).

## <a name="next-steps"></a>Pasos siguientes

[Opciones de soporte técnico de Power BI Pro y Power BI Premium](service-support-options.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)