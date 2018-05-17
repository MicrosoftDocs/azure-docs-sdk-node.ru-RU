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
# <a name="azure-modules-for-nodejs"></a>Модули Azure для Node.js

Управляйте ресурсами Azure и подключайтесь к службам из приложений Node.js с помощью модулей Azure для Node.js. Код доступен в виде [модулей npm](node-sdk-azure-install.md) для использования в проектах. 

## <a name="manage-azure-resources"></a>Управление ресурсами Azure

Используйте модули управления, чтобы создавать ресурсы и выполнять запросы к ним из приложений, а также создавать собственные средства автоматизации Azure. 

Например, для создания виртуальной машины Linux, использующей существующий сетевой интерфейс, напишите следующий код:

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

Полный список модулей см. в [инструкциях по установке](node-sdk-azure-install.md). Инструкции по настройке аутентификации, выполнению примера кода, а также созданию и обновлению ресурсов в подписке Azure см. в [статье по началу работы](node-sdk-azure-get-started.md). 

## <a name="connect-to-azure-services"></a>Подключение к службам Azure

Модули Azure можно использовать не только для создания ресурсов и управления ими в Azure, но и для подключения и использования облачных служб в приложениях. Например, для обновления табличной базы данных SQL или обновления файлов в службе хранилища Azure. Выберите пакет, который нужен для работы определенной службы, в [полном списке](node-sdk-azure-install.md) и ознакомьтесь с руководствами и примерами кода, которые помогут вам использовать модули в приложениях, в [центре разработчиков Node.js](https://azure.microsoft.com/develop/nodejs/).

Например, чтобы вывести содержимое каждого большого двоичного объекта в контейнере хранилища Azure, используйте следующий код:

```javascript
var azure = require('azure-storage');
var blobService = azure.createBlobService(storageConnectionString);
blobService.listBlobsSegmented('testcontainer', null, function(error, result, response) {
   if (err) return console.log(err);
   console.log(result);
});
```

## <a name="sample-code-and-reference"></a>Примеры кода и справочные материалы

В примерах кода ниже представлены общие задачи, выполняемые с помощью модулей управления Azure. Это готовый код, который вы можете использовать в своих приложениях.

- [Виртуальные машины](node-samples-services-compute.md)
- [Веб-приложения](node-samples-services-web-and-mobile.md)
- [База данных SQL](node-samples-services-database.md)
   
[Справочник](https://docs.microsoft.com/javascript/api) по всем модулям служб и модулям управления. Сведения о новых функциях и критически важных изменениях, а также инструкции по переходу с предыдущих версий см. в [заметках о выпуске](https://github.com/Azure/azure-sdk-for-node/releases).