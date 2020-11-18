---
title: Uso de claves administradas por el cliente en Power BI
description: Obtenga información sobre cómo usar claves administradas por el cliente en Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 215c84b9af9d3b785c055d633a41b99bbea2bb2f
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512594"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Uso de claves administradas por el cliente en Power BI

Power BI cifra los datos en reposo y en proceso. De forma predeterminada, Power BI usa claves administradas por Microsoft para cifrar los datos. Las organizaciones pueden optar por usar sus propias claves para el cifrado del contenido del usuario en reposo en Power BI, desde imágenes de informe hasta conjuntos de datos importados en capacidades Premium. 

## <a name="why-use-customer-managed-keys"></a>Por qué usar claves administradas por el cliente

Con las claves administradas por el cliente (CMK) de Power BI, las organizaciones pueden cumplir los requisitos de cumplimiento para el cifrado de datos en reposo con su proveedor de servicios en la nube (en este caso, Microsoft). CMK solo se ofrece a los clientes nuevos de Power BI Premium y permite a las organizaciones cifrar el contenido del usuario de Power BI mediante una clave que proporcionan y administran. La revocación de una clave administrada por el cliente hace que el contenido del usuario dentro de Power BI sea ilegible para el resto durante una hora, incluido Microsoft. En comparación con la oferta BYOK, CMK también abarca el contenido del usuario que genera el servicio, además de los datos del cliente que se importan en los informes y conjuntos de datos hospedados en capacidades Premium, aplica directivas de almacenamiento en caché más estrictas y solo puede aplicar una única clave para cifrar todos los datos.


## <a name="how-to-use-customer-managed-keys"></a>Procedimiento para usar claves administradas por el cliente
Para participar en las claves administradas por el cliente de Power BI, su organización debe ponerse en contacto con el administrador de la cuenta de Microsoft de la misma para validar que esta cumple ciertos requisitos de tamaño necesarios a fin de habilitar CMK.  


## <a name="next-steps"></a>Pasos siguientes

En los vínculos siguientes se proporciona información que puede ser útil para las claves administradas por el cliente:

* [Sus propias claves de cifrado para Power BI](service-encryption-byok.md)
* [Configuración de compatibilidad con Multi-Geo en Power BI Premium](service-admin-premium-multi-geo.md)
* [Cómo funcionan las capacidades](service-premium-what-is.md#how-capacities-function)
* [Actualización incremental](service-premium-incremental-refresh.md)
