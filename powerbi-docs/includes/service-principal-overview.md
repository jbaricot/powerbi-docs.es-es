---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621602"
---
La entidad de servicio es un método de autenticación que se puede usar para permitir que una aplicación de Azure AD tenga acceso a las API y el contenido del servicio Power BI.

Al crear una aplicación de Azure Active Directory (Azure AD), se crea un [objeto de entidad de servicio](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). El objeto de entidad de servicio, también conocido como *entidad de servicio*, permite que Azure AD autentique su aplicación. Una vez autenticada, la aplicación puede acceder a los recursos del inquilino de Azure AD.

Para realizar la autenticación, la entidad de servicio usa el *identificador de aplicación* de la aplicación de Azure AD y uno de los siguientes:
* Secreto de aplicación
* Certificado