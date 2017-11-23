---
title: "Модули Operational Insights Azure для Node.js"
description: "Справочник по модулям Operational Insights Azure для Node.js"
keywords: Azure,SDK,API,Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="79f58-104">Модули Operational Insights Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="79f58-104">Azure Operational Insights Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="79f58-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="79f58-105">Overview</span></span>

## <a name="management-package"></a><span data-ttu-id="79f58-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="79f58-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="79f58-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="79f58-107">Install the npm module</span></span>

<span data-ttu-id="79f58-108">Установите модуль Azure Operational Insights для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="79f58-108">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="79f58-109">Пример</span><span class="sxs-lookup"><span data-stu-id="79f58-109">Example</span></span> 

<span data-ttu-id="79f58-110">Этот пример создает клиент, подключается к Operational Insights и извлекает список рабочих областей для конкретной группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="79f58-110">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a><span data-ttu-id="79f58-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="79f58-111">Samples</span></span>

<span data-ttu-id="79f58-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="79f58-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
