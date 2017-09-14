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
# <a name="create-an-azure-service-principal-with-nodejs"></a><span data-ttu-id="a2c46-104">Создание субъекта-службы Azure с помощью Node.js</span><span class="sxs-lookup"><span data-stu-id="a2c46-104">Create an Azure service principal with Node.js</span></span> 

<span data-ttu-id="a2c46-105">Если у вас есть приложение, которому нужно предоставить доступ к ресурсам, вы можете настроить для такого приложения удостоверение и выполнить для него аутентификацию с помощью собственных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="a2c46-105">When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials.</span></span> <span data-ttu-id="a2c46-106">Такое удостоверение называется *субъект-служба*.</span><span class="sxs-lookup"><span data-stu-id="a2c46-106">This identity is known as a *service principal*.</span></span> <span data-ttu-id="a2c46-107">По сути, вы создаете ключи для учетной записи Azure Active Directory, которые затем предоставляете пакету SDK для аутентификации. При этом пользователю не нужно вводить имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="a2c46-107">Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.</span></span>

<span data-ttu-id="a2c46-108">Использование субъекта-службы позволяет выполнять следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="a2c46-108">The service principal approach enables you to:</span></span>
- <span data-ttu-id="a2c46-109">Назначить удостоверению приложения разрешения, которые отличаются от ваших разрешений.</span><span class="sxs-lookup"><span data-stu-id="a2c46-109">Assign permissions to the app identity that are different than your own permissions.</span></span> <span data-ttu-id="a2c46-110">Как правило, приложение получает именно те разрешения, которые требуются для его работы.</span><span class="sxs-lookup"><span data-stu-id="a2c46-110">Typically, these permissions are restricted to exactly what the app needs to do.</span></span>
- <span data-ttu-id="a2c46-111">Использовать сертификат для аутентификации при выполнении автоматического скрипта.</span><span class="sxs-lookup"><span data-stu-id="a2c46-111">Use a certificate for authentication when running an unattended script.</span></span>

<span data-ttu-id="a2c46-112">В этой статье описано три способа создания субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="a2c46-112">This topic shows you three techniques for creating a service principal.</span></span>

- <span data-ttu-id="a2c46-113">Портал Azure</span><span class="sxs-lookup"><span data-stu-id="a2c46-113">Azure portal</span></span>
- <span data-ttu-id="a2c46-114">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="a2c46-114">Azure CLI 2.0</span></span>
- <span data-ttu-id="a2c46-115">Пакет Azure SDK для Node.js</span><span class="sxs-lookup"><span data-stu-id="a2c46-115">Azure SDK for Node.js</span></span>

## <a name="create-a-service-principal-using-the-azure-portal"></a><span data-ttu-id="a2c46-116">Создание субъекта-службы с помощью портала Azure</span><span class="sxs-lookup"><span data-stu-id="a2c46-116">Create a service principal using the Azure portal</span></span>

<span data-ttu-id="a2c46-117">Чтобы создать субъект-службу, выполните инструкции из руководства по [созданию приложения Azure Active Directory и субъекта-службы с доступом к ресурсам с помощью портала](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/).</span><span class="sxs-lookup"><span data-stu-id="a2c46-117">Follow the steps outlined in the topic, [Use portal to create an Azure Active Directory application and service principal that can access resources](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/), to generate the service principal.</span></span>

## <a name="create-a-service-principal-using-the-azure-cli-20"></a><span data-ttu-id="a2c46-118">Создание субъекта-службы с помощью Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="a2c46-118">Create a service principal using the Azure CLI 2.0</span></span>

<span data-ttu-id="a2c46-119">Чтобы создать субъект-службу с помощью [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2), сделайте следующее:</span><span class="sxs-lookup"><span data-stu-id="a2c46-119">Creating a service principal using the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2) can be accomplished with the following steps:</span></span>

1. <span data-ttu-id="a2c46-120">Загрузите [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="a2c46-120">Download the [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

2. <span data-ttu-id="a2c46-121">Откройте окно терминала.</span><span class="sxs-lookup"><span data-stu-id="a2c46-121">Open a terminal window.</span></span>

3. <span data-ttu-id="a2c46-122">Введите следующую команду, чтобы начать процесс входа:</span><span class="sxs-lookup"><span data-stu-id="a2c46-122">Type the following command to start the login process:</span></span>

    ```shell
    $ az login
    ```

4. <span data-ttu-id="a2c46-123">Вызов команды `az login` возвращает URL-адрес и код.</span><span class="sxs-lookup"><span data-stu-id="a2c46-123">Calling `az login` results in a URL and a code.</span></span> <span data-ttu-id="a2c46-124">Откройте указанный URL-адрес, введите код и войдите с помощью удостоверения Azure (это может произойти автоматически, если вы уже выполняли такой вход).</span><span class="sxs-lookup"><span data-stu-id="a2c46-124">Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in).</span></span> <span data-ttu-id="a2c46-125">У вас появится доступ к учетной записи через интерфейс командной строки.</span><span class="sxs-lookup"><span data-stu-id="a2c46-125">You'll then be able to access your account via the CLI.</span></span>

5. <span data-ttu-id="a2c46-126">Получите идентификатор подписки и клиента:</span><span class="sxs-lookup"><span data-stu-id="a2c46-126">Get your subscription and tenant id:</span></span>

    ```shell
    $ az account list
    ```

    <span data-ttu-id="a2c46-127">Ниже приведен пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="a2c46-127">The following shows an example of the output:</span></span>

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

    <span data-ttu-id="a2c46-128">**Запишите идентификатор подписки, так как он понадобится на шаге 7.**</span><span class="sxs-lookup"><span data-stu-id="a2c46-128">**Note the subscription ID as it will be used in Step 7.**</span></span>

6. <span data-ttu-id="a2c46-129">Создайте субъект-службу, чтобы получить объект JSON, который содержит другие сведения, необходимые для аутентификации в Azure.</span><span class="sxs-lookup"><span data-stu-id="a2c46-129">Create a service principal to get a JSON object containing the other pieces of information you need to authenticate with Azure.</span></span>

    ```shell
    $ az ad sp create-for-rbac
    ```

    <span data-ttu-id="a2c46-130">Ниже приведен пример выходных данных:</span><span class="sxs-lookup"><span data-stu-id="a2c46-130">The following shows an example of the output:</span></span>

    ```shell
    {
    "appId": "<appId>",
    "displayName": "<displayName>",
    "name": "<name>",
    "password": "<password>",
    "tenant": "<tenant>"
    }
    ```

    <span data-ttu-id="a2c46-131">**Запишите значения клиента, имени и пароля, так как они будут использоваться на шаге 7.**</span><span class="sxs-lookup"><span data-stu-id="a2c46-131">**Note the tenant, name, and password values as they'll be used in Step 7.**</span></span>

7. <span data-ttu-id="a2c46-132">Настройте переменные среды. Для этого замените заполнители &lt;subscriptionId>, &lt;tenant>, &lt;name> и &lt;password> значениями, полученными на шагах 4 и 5.</span><span class="sxs-lookup"><span data-stu-id="a2c46-132">Set up the environment variables - replacing the &lt;subscriptionId>, &lt;tenant>, &lt;name>, and &lt;password> placeholders with the values you obtained in steps 4 and 5.</span></span> 

    <span data-ttu-id="a2c46-133">**Использование Bash**</span><span class="sxs-lookup"><span data-stu-id="a2c46-133">**Using bash**</span></span>

    ```shell
    export azureSubId='<subscriptionId>'
    export azureServicePrincipalTenantId='<tenant>'
    export azureServicePrincipalClientId='<name>'
    export azureServicePrincipalPassword='<password>'
    ```

    <span data-ttu-id="a2c46-134">**Использование PowerShell**</span><span class="sxs-lookup"><span data-stu-id="a2c46-134">**Using PowerShell**</span></span>

    ```shell
    $env:azureSubId='<subscriptionId>'
    $env:azureServicePrincipalTenantId='<tenant>'
    $env:azureServicePrincipalClientId='<name>'
    $env:azureServicePrincipalPassword='<password>'
    ```

## <a name="create-a-service-principal-using-the-azure-sdk-for-nodejs"></a><span data-ttu-id="a2c46-135">Создание субъекта-службы с помощью пакета Azure SDK для Node.js</span><span class="sxs-lookup"><span data-stu-id="a2c46-135">Create a service principal using the Azure SDK for Node.js</span></span>

<span data-ttu-id="a2c46-136">Чтобы создать субъект-службу с помощью программных средства JavaScript, используйте [скрипт ServicePrincipal](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span><span class="sxs-lookup"><span data-stu-id="a2c46-136">To programmatically create a service principal using JavaScript, use the [ServicePrincipal script](https://github.com/Azure/azure-sdk-for-node/tree/master/Documentation/ServicePrincipal).</span></span>   

## <a name="using-the-service-principal"></a><span data-ttu-id="a2c46-137">Использование субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="a2c46-137">Using the service principal</span></span>

<span data-ttu-id="a2c46-138">Когда вы создадите субъект-службу, вы сможете использовать ключи субъекта-службы для аутентификации с помощью пакета Azure SDK для Node.js, как показано в следующем фрагменте кода JavaScript.</span><span class="sxs-lookup"><span data-stu-id="a2c46-138">Once you have a service principal, the following JavaScript code snippet illustrates how to use the service principal keys to authenticate with the Azure SDK for Node.js.</span></span> <span data-ttu-id="a2c46-139">Замените следующие заполнители: &lt;clientId or appId>, &lt;secret or password> и &lt;domain or tenant>:</span><span class="sxs-lookup"><span data-stu-id="a2c46-139">Modify the following placeholders: &lt;clientId or appId>, &lt;secret or password>, and &lt;domain or tenant>,</span></span>

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
