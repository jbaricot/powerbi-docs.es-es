---
title: Solución de problemas de subinformes en informes paginados de Power BI
description: En este artículo, obtendrá información sobre los orígenes de datos admitidos para los informes paginados en el servicio Power BI y cómo conectarse a orígenes de datos de Azure SQL Database.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 6de85f6dda69e902a98d6ee63d1fc4b86fb4180b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615643"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Solución de problemas de subinformes en informes paginados de Power BI

A veces, al usar subinformes en informes paginados, puede que obtenga un resultado inesperado o que la característica no funcione como se esperaba. En este artículo se proporcionan soluciones para problemas comunes al usar subinformes. Un *subinforme* es un elemento de informe que muestra otro informe dentro del cuerpo del informe paginado principal. Vea [Subinformes en informes paginados de Power BI](subreports.md) para saber más.

## <a name="subreport-couldnt-be-found"></a>No se ha encontrado el subinforme

**Descripción:** El subinforme no se representa y se muestra un mensaje de error.

### <a name="message"></a>Mensaje

"No se encontró el subinforme 'Subreport1' en la ubicación especificada 'CustomerDetails'. Compruebe que el subinforme se ha publicado y que el nombre es correcto".

### <a name="possible-reasons"></a>Razones posibles

- No existe ningún subinforme con el nombre especificado en la misma área de trabajo o aplicación que el informe principal.
- El usuario no tiene acceso al subinforme.
- El número de subinformes del informe principal ha alcanzado el límite de subinformes (50 subinformes).

### <a name="troubleshooting-steps"></a>Pasos para solucionar problemas

**En una área de trabajo**

- Compruebe que existe el informe con el nombre que se indica en el mensaje de error. El nombre distingue mayúsculas de minúsculas.

**En una aplicación**

- Compruebe que existe el informe con el nombre que se indica en mensaje de error en la aplicación. Póngase en contacto con el autor de la aplicación para obtener más ayuda.

**Si el informe está compartido**

1. Compruebe que el informe con el nombre que se indica en mensaje de error está compartido.
2. Si el informe existe, compruebe que el nombre del propietario es el mismo para el informe principal y para el subinforme. Después, póngase en contacto con el propietario del informe principal con esa información.

## <a name="subreport-renders-with-unexpected-content"></a>El subinforme se representa con contenido inesperado

### <a name="possible-reason"></a>Posible motivo

Power BI permite a los usuarios tener varios informes con el mismo nombre en la misma área de trabajo

### <a name="troubleshooting-steps-for-report-authors"></a>Pasos para solucionar el problema (para autores de informes)

1. Abra el informe principal en Power BI Report Builder y determine el nombre del subinforme.
2. Busque informes con el mismo nombre en el área de trabajo.
3. Busque el informe esperado y cambie el nombre del resto.

**Para los que no son autores:** Póngase en contacto con el autor.

## <a name="data-retrieval-fails"></a>Errores de recuperación de datos

**Descripción:** Se produce un error en la recuperación de datos al representar el subinforme. El subinforme no se representa y se muestra un mensaje de error.

### <a name="message"></a>Mensaje

"Error de recuperación de datos para el subinforme, 'Subreport1', ubicado en: 'InvoiceDetails'. Compruebe los archivos de registro para obtener más información".

### <a name="troubleshooting-steps"></a>Pasos para solucionar problemas

Los pasos para solucionar este problema son los mismos que para los informes con problemas de acceso a datos.

## <a name="rendering-fails-unspecified-parameters"></a>Error de representación: parámetros no especificados

**Descripción:** La representación de subinformes produce un error debido a parámetros no especificados. El subinforme tiene parámetros obligatorios, pero el informe principal no los establece todos.

### <a name="message"></a>Mensaje 
"No se especificaron uno o más parámetros del subinforme 'Subreport1', ubicado en: 'SubreportAWithDS'".

### <a name="troubleshooting-steps-for-the-report-author"></a>Pasos para solucionar el problema (para el autor de informe)

1. Abra el informe principal en Power BI Report Builder.
2. Abra el subinforme en Power BI Report Builder.
3. Compruebe que el conjunto de parámetros que se pasan dentro del elemento de informe del subinforme en el informe principal coincide con el conjunto de parámetros del subinforme.

**Para los que no son autores:** Póngase en contacto con el autor.

## <a name="rendering-fails-recursion-limit"></a>Error de representación: Límite de recursión

**Descripción:** La representación del subinforme produce un error debido al límite de recursión. Los subinformes no se pueden anidar más de 20 niveles.

### <a name="message"></a>Mensaje

"El informe o subinforme tiene un subinforme recursivo, 'Subreport1', que supera el límite permitido de recursión máxima".

### <a name="troubleshooting-steps-for-report-authors"></a>Pasos para solucionar el problema (para autores de informes)

- Reduzca el anidamiento.
- Rediseñe la estructura del informe.

## <a name="other-errors"></a>Otros errores

**Descripción:** Errores que no se encuentran en ninguna de las categorías anteriores.

### <a name="message"></a>Mensaje

"Error: no se pudo mostrar el subinforme".

### <a name="possible-reasons"></a>Razones posibles

- Varios errores durante la representación de subinformes, por ejemplo, los parámetros no coinciden con los problemas de recuperación de datos.
- Errores inesperados.

### <a name="troubleshooting-steps-for-report-authors"></a>Pasos para solucionar el problema (para autores de informes)

1. Compruebe que el subinforme se puede representar directamente.
2. Si el subinforme se puede representar, compruebe los parámetros en el subinforme y en el informe principal.
3. Asegúrese de que el informe principal no tenga más de 50 subinformes únicos y de que el subinforme no esté anidado en más de 20 niveles.
4. Si no puede resolver el problema, póngase en contacto con el soporte técnico de Power BI.

**Para los que no son autores:** Póngase en contacto con el autor.

## <a name="next-steps"></a>Pasos siguientes

[Subinformes en informes paginados de Power BI](subreports.md)

[Visualización de un informe paginado en el servicio Power BI](../consumer/paginated-reports-view-power-bi-service.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
