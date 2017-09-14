---
title: "Модули виртуальных машин Azure для Node.js"
description: "Справочник по модулям виртуальных машин Azure для Node.js"
keywords: Azure, Node, SDK, API, virtual machine, vm, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="c48cb-104">Модули виртуальных машин Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="c48cb-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c48cb-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c48cb-105">Overview</span></span>

<span data-ttu-id="c48cb-106">Определите, настройте и разверните новые виртуальные машины Windows и Linux и масштабируемые наборы виртуальных машин из кода с помощью модулей управления Azure для Node.js.</span><span class="sxs-lookup"><span data-stu-id="c48cb-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="c48cb-107">С помощью этих модулей можно запускать и останавливать существующие виртуальные машины, а также подключать и отключать диски остановленной виртуальной машины в подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="c48cb-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="c48cb-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="c48cb-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c48cb-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="c48cb-109">Install the npm module</span></span>

<span data-ttu-id="c48cb-110">Установите модуль npm служб вычислений Azure.</span><span class="sxs-lookup"><span data-stu-id="c48cb-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="c48cb-111">Пример</span><span class="sxs-lookup"><span data-stu-id="c48cb-111">Example</span></span>

<span data-ttu-id="c48cb-112">Следующий пример показывает, как войти в Azure, создать клиент управления и перечислить все образы виртуальных машин для указанного расположения, издателя, предложения и SKU.</span><span class="sxs-lookup"><span data-stu-id="c48cb-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="c48cb-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="c48cb-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="c48cb-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="c48cb-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
