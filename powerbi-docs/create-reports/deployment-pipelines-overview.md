---
title: Introducción a las canalizaciones de implementación
description: Conozca qué son las canalizaciones de implementación en Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 09/09/2020
ms.openlocfilehash: 3994a5cdad4d80c87d4153ffe57af685d7a21d36
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "90008592"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Introducción a las canalizaciones de implementación (versión preliminar)

En el mundo actual, una parte fundamental de la toma de decisiones en casi todas las organizaciones es el análisis. El creciente uso de Power BI como herramienta de análisis exige que utilice más datos, tenga una apariencia atractiva y sea fácil de usar. No obstante, por encima de todo, Power BI debe estar siempre disponible y ser confiable. Para cumplir estos requisitos, los creadores de BI deben colaborar de forma eficaz.

La herramienta de canalizaciones de implementación permite a los creadores de BI administrar el ciclo de vida del contenido de la organización. Se trata de una herramienta eficaz y que pueden reutilizar los creadores de una empresa con capacidad Premium. Esta herramienta permite a los creadores desarrollar y probar contenidos en Power BI antes de que los usuarios los consuman. Los tipos de contenido incluyen informes, paneles y conjuntos de datos.

La herramienta está diseñada como una canalización con tres fases:

* **<a name="development"></a>Desarrollo**
    
    Esta fase se usa para diseñar, compilar y cargar contenido nuevo con los compañeros creadores. Esta es la primera fase de las canalizaciones de implementación.

* **<a name="test"></a>Prueba**

    Después de realizar todos los cambios en el contenido, ya puede entrar en la fase de prueba. Cargue el contenido modificado para que se pueda trasladar a esta fase de prueba. A continuación, se muestran tres ejemplos de lo que se puede hacer en el entorno de prueba:

    * Compartir contenido con evaluadores y revisores

    * Cargar y ejecutar pruebas con grandes volúmenes de datos

    * Probar la aplicación para ver cómo se buscarán los usuarios finales

* **<a name="production"></a>Producción**

    Después de probar el contenido, use la fase de producción para compartir la versión final del contenido con los usuarios empresariales de la organización.

![Captura de pantalla de una canalización de implementación funcional con las tres fases (desarrollo, prueba y producción) rellenadas.](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Pasos siguientes

>[!div class="nextstepaction"]
>[Introducción a las canalizaciones de implementación](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Descripción del proceso de las canalizaciones de implementación](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Solución de problemas de las canalizaciones de implementación](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Procedimientos recomendados de las canalizaciones de implementación](deployment-pipelines-best-practices.md)
