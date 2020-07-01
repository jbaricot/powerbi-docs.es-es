---
title: Resúmenes de actualización de Power BI
description: Más información sobre el uso de resúmenes de actualización en Power BI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/18/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 7a1fabd1c61219d7f195253a4384accfd2521d24
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85236008"
---
# <a name="refresh-summaries-for-power-bi"></a>Resúmenes de actualización de Power BI

En la página de **resúmenes de actualización** de Power BI, que se encuentra en el portal de administración de Power BI, se ofrece control e información sobre las programaciones de actualización, las capacidades y las posibles superposiciones de programación de actualización. Puede usar la página de resúmenes de actualización para determinar si debe ajustar las programaciones de actualización, conocer los códigos de error asociados a los problemas de actualización y administrar correctamente la programación de actualización de los datos. 

La página de resúmenes de actualización tiene dos vistas:

* **Historial**: muestra el historial del resumen de actualización de las capacidades Power BI Premium de las que es administrador.

* **Programación**: muestra la vista de programación de la actualización programada, que también puede descubrir problemas con franjas horarias que están saturadas.

También puede exportar información sobre un evento de actualización a un archivo CSV, que puede proporcionar información importante y una visión general de los eventos o errores de actualización que pueden afectar al rendimiento o la finalización de los eventos de actualización programada.

En las siguientes secciones se examina cada una de estas vistas a su vez. 

## <a name="refresh-history"></a>Actualizar historial

Puede seleccionar la vista **Historial** haciendo clic en **Historial** en la página de resúmenes de actualización.

![Vista historial en resúmenes de actualización](media/refresh-summaries/refresh-summaries-01a.jpg)

El historial proporciona una visión general de los resultados de las actualizaciones programadas recientemente en las capacidades en las que tiene privilegios de administrador. Puede ordenar la vista por cualquier columna si hace clic en su encabezado. Puede ordenar la vista por la columna seleccionada en orden ascendente o descendente, o mediante filtros de texto.

![Ordenamiento de la vista Historial](media/refresh-summaries/refresh-summaries-01b.jpg)

En la vista Historial, los datos asociados a una actualización determinada se basan en los 60 registros más recientes para cada actualización programada.

También puede exportar información de cualquier actualización programada a un archivo CSV, que incluye información detallada, como los mensajes de error de cada evento de actualización. La exportación a un archivo CSV permite ordenar el archivo por cualquiera de las columnas, buscar palabras, ordenar por códigos de error o por propietarios, etc. En la imagen siguiente se muestra un ejemplo de archivo .CSV exportado. 

![Exportación de información sobre una actualización](media/refresh-summaries/refresh-summaries-05.jpg)

Con la información del archivo exportado, puede revisar la capacidad, la duración y los mensajes de error registrados para la instancia de actualización. 


## <a name="refresh-schedule"></a>Programación de la actualización

Puede seleccionar la vista **Programación** haciendo clic en **Programación** en resúmenes de actualización. La vista Programación muestra la información de programación de la semana, dividida en franjas horarias de 30 minutos. 

![Vista Programación](media/refresh-summaries/refresh-summaries-02a.jpg)

La vista Programación es muy útil para determinar si los eventos de actualización programados están correctamente espaciados, lo que permite que todas las actualizaciones se completen sin superponerse, o si se han programado eventos de actualización que están tardando demasiado y creando contención de recursos. Si encuentra este tipo de contención de recursos, debe ajustar las programaciones de actualización para evitar conflictos o superposiciones, de modo que las actualizaciones programadas se puedan completar correctamente. 

![Vista Programación](media/refresh-summaries/refresh-summaries-02.jpg)

La columna *Tiempo de actualización reservado (minutos)* es un cálculo del promedio de hasta 60 registros por conjunto de datos asociado. El valor numérico de cada franja horaria de 30 minutos es la suma de los minutos calculados para todas las actualizaciones programadas que se inician en la franja horaria **y** cualquier actualización programada establecida para iniciarse en la franja horaria *anterior*, pero cuya duración media se desborda en la franja horaria seleccionada.

Puede seleccionar una franja horaria y luego seleccionar el botón **Detalles** asociado para ver los eventos de actualización programada que contribuyen al tiempo de actualización que se reserva, sus propietarios y cuánto tiempo tardan en completarse.

Veamos un ejemplo de cómo funciona esto. El siguiente cuadro de diálogo se muestra al seleccionar la franja horaria de las 20:30 horas del domingo y hacer clic en **Detalles**.

![Vista Programación](media/refresh-summaries/refresh-summaries-04.jpg)

Existen tres eventos de actualización programada en esta franja horaria. 

La actualización programada n.º 1 y n.º 3 están programadas para esta franja horaria de las 20:30 horas, lo que se puede determinar examinando el valor de la columna **Franja horaria programada**. Sus duraciones medias son 4:39 y seis segundos (0:06), respectivamente. Todo bien allí.

Sin embargo, la actualización programada n.º 2 está programada para la franja horaria de las 20:00 horas, pero dado que tarda un promedio de más de 48 minutos en completarse (se ve en la columna **Duración promedio**), el evento de actualización se desborda en la siguiente franja horaria de 30 minutos. 

Eso no está bien. En este caso, el administrador debe ponerse en contacto con los propietarios de esa instancia de actualización programada y sugerirles que busquen otra franja horaria para esa actualización programada, o bien volver a programar las demás actualizaciones para que no se superpongan, o buscar alguna otra solución para evitar dicha superposición. 


## <a name="next-steps"></a>Pasos siguientes

- [Actualizar datos en Power BI](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [Puerta de enlace de datos local (modo personal)](service-gateway-onprem.md)  
- [Solución de problemas con la puerta de enlace de datos local](service-gateway-onprem-tshoot.md)  
- [Solución de problemas de Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)