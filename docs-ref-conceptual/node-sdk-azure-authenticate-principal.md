---
title: Создание субъекта-службы Azure с помощью Node.js
description: Узнайте, как использовать аутентификацию субъекта-службы с помощью Node.js
author: rloutlaw
manager: routlaw
ms.author: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 81958e3d928eb2fe7d391044e3242492e54a1011
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="cf727-103">Создание субъекта-службы Azure с помощью Node.js</span><span class="sxs-lookup"><span data-stu-id="cf727-103">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="cf727-104">Если у вас есть приложение, которому нужно предоставить доступ к ресурсам, вы можете настроить для такого приложения удостоверение и выполнить для него аутентификацию с помощью собственных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="cf727-104">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="cf727-105">Такое удостоверение называется *субъект-служба*.</span><span class="sxs-lookup"><span data-stu-id="cf727-105">This identity is known as a *service principal*.</span></span> <span data-ttu-id="cf727-106">По сути, вы создаете ключи для учетной записи Azure Active Directory, которые затем предоставляете пакету SDK для аутентификации. При этом пользователю не нужно вводить имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="cf727-106">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="cf727-107">Использование субъекта-службы позволяет выполнять следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="cf727-107">The service principal approach enables you to:</span></span>
- <span data-ttu-id="cf727-108">Назначить удостоверению приложения разрешения, которые отличаются от ваших разрешений.</span><span class="sxs-lookup"><span data-stu-id="cf727-108">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="cf727-109">Как правило, приложение получает именно те разрешения, которые требуются для его работы.</span><span class="sxs-lookup"><span data-stu-id="cf727-109">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="cf727-110">Использовать сертификат для аутентификации при выполнении автоматического скрипта.</span><span class="sxs-lookup"><span data-stu-id="cf727-110">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="cf727-111">В этой статье описано три способа создания субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="cf727-111">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="cf727-112">Портал Azure</span><span class="sxs-lookup"><span data-stu-id="cf727-112">Azure portal</span></span>
- <span data-ttu-id="cf727-113">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="cf727-113">Azure CLI 2.0</span></span>
- <span data-ttu-id="cf727-114">Пакет Azure SDK для Node.js</span><span class="sxs-lookup"><span data-stu-id="cf727-114">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="cf727-115">Создание субъекта-службы с помощью портала Azure</span><span class="sxs-lookup"><span data-stu-id="cf727-115">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="cf727-116">Чтобы создать субъект-службу, выполните инструкции из руководства по [созданию приложения Azure Active Directory и субъекта-службы с доступом к ресурсам с помощью портала](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/).</span><span class="sxs-lookup"><span data-stu-id="cf727-116">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="cf727-117">Создание субъекта-службы с помощью Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="cf727-117">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="cf727-118">Чтобы создать субъект-службу с помощью [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2), сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="cf727-118">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="cf727-119">Загрузите [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="cf727-119">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="cf727-120">Откройте окно терминала.</span><span class="sxs-lookup"><span data-stu-id="cf727-120">Open a terminal window.</span></span>

3. <span data-ttu-id="cf727-121">Введите следующую команду, чтобы начать процесс входа:</span><span class="sxs-lookup"><span data-stu-id="cf727-121">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="cf727-122">Вызов команды `az login` возвращает URL-адрес и код.</span><span class="sxs-lookup"><span data-stu-id="cf727-122">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="cf727-123">Откройте указанный URL-адрес, введите код и войдите с помощью удостоверения Azure (это может произойти автоматически, если вы уже выполняли такой вход).</span><span class="sxs-lookup"><span data-stu-id="cf727-123">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="cf727-124">У вас появится доступ к учетной записи через интерфейс командной строки.</span><span class="sxs-lookup"><span data-stu-id="cf727-124">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="cf727-125">Получите идентификатор подписки и клиента:</span><span class="sxs-lookup"><span data-stu-id="cf727-125">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="cf727-126">Ниже приведен пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="cf727-126">The following shows an example of the output:</span></span>

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

    <span data-ttu-id="cf727-127">**Запишите идентификатор подписки, так как он понадобится на шаге 7.**</span><span class="sxs-lookup"><span data-stu-id="cf727-127">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="cf727-128">Создайте субъект-службу, чтобы получить объект JSON, который содержит другие сведения, необходимые для аутентификации в Azure.</span><span class="sxs-lookup"><span data-stu-id="cf727-128">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="cf727-129">Ниже приведен пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="cf727-129">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="cf727-130">**Запишите значения клиента, имени и пароля, так как они будут использоваться на шаге 7.**</span><span class="sxs-lookup"><span data-stu-id="cf727-130">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="cf727-131">Настройте переменные среды. Для этого замените заполнители &lt;subscriptionId>, &lt;tenant>, &lt;name> и &lt;password> значениями, полученными на шагах 4 и 5.</span><span class="sxs-lookup"><span data-stu-id="cf727-131">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="cf727-132">**Использование Bash**</span><span class="sxs-lookup"><span data-stu-id="cf727-132">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="cf727-133">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="cf727-133">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="cf727-134">Создание субъекта-службы с помощью пакета Azure SDK для Node.js</span><span class="sxs-lookup"><span data-stu-id="cf727-134">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="cf727-135">Чтобы создать субъект-службу с помощью программных средства JavaScript, используйте [скрипт ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="cf727-135">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="cf727-136">Использование субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="cf727-136">Using the service principal</span></span>

<span data-ttu-id="cf727-137">Когда вы создадите субъект-службу, вы сможете использовать ключи субъекта-службы для аутентификации с помощью пакета Azure SDK для Node.js, как показано в следующем фрагменте кода JavaScript.</span><span class="sxs-lookup"><span data-stu-id="cf727-137">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="cf727-138">Замените следующие заполнители: &lt;clientId or appId>, &lt;secret or password> и &lt;domain or tenant>:</span><span class="sxs-lookup"><span data-stu-id="cf727-138">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

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
