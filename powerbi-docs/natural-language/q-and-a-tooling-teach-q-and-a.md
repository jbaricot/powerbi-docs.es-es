---
title: Enseñanza de Preguntas y respuestas para comprender las preguntas y los términos de Preguntas y respuestas de Power BI
description: Cómo usar Preguntas y respuestas de Power BI para explorar los datos
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/21/2020
ms.author: maggies
LocalizationGroup: Ask questions of your datadefintion
ms.openlocfilehash: b2eff10484a7e05a9e51dfc09d44598de034ee88
ms.sourcegitcommit: be424c5b9659c96fc40bfbfbf04332b739063f9c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2020
ms.locfileid: "91635249"
---
# <a name="teach-qa-to-understand-questions-and-terms-in-power-bi-qa"></a>Enseñanza de Preguntas y respuestas para comprender las preguntas y los términos de Preguntas y respuestas de Power BI

En la sección **Enseñanza de Preguntas y respuestas** de la configuración de Preguntas y respuestas, se entrena a Preguntas y respuestas para que comprenda las preguntas y los términos de lenguaje natural que no haya reconocido. Para empezar, envíe una pregunta que contenga una o varias palabras que Preguntas y respuestas no reconozca. Preguntas y respuestas le pide que defina ese término. Escriba un filtro o un nombre de campo que se corresponda con lo que representa la palabra. Preguntas y respuestas vuelve a interpretar la pregunta original. Si está satisfecho con los resultados, puede guardarlos.

> [!NOTE]
> La funcionalidad Enseñanza de Preguntas y respuestas solo admite el modo de importación. Tampoco admite la conexión a un origen de datos local o de Azure Analysis Services. Esta limitación se debe quitar en las versiones posteriores de Power BI.

## <a name="start-to-teach-qa"></a>Empezar a enseñar a Preguntas y respuestas

1. En Power BI Desktop, en la cinta de opciones **Modelado**, seleccione **Configuración de Preguntas y respuestas** > **Enseñanza de Preguntas y respuestas**.

    ![Sinónimo en rojo de Enseñanza de Preguntas y respuestas](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-synonym-red.png)

2. Escriba una frase con un término que Preguntas y respuestas no reconozca y seleccione **Enviar**.

3. Seleccione la palabra subrayada en color rojo. 

    Preguntas y respuestas ofrece sugerencias y le pide que proporcione la definición correcta del término. 
    
3. En **Definición de los términos que Preguntas y respuestas no ha entendido**, proporcione una definición.

    ![Vista previa de sinónimos de Enseñanza de Preguntas y respuestas](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-fixpreview.png)

4. Seleccione **Guardar** para obtener una vista previa actualizada.

5. Escriba la siguiente pregunta o seleccione la **X** para cerrar.

Los consumidores del informe no verán este cambio hasta que vuelva a publicar el informe en el servicio.

## <a name="define-nouns-and-adjectives"></a>Definición de sustantivos y adjetivos

Puede enseñar a Preguntas y respuestas dos tipos de términos:

- Sustantivos
- Adjetivos

### <a name="define-a-noun-synonym"></a>Definición de un sinónimo de sustantivo

Cuando trabaje con datos, tendrá nombres de campos a los que se puede hacer referencia con nombres alternativos. Un ejemplo podría ser "Ventas". Varias palabras o frases pueden hacer referencia a las ventas, como "ingresos". Si una columna se denomina "Ventas" y el tipo de los consumidores del informe es "Ingresos", es posible que Preguntas y respuestas no pueda seleccionar la columna correcta para responder a la pregunta de forma apropiada. En ese caso, puede ser conveniente indicar a Preguntas y respuestas que "Ventas" e "Ingresos" hacen referencia a lo mismo.

Preguntas y respuestas detecta automáticamente cuándo una palabra desconocida es un nombre que usa los conocimientos de Microsoft Office. Si Preguntas y respuestas detecta un nombre, se lo indica de la siguiente manera:

- <your term> **se refiere a** 

Rellene el cuadro con el término a partir de los datos.

![La captura de pantalla muestra parte del cuadro de preguntas y respuestas con la palabra Ingresos y el mensaje Ingresos hace referencia a "junto al cuadro de texto".](media/q-and-a-tooling-teach-q-and-a/qna-tooling-synonym-prompt.png)

Si proporciona un valor que no sea un campo del modelo de datos, puede obtener resultados no deseados.

### <a name="define-an-adjective-filter-condition"></a>Definición de una condición de filtro de adjetivo

En ocasiones, es posible que desee definir términos que actúan como una condición en los datos subyacentes. Un ejemplo podría ser "Publicadores extraordinarios". "Extraordinarios" podría ser una condición que solo seleccione publicadores que hayan publicado un número de productos. Preguntas y respuestas intenta detectar adjetivos y muestra un mensaje diferente:

- <field name> **que tiene**  

Rellene el cuadro con la condición.

![La captura de pantalla muestra parte del cuadro de preguntas y respuestas con las palabras Publicadores increíbles y el mensaje Publicadores que tienen junto a un cuadro de texto y las palabras son increíbles.](media/q-and-a-tooling-teach-q-and-a/qna-tooling-adjectives.png)

Algunas de las condiciones de ejemplo que se pueden definir son:

- País que sea EE. UU.
- País que no sea EE. UU.
- Productos > 100
- Productos mayores que 100
- Productos = 100
- Productos es 100
- Productos < 100
- Productos menores que 100

En estos ejemplos, "Productos" puede ser un nombre de columna o una medida. 

También puede especificar una agregación en la propia expresión de Preguntas y respuestas. Por ejemplo, si "Productos populares" son productos con al menos 100 unidades vendidas, puede definir productos con la "suma de unidades vendidas > 100" como popular.  

:::image type="content" source="media/q-and-a-tooling-teach-q-and-a/power-bi-qna-popular-products.png" alt-text="Definir productos populares":::

Solo se puede definir una condición en las herramientas. Para definir condiciones más complejas, use DAX para crear una columna o medida calculada y, después, use la sección de herramientas para crear una condición única para esa columna o medida.

## <a name="manage-terms"></a>Administrar términos

Una vez que haya especificado las definiciones, puede volver a ver todas las correcciones que ha realizado y editarlas o eliminarlas. 

1. En **Configuración de Preguntas y respuestas**, vaya a la sección **Administrar términos**.

2. Elimine los términos que ya no desee. Actualmente no se pueden editar los términos. Para volver a definir un término, elimínelo y defínalo.

    ![Administrar términos de Preguntas y respuestas](media/q-and-a-tooling-teach-q-and-a/qna-manage-terms.png)

## <a name="next-steps"></a>Pasos siguientes

Hay una serie de procedimientos recomendados para mejorar el motor de lenguaje natural. Para más información, vea [Procedimientos recomendados de Preguntas y respuestas](q-and-a-best-practices.md).
