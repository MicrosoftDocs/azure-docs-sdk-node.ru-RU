---
title: "Модули диспетчера трафика Azure для Node.js"
description: "Справочник по модулям диспетчера трафика Azure для Node.js"
keywords: Azure,SDK,API,Traffic Manager, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="5895f-104">Модули диспетчера трафика Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="5895f-104">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5895f-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="5895f-105">Overview</span></span>

<span data-ttu-id="5895f-106">Диспетчер трафика Microsoft Azure позволяет управлять распределением пользовательского трафика между конечными точками службы в разных центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="5895f-106">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="5895f-107">К конечным точкам службы, поддерживаемым диспетчером трафика Azure, относятся виртуальные машины, веб-приложения и облачные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="5895f-107">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="5895f-108">Можно также использовать диспетчер трафика Azure для внешних конечных точек, не относящихся к среде Azure.</span><span class="sxs-lookup"><span data-stu-id="5895f-108">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="5895f-109">См. дополнительные сведения о [диспетчере трафика Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="5895f-109">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="5895f-110">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="5895f-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5895f-111">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="5895f-111">Install the npm module</span></span>

<span data-ttu-id="5895f-112">Установите модуль npm диспетчера трафика Azure.</span><span class="sxs-lookup"><span data-stu-id="5895f-112">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="5895f-113">Пример</span><span class="sxs-lookup"><span data-stu-id="5895f-113">Example</span></span>

<span data-ttu-id="5895f-114">Этот пример перечисляет все диспетчеры трафика для данной группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="5895f-114">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="5895f-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="5895f-115">Samples</span></span>

<span data-ttu-id="5895f-116">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="5895f-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
