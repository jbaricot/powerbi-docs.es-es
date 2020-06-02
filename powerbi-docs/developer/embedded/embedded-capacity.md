---
title: Capacidad y SKU de los análisis incrustados de Power BI
description: Comprenda que son las capacidades y SKU de los análisis incrustados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/17/2020
ms.openlocfilehash: 1e2426b12bf6205e5ed2fc6cfb0540c67740df7d
ms.sourcegitcommit: 2cb249fc855e369eed1518924fbf026d5ee07eb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2020
ms.locfileid: "83813632"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Capacidad y SKU de los análisis incrustados de Power BI

Al pasar a producción, los análisis incrustados de Power BI requieren una capacidad dedicada (SKU *A*, *EM* o *P*) para la publicación de contenido incrustado de Power BI.

Una capacidad es un conjunto dedicado de recursos reservados para uso exclusivo. Le permite publicar paneles, informes y conjuntos de datos para los usuarios sin tener que adquirir licencias por usuario. También ofrece un rendimiento confiable y continuo de su contenido.

>[!NOTE]
>Para la publicación, necesitará una cuenta de Power BI Pro.

## <a name="what-is-embedded-analytics"></a>¿Qué son los análisis incrustados?

Los análisis incrustados de Power BI incluyen dos soluciones:
* *Power BI Embedded*: oferta de Azure
* Incrustación de Power BI como parte de *Power BI Premium*: oferta de Office

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded está pensado para aquellos ISV y desarrolladores que quieran insertar objetos visuales en sus aplicaciones.

Las aplicaciones que usan Power BI Embedded permiten a los usuarios consumir contenido almacenado en la capacidad de Power BI Embedded.

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../../admin/service-premium-what-is.md) está dirigido a empresas que quieran una solución de inteligencia empresarial completa que proporcione una vista única de su organización, asociados, clientes y proveedores.

Power BI Premium es un producto SaaS que permite que los usuarios consuman el contenido a través del portal de Power BI, una aplicación móvil y aplicaciones desarrolladas internamente (servicio Power BI). Esto permite a Power BI Premium proporcionar una solución para aplicaciones internas y externas orientadas a los clientes.

## <a name="capacity-and-skus"></a>Capacidad y SKU

Cada capacidad ofrece una selección de SKU, y cada SKU proporciona diferentes niveles de recursos para la memoria y la capacidad de computación. El tipo de SKU que necesite dependerá del tipo de solución que quiera implementar.

Para saber qué cargas de trabajo se admiten para cada nivel, consulte el artículo [Configuración de cargas de trabajo en una capacidad Premium](../../admin/service-admin-premium-workloads.md).

Para planear y probar su capacidad, use estos vínculos:
* [Planificación de capacidad](embedded-capacity-planning.md)
* [Enfoques de prueba](../../admin/service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>SKU de Power BI Embedded

Power BI Embedded se suministra con una [SKU *a*](../../admin/service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios).

### <a name="power-bi-premium-skus"></a>SKU de Power BI Premium

Power BI Premium ofrece dos SKU: *P* y *EM*.
* [Diferencias entre los SKU *P* y *EM*](../../admin/service-premium-what-is.md#subscriptions-and-licensing)
* [Compra de un SKU Premium](../../admin/service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>¿Qué SKU debo usar?

En la tabla que aparece a continuación se proporciona un resumen de las características, la capacidad requerida y la SKU específica que se necesita para cada una de ellas.

En esta tabla, una aplicación personalizada hace referencia a una aplicación web creada mediante el análisis insertado. Al hacer la inserción en una aplicación web personalizada como desarrollador (mediante los SDK de JavaScript o .NET o las API REST), tiene la capacidad de controlar y personalizar la experiencia de usuario. Esta capacidad no está disponible cuando se usan otras opciones de inserción, como el servicio Power BI y Power BI Mobile.


|         |         |         |
|---------|---------|---------|
|**Escenario**</br><p></p>|**Azure**</br>(SKU A)|**Office**</br>(SKU de P y EM)|
|[Insertar para los clientes](embed-sample-for-customers.md)</br>(datos en posesión de la aplicación)     |✔        |✔        |
|[Insertar para la organización](embed-sample-for-your-organization.md)</br>(datos en posesión del usuario)     |✖        |✔         |
|Aplicaciones de Microsoft 365</br>(antes conocidas como aplicaciones de Office 365)<ul><li>[Insertar en Teams](../../collaborate-share/service-embed-report-microsoft-teams.md)</li><li>[Insertar en SharePoint](../../collaborate-share/service-embed-report-spo.md)</li></ul>     |✖        |✔        |
|[Inserción de dirección URL segura](../../collaborate-share/service-embed-secure.md)</br>(inserción desde el servicio Power BI)     |✖        |✔        |

>[!NOTE]
>* Para publicar contenido en un área de trabajo de aplicación de Power BI, se necesita una [licencia de Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md).
>* Solo la **SKU de P** permite a los usuarios de Power BI gratuitos consumir aplicaciones y contenido compartido de Power BI en el servicio Power BI.

### <a name="capacity-considerations"></a>Consideraciones de capacidad

En la tabla siguiente se enumeran las consideraciones sobre el pago y uso por capacidad.

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>¿Qué es Power BI Embedded de Azure?</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>Oferta</strong></p></td>
<td style="text-align: center"><p>Azure</p></td>
<td style="text-align: center" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center"><p>A</p></td>
<td style="text-align: center"><p>EM</p></td>
<td style="text-align: center"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Facturación</strong></td>
<td style="text-align: center">Cada hora</td>
<td style="text-align: center">Mensual</td>
<td style="text-align: center">Mensual</td>
</tr>
<tr>
<td><p><strong>Asignación</strong></td>
<td style="text-align: center">Ninguno</td>
<td style="text-align: center">Anualmente</td>
<td style="text-align: center">Mensual o anual</td>
</tr>
<tr>
<td valign="top"><p><strong>Uso</strong></td>
<td style="text-align: center">Los recursos de Azure se pueden:<li><a href="azure-pbie-scale-capacity.md">Escalar vertical y horizontalmente</a></li><li><a href="azure-pbie-pause-start.md">Pausar y reanudar</a>
</td></li>
<td style="text-align: center">Incrustar en aplicaciones y en</br> aplicaciones de Microsoft</td>
<td style="text-align: center">Incrustar en aplicaciones, así como en</br> la memoria y capacidad de computación</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>del servicio Power BI

En la tabla siguiente se describen los recursos y los límites de cada SKU.

| Nodos de capacidad | Total de núcleos virtuales | Núcleos virtuales de back-end | RAM (GB) | Núcleos virtuales de front-end | Límites de conexiones dinámicas/DirectQuery (por segundo) | Paralelismo de actualización de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Insertar desde aplicaciones](embed-from-apps.md)