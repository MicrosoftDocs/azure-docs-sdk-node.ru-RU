---
title: "Создание субъекта-службы Azure с помощью Node.js"
description: "Узнайте, как использовать аутентификацию субъекта-службы с помощью Node.js"
keywords: Azure, Node, SDK, API, authentication, active directory, service principal
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: faa97e7a9ab6a8b6e04eeee590c7b642d26ba620
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="create-an-azure-service-principal-with-nodejs"></a>Создание субъекта-службы Azure с помощью Node.js 

Если у вас есть приложение, которому нужно предоставить доступ к ресурсам, вы можете настроить для такого приложения удостоверение и выполнить для него аутентификацию с помощью собственных учетных данных. Такое удостоверение называется *субъект-служба*. По сути, вы создаете ключи для учетной записи Azure Active Directory, которые затем предоставляете пакету SDK для аутентификации. При этом пользователю не нужно вводить имя пользователя и пароль.

Использование субъекта-службы позволяет выполнять следующие задачи.
- Назначить удостоверению приложения разрешения, которые отличаются от ваших разрешений. Как правило, приложение получает именно те разрешения, которые требуются для его работы.
- Использовать сертификат для аутентификации при выполнении автоматического скрипта.

В этой статье описано три способа создания субъекта-службы.

- Портал Azure
- Azure CLI 2.0
- Пакет Azure SDK для Node.js

## <a name="create-a-service-principal-using-the-azure-portal"></a>Создание субъекта-службы с помощью портала Azure

Чтобы создать субъект-службу, выполните инструкции из руководства по [созданию приложения Azure Active Directory и субъекта-службы с доступом к ресурсам с помощью портала](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/).

## <a name="create-a-service-principal-using-the-azure-cli-20"></a>Создание субъекта-службы с помощью Azure CLI 2.0

Чтобы создать субъект-службу с помощью [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2), сделайте следующее:

1. Загрузите [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).

2. Откройте окно терминала.

3. Введите следующую команду, чтобы начать процесс входа:

    ```shell
    $ az login
    ```

4. Вызов команды `az login` возвращает URL-адрес и код. Откройте указанный URL-адрес, введите код и войдите с помощью удостоверения Azure (это может произойти автоматически, если вы уже выполняли такой вход). У вас появится доступ к учетной записи через интерфейс командной строки.

5. Получите идентификатор подписки и клиента:

    ```shell
    $ az account list
    ```

    Ниже приведен пример выходных данных:

    ```shell
    {
    "cloudName": "AzureCloud",
    "id": "<subscriptionId>",
    "isDefault": true,
    "name": "<subscriptionName>",
    "registeredProviders": [],
    "state": "Enabled",
    "tenantId": "<tenantId>",
        "user": {
            "name": "hello@example.com",
            "type": "user"
        }
    }
    ```

    **Запишите идентификатор подписки, так как он понадобится на шаге 7.**

6. Создайте субъект-службу, чтобы получить объект JSON, который содержит другие сведения, необходимые для аутентификации в Azure.

    ```shell
    $ az ad sp create-for-rbac
    ```

    Ниже приведен пример выходных данных:

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    **Запишите значения клиента, имени и пароля, так как они будут использоваться на шаге 7.**

7. Настройте переменные среды. Для этого замените заполнители &lt;subscriptionId>, &lt;tenant>, &lt;name> и &lt;password> значениями, полученными на шагах 4 и 5. 

    **Использование Bash**

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    **Использование PowerShell**

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a>Создание субъекта-службы с помощью пакета Azure SDK для Node.js

Чтобы создать субъект-службу с помощью программных средства JavaScript, используйте [скрипт ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).   

## <a name="using-the-service-principal"></a>Использование субъекта-службы

Когда вы создадите субъект-службу, вы сможете использовать ключи субъекта-службы для аутентификации с помощью пакета Azure SDK для Node.js, как показано в следующем фрагменте кода JavaScript. Замените следующие заполнители: &lt;clientId or appId>, &lt;secret or password> и &lt;domain or tenant>:

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithServicePrincipalSecret(
  <clientId or appId>,
  <secret or password>,
  <domain or tenant>,
  (err, credentials) => {
    if (err) throw err

    let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

    // ..use the client instance to manage service resources.
  }
);
```
