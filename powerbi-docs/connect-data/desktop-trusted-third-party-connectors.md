---
title: Conectores de terceros de confianza en Power BI
description: Confianza en un conector de terceros firmado en Power BI
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 06b117a271671092a94aa8e7994269344b444178
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90859621"
---
# <a name="trusted-third-party-connectors"></a>Conectores de terceros de confianza

## <a name="why-do-you-need-trusted-third-party-connectors"></a>¿Por qué necesita conectores de terceros de confianza?

En Power BI, generalmente se recomienda mantener el nivel de "seguridad de la extensión de datos" en el nivel superior, lo que evita que se pueda cargar código no certificado por Microsoft. Sin embargo, puede haber muchos casos en los que desee cargar conectores específicos como los que haya escrito usted mismo o los que haya proporcionado un consultor o un proveedor fuera de la ruta de certificación de Microsoft.

El desarrollador de un conector determinado puede firmarlo con un certificado y proporcionarle la información que necesita para cargarlo de forma segura sin reducir el nivel de seguridad.

Si desea obtener más información sobre la configuración de seguridad, puede leer sobre esta [aquí](./desktop-connector-extensibility.md).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Uso del registro para confiar en conectores de terceros

La confianza en conectores de terceros de Power BI se realiza mediante la huella digital del certificado en el que desea confiar en un valor del registro especificado. Si esta huella digital coincide con la huella digital del certificado del conector que desea cargar, podrá cargarlo en el nivel de seguridad "Recomendado" de Power BI. 

La ruta de acceso del registro es HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Asegúrese de que la ruta existe o créela. Hemos elegido esta ubicación porque está controlada principalmente por la directiva de TI y además requiere un acceso de administración a la máquina local para editar. 

![Registro de Power BI Desktop sin ningún conjunto de claves de terceros de confianza](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Agregue un nuevo valor en la ruta de acceso especificada anteriormente. El tipo debe ser "valor de cadena múltiple" (REG_MULTI_SZ) y debe llamarse "TrustedCertificateThumbprints". 

![Registro de Power BI Desktop con una entrada para conectores de terceros de confianza pero sin claves](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Agregue las huellas digitales de los certificados en los que desea confiar. Puede agregar varios certificados mediante "\0" como delimitador, o bien, en el Editor del Registro, puede hacer clic con el botón derecho en -> Modificar y colocar cada huella digital en una línea nueva. La huella digital de ejemplo se ha tomado de un certificado autofirmado. 

 ![Registro de Power BI Desktop con un conjunto de claves de terceros de confianza](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Si ha seguido las instrucciones correctamente y el desarrollador le ha proporcionado la huella digital adecuada, ahora debería poder confiar de forma segura en los conectores firmados con el certificado asociado.

## <a name="how-to-sign-connectors"></a>Firma de conectores

Si tiene un conector que usted o un desarrollador deben firmar, puede consultar cómo hacerlo en la documentación de Power Query que se encuentra [aquí](/power-query/handlingconnectorsigning).