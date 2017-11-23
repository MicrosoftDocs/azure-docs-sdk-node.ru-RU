---
title: "Модули Azure Service Fabric для Node.js"
description: "Справочник по модулям Azure Service Fabric для Node.js"
keywords: Azure,SDK,API,Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="bf3c5-104">Модули Azure Service Fabric для Node.js</span><span class="sxs-lookup"><span data-stu-id="bf3c5-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bf3c5-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="bf3c5-105">Overview</span></span>

<span data-ttu-id="bf3c5-106">Azure Service Fabric — это платформа распределенных систем, которая дает возможность не только легко упаковывать и развертывать масштабируемые надежные микрослужбы и контейнеры, но и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="bf3c5-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="bf3c5-107">Дополнительные сведения об [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="bf3c5-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="bf3c5-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bf3c5-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bf3c5-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bf3c5-109">Install the npm module</span></span>

<span data-ttu-id="bf3c5-110">Установите модуль npm Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="bf3c5-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="bf3c5-111">Пример</span><span class="sxs-lookup"><span data-stu-id="bf3c5-111">Example</span></span>

<span data-ttu-id="bf3c5-112">В этом примере показано, как получить список кластеров для подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="bf3c5-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="bf3c5-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="bf3c5-113">Samples</span></span>

<span data-ttu-id="bf3c5-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bf3c5-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
