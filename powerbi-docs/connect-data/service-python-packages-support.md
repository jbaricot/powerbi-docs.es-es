---
title: Conozca qué paquetes de Python se admiten
description: Paquetes de Python compatibles e incompatibles con Power BI
author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/26/2020
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: b1dc77d2ebf0803430ceeace7e14bfa62a6d2a60
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785242"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>Creación de objetos visuales mediante paquetes de Python en el servicio Power BI
Puede usar el eficaz [lenguaje de programación Python](https://www.python.org/) para crear objetos visuales en el servicio Power BI. En el servicio Power BI se admiten muchos paquetes de Python y con el tiempo se van admitiendo más.

En las secciones siguientes se proporciona una tabla con los paquetes de Python que se admiten en Power BI, ordenados alfabéticamente. 

## <a name="request-support-for-a-new-python-package"></a>Solicitar compatibilidad para nuevos paquetes de Python
Los paquetes de Python admitidos para el **servicio Power BI** se encuentran en la siguiente sección, titulada **Paquetes admitidos**. Si quiere solicitar soporte técnico de un paquete de Python que no se encuentra en esa lista, envíe su solicitud a [Power BI Ideas](https://ideas.powerbi.com).

## <a name="requirements-and-limitations-of-python-packages"></a>Requisitos y limitaciones de los paquetes de Python
Hay una serie de requisitos y limitaciones para los paquetes de Python:

* Tiempo de ejecución actual de Python: Python 3.7.7.
* El servicio Power BI, en su mayor parte, es compatible con los paquetes de Python con licencias de software gratuitas y de código abierto como GPL-2, GPL-3, MIT+, etc.
* El servicio Power BI admite paquetes publicados en PyPI. El servicio no es compatible con paquetes de Python personalizados o privados. Animamos a los usuarios a que pongan sus paquetes privados a disposición de PyPI antes de solicitar que el paquete esté disponible en el servicio Power BI.
* Para los objetos visuales de Python en **Power BI Desktop**, puede instalar cualquier paquete, incluidos los paquetes de Python personalizados.
* Por motivos de privacidad y seguridad, no se admiten los paquetes de Python que proporcionan consultas cliente-servidor mediante la World Wide Web en el servicio. Las redes están bloqueadas para estos intentos.
* El proceso de aprobación para incluir un nuevo paquete de Python tiene un árbol de dependencias. No se admiten algunas dependencias que deben estar instaladas en el servicio.

## <a name="python-packages-that-are-supported-in-power-bi"></a>Paquetes de Python compatibles con Power BI
En la siguiente tabla se muestran los paquetes **compatibles** con el servicio Power BI.


|        Paquete        |   Versión   |                                   Vínculo                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|Pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|s  eaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>Pasos siguientes
Para más información sobre Python en Power BI, eche un vistazo a los siguientes artículos:

* [Creación de objetos visuales de Power BI con Python](desktop-python-visuals.md)
* [Ejecución de scripts de Python en Power BI Desktop](desktop-python-scripts.md)
* [Uso de Python en el Editor de consultas](desktop-python-in-query-editor.md)
