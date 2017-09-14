---
title: "Модули реестра контейнеров Azure для Node.js"
description: "Справочник по модулям реестра контейнеров Azure для Node.js"
keywords: Azure,SDK,API,Container Registry, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: 6ded68c19971a8fe580f440862d0fe05a1def6a2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="800b6-104">Модули реестра контейнеров Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="800b6-104">Azure Container Registry modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="800b6-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="800b6-105">Overview</span></span>

<span data-ttu-id="800b6-106">Реестр контейнеров Azure — это управляемая служба реестра Docker, основанная на реестре Docker 2.0 с открытым кодом.</span><span class="sxs-lookup"><span data-stu-id="800b6-106">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="800b6-107">Создавайте и настраивайте реестры контейнеров Azure, чтобы хранить частные образы контейнеров Docker и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="800b6-107">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="800b6-108">Используйте реестры контейнеров Azure с имеющимися конвейерами разработки и развертывания контейнеров, изучив сведения, предоставленные сообществом Docker.</span><span class="sxs-lookup"><span data-stu-id="800b6-108">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="800b6-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="800b6-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="800b6-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="800b6-110">Install the npm module</span></span>

<span data-ttu-id="800b6-111">Установите модуль npm реестра контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="800b6-111">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="800b6-112">Пример</span><span class="sxs-lookup"><span data-stu-id="800b6-112">Example</span></span>

<span data-ttu-id="800b6-113">Этот пример возвращает список доступных контейнеров.</span><span class="sxs-lookup"><span data-stu-id="800b6-113">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="800b6-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="800b6-114">Samples</span></span>

<span data-ttu-id="800b6-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="800b6-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
