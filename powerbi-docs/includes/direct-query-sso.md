---
title: Archivo de inclusión
description: Archivo de inclusión
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82255823"
---
## <a name="single-sign-on"></a>Inicio de sesión único

Después de publicar un conjunto de datos DirectQuery de Azure SQL en el servicio, puede habilitar el inicio de sesión único (SSO) mediante OAuth2 de Azure Active Directory (Azure AD) para los usuarios finales.

Para habilitar el inicio de sesión único, vaya a la configuración del conjunto de datos, abra la pestaña **Orígenes de datos** y active la casilla SSO.

![Configuración del cuadro de diálogo de Azure SQL con DirectQuery](media/direct-query-sso/sso-dialog.png)

Cuando se habilita la opción SSO y los usuarios acceden a informes creados sobre el origen de datos, Power BI envía sus credenciales autenticadas de Azure AD en las consultas a la base de datos o el almacenamiento de datos de Azure SQL. Esta opción permite a Power BI respetar la configuración de seguridad establecida en el nivel de origen de datos.

La opción SSO surte efecto en todos los conjuntos de datos que usan este origen de datos. No afecta el método de autenticación utilizado para los escenarios de importación.

