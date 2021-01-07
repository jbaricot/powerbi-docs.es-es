---
title: Uso de Kerberos para el inicio de sesión único (SSO) en SAP HANA
description: Configuración del servidor de SAP HANA para habilitar el SSO del servicio Power BI
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675129"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Uso de Kerberos para el inicio de sesión único (SSO) en SAP HANA

> [!IMPORTANT]
> Como [SAP ya no admite OpenSSL](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html), Microsoft también ha dejado de ofrecer soporte técnico. Las conexiones existentes seguirán funcionando, pero a partir de febrero de 2021 no se podrán crear conexiones. En el futuro, use CommonCryptoLib en su lugar.

En este artículo se describe cómo configurar el origen de datos SAP HANA para habilitar el SSO del servicio Power BI.

> [!NOTE]
> Antes de intentar actualizar un informe basado en SAP HANA que usa el inicio de sesión único de Kerberos, complete los dos pasos de este artículo y los de [Configuración del inicio de sesión único de Kerberos](service-gateway-sso-kerberos.md).

## <a name="enable-sso-for-sap-hana"></a>Habilitación del SSO para SAP HANA

Para habilitar el SSO para SAP HANA, siga estos pasos:

1. Asegúrese de que el servidor de SAP HANA ejecuta la versión mínima requerida, que depende del nivel de plataforma de su servidor de SAP HANA:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. En la máquina de puerta de enlace, instale el controlador ODBC de SAP HANA más reciente. La versión mínima es HANA ODBC versión 2.00.020.00, de agosto de 2017.

3. Asegúrese de que el servidor de SAP HANA se haya configurado para el SSO basado en Kerberos. Para obtener más información sobre cómo configurar SSO para SAP HANA mediante Kerberos, vea [Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) (Inicio de sesión único con Kerberos) en la Guía de seguridad de SAP HANA. Consulte también los vínculos de esa página, en particular SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

También se recomienda seguir estos pasos adicionales, que pueden comportar una pequeña mejora de rendimiento:

1. En el directorio de instalación de la puerta de enlace, busque y abra este archivo de configuración: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Busque la propiedad `FullDomainResolutionEnabled` y cambie su valor a `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

Ahora, [ejecute un informe de Power BI](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la puerta de enlace de datos local y DirectQuery, consulte los recursos siguientes:

* [¿Qué es una puerta de enlace de datos local?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](power-bi-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)
