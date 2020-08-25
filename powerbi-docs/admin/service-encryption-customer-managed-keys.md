---
title: Uso de claves administradas por el cliente en Power BI
description: Obtenga información sobre cómo usar claves administradas por el cliente en Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160949"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Uso de claves administradas por el cliente en Power BI

Power BI cifra los datos en reposo y en proceso. De forma predeterminada, Power BI usa claves administradas por Microsoft para cifrar los datos. Las organizaciones pueden optar por usar sus propias claves para el cifrado del contenido del usuario en reposo en Power BI, desde imágenes de informe hasta conjuntos de datos importados en capacidades Premium. 

## <a name="why-use-customer-managed-keys"></a>Por qué usar claves administradas por el cliente
Con las claves administradas por el cliente (CMK) de Power BI, las organizaciones pueden cumplir los requisitos de cumplimiento para el cifrado de datos en reposo con su proveedor de servicios en la nube (en este caso, Microsoft). CMK permite a las organizaciones cifrar el contenido del usuario de Power BI con una clave que ellas proporcionan y administran. La revocación de una clave administrada por el cliente hace que el contenido del usuario dentro de Power BI sea ilegible para el resto durante una hora, incluido Microsoft. En comparación con la oferta BYOK, CMK también abarca el contenido de los usuarios fuera de las capacidades Premium de Power BI, aplica directivas de almacenamiento en caché más estrictas y, de forma predeterminada, habilita BYOK en todas las capacidades. 
 
## <a name="how-to-use-customer-managed-keys"></a>Procedimiento para usar claves administradas por el cliente
Para participar en las claves administradas por el cliente de Power BI, la organización debe cumplir los requisitos de tamaño. El administrador global de la organización debe enviar una solicitud de soporte técnico a Microsoft, o bien ponerse en contacto con el administrador de cuentas de Microsoft de la organización para obtener más información sobre el proceso.  


## <a name="next-steps"></a>Pasos siguientes

En los vínculos siguientes se proporciona información que puede ser útil para las claves administradas por el cliente:

* [Sus propias claves de cifrado para Power BI](service-encryption-byok.md)
* [Configuración de compatibilidad con Multi-Geo en Power BI Premium](service-admin-premium-multi-geo.md)
* [Cómo funcionan las capacidades](service-premium-what-is.md#how-capacities-function)
* [Actualización incremental](service-premium-incremental-refresh.md)
