---
title: Compatibilidad de Multi-Geo con Power BI Premium
description: Obtenga información sobre cómo puede implementar contenido en centros de datos de regiones distintas de la región principal del inquilino de Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: b0132996be1ed70f228ce96d413c4925dc1a3e48
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512778"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Configuración de compatibilidad con Multi-Geo en Power BI Premium

Multi-Geo es una característica de Power BI Premium que ayuda a que los clientes multinacionales aborden los requisitos de residencia de datos organizacionales, regionales o específicos del sector. Como cliente de Power BI Premium, puede implementar contenido en centros de datos de regiones distintas de la región principal del inquilino de Power BI. Una geoárea (geografía) puede contener más de una región. Por ejemplo, Estados Unidos es una geoárea y Centro-oeste de EE. UU. y Centro-sur de EE. UU. son regiones de Estados Unidos. Puede elegir implementar contenido en cualquiera de las geoáreas siguientes:

- Estados Unidos
- Canadá
- Reino Unido
- Brasil
- Europa
- Japón
- India
- Asia Pacífico
- Australia
- África

Multi-Geo no está disponible para Power BI Alemania, Power BI China operado por 21Vianet o Power BI para la Administración Pública de Estados Unidos.

Multi-Geo ahora está también disponible en Power BI Embedded. Más información en [Compatibilidad de Multi-Geo con Power BI Embedded](../developer/embedded/embedded-multi-geo.md).

> [!NOTE]
> Power BI Premium publicó recientemente una nueva versión Premium, denominada **Premium Gen2**, que se encuentra actualmente en versión preliminar. Premium Gen2 simplifica la administración de las funcionalidades Premium y reduce la sobrecarga de administración. Para más información, vea [Power BI Premium Generation 2 (versión preliminar)](service-premium-what-is.md#power-bi-premium-generation-2-preview).

## <a name="enable-and-configure"></a>Habilitación y configuración

Para las capacidades nuevas, habilite Multi-Geo al seleccionar una región distinta de la región predeterminada en la lista desplegable.  Cada capacidad muestra la región donde está ubicada actualmente, como **Centro-oeste de EE. UU**.

![Tamaño de capacidad: seleccione una región. Multi-Geo de Power BI](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

Después de crear una capacidad, esta permanece en esa región y todas las áreas de trabajo creadas almacenarán su contenido en esa región. Puede migrar las áreas de trabajo desde una región a otra a través de la lista desplegable en la pantalla de configuración del área de trabajo.

![Edición del área de trabajo: elija una capacidad disponible. Multi-Geo de Power BI](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

Verá este mensaje para confirmar el cambio.

![Confirmación del cambio del área de trabajo asignada](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

En este momento, no es necesario restablecer las credenciales de la puerta de enlace durante una migración.  Una vez que se almacenan en la región de capacidad Premium, deberá restablecerlas después de la migración.

Durante la migración, ciertas operaciones pueden generar errores, como la publicación de conjuntos de datos nuevos o la actualización programada de datos.  

Los elementos siguientes se almacenan en la región Premium cuando Multi-Geo está habilitado:

- Modelos (archivos .ABF) para conjuntos de datos de importación y DirectQuery
- Caché de consultas
- Imágenes de R

Estos elementos permanecen en la región principal del inquilino:

- Conjuntos de datos de inserción
- Libros de Excel
- Metadatos de informes/paneles: por ejemplo, nombres de icono, consultas de icono
- Buses de servicio para consultas de puerta de enlace o trabajos de actualización programada
- Permisos
- Credenciales de conjuntos de datos



## <a name="view-capacity-regions"></a>Vista de regiones de capacidad

En el Portal de administración, puede ver todas las capacidades del inquilino de Power BI y las regiones donde se ubican actualmente.

![Vista de capacidades Premium](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Cambio de la región de contenido existente

Si necesita cambiar la región de contenido existente, tiene dos opciones.

- Crear una segunda capacidad y mover las áreas de trabajo. Los usuarios gratuitos no experimentarán tiempo de inactividad siempre que el inquilino tenga núcleos virtuales libres.
- Si la creación de una segunda capacidad no es opción, puede mover de manera temporal el contenido de vuelta a la capacidad compartida desde Premium. No necesita núcleos virtuales adicionales, pero los usuarios gratuitos experimentarán cierto tiempo de inactividad.

## <a name="move-content-out-of-multi-geo"></a>Movimiento de contenido fuera de Multi-Geo  

Puede quitar áreas de trabajo de la capacidad Multi-Geo de una de estas dos maneras:

- Elimine la capacidad actual donde se ubica el área de trabajo.  Esta acción devuelve el área de trabajo a la capacidad compartida en la región principal.
- Migre las áreas de trabajo individuales de vuelta a la capacidad Premium ubicada en el inquilino principal.

Los conjuntos de datos con formato de almacenamiento grande no se deben mover de la región en la que se han creado. Los informes basados en un conjunto de datos de formato grande no podrán cargar el conjunto de datos y devolverán un error *No se puede cargar el modelo*. Vuelva a colocar el conjunto de datos con formato de almacenamiento grande en su región original para que esté disponible de nuevo.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

- Confirme que cualquier movimiento que inició entre regiones cumple con todos los requisitos de cumplimiento corporativos y gubernamentales antes de iniciar la transferencia de datos.
- Una consulta en caché almacenada en una región remota permanece en esa región en reposo. Sin embargo, otros datos en tránsito pueden ir y venir entre distintas geografías.
- Al mover datos de una región a otra en un entorno de Multi-Geo, los datos de origen pueden permanecer en la región desde donde se movieron los datos durante hasta 30 días. Durante ese período, los usuarios finales no tienen acceso a ellos. Se quitan de esta región y se destruyen durante el período de 30 días.
- El tráfico de texto de consulta y de resultado de consulta para los modelos de datos importados no atraviesa la región principal. Los metadatos del informe sí provienen todavía de la región remota y ciertos estados de enrutamiento DNS pueden llevar el tráfico fuera de la región. 
- En la actualidad la característica [flujos de datos](../transform-model/dataflows/dataflows-introduction-self-service.md) no se admite en Multi-GEO.
- Si se mueven conjuntos de valores con formato de almacenamiento grande desde la región en la que se han creado, se producirá un error en los informes al cargar el conjunto de datos. Vuelva a colocar el conjunto de datos de almacenamiento grande en su región original para que esté disponible. 

## <a name="next-steps"></a>Pasos siguientes

- [¿Qué es Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo para capacidades de Power BI Embedded](../developer/embedded/embedded-multi-geo.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

Power BI ha introducido Power BI Premium Gen2 como una oferta en versión preliminar, lo que mejora la experiencia con Power BI Premium mediante mejoras en los siguientes aspectos:
* Rendimiento
* Concesión de licencias por usuario
* Mayor escala
* Métricas mejoradas
* Escalado automático
* Menor sobrecarga de administración

Para más información sobre Power BI Premium Gen2, vea [Power BI Premium Generation 2 (versión preliminar)](service-premium-what-is.md#power-bi-premium-generation-2-preview).
