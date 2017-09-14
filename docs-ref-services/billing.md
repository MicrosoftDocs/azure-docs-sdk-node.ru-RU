---
title: "Модули выставления счетов Azure для Node.js"
description: "Справочник по выставления счетов Azure для Node.js"
keywords: Azure,SDK,API,Billing, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: fa861aebbd5cbced6477ceeb67dbb5acc7eb233e
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="f1597-104">Модули выставления счетов Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="f1597-104">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f1597-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="f1597-105">Overview</span></span>
<span data-ttu-id="f1597-106">API-интерфейсы выставления счетов Azure предоставляют доступ к счетам и сведениям об их выставлении в Azure.</span><span class="sxs-lookup"><span data-stu-id="f1597-106">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="f1597-107">Чтобы использовать этот API, администратор учетной записи должен дать согласие на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="f1597-107">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="f1597-108">См. статью [Управление доступом к сведениям о счетах Azure с помощью управления доступом на основе ролей](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="f1597-108">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f1597-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="f1597-109">Install the npm module</span></span> 

<span data-ttu-id="f1597-110">Установите модуль npm выставления счетов Azure.</span><span class="sxs-lookup"><span data-stu-id="f1597-110">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="f1597-111">Пример</span><span class="sxs-lookup"><span data-stu-id="f1597-111">Example</span></span> 
 
<span data-ttu-id="f1597-112">Этот пример печатает список всех предыдущих накладных.</span><span class="sxs-lookup"><span data-stu-id="f1597-112">This example prints a list of all of your past invoices.</span></span>
 
```javascript 
const msRestAzure = require('ms-rest-azure');
const BillingManagement = require('azure-arm-billing');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    let client = new BillingManagement(credentials, subscriptionId);
    return client.invoices.list();
  })
  .then(invoices => {
    console.log('List of invoices:');
    console.dir(invoices, { depth: null, colors: true });
  });
``` 


## <a name="samples"></a><span data-ttu-id="f1597-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="f1597-113">Samples</span></span>

<span data-ttu-id="f1597-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="f1597-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
