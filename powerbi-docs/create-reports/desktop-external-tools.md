---
title: Uso de herramientas externas en Power BI (versión preliminar)
description: Amplíe el uso de Power BI Desktop con herramientas externas.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/29/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 69929ff48428ebf73044c296eabc419f8e442b3b
ms.sourcegitcommit: 00c0b24d5e80009d18cec6da4fee8a9611bcba04
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411966"
---
# <a name="using-external-tools-in-power-bi-desktop-preview"></a>Uso de herramientas externas en Power BI Desktop (versión preliminar)

A partir de la versión de julio de 2020 de Power BI Desktop, puede usar herramientas externas para proporcionar funcionalidad y valor adicionales a Power BI Desktop. La compatibilidad con las herramientas externas le permite aprovechar la multitud de herramientas de la comunidad para Analysis Services para los profesionales de BI, como la creación y optimización de expresiones y consultas de DAX y la administración del ciclo de vida de las aplicaciones (ALM).

La cinta de opciones **Herramientas externas** de Power BI Desktop contiene botones para herramientas externas instaladas en el equipo y registradas en Power BI Desktop. Las herramientas externas iniciadas desde Power BI Desktop se conectan automáticamente al motor de Analysis Services que funciona como parte de Power BI Desktop, lo que proporciona una experiencia fluida para los usuarios.

![Cinta de opciones de herramientas externas en Power BI Desktop](media/desktop-external-tools/desktop-external-tools-01.png)

Entre estas herramientas externas destacadas se incluyen las siguientes, con vínculos a su ubicación de instalación. El soporte técnico de cada herramienta externa lo ofrece su creador correspondiente:

* [Tabular Editor](https://tabulareditor.com/)
* [DAX Studio](https://daxstudio.org)
* [Kit de herramientas de ALM](http://alm-toolkit.com)


En las secciones siguientes se describen las operaciones compatibles con las herramientas externas, una lista de las herramientas destacadas incluidas en Power BI Desktop y las instrucciones sobre cómo registrar herramientas adicionales.

## <a name="supported-write-operations"></a>Operaciones de escritura admitidas

Las herramientas externas pueden conectarse al conjunto de datos de Power BI Desktop (modelo de Analysis Services) para editar los objetos siguientes. No se admite la edición de un archivo de plantilla de Power BI Desktop (PBIT).

* [Medidas](https://docs.microsoft.com/analysis-services/tabular-models/measures-ssas-tabular) para los cálculos
* [Grupos de cálculo](https://docs.microsoft.com/analysis-services/tabular-models/calculation-groups) para la reutilización del cálculo en modelos complejos
* [Perspectivas](https://docs.microsoft.com/analysis-services/tabular-models/perspectives-ssas-tabular) para definir vistas específicas del dominio empresarial centradas de los metadatos del conjunto de datos

Es posible la administración de traducciones de metadatos mediante herramientas externas, pero actualmente no se admite en esta versión preliminar. Si la configuración regional del usuario actual es una traducción, la edición de objetos en la lista de campos no funciona correctamente con la versión actual de Power BI Desktop. 

Se puede tener acceso a todos los metadatos del conjunto de datos [Modelo de objetos tabulares](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) para fines de solo lectura, pero la edición de los objetos no incluidos en la lista del artículo [Modelo de objetos tabulares](https://docs.microsoft.com/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo) todavía no se admite en la instancia de Analysis Services de Power BI Desktop.


## <a name="featured-external-tools"></a>Herramientas externas destacadas

Las siguientes herramientas de la comunidad de código abierto funcionan con Power BI Desktop. El soporte técnico de cada una lo ofrece su creador correspondiente. El instalador respectivo de cada herramienta la registra en Power BI Desktop tras la instalación:

* Tabular Editor
* DAX Studio
* ALM Toolkit

Veamos cada una de ellas por separado.

### <a name="tabular-editor"></a>Tabular Editor

Puede instalar [Tabular Editor](https://tabulareditor.com/) desde el siguiente vínculo: [Sitio web de Tabular Editor](https://tabulareditor.com/)

Tabular Editor permite a los profesionales de BI compilar, mantener y administrar fácilmente modelos tabulares mediante un editor intuitivo y ligero. Una vista jerárquica muestra todos los objetos del modelo tabular, organizados por carpetas para mostrar con compatibilidad para la edición de propiedades de selección múltiple y el resaltado de sintaxis de DAX.

![Captura de pantalla de Tabular Editor](media/desktop-external-tools/desktop-external-tools-02.png)

El código fuente de Tabular Editor se puede encontrar en el siguiente repositorio de GitHub: [Tabular Editor en GitHub](https://github.com/otykier/TabularEditor)

El autor de la herramienta principal para Tabular Editor es [Daniel Otykier](https://www.linkedin.com/in/daniel-otykier-2231876).


### <a name="dax-studio"></a>DAX Studio

Puede instalar [DAX Studio](https://daxstudio.org) desde el siguiente vínculo: [Sitio web de DAX Studio](https://daxstudio.org)

DAX Studio es conocido por ser una completa herramienta para la creación, el diagnóstico, el ajuste del rendimiento y el análisis de DAX. Entre sus características se incluyen la exploración de objetos, el seguimiento integrado, los desgloses de la ejecución de consultas con estadísticas detalladas y resaltado y aplicación de formato de sintaxis de DAX. En la siguiente imagen se muestra una pantalla de DAX Studio. 

![Captura de pantalla de DAX Studio](media/desktop-external-tools/desktop-external-tools-03.png)

El código fuente de DAX Studio se puede encontrar en el siguiente repositorio de GitHub: [DAX Studio en GitHub](https://github.com/DaxStudio/DaxStudio)

El autor de la herramienta principal para DAX Studio es [Darren Gosbell](https://www.linkedin.com/in/darrengosbell).

### <a name="alm-toolkit"></a>ALM Toolkit

Puede instalar [ALM Toolkit](http://alm-toolkit.com) desde el siguiente vínculo: [Sitio web de ALM Toolkit](http://alm-toolkit.com)

ALM Toolkit es una herramienta de comparación de esquemas para conjuntos de datos de Power BI, usada para escenarios de administración del ciclo de vida de las aplicaciones (ALM). Con ella, puede realizar una implementación sencilla en todos los entornos y retener los datos históricos de actualización incremental. Con ALM Toolkit, puede comparar y combinar archivos de metadatos, ramas y repositorios. También puede reutilizar definiciones comunes entre conjuntos de datos.

![Captura de pantalla de ALM Toolkit](media/desktop-external-tools/desktop-external-tools-04.png)

El código fuente de ALM Toolkit se puede encontrar en el siguiente repositorio de GitHub: [ALM Toolkit en GitHub](https://github.com/microsoft/analysis-services)

El autor de la herramienta principal para ALM Toolkit es [Christian Wade](https://www.linkedin.com/in/christianwade1).


## <a name="how-to-register-external-tools"></a>Registro de herramientas externas

Para registrar otras herramientas externas con Power BI Desktop, cree un archivo JSON con el siguiente contenido:

```json
{
    "name": "<tool name>",
    "description": "<tool description>",
    "path": "<tool executable path>",
    "arguments": "<optional command line arguments>",
    "iconData": "image/png;base64,<encoded png icon data>"
}
```

La siguiente lista describe la lista de elementos en el archivo JSON:
 
* **name:** proporcione un nombre para la herramienta, que aparecerá como un título de botón en la cinta de opciones Herramientas externas en Power BI Desktop.
* **description:** (opcional) proporcione una descripción que aparecerá como información sobre herramientas en el botón de la cinta de opciones Herramientas externas en Power BI Desktop.
* **path:** proporcione la ruta de acceso completa al archivo ejecutable de la herramienta.
* **arguments:** (opcional) proporcione una cadena de argumentos de la línea de comandos con los que se debe iniciar el archivo ejecutable de la herramienta. Puede usar cualquiera de los siguientes marcadores de posición:
    * **%server%:** se reemplaza por el nombre del servidor y el número de puerto de la instancia local del modelo tabular de Analysis Services para los modelos de datos importados/DirectQuery.
    * **%database%:** se reemplaza por el nombre de base de datos del modelo hospedado en la instancia local del modelo tabular de Analysis Services para los modelos de datos importados/DirectQuery.
* **iconData:** proporcione datos de imagen, que se representarán como un icono de botón en la cinta de Herramientas externas en Power BI Desktop. Se debe dar formato a la cadena según la sintaxis de los URI de datos sin el prefijo "data:".
 
Asigne al archivo el nombre `"<tool name>.pbitool.json"` y colóquelo en la siguiente carpeta:

* `%commonprogramfiles%\Microsoft Shared\Power BI Desktop\External Tools`

En entornos de 64 bits, coloque los archivos en la siguiente carpeta:

* **Archivos de programa (x86)\Common Files\Microsoft Shared\Power BI Desktop\External Tools**

Los archivos de la ubicación especificada con la extensión **.pbitool.json** se cargan en Power BI Desktop cuando se inicia.

## <a name="disabling-external-tools-using-the-registry"></a>Deshabilitación de herramientas externas mediante el Registro

Las herramientas externas se pueden deshabilitar mediante **Directivas de grupo** o si se modifica el Registro, que es similar al proceso para deshabilitar **objetos visuales personalizados**.

    Registry key: *Software\Policies\Microsoft\Power BI Desktop\*

    Registry value: *EnableExternalTools*

Un valor de 1 (decimal) permite el uso de herramientas externas en Power BI, que es el valor predeterminado.

Un valor de 0 (decimal) deshabilita el uso de herramientas externas en Power BI.


## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Uso de la obtención de detalles entre varios informes de Power BI](desktop-cross-report-drill-through.md)
* [Uso de segmentaciones de datos en Power BI Desktop](../visuals/power-bi-visualization-slicers.md)


