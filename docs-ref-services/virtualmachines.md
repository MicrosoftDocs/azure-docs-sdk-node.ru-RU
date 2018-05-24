---
title: Использование модулей виртуальных машин для Node.js в Azure
description: Справочное руководство по модулям виртуальных машин Azure для Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="142d0-103">Модули виртуальных машин Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="142d0-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="142d0-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="142d0-104">Overview</span></span>

<span data-ttu-id="142d0-105">Определите, настройте и разверните новые виртуальные машины Windows и Linux и масштабируемые наборы виртуальных машин из кода с помощью модулей управления Azure для Node.js.</span><span class="sxs-lookup"><span data-stu-id="142d0-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="142d0-106">С помощью этих модулей можно запускать и останавливать существующие виртуальные машины, а также подключать и отключать диски остановленной виртуальной машины в подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="142d0-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="142d0-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="142d0-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="142d0-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="142d0-108">Install the npm module</span></span>

<span data-ttu-id="142d0-109">Установите модуль npm служб вычислений Azure.</span><span class="sxs-lookup"><span data-stu-id="142d0-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="142d0-110">Пример</span><span class="sxs-lookup"><span data-stu-id="142d0-110">Example</span></span>

<span data-ttu-id="142d0-111">Следующий пример показывает, как войти в Azure, создать клиент управления и перечислить все образы виртуальных машин для указанного расположения, издателя, предложения и SKU.</span><span class="sxs-lookup"><span data-stu-id="142d0-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="142d0-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="142d0-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="142d0-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="142d0-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
