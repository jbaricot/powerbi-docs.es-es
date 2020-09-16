---
title: Archivo de inclusión
description: Archivo de inclusión
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: ed87101fe7f5fadd24594d53bbd0ffb6f029faa4
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "90012877"
---
## <a name="single-sign-on"></a>Inicio de sesión único

Después de publicar un conjunto de datos DirectQuery de Azure SQL en el servicio, puede habilitar el inicio de sesión único (SSO) mediante OAuth2 de Azure Active Directory (Azure AD) para los usuarios finales.

Para habilitar el inicio de sesión único, vaya a la configuración del conjunto de datos, abra la pestaña **Orígenes de datos** y active la casilla SSO.

![Configuración del cuadro de diálogo de Azure SQL con DirectQuery](media/direct-query-sso/sso-dialog.png)

Cuando se habilita la opción SSO y los usuarios acceden a informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas a la base de datos o el almacenamiento de datos de Azure SQL. Esta opción permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.

La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación.

> [!Note]
> No se admite Azure Multi-Factor Authentication (MFA). Los usuarios que quieran usar SSO con DirectQuery se deben excluir de MFA.
