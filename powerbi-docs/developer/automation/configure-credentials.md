---
title: Configuración de credenciales mediante programación para Power BI
description: Procedimientos para configurar credenciales mediante programación cuando se automatiza Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 02/23/2020
ms.openlocfilehash: 1c8741736f0639cba7f8df3f9891a6fe20397d8e
ms.sourcegitcommit: 87b7cb4a2e626711b98387edaa5ff72dc26262bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79079517"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Configuración de credenciales mediante programación para Power BI

Siga estos pasos para configurar las credenciales mediante programación para Power BI.

## <a name="update-credentials-flow-for-data-sources"></a>Actualización de un flujo de credenciales para orígenes de datos

1. Llame a [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) (Obtener orígenes de datos) para detectar los orígenes de datos del conjunto de datos. En el cuerpo de la respuesta de cada origen de datos están el tipo, los detalles de conexión, la puerta de enlace y el identificador del origen de datos.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Compile la cadena de credenciales de acuerdo con los [Ejemplos de actualización de origen de datos](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) y en función del tipo de credenciales.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Llame a [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Obtener puerta de enlace) para recuperar la clave pública de puerta de enlace.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Cifre las credenciales.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

    Cifre la cadena de credenciales con la clave pública de puerta de enlace del paso 2. Diferentes versiones de puerta de enlace pueden tener distintos tamaños de clave pública. Consulte los ejemplos siguientes en el código del SDK, disponible en el [repositorio de GitHub para PowerBI-CSharp](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Compile los detalles de las credenciales con credenciales cifradas.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    Use la clase AssymetricKeyEncriptor con la clave pública recuperada en el **paso 3**.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. Llame a [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Actualizar origen de datos) para establecer las credenciales.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Configuración de un nuevo origen de datos para una puerta de enlace de datos

1. Instale la [puerta de enlace de datos local](https://powerbi.microsoft.com/gateway/) en el equipo.

2. Llame a [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) (Obtener puertas de enlace) para recuperar el identificador y la clave pública de la puerta de enlace.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Compile los detalles de la credencial de la misma forma que se describe en [Actualización de un flujo de credenciales para orígenes de datos](#update-credentials-flow-for-data-sources), mediante la clave pública de la puerta de enlace recuperada en el **paso 2**.

4. Compile el cuerpo de la solicitud.

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. Llame a la API [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Crear origen de datos).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>Tipos de credenciales

Cuando se llama a [Crear origen de datos](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) o [Actualizar origen de datos](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) en una **puerta de enlace empresarial local** mediante la [API REST de Power BI](https://docs.microsoft.com/rest/api/power-bi/), el valor de credenciales se debe cifrar con la clave pública de la puerta de enlace.

>[!NOTE]
>El SDK de .NET v3 también puede ejecutar los ejemplos del SDK de .NET v2 que se enumeran a continuación.

### <a name="windows-and-basic-credentials"></a>Windows y credenciales básicas

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Credenciales de clave

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**Credenciales de OAuth2**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Credenciales anónimas**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[SDK de .NET v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Solución de problemas

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>No se ha encontrado ninguna puerta de enlace ni identificador de origen de datos al llamar a Get datasources

Este problema significa que el conjunto de datos no está enlazado a una puerta de enlace. Al crear un conjunto de datos, para cada conexión de nube se crea de forma automática un origen de datos sin credenciales en la puerta de enlace en la nube del usuario. Esta puerta de enlace se usa para almacenar las credenciales para las conexiones en la nube.

Después de crear el conjunto de datos, se crea un enlace automático entre el conjunto de datos y una puerta de enlace adecuada, que contiene los orígenes de datos coincidentes para todas las conexiones. Si no hay ninguna puerta de enlace de este tipo o varias puertas de enlace adecuadas, se produce un error en el enlace automático.

Si utiliza un conjunto de datos local, cree los orígenes de datos locales que faltan y enlácelos manualmente a una puerta de enlace mediante [Enlazar a puerta de enlace](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Para detectar las puertas de enlace que se pueden enlazar, use [Detectar puertas de enlace](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).