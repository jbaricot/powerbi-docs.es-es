---
title: Uso de la misma cuenta para Power BI y Azure
description: Uso del mismo inicio de sesión de la cuenta para Power BI y Azure
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 2706fd8eb4cb2fddda99710e7c1dc32c2300aa26
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413619"
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>Uso de la misma cuenta para Power BI y Azure

Si es usuario de Power BI y de Azure, puede que quiera usar el mismo inicio de sesión para ambos servicios, por lo que no es necesario escribir la contraseña dos veces.

Se realiza el registro en Power BI con su cuenta de la organización, asociada a su dirección de correo electrónico educativa o profesional.  Se realiza el registro en Azure con una cuenta Microsoft o su cuenta de la organización.

Si desea usar el mismo inicio de sesión para Azure y Power BI, asegúrese de iniciar sesión en Azure con su cuenta de la organización.

**¿Qué ocurre si ya ha iniciado sesión en Azure con su cuenta Microsoft?**

Puede agregar su cuenta de la organización como coadministrador en Azure mediante estos pasos:

1. Inicie sesión en [Azure Portal](https://portal.azure.com/). Si es usuario de varios directorios de Azure, haga clic en **Suscripciones** y, luego, filtre para ver solo el directorio y las suscripciones que quiere editar.

1. En el panel de navegación, seleccione **Control de acceso (IAM)** y, luego, **Agregar** \> **Agregar coadministrador**.

    ![Captura de pantalla del control de acceso con Agregar coadministrador destacado.](media/service-admin-how-to-use-the-same-account-as-azure/add-co-administrator.png)

1. Escriba la dirección de correo electrónico asociada a su cuenta de la organización y seleccione **Agregar**.

1. La próxima vez que inicie sesión en Azure Portal, use su dirección de correo electrónico de la organización.

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
