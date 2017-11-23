---
title: "Модули Azure DevTest Labs для Node.js"
description: "Справочник по модулям Azure DevTest Labs для Node.js"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="fcd19-104">Модули Azure DevTest Labs для Node.js</span><span class="sxs-lookup"><span data-stu-id="fcd19-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fcd19-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="fcd19-105">Overview</span></span>

<span data-ttu-id="fcd19-106">Azure DevTest Labs — это служба, помогающая разработчикам и тест-инженерам быстро создавать среды в Azure при минимальных потерях и контроле издержек.</span><span class="sxs-lookup"><span data-stu-id="fcd19-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="fcd19-107">Для проверки последней версии вашего приложения вы можете быстро развернуть среду Windows и Linux, используя многоразовые шаблоны и артефакты.</span><span class="sxs-lookup"><span data-stu-id="fcd19-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="fcd19-108">Для подготовки сред по запросу интегрируйте с DevTest Labs конвейер развертывания.</span><span class="sxs-lookup"><span data-stu-id="fcd19-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="fcd19-109">Масштабируйте нагрузочное тестирование, подготавливая несколько агентов тестирования, и создавайте подготовленные среды для обучения и демонстраций.</span><span class="sxs-lookup"><span data-stu-id="fcd19-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="fcd19-110">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="fcd19-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fcd19-111">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="fcd19-111">Install the npm module</span></span>

<span data-ttu-id="fcd19-112">Установите модуль npm Azure DevTest Labs.</span><span class="sxs-lookup"><span data-stu-id="fcd19-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="fcd19-113">Пример</span><span class="sxs-lookup"><span data-stu-id="fcd19-113">Example</span></span>

<span data-ttu-id="fcd19-114">Этот пример извлекает и печатает сведения лаборатории.</span><span class="sxs-lookup"><span data-stu-id="fcd19-114">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fcd19-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="fcd19-115">Samples</span></span>

<span data-ttu-id="fcd19-116">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="fcd19-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
