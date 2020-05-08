---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "61194086"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Uso de la función DAX username() o userprincipalname()
Puede aprovechar las ventajas de las funciones DAX *username()* o *userprincipalname()* dentro del conjunto de datos. Puede usarlas dentro de expresiones en Power BI Desktop. Cuando publique el modelo, se utilizará dentro del servicio Power BI.

En Power BI Desktop, *username()* devolverá un usuario con el formato de *DOMINIO\Usuario* y *userprincipalname()* lo devolverá con el formato de <em>user@contoso.com</em>.

En el servicio Power BI, *username()* y *userprincipalname()* devolverán ambos el nombre principal de usuario (UPN) del usuario. Es similar a una dirección de correo electrónico.

