---
title: Модули Operational Insights Azure для Node.js
description: Справочник по модулям Operational Insights Azure для Node.js
author: MGoedtel
ms.author: magoedte
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: c8a137c4759982e0551d9048ac271780e6a68afe
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50270977"
---
# <a name="azure-operational-insights-modules-for-nodejs"></a><span data-ttu-id="020ea-103">Модули Operational Insights Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="020ea-103">Azure Operational Insights Modules for Node.js</span></span>

<span data-ttu-id="020ea-104">Установите модуль Azure Operational Insights для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="020ea-104">Use npm to install the Azure Operational Insights module for Node.js</span></span>

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a><span data-ttu-id="020ea-105">Пример</span><span class="sxs-lookup"><span data-stu-id="020ea-105">Example</span></span> 

<span data-ttu-id="020ea-106">Этот пример создает клиент, подключается к Operational Insights и извлекает список рабочих областей для конкретной группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="020ea-106">This example creates a client, connects to Operational Insights and retreives a list of workspaces by a specified resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="020ea-107">Примеры</span><span class="sxs-lookup"><span data-stu-id="020ea-107">Samples</span></span>

<span data-ttu-id="020ea-108">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="020ea-108">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
