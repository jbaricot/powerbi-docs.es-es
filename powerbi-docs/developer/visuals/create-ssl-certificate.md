---
title: Creación de certificados SSL para objetos visuales de Power BI
description: Obtenga información sobre cómo generar certificados SSL mediante herramientas de objetos visuales de Power BI en Windows, Mac o Linux, o manualmente.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: f6f458d2fe82668074d7cfb046cb5a72afa35c38
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048795"
---
# <a name="create-an-ssl-certificate"></a>Creación de un certificado SSL

En este artículo se describe cómo generar e instalar certificados de Capa de sockets seguros (SSL) para objetos visuales de Power BI.

Para los procedimientos de Windows, macOS X y Linux, debe tener instalado el paquete **pbiviz** de herramientas de objetos visuales de Power BI. Para obtener más información, vea [Configuración del entorno para el desarrollo de un objeto visual de Power BI](./environment-setup.md). 

## <a name="create-a-certificate-on-windows"></a>Creación de un certificado en Windows

Para generar el certificado mediante el cmdlet `New-SelfSignedCertificate` de PowerShell en Windows 8 y versiones posteriores, ejecute el siguiente comando:

```powershell
pbiviz --install-cert
```

En Windows 7, la herramienta `pbiviz` requiere que la utilidad OpenSSL esté disponible desde la línea de comandos. Para instalar OpenSSL, vaya a [OpenSSL](https://www.openssl.org) o [OpenSSL Binaries](https://wiki.openssl.org/index.php/Binaries).

Para obtener más información e instrucciones para instalar un certificado, consulte la sección [Creación e instalación de un certificado](./environment-setup.md#create-and-install-a-certificate).

## <a name="create-a-certificate-on-macos-x"></a>Creación de un certificado en macOS X

La utilidad OpenSSL suele estar disponible en el sistema operativo macOS X.

También puede instalar la utilidad OpenSSL si ejecuta alguno de los siguientes comandos:

- En el administrador de paquetes *Brew* :
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- Mediante *MacPorts* :
  
  ```cmd
  sudo port install openssl
  ```

Después de instalar la utilidad OpenSSL, ejecute el siguiente comando para generar un nuevo certificado:

```cmd
pbiviz --install-cert
```

Para obtener más información e instrucciones, consulte la pestaña de OSX en [Creación e instalación de un certificado](./environment-setup.md#create-and-install-a-certificate).

## <a name="create-a-certificate-on-linux"></a>Creación de un certificado en Linux

Normalmente, la utilidad OpenSSL está disponible en el sistema operativo Linux.

Antes de comenzar, ejecute los siguientes comandos para asegurarse de que `openssl` y `certutil` estén instalados:

```sh
which openssl
which certutil
```

Si no están instalados `openssl` y `certutil`, instale las utilidades `openssl` y `libnss3`.

### <a name="create-the-ssl-configuration-file"></a>Creación del archivo de configuración de SSL

Cree un archivo llamado */tmp/openssl.cnf* que contenga el texto siguiente:

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>Generación de una entidad de certificado raíz

Para generar la entidad de certificado raíz (CA) para firmar los certificados locales, ejecute los siguientes comandos:

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>Generación de un certificado para localhost 

Para generar un certificado para `localhost` mediante entidad de certificado generada y para *OpenSSL.cnf* , ejecute los siguientes comandos:

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>Adición de certificados raíz

Para agregar un certificado raíz a la base de datos del explorador Chrome, ejecute:

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

Para agregar un certificado raíz a la base de datos del explorador Mozilla Firefox, ejecute:

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

Para agregar un certificado raíz para todo el sistema, ejecute:

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>Supresión de certificados raíz

Para quitar un certificado raíz, ejecute:

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>Generación manual de un certificado

También puede generar manualmente un certificado SSL mediante OpenSSL. Puede especificar cualquier herramienta para generar los certificados.

Si la utilidad OpenSSL ya está instalada, genere un nuevo certificado mediante la ejecución de lo siguiente:

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

Normalmente, puede encontrar los certificados de servidor web correspondientes a `PowerBI-visuals-tools` si ejecuta uno de los siguientes comandos:

- Para la instancia global de las herramientas:
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- Para la instancia local de las herramientas:
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>Formato PEM

Si usa el formato de certificados de correo mejorados de privacidad (PEM), guarde el archivo de certificado como *PowerBIVisualTest_public.crt* y guarde la clave privada como *PowerBIVisualTest_public.crt* .

### <a name="pfx-format"></a>Formato PFX

Si usa el formato de certificado de intercambio de información personal (PFX), guarde el archivo de certificado como *PowerBIVisualTest_public.pfx* .

Si el archivo de certificado PFX requiere una frase de contraseña:

1. En el archivo de configuración, especifique:
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. En la sección `server`, especifique la frase de contraseña; para ello, reemplace el marcador de posición \<YOUR PASSPHRASE>:

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>Pasos siguientes
- [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md)
- [Ejemplos de objetos visuales de Power BI](samples.md)
- [Publicación de objetos visuales de Power BI en AppSource](office-store.md)