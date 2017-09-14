---
title: "Модули помощника по Azure для Node.js"
description: "Справочник по модулям помощника по Azure для Node.js"
keywords: Azure,SDK,API,Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="bc8be-104">Модули помощника по Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="bc8be-104">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bc8be-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="bc8be-105">Overview</span></span>

<span data-ttu-id="bc8be-106">Azure Advisor — это персонализированный облачный консультант, который поможет следовать рекомендациям по оптимизации развернутых служб Azure.</span><span class="sxs-lookup"><span data-stu-id="bc8be-106">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="bc8be-107">Помощник по Azure анализирует конфигурацию ресурсов и данные телеметрии их использования и рекомендует решения, которые помогут повысить эффективность затрат, производительность, уровень доступности и безопасности ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="bc8be-107">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="bc8be-108">С помощью Помощника можно:</span><span class="sxs-lookup"><span data-stu-id="bc8be-108">With Advisor, you can:</span></span>
- <span data-ttu-id="bc8be-109">получить упреждающие, действенные и персонализированные практические рекомендации;</span><span class="sxs-lookup"><span data-stu-id="bc8be-109">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="bc8be-110">повысить производительность, безопасность и уровень доступности ресурсов, выявляя при этом любые возможности сократить общие затраты на Azure;</span><span class="sxs-lookup"><span data-stu-id="bc8be-110">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="bc8be-111">получить рекомендации о доступных встроенных действиях.</span><span class="sxs-lookup"><span data-stu-id="bc8be-111">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="bc8be-112">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bc8be-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bc8be-113">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bc8be-113">Install the npm module</span></span>

<span data-ttu-id="bc8be-114">Установите модуль npm помощника по Azure.</span><span class="sxs-lookup"><span data-stu-id="bc8be-114">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="bc8be-115">Пример</span><span class="sxs-lookup"><span data-stu-id="bc8be-115">Example</span></span>

<span data-ttu-id="bc8be-116">Этот пример отображает список рекомендаций помощника по Azure.</span><span class="sxs-lookup"><span data-stu-id="bc8be-116">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="bc8be-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="bc8be-117">Samples</span></span>

<span data-ttu-id="bc8be-118">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bc8be-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
