---
title: Aplicación de creación de entidad de servicio
description: Aplicación de creación de entidad de servicio
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315840"
---
1. Inicie sesión en [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Busque **Registros de aplicaciones** y haga clic en el vínculo **Registros de aplicaciones**.

    ![registro de aplicaciones de Azure](media/embedded-service-principal/azure-app-registration.png)

3. Haga clic en **Nuevo registro**.

    ![nuevo registro](media/embedded-service-principal/new-registration.png)

4. Rellene la información necesaria:
    * **Nombre**: escriba un nombre para la aplicación.
    * **Tipos de cuenta admitidos**: seleccione tipos de cuenta admitidos.
    * (Opcional) **URI de redireccionamiento**: escriba un URI si es necesario.

5. Haga clic en **Registrar**.

6. Después del registro, el *identificador de la aplicación* está disponible en la pestaña **Información general**. Copie y guarde el *identificador de aplicación* para su uso posterior.

    ![identificador de aplicación](media/embedded-service-principal/application-id.png)