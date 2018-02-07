---
title: "Модули диспетчера трафика Azure для Node.js"
description: "Справочник по модулям диспетчера трафика Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: cf0834a0eadc67868efb165d60d39c681d4435eb
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="bbb29-103">Модули диспетчера трафика Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="bbb29-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bbb29-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="bbb29-104">Overview</span></span>

<span data-ttu-id="bbb29-105">Диспетчер трафика Microsoft Azure позволяет управлять распределением пользовательского трафика между конечными точками службы в разных центрах обработки данных.</span><span class="sxs-lookup"><span data-stu-id="bbb29-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="bbb29-106">К конечным точкам службы, поддерживаемым диспетчером трафика Azure, относятся виртуальные машины, веб-приложения и облачные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="bbb29-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="bbb29-107">Можно также использовать диспетчер трафика Azure для внешних конечных точек, не относящихся к среде Azure.</span><span class="sxs-lookup"><span data-stu-id="bbb29-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="bbb29-108">См. дополнительные сведения о [диспетчере трафика Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="bbb29-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="bbb29-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bbb29-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bbb29-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bbb29-110">Install the npm module</span></span>

<span data-ttu-id="bbb29-111">Установите модуль npm диспетчера трафика Azure.</span><span class="sxs-lookup"><span data-stu-id="bbb29-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="bbb29-112">Пример</span><span class="sxs-lookup"><span data-stu-id="bbb29-112">Example</span></span>

<span data-ttu-id="bbb29-113">Этот пример перечисляет все диспетчеры трафика для данной группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="bbb29-113">This example lists all Traffic Managers for a given resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="bbb29-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="bbb29-114">Samples</span></span>

<span data-ttu-id="bbb29-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bbb29-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
