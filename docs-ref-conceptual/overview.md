---
title: Модули Azure для Node.js
description: Обзор модулей служб и управления Azure для Node.js
author: rloutlaw
ms.author: routlaw
manager: routlaw
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 165e1580e408b71b6147e51c41e22bc8fe7277a1
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-modules-for-nodejs"></a><span data-ttu-id="df9c3-103">Модули Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="df9c3-103">Azure modules for Node.js</span></span>

<span data-ttu-id="df9c3-104">Управляйте ресурсами Azure и подключайтесь к службам из приложений Node.js с помощью модулей Azure для Node.js.</span><span class="sxs-lookup"><span data-stu-id="df9c3-104">Manage Azure resources and connect to services from your Node.js applications with the Azure modules for Node.js.</span></span> <span data-ttu-id="df9c3-105">Код доступен в виде [модулей npm](node-sdk-azure-install.md) для использования в проектах.</span><span class="sxs-lookup"><span data-stu-id="df9c3-105">The code is available as [npm modules](node-sdk-azure-install.md) for use in your projects.</span></span> 

## <a name="manage-azure-resources"></a><span data-ttu-id="df9c3-106">Управление ресурсами Azure</span><span class="sxs-lookup"><span data-stu-id="df9c3-106">Manage Azure resources</span></span>

<span data-ttu-id="df9c3-107">Используйте модули управления, чтобы создавать ресурсы и выполнять запросы к ним из приложений, а также создавать собственные средства автоматизации Azure.</span><span class="sxs-lookup"><span data-stu-id="df9c3-107">Use management modules to create and query resources from your apps or to build your own Azure automation tools.</span></span> 

<span data-ttu-id="df9c3-108">Например, для создания виртуальной машины Linux, использующей существующий сетевой интерфейс, напишите следующий код:</span><span class="sxs-lookup"><span data-stu-id="df9c3-108">For example, to create a Linux VM using an existing network interface, you would write the following code:</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ComputeManagementClient = require('azure-arm-compute');

// read in service principal values from env variables
const clientId = process.env['CLIENT_ID'];
const domain = process.env['DOMAIN'];
const secret = process.env['APPLICATION_SECRET'];
const subscriptionId = process.env['AZURE_SUBSCRIPTION_ID'];

msRestAzure.loginWithServicePrincipalSecret(clientId, secret, domain, function (err, credentials, subscriptions) {
    if (err) return console.log(err);
    const computeClient = new ComputeManagementClient(credentials, subscriptionId);
    // customize the VM 
    const vmParameters = {
        location: "eastus",
        osProfile: {
            computerName: "newLinuxVM",
            adminUsername: adminUsername,
            adminPassword: adminPassword
        },
        linuxConfiguration: {
            ssh: {
                publicKeys: [mySshKey]
            }
        },
        hardwareProfile: {
            vmSize: 'Basic_A1'
        },
        networkProfile: {
            networkInterfaces: [
                {
                    id: myNetworkInterfaceId,
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
 
    // create the VM
    computeClient.virtualMachines.createOrUpdate("myResourceGroup", "newLinuxVM", vmParameters, function (err, data) {
        if (err) return console.log(err);
    });

});
```

<span data-ttu-id="df9c3-109">Полный список модулей см. в [инструкциях по установке](node-sdk-azure-install.md). Инструкции по настройке аутентификации, выполнению примера кода, а также созданию и обновлению ресурсов в подписке Azure см. в [статье по началу работы](node-sdk-azure-get-started.md).</span><span class="sxs-lookup"><span data-stu-id="df9c3-109">Review the [install instructions](node-sdk-azure-install.md) for a full list of the modules and the [get started article](node-sdk-azure-get-started.md) to set up authentication and run sample code to create and update resources against your own Azure subscription.</span></span> 

## <a name="connect-to-azure-services"></a><span data-ttu-id="df9c3-110">Подключение к службам Azure</span><span class="sxs-lookup"><span data-stu-id="df9c3-110">Connect to Azure services</span></span>

<span data-ttu-id="df9c3-111">Модули Azure можно использовать не только для создания ресурсов и управления ими в Azure, но и для подключения и использования облачных служб в приложениях.</span><span class="sxs-lookup"><span data-stu-id="df9c3-111">In addition to using the Azure modules to create and manage resources within Azure, you can also use packages to connect and use Azure cloud services in your apps.</span></span> <span data-ttu-id="df9c3-112">Например, для обновления табличной базы данных SQL или обновления файлов в службе хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="df9c3-112">For example, you might update a table SQL Database or upload files to Azure Storage.</span></span> <span data-ttu-id="df9c3-113">Выберите пакет, который нужен для работы определенной службы, в [полном списке](node-sdk-azure-install.md) и ознакомьтесь с руководствами и примерами кода, которые помогут вам использовать модули в приложениях, в [центре разработчиков Node.js](https://azure.microsoft.com/develop/nodejs/).</span><span class="sxs-lookup"><span data-stu-id="df9c3-113">Select the package you need for a particular service from the [complete list](node-sdk-azure-install.md) and visit the [Node.js developer center](https://azure.microsoft.com/develop/nodejs/) for tutorials and sample code to learn how to use the modules in your apps.</span></span>

<span data-ttu-id="df9c3-114">Например, чтобы вывести содержимое каждого большого двоичного объекта в контейнере хранилища Azure, используйте следующий код:</span><span class="sxs-lookup"><span data-stu-id="df9c3-114">For example, to print out the contents of every blob in an Azure storage container:</span></span>

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a><span data-ttu-id="df9c3-115">Примеры кода и справочные материалы</span><span class="sxs-lookup"><span data-stu-id="df9c3-115">Sample code and reference</span></span>

<span data-ttu-id="df9c3-116">В примерах кода ниже представлены общие задачи, выполняемые с помощью модулей управления Azure. Это готовый код, который вы можете использовать в своих приложениях.</span><span class="sxs-lookup"><span data-stu-id="df9c3-116">The following samples cover common tasks with the Azure management modules and have code ready to use in your own apps:</span></span>

- [<span data-ttu-id="df9c3-117">Виртуальные машины</span><span class="sxs-lookup"><span data-stu-id="df9c3-117">Virtual machines</span></span>](node-samples-services-compute.md)
- [<span data-ttu-id="df9c3-118">Веб-приложения</span><span class="sxs-lookup"><span data-stu-id="df9c3-118">Web apps</span></span>](node-samples-services-web-and-mobile.md)
- [<span data-ttu-id="df9c3-119">База данных SQL</span><span class="sxs-lookup"><span data-stu-id="df9c3-119">SQL Database</span></span>](node-samples-services-database.md)
   
<span data-ttu-id="df9c3-120">[Справочник](https://docs.microsoft.com/javascript/api) по всем модулям служб и модулям управления.</span><span class="sxs-lookup"><span data-stu-id="df9c3-120">A [reference](https://docs.microsoft.com/javascript/api) is available for all modules in both the service and management modules.</span></span> <span data-ttu-id="df9c3-121">Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу с предыдущих версий см. в [заметках о выпуске](https://github.com/Azure/azure-sdk-for-node/releases).</span><span class="sxs-lookup"><span data-stu-id="df9c3-121">New features, breaking changes, and migration instructions from previous versions are available in the [release notes](https://github.com/Azure/azure-sdk-for-node/releases).</span></span>