---
title: Datos del informe en el Generador de informes de Power BI
description: El primer paso para diseñar un informe en Power BI Report Builder consiste en crear orígenes de datos y conjuntos de datos que representan los datos del informe subyacentes.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 08/04/2020
ms.openlocfilehash: 97b93f23c8070af1b514032cea122b257097d664
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297941"
---
# <a name="report-data-in-power-bi-report-builder"></a>Datos del informe en el Generador de informes de Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Los datos del informe pueden proceder de varios orígenes de datos de la organización. El primer paso para diseñar un informe en el Generador de informes de Power BI consiste en crear los orígenes de datos y los conjuntos de datos que representan los datos del informe subyacente. Cada origen de datos incluye información de conexión de datos. Cada conjunto de datos incluye un comando de consulta que define el conjunto de campos que se utilizan como datos de un origen de datos. Para visualizar los datos de cada conjunto de datos, agregue una región de datos, como una tabla, una matriz, un gráfico o un mapa. Cuando se procesa el informe, las consultas se ejecutan en el origen de datos y cada región de datos se expande según sea necesario para mostrar los resultados de la consulta para el conjunto de datos.  

Obtenga información sobre la [Creación de un origen de datos insertado para informes paginados en el Generador de informes de Power BI](paginated-reports-embedded-data-source.md).


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> Términos  
  
- **Conexión de datos.** También se conoce como un *origen de datos*. Una conexión de datos incluye un nombre de conexión y propiedades que dependen del tipo de conexión. Por diseño, una conexión de datos no incluye las credenciales. Una conexión de datos no especifica qué datos deben recuperarse del origen de datos externo. Para ello, se especifica una consulta cuando se crea un conjunto de datos.  
  
- **Cadena de conexión.** Una cadena de conexión es una versión de cadena de las propiedades de conexión que son necesarias para conectarse a un origen de datos. Las propiedades de conexión varían en función del tipo de conexión de datos. 

    > [!NOTE]
    > Las cadenas de conexión del origen de datos no se pueden basar en expresiones.
  
- **Origen de datos incrustado.** También conocido como *origen de datos específicos del informe*. Es un origen de datos que se define en un informe y se usa solo en ese informe.  
  
- **Credenciales.** Las credenciales son la información de autenticación que se debe proporcionar para poder tener acceso a datos externos.  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> Sugerencias para especificar los datos del informe

 Use la siguiente información para diseñar una estrategia de datos de informe.  
  
- **Filtrar datos** Los datos del informe se pueden filtrar en la consulta o en el informe. Puede usar conjuntos de datos y variables de consulta para crear parámetros en cascada y proporcionar al usuario la posibilidad de reducir las opciones de miles de selecciones a un número más fácil de administrar. Puede filtrar los datos en una tabla o un gráfico basándose en los valores de parámetro u otros valores que especifique.  
  
- **Parámetros** Los comandos de consulta de conjunto datos que incluyen variables de consulta crean automáticamente los parámetros de informe correspondientes. También puede crear los parámetros de forma manual. Al ver un informe, la barra de herramientas de informe muestra los parámetros. Los usuarios pueden seleccionar valores para controlar el aspecto del informe o de los datos del informe. Para personalizar los datos de destinatarios específicos, puede crear conjuntos de parámetros de informe con diferentes valores predeterminados vinculados a la misma definición de informe o usar el campo integrado **UserID** . 
  
- **Datos de grupo y de agregado** Los datos del informe se pueden agrupar y agregar en la consulta o en el informe. Si agrega valores a la consulta, puede continuar combinando valores en el informe dentro de los límites de lo que es significativo.  
  
- **Ordenar datos** Los datos de informe se pueden clasificar en la consulta o en el informe. En las tablas, también puede agregar un botón de ordenación interactivo para permitir al usuario controlar el criterio de ordenación.  
  
- **Datos basados en expresiones** Dado que la mayoría de las propiedades del informe pueden estar basadas en expresiones y las expresiones pueden incluir referencias a campos de conjunto de datos y parámetros de informe, puede escribir expresiones eficaces para controlar los datos y el aspecto del informe. Puede proporcionar a un usuario la capacidad de controlar los datos que visualiza si define parámetros.  
  
- **Mostrar datos de un conjunto de datos** Los datos de un conjunto de datos aparecen normalmente en una o varias regiones de datos, por ejemplo, una tabla y un gráfico.  
  
- **Mostrar datos de varios conjuntos de datos**  Puede escribir expresiones en una región de datos basada en un conjunto de datos que buscan valores o agregados en otros conjuntos de datos. Puede incluir subinformes en una tabla basada en un conjunto de datos para mostrar los datos de un origen de datos.  
  
 Use la lista siguiente como ayuda para definir orígenes de datos para un informe.  
  
- Comprenda la arquitectura de nivel de datos de software de su organización y los problemas potenciales que surgen de los tipos de datos. Conozca cómo las extensiones de datos y de procesamiento de datos pueden afectar a los resultados de la consulta. Los tipos de datos difieren entre el origen de datos, los proveedores de datos y los tipos de datos almacenados en el archivo de definición de informe (.rdl).  
  
- Los orígenes de datos y los conjuntos de datos se crean en un informe y se publican en el servicio Power BI. Una vez que se publican, puede configurar las credenciales directamente en el servicio Power BI o en la puerta de enlace empresarial. 

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué son los informes paginados en Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Guía de recuperación de datos de informes paginados](../guidance/report-paginated-data-retrieval.md)
