---
title: Tutorial sobre cómo obtener el secreto del cliente en análisis insertados
description: Tutorial sobre cómo obtener el secreto del cliente en análisis insertados.
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 12/09/2020
ms.custom: include file
ms.openlocfilehash: 875243aa890b80d21a73b20dec291329d256ba21
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494734"
---
Para obtener el secreto de cliente, haga lo siguiente:

1. Inicie sesión en [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Busque **Registros de aplicaciones** y seleccione el vínculo **Registros de aplicaciones**.

3. Seleccione la aplicación de Azure AD que use para insertar el contenido de Power BI.

4. En **Administrar**, seleccione **Certificados y secretos**.

5. En **Secretos de cliente**, seleccione **Nuevo secreto de cliente**.

6. En la ventana emergente **Agregar un secreto de cliente**, escriba una descripción del secreto de la aplicación, seleccione cuándo expira el secreto de la aplicación y seleccione **Agregar**.

7. En la sección **Secretos de cliente**, copie la cadena de la columna **Valor** del secreto de aplicación recién creado. El valor del secreto de cliente es el *identificador de cliente*.