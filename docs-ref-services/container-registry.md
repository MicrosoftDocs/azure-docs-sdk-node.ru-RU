---
title: Модули реестра контейнеров Azure для Node.js
description: Справочник по модулям реестра контейнеров Azure для Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: f24fa268f9c471925a1bdf0cbae8044d97bc7679
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51477928"
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="bb786-103">Модули реестра контейнеров Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="bb786-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="bb786-104">Реестр контейнеров Azure — это управляемая служба реестра Docker, основанная на реестре Docker 2.0 с открытым кодом.</span><span class="sxs-lookup"><span data-stu-id="bb786-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="bb786-105">Создавайте и настраивайте реестры контейнеров Azure, чтобы хранить частные образы контейнеров Docker и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="bb786-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="bb786-106">Используйте реестры контейнеров Azure с имеющимися конвейерами разработки и развертывания контейнеров, изучив сведения, предоставленные сообществом Docker.</span><span class="sxs-lookup"><span data-stu-id="bb786-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="bb786-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bb786-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bb786-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bb786-108">Install the npm module</span></span>

<span data-ttu-id="bb786-109">Установите модуль npm реестра контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="bb786-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="bb786-110">Пример</span><span class="sxs-lookup"><span data-stu-id="bb786-110">Example</span></span>

<span data-ttu-id="bb786-111">Этот пример возвращает список доступных контейнеров.</span><span class="sxs-lookup"><span data-stu-id="bb786-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="bb786-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="bb786-112">Samples</span></span>

<span data-ttu-id="bb786-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bb786-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
