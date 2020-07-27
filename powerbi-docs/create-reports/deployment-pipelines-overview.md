---
title: Introducción a las canalizaciones de implementación
description: Conozca qué son las canalizaciones de implementación en Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: 5522d84cab235270a2eb368be02cfa0fb4e5eaa9
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557150"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Introducción a las canalizaciones de implementación (versión preliminar)

En el mundo actual, una parte fundamental de la toma de decisiones en casi todas las organizaciones es el análisis. El creciente uso de Power BI como herramienta de análisis exige que utilice más datos, tenga una apariencia atractiva y sea fácil de usar. No obstante, por encima de todo, Power BI debe estar siempre disponible y ser confiable. Para cumplir estos requisitos, los creadores de BI deben colaborar de forma eficaz.

Las canalizaciones de implementación son una herramienta eficaz y reutilizable que permite a los creadores de BI de una empresa con capacidad Premium administrar el ciclo de vida del contenido de la organización. Así, pueden desarrollar y probar contenido de Power BI, como informes, paneles y conjuntos de datos antes de que los consuman los usuarios finales.

La herramienta está diseñada como una canalización con tres fases:

* **<a name="development"></a>Desarrollo**
    
    Esta fase se usa para diseñar, compilar y cargar contenido nuevo con los compañeros creadores. Esta es la primera fase de las canalizaciones de implementación.

* **<a name="test"></a>Prueba**

    Una vez cargado el contenido y que se han realizado todos los cambios en la fase de desarrollo, el contenido se puede trasladar a esta fase para llevar a cabo pruebas con él. A continuación, se muestran tres ejemplos de lo que se puede hacer en el entorno de prueba:

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