---
title: Модули коммерческих предложений Azure для Node.js
description: Справочник по модулям коммерческих предложений Azure для Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51459408"
---
# <a name="azure-commerce-modules-for-nodejs"></a><span data-ttu-id="4e93e-103">Модули коммерческих предложений Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="4e93e-103">Azure Commerce modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4e93e-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="4e93e-104">Overview</span></span>

<span data-ttu-id="4e93e-105">Используйте API коммерческих предложений Azure для извлечения данных об использовании и ресурсах в предпочитаемые средства анализа данных.</span><span class="sxs-lookup"><span data-stu-id="4e93e-105">Use Azure Commerce APIs to pull usage and resource data into your preferred data analysis tools.</span></span> <span data-ttu-id="4e93e-106">API использования ресурсов и RateCard в Azure позволяют точно прогнозировать расходы и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="4e93e-106">The Azure Resource Usage and RateCard APIs can help you accurately predict and manage your costs.</span></span> <span data-ttu-id="4e93e-107">Интерфейсы API реализованы в виде поставщика ресурсов и относятся к семейству API, предоставляемых Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="4e93e-107">The APIs are implemented as a Resource Provider and part of the family of APIs exposed by the Azure Resource Manager.</span></span>

## <a name="management-package"></a><span data-ttu-id="4e93e-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="4e93e-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4e93e-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="4e93e-109">Install the npm module</span></span>

<span data-ttu-id="4e93e-110">Установите модуль npm коммерческих предложений Azure.</span><span class="sxs-lookup"><span data-stu-id="4e93e-110">Install the Azure Commerce npm module</span></span>

```bash
npm install azure-arm-commerce
```

### <a name="example"></a><span data-ttu-id="4e93e-111">Пример</span><span class="sxs-lookup"><span data-stu-id="4e93e-111">Example</span></span>

<span data-ttu-id="4e93e-112">Этот пример извлекает предполагаемое использование данных в Azure за последний месяц.</span><span class="sxs-lookup"><span data-stu-id="4e93e-112">This example retrieves your estimated Azure consumption data for the last month.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4e93e-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="4e93e-113">Samples</span></span>

<span data-ttu-id="4e93e-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="4e93e-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
