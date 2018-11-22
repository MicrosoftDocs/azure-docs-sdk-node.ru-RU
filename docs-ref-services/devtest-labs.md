---
title: Модули Azure DevTest Labs для Node.js
description: Справочник по модулям Azure DevTest Labs для Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 4528bf6a09bc86d23bfec982988added1aa3e257
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52133758"
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="2b79a-103">Модули Azure DevTest Labs для Node.js</span><span class="sxs-lookup"><span data-stu-id="2b79a-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="2b79a-104">Azure DevTest Labs — это служба, помогающая разработчикам и тест-инженерам быстро создавать среды в Azure при минимальных потерях и контроле издержек.</span><span class="sxs-lookup"><span data-stu-id="2b79a-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="2b79a-105">Для проверки последней версии вашего приложения вы можете быстро развернуть среду Windows и Linux, используя многоразовые шаблоны и артефакты.</span><span class="sxs-lookup"><span data-stu-id="2b79a-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="2b79a-106">Для подготовки сред по запросу интегрируйте с DevTest Labs конвейер развертывания.</span><span class="sxs-lookup"><span data-stu-id="2b79a-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="2b79a-107">Масштабируйте нагрузочное тестирование, подготавливая несколько агентов тестирования, и создавайте подготовленные среды для обучения и демонстраций.</span><span class="sxs-lookup"><span data-stu-id="2b79a-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="2b79a-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="2b79a-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2b79a-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="2b79a-109">Install the npm module</span></span>

<span data-ttu-id="2b79a-110">Установите модуль npm Azure DevTest Labs.</span><span class="sxs-lookup"><span data-stu-id="2b79a-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="2b79a-111">Пример</span><span class="sxs-lookup"><span data-stu-id="2b79a-111">Example</span></span>

<span data-ttu-id="2b79a-112">Этот пример извлекает и печатает сведения лаборатории.</span><span class="sxs-lookup"><span data-stu-id="2b79a-112">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="2b79a-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="2b79a-113">Samples</span></span>

<span data-ttu-id="2b79a-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="2b79a-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
