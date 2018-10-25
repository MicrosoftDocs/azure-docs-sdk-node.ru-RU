---
title: Модули виртуальной сети Azure для Node.js
description: Справочник по модулям виртуальной сети Azure для Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 11341fdff5df3b7521319d841707493db1d07732
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "49670859"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="f99bf-103">Модули виртуальной сети Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="f99bf-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f99bf-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="f99bf-104">Overview</span></span>

<span data-ttu-id="f99bf-105">Служба виртуальной сети Azure позволяет безопасно подключать ресурсы Azure между собой с помощью виртуальных сетей.</span><span class="sxs-lookup"><span data-stu-id="f99bf-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="f99bf-106">Виртуальная сеть — это представление вашей собственной сети в облаке.</span><span class="sxs-lookup"><span data-stu-id="f99bf-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="f99bf-107">Это логическая изоляция облака Azure, выделенного для вашей подписки.</span><span class="sxs-lookup"><span data-stu-id="f99bf-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="f99bf-108">Виртуальные сети можно также подключать к локальной сети.</span><span class="sxs-lookup"><span data-stu-id="f99bf-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="f99bf-109">Дополнительные сведения о [виртуальной сети Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="f99bf-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="f99bf-110">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="f99bf-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f99bf-111">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="f99bf-111">Install the npm module</span></span>

<span data-ttu-id="f99bf-112">Установите модуль npm виртуальной сети Azure</span><span class="sxs-lookup"><span data-stu-id="f99bf-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="f99bf-113">Пример</span><span class="sxs-lookup"><span data-stu-id="f99bf-113">Example</span></span>

<span data-ttu-id="f99bf-114">Этот пример извлекает и печатает список виртуальных сетей.</span><span class="sxs-lookup"><span data-stu-id="f99bf-114">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="f99bf-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="f99bf-115">Samples</span></span>

<span data-ttu-id="f99bf-116">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="f99bf-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
