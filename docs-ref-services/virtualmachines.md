---
title: Использование модулей виртуальных машин для Node.js в Azure
description: Справочное руководство по модулям виртуальных машин Azure для Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 5ba40cb4c068b1af62aa8c654cbf2c3f66f83ff1
ms.sourcegitcommit: b4cf45cb23da56718b482cf7fc240c592e15206b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="13d28-103">Модули виртуальных машин Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="13d28-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="13d28-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="13d28-104">Overview</span></span>

<span data-ttu-id="13d28-105">Определите, настройте и разверните новые виртуальные машины Windows и Linux и масштабируемые наборы виртуальных машин из кода с помощью модулей управления Azure для Node.js.</span><span class="sxs-lookup"><span data-stu-id="13d28-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="13d28-106">С помощью этих модулей можно запускать и останавливать существующие виртуальные машины, а также подключать и отключать диски остановленной виртуальной машины в подписке Azure.</span><span class="sxs-lookup"><span data-stu-id="13d28-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="13d28-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="13d28-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="13d28-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="13d28-108">Install the npm module</span></span>

<span data-ttu-id="13d28-109">Установите модуль npm служб вычислений Azure.</span><span class="sxs-lookup"><span data-stu-id="13d28-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="13d28-110">Пример</span><span class="sxs-lookup"><span data-stu-id="13d28-110">Example</span></span>

<span data-ttu-id="13d28-111">Следующий пример показывает, как войти в Azure, создать клиент управления и перечислить все образы виртуальных машин для указанного расположения, издателя, предложения и SKU.</span><span class="sxs-lookup"><span data-stu-id="13d28-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

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

## <a name="samples"></a><span data-ttu-id="13d28-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="13d28-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="13d28-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="13d28-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
