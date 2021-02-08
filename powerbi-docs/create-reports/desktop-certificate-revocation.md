---
title: Comprobación de la revocación de certificados en Power BI Desktop
description: Procedimiento para revocar certificados en Power BI Desktop en la interfaz de usuario y en el Registro
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 482f0f8279de9818b631ff79e7b37a215e7397bd
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2021
ms.locfileid: "99056375"
---
# <a name="certificate-revocation-in-power-bi-desktop"></a>Revocación de certificados en Power BI Desktop

Power BI ofrece dos formas de habilitar o deshabilitar una comprobación de certificados. En noviembre de 2020, presentamos una comprobación simple (activación o desactivación) de revocación de certificados para las conexiones web de Power BI Desktop. Ahora puede tener un control más preciso de la comprobación de la revocación de certificados.

## <a name="simple-certificate-revocation"></a>Revocación de certificados simple

En la interfaz de usuario de Power BI Desktop, puede habilitar o deshabilitar la característica.

- En el menú **Archivo** > **Opciones y configuración** > **Opciones**, seleccione **Seguridad** y, después, active o desactive la opción **Habilitar comprobación de revocación de certificados**.

## <a name="more-fine-grained-control"></a>Control más preciso

Puede disponer de un control más preciso de la comprobación de revocación de certificados mediante una tercera opción. 

- **Básica**: la comprobación básica acepta certificados cuyo estado de revocación es desconocido; por ejemplo, porque el certificado no lo especifica. Esta comprobación es importante para las organizaciones que usan servidores proxy corporativos. Es lo mismo que seleccionar la casilla en Power BI Desktop.
- **Deshabilitada**: es lo mismo que deshabilitar la casilla en Power BI Desktop.
- **Completa**: puede deshabilitar o habilitar la comprobación de revocaciones en el modo *completo*, que no admite certificados con un estado de revocación desconocido. 


|Estado de información de revocación de certificados | Comprobación completa | Comprobación básica | None |
|---------|---------|---------|---------|
|Revocada     |  ❌  | ❌  | ✔   |
|Desconocido  |  ❌    |  ✔   |    ✔  |
|No revocado  | ✔  |    ✔ |    ✔  |

La casilla simple Habilitar o deshabilitar sigue en la interfaz de usuario de Power BI Desktop. Para usar el control más específico, establezca el siguiente valor del Registro de DWORD: `DisableCertificateRevocationCheck`. Este valor se establece en la clave del Registro de Power BI Desktop. Es uno de estos, en función de su sistema operativo:

```
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop
```

O:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop
```

Establezca el valor del Registro en uno de los valores siguientes: 

|Value  |Modo  |Configuración  |
|---------|---------|---------|
|0     | Básico   | Se aceptan los certificados con un estado de revocación desconocido. Es equivalente a habilitar la casilla en Power BI Desktop. |
|1     | Disabled  | Ignora todas las comprobaciones de revocación. Es equivalente a deshabilitar la casilla en Power BI Desktop.  |
|2     | Completo  |  Requiere que no se revoquen los certificados. No acepta los certificados con un estado de revocación desconocido. |

Configure este valor del Registro para beneficiarse de un control más preciso hoy mismo.