---
title: Descripción general de la entidad de servicio
description: Descripción general de la entidad de servicio
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 8482278d9054228dedafb6bd1b37368f5a4b5dce
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315833"
---
La entidad de servicio es un método de autenticación que se puede usar para permitir que una aplicación de Azure AD tenga acceso a las API y el contenido del servicio Power BI.

Al crear una aplicación de Azure Active Directory (Azure AD), se crea un [objeto de entidad de servicio](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). El objeto de entidad de servicio, también conocido como *entidad de servicio*, permite que Azure AD autentique su aplicación. Una vez autenticada, la aplicación puede acceder a los recursos del inquilino de Azure AD.

Para realizar la autenticación, la entidad de servicio usa el *identificador de aplicación* de la aplicación de Azure AD y uno de los siguientes:

* Secreto de aplicación
* Certificado