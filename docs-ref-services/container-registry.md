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
ms.openlocfilehash: ca83b97e94312498f4f93c587cf0c90485136841
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="8cce3-103">Модули реестра контейнеров Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="8cce3-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="8cce3-104">Реестр контейнеров Azure — это управляемая служба реестра Docker, основанная на реестре Docker 2.0 с открытым кодом.</span><span class="sxs-lookup"><span data-stu-id="8cce3-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="8cce3-105">Создавайте и настраивайте реестры контейнеров Azure, чтобы хранить частные образы контейнеров Docker и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="8cce3-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="8cce3-106">Используйте реестры контейнеров Azure с имеющимися конвейерами разработки и развертывания контейнеров, изучив сведения, предоставленные сообществом Docker.</span><span class="sxs-lookup"><span data-stu-id="8cce3-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="8cce3-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="8cce3-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="8cce3-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="8cce3-108">Install the npm module</span></span>

<span data-ttu-id="8cce3-109">Установите модуль npm реестра контейнеров Azure.</span><span class="sxs-lookup"><span data-stu-id="8cce3-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="8cce3-110">Пример</span><span class="sxs-lookup"><span data-stu-id="8cce3-110">Example</span></span>

<span data-ttu-id="8cce3-111">Этот пример возвращает список доступных контейнеров.</span><span class="sxs-lookup"><span data-stu-id="8cce3-111">This example gets a list of the available containers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="8cce3-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="8cce3-112">Samples</span></span>

<span data-ttu-id="8cce3-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="8cce3-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
