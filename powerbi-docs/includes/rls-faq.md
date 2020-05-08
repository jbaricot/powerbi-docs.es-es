---
ms.openlocfilehash: cd0696b44e285119193059304c89cfa04c755771
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "71409385"
---
## <a name="faq"></a>Preguntas frecuentes
**Pregunta:** ¿Qué ocurre si tengo roles y reglas creados previamente para un conjunto de datos en el servicio Power BI? ¿Seguirán funcionando si no hago nada?  
**Respuesta:** No, los objetos visuales no se representarán correctamente. Tendrá que volver a crear los roles y las reglas en Power BI Desktop y, después, publicarlos en el servicio Power BI.

**Pregunta:** ¿Puedo crear estos roles para orígenes de datos de Analysis Services?  
**Respuesta:** Puede hacerlo si importa los datos a Power BI Desktop. Si usa una conexión dinámica, no podrá configurar RLS en el servicio Power BI. Esto se define en el modelo local de Analysis Services.

**Pregunta:** ¿Puedo usar RLS para limitar las columnas o medidas accesibles por mis usuarios?  
**Respuesta:** No, si un usuario tiene acceso a una fila de datos determinada, puede ver todas las columnas de datos de esa fila.

**Pregunta:** ¿Permite RLS ocultar datos detallados pero dar acceso a datos resumidos en objetos visuales?  
**Respuesta:** No, aunque proteja las filas de datos individuales, los usuarios siempre pueden ver los detalles o los datos resumidos.

**Pregunta:** El origen de datos ya tiene definidos roles de seguridad (por ejemplo, roles de SQL Server o de SAP BW). ¿Cuál es la relación entre estos y RLS?  
**Respuesta:** La respuesta depende de si se importan datos o se usa DirectQuery. Si se van a importar datos en el conjunto de datos de Power BI, no se usarán los roles de seguridad del origen de datos. En este caso, se debe definir RLS para aplicar las reglas de seguridad para los usuarios que se conectan en Power BI. Si usa DirectQuery, se usan los roles de seguridad en el origen de datos. Cuando un usuario abre un informe, Power BI envía una consulta al origen de datos subyacente, que aplica las reglas de seguridad a los datos basándose en las credenciales del usuario.
