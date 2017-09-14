---
title: "Начало работы с модулями Azure для Node.js"
description: "Базовое использование модулей Azure для Node.js с подпиской Azure."
keywords: Azure, Node, SDK, API, get-started, node.js
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: get-started-article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: ec83d58585014cca05885af4de55473637c410e8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="get-started-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="73334-104">Начало работы с модулями Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="73334-104">Get started with the Azure modules for Node.js</span></span>

<span data-ttu-id="73334-105">Это руководство поможет вам установить модули Azure для Node.js, выполнить аутентификацию в Azure с помощью субъекта-службы и запустить пример кода, который создает ресурсы в подписке Azure и подключается к облачным службам Azure.</span><span class="sxs-lookup"><span data-stu-id="73334-105">This guide walks you through installing Azure Node.js modules, authenticating to Azure with a service principal, and running sample code that creates resources in your Azure subscription and connects to Azure cloud services.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73334-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="73334-106">Prerequisites</span></span>

- <span data-ttu-id="73334-107">Учетная запись Azure.</span><span class="sxs-lookup"><span data-stu-id="73334-107">An Azure account.</span></span> <span data-ttu-id="73334-108">Если у вас ее нет, [получите бесплатную пробную версию](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="73334-108">If you don't have one , [get a free trial](https://azure.microsoft.com/free/)</span></span>
- [<span data-ttu-id="73334-109">Node.js</span><span class="sxs-lookup"><span data-stu-id="73334-109">Node.js</span></span>](https://nodejs.org)
- <span data-ttu-id="73334-110">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) или [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span><span class="sxs-lookup"><span data-stu-id="73334-110">[Azure Cloud Shell](https://docs.microsoft.coms/azure/cloud-shell/quickstart) or [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2).</span></span>

[!INCLUDE [azure-cloud-shell](../docs-ref-conceptual/includes/cloud-shell-try-it.md)]

## <a name="prepare-your-environment"></a><span data-ttu-id="73334-111">Подготовка среды</span><span class="sxs-lookup"><span data-stu-id="73334-111">Prepare your environment</span></span>

<span data-ttu-id="73334-112">Создайте проект в пустом каталоге и установите следующие модули npm:</span><span class="sxs-lookup"><span data-stu-id="73334-112">Create a new project in an empty directory and install the following npm modules:</span></span>

```bash
cd azure-node-quickstart
npm init -y
npm install --save azure ms-rest-azure azure-arm-compute azure-arm-network azure-storage azure-arm-storage
```

## <a name="set-up-authentication"></a><span data-ttu-id="73334-113">Настройка проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="73334-113">Set up authentication</span></span>

<span data-ttu-id="73334-114">Чтобы выполнить пример кода из этого руководства, предоставьте приложению Node.js в вашей подписке Azure разрешения на чтение и создание.</span><span class="sxs-lookup"><span data-stu-id="73334-114">Your Node.js applications need read and create permissions in your Azure subscription to run the sample code in this guide.</span></span> <span data-ttu-id="73334-115">Создайте субъект-службу и настройте приложение для выполнения со связанными учетными данными.</span><span class="sxs-lookup"><span data-stu-id="73334-115">Create a service principal and configure your application to run with its credentials.</span></span> <span data-ttu-id="73334-116">Субъект-служба это неинтерактивная учетная запись, связанная с вашим идентификатором. Этой учетной записи предоставляются только те разрешения, которые нужны для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="73334-116">Service principals are a non-interactive account associated with your identity to which you grant only the privileges your app needs to run.</span></span>

<span data-ttu-id="73334-117">[Создайте субъект-службу с помощью Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) и запишите выходные данные.</span><span class="sxs-lookup"><span data-stu-id="73334-117">[Create a service principal using the Azure CLI 2.0](https://docs.microsoft.com/cli/azure/create-an-azure-service-principal-azure-cli) and capture the output.</span></span> <span data-ttu-id="73334-118">Вместо `MY_SECURE_PASSWORD` нужно указать в аргументе пароля [безопасный пароль](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy).</span><span class="sxs-lookup"><span data-stu-id="73334-118">You'll need to provide a [secure password](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-policy) in the password argument instead of `MY_SECURE_PASSWORD`.</span></span>

```azurecli-interactive
az ad sp create-for-rbac --name AzureNodeTest --password MY_SECURE_PASSWORD
```

```json
{
  "appId": "a487e0c1-82af-47d9-9a0b-af184eb87646d",
  "displayName": "AzureNodeTest",
  "name": "http://AzureNodeTest",
  "password": password,
  "tenant": ""
}
```

<span data-ttu-id="73334-119">Экспортируйте значения *appId*, *password* и *tenant* в качестве переменных среды:</span><span class="sxs-lookup"><span data-stu-id="73334-119">Export the values for *appId*, *password* and *tenant* as environment variables:</span></span>

```bash
export AZURE_ID a487e0c1-82af-47d9-9a0b-af184eb87646d
export AZURE_PASS password
export AZURE_TENANT XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

<span data-ttu-id="73334-120">Выберите идентификатор подписки с помощью команды [az account show](https://docs.microsoft.com/cli/azure/account#show):</span><span class="sxs-lookup"><span data-stu-id="73334-120">Get the ID for your subscription with [az account show](https://docs.microsoft.com/cli/azure/account#show)</span></span>

```azurecli-interactive
az account show
```

```json
{
   "environmentName": "AzureCloud",
   "id": "306943934-0323-4ae4d-a42b-f6613d1664ac",
   "isDefault": true
}
```

<span data-ttu-id="73334-121">Экспортируйте идентификатор подписки как переменную среды:</span><span class="sxs-lookup"><span data-stu-id="73334-121">Export the subscription ID as an environment variable</span></span>

```bash
export AZURE_SUB 306943934-0323-4ae4d-a42b-f6613d1664ac
```

## <a name="create-a-linux-virtual-machine"></a><span data-ttu-id="73334-122">Создание виртуальной машины Linux</span><span class="sxs-lookup"><span data-stu-id="73334-122">Create a Linux virtual machine</span></span>

<span data-ttu-id="73334-123">Создайте файл *createVM.js* в текущем каталоге с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="73334-123">Create a new file *createVM.js* in the current directory with the following code.</span></span> <span data-ttu-id="73334-124">Замените значение `adminPass` надежным паролем.</span><span class="sxs-lookup"><span data-stu-id="73334-124">Update the value of `adminPass` with a good password.</span></span>

```javascript
'use strict';

const MsRest = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');
const NetworkManagementClient = require('azure-arm-network');

MsRest.loginWithServicePrincipalSecret(
    process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {

        let adminPass = YOUR_VALUE_HERE;
        const networkClient = new NetworkManagementClient(credentials, process.env.AZURE_SUB);
        const computeClient = new ComputeManagementClient(credentials, process.env.AZURE_SUB);

        let nicParameters = {
            location: "eastus",
            ipConfigurations: [
                {
                    name: "vmnetinterface",
                    privateIPAllocationMethod: 'Dynamic',
                }
            ]
        };

        const vnetParameters = {
            location: "eastus",
            addressSpace: {
                addressPrefixes: ['10.0.0.0/16']
            },
            dhcpOptions: {
                dnsServers: ['10.1.1.1', '10.1.2.4']
            },
            subnets: [{ name: "mynodesubnet", addressPrefix: '10.0.0.0/24' }],
        };

        let vmParameters = {
            location: "eastus",
            osProfile: {
                computerName: "newLinuxVM",
                adminUsername: "testadmin",
                adminPassword: admin_password
            },
            hardwareProfile: {
                vmSize: 'Basic_A1'
            },
            networkProfile: {
                networkInterfaces: [
                    {
                        primary: true
                    }
                ]
            },
            storageProfile: {
                imageReference: {
                    publisher: 'Canonical',
                    offer: 'UbuntuServer',
                    sku: '16.04-LTS',
                    version: 'latest'
                },
            }
        };

        let publicIPParameters = {
            location: "eastus",
            publicIPAllocationMethod: 'Dynamic'
        };

        networkClient.virtualNetworks.createOrUpdate("myResourceGroup", "mynodevnet", vnetParameters)
            .then(function (vnetwork) {
                networkClient.subnets.get("myResourceGroup", "mynodevnet", "mynodesubnet")
                    .then(function (subnetInfo) {
                        nicParameters.ipConfigurations[0].subnet = subnetInfo;
                        networkClient.publicIPAddresses.createOrUpdate("myResourceGroup", "myLinuxPublicIP", publicIPParameters)
                            .then(function (publicIP) {
                                nicParameters.ipConfigurations[0].publicIPAddress = publicIP;
                                networkClient.networkInterfaces.createOrUpdate("myResourceGroup", "vmnetinterface", nicParameters)
                                    .then(function (vmNetworkInterface) {
                                        vmParameters.networkProfile.networkInterfaces[0].id = vmNetworkInterface.id;
                                        computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, (err, data) => {
                                            if (err) return console.log(err);
                                            console.log("Created new Linux VM");
                                        });
                                    });
                            });
                    });
            });
    });
```

<span data-ttu-id="73334-125">Запустите код из командной строки:</span><span class="sxs-lookup"><span data-stu-id="73334-125">Run the code from the command line:</span></span>

```bash
node createVM.js
```

<span data-ttu-id="73334-126">Когда код будет выполнен, получите IP-адрес новой виртуальной машины и выполните вход с использованием SSH и значения `adminPass` из кода.</span><span class="sxs-lookup"><span data-stu-id="73334-126">Once the code completes, get the IP of your new virtual machine and log in with SSH using the value for `adminPass` from your code.</span></span>

```azurecli-interactive
az vm list-ip-addresses --name newLinuxVM
```

```bash
ssh testadmin@*vm_ip_address*
```

## <a name="write-a-blob-to-azure-storage"></a><span data-ttu-id="73334-127">Запись большого двоичного объекта в службу хранилища Azure</span><span class="sxs-lookup"><span data-stu-id="73334-127">Write a blob to Azure Storage</span></span>

<span data-ttu-id="73334-128">Создайте файл *uploadFile.js* в текущем каталоге с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="73334-128">Create a new file *uploadFile.js* in the current directory with the following code.</span></span>

```javascript
'use strict'

const MsRest = require('ms-rest-azure');
const storage = require('azure-storage');
const storageManagementClient = require('azure-arm-storage');

MsRest.loginWithServicePrincipalSecret(process.env.AZURE_ID, process.env.AZURE_PASS, process.env.AZURE_TENANT, (err, credentials) => {
    const client = new storageManagementClient(credentials, process.env.AZURE_SUB);

    const createParameters = {
        location: 'eastus',
        sku: {
            name: 'Standard_LRS'
        },
        kind: 'BlobStorage',
        accessTier: 'Hot'
    };

    const blobAccountName = "nodedemo" + Math.random().toString(10).substr(4, 7);

    client.storageAccounts.create("myResourceGroup", blobAccountName, createParameters, (err, result, httpRequest, response) => {
        if (err) console.log(err);

        // get a connection string for the account
        client.storageAccounts.listKeys("myResourceGroup", blobAccountName, (err, result) => {
            if (err) console.log(err);

            // get a storage key and use it to connect to the azure-storage module
            const blobSvc = storage.createBlobService(blobAccountName, result.keys[0].value);
            blobSvc.createContainerIfNotExists('mycontainer', { publicAccessLevel: 'blob' }, function (error, result, response) {
                if (!error) {
                    blobSvc.createBlockBlobFromText('mycontainer', 'myblob', 'Hello Azure!', function (error, result, response) {
                        if (!error) {
                            console.log("File uploaded to " + "https://" + blobAccountName + ".blob.core.windows.net/mycontainer/myblob");
                        }
                    });
                }
            });

        });
    });
});
```

<span data-ttu-id="73334-129">Выполните команду, затем скопируйте и вставьте URL-адрес из выходных данных в веб-браузер, чтобы отобразить файл в службе хранилища Azure:</span><span class="sxs-lookup"><span data-stu-id="73334-129">Run the command and then copy and paste the URL from the output into your web browser to view the file in Azure Storage:</span></span>

```bash
node uploadFile.js
```

## <a name="clean-up-resources"></a><span data-ttu-id="73334-130">Очистка ресурсов</span><span class="sxs-lookup"><span data-stu-id="73334-130">Clean up resources</span></span>

<span data-ttu-id="73334-131">Удалите группу ресурсов, чтобы удалить ресурсы, созданные во время работы с этим руководством.</span><span class="sxs-lookup"><span data-stu-id="73334-131">Delete the resource group to remove the resources created in this guide.</span></span>

```azurecli-interactive
az group delete --name myResourceGroup
```

## <a name="next-steps"></a><span data-ttu-id="73334-132">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="73334-132">Next steps</span></span>

<span data-ttu-id="73334-133">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="73334-133">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>

## <a name="reference"></a><span data-ttu-id="73334-134">Справочные материалы</span><span class="sxs-lookup"><span data-stu-id="73334-134">Reference</span></span> 

<span data-ttu-id="73334-135">[Справочник](/nodejs/api/overview/azure/?view=azure-node-2.0.0) по всем пакетам.</span><span class="sxs-lookup"><span data-stu-id="73334-135">A [reference](/nodejs/api/overview/azure/?view=azure-node-2.0.0) is available for all packages.</span></span>

## <a name="get-help-and-give-feedback"></a><span data-ttu-id="73334-136">Справка и отзывы</span><span class="sxs-lookup"><span data-stu-id="73334-136">Get help and give feedback</span></span>

<span data-ttu-id="73334-137">Задавайте вопросы сообществу на сайте [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span><span class="sxs-lookup"><span data-stu-id="73334-137">Post questions to the community on [Stack Overflow](https://stackoverflow.com/questions/tagged/azure+node.js).</span></span> <span data-ttu-id="73334-138">Сообщайте об ошибках и нерешенных проблемах с модулями Azure для Node.js на странице [проектов GitHub](https://github.com/Azure/azure-sdk-for-node).</span><span class="sxs-lookup"><span data-stu-id="73334-138">Report bugs and open issues against the Azure modules for Node.js on the [project GitHub](https://github.com/Azure/azure-sdk-for-node).</span></span>

