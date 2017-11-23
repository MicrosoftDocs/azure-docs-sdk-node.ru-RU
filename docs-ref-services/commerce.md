---
title: "Модули коммерческих предложений Azure для Node.js"
description: "Справочник по модулям коммерческих предложений Azure для Node.js"
keywords: Azure,SDK,API,Commerce, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="c73f3-104">Модули коммерческих предложений Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="c73f3-104">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c73f3-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c73f3-105">Overview</span></span>

<span data-ttu-id="c73f3-106">Используйте API коммерческих предложений Azure для извлечения данных об использовании и ресурсах в предпочитаемые средства анализа данных.</span><span class="sxs-lookup"><span data-stu-id="c73f3-106">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="c73f3-107">API использования ресурсов и RateCard в Azure позволяют точно прогнозировать расходы и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="c73f3-107">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="c73f3-108">Интерфейсы API реализованы в виде поставщика ресурсов и относятся к семейству API, предоставляемых Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="c73f3-108">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="c73f3-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="c73f3-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c73f3-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="c73f3-110">Install the npm module</span></span>

<span data-ttu-id="c73f3-111">Установите модуль npm коммерческих предложений Azure.</span><span class="sxs-lookup"><span data-stu-id="c73f3-111">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="c73f3-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c73f3-112">Example</span></span>

<span data-ttu-id="c73f3-113">Этот пример извлекает предполагаемое использование данных в Azure за последний месяц.</span><span class="sxs-lookup"><span data-stu-id="c73f3-113">This example retrieves your estimated Azure consumption data for the last month.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="c73f3-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="c73f3-114">Samples</span></span>

<span data-ttu-id="c73f3-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="c73f3-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
