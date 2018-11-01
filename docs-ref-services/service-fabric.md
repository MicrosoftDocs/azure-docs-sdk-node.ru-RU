---
title: Модули Azure Service Fabric для Node.js
description: Справочник по модулям Azure Service Fabric для Node.js
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 3fd2f73bc6fddf01548bbb92cce540775d4c7c76
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50340252"
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="6a5dd-103">Модули Azure Service Fabric для Node.js</span><span class="sxs-lookup"><span data-stu-id="6a5dd-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6a5dd-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="6a5dd-104">Overview</span></span>

<span data-ttu-id="6a5dd-105">Azure Service Fabric — это платформа распределенных систем, которая дает возможность не только легко упаковывать и развертывать масштабируемые надежные микрослужбы и контейнеры, но и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="6a5dd-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="6a5dd-106">Дополнительные сведения об [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="6a5dd-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="6a5dd-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="6a5dd-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6a5dd-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="6a5dd-108">Install the npm module</span></span>

<span data-ttu-id="6a5dd-109">Установите модуль npm Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="6a5dd-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="6a5dd-110">Пример</span><span class="sxs-lookup"><span data-stu-id="6a5dd-110">Example</span></span>

<span data-ttu-id="6a5dd-111">В этом примере показано, как получить список кластеров для подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="6a5dd-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="6a5dd-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="6a5dd-112">Samples</span></span>

<span data-ttu-id="6a5dd-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="6a5dd-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
