---
title: Aplicación de creación de entidad de servicio
description: Aplicación de creación de entidad de servicio
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 80886eab6de6c125d0361b326f5d31d2b3bb35e5
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524540"
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

    ![Captura de pantalla en la que se muestra dónde obtener un identificador de aplicación en la pestaña Información general.](media/embedded-service-principal/application-id.png)