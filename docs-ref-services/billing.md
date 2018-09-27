---
title: Модули выставления счетов Azure для Node.js
description: Справочник по выставления счетов Azure для Node.js
author: tfitzmac
ms.author: tomfitz
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: billing
ms.product: ''
ms.technology: ''
ms.openlocfilehash: 20df85ae5e504e460a501737aa07b6692a0da3c7
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2018
ms.locfileid: "47346683"
---
# <a name="azure-billing-modules-for-nodejs"></a><span data-ttu-id="4517a-103">Модули выставления счетов Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="4517a-103">Azure Billing modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4517a-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="4517a-104">Overview</span></span>
<span data-ttu-id="4517a-105">API-интерфейсы выставления счетов Azure предоставляют доступ к счетам и сведениям об их выставлении в Azure.</span><span class="sxs-lookup"><span data-stu-id="4517a-105">The Azure Billing APIs provide access to your Azure billing information and invoices.</span></span>

<span data-ttu-id="4517a-106">Чтобы использовать этот API, администратор учетной записи должен дать согласие на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="4517a-106">To use this API, the account admin must opt in via the Azure portal.</span></span> <span data-ttu-id="4517a-107">См. статью [Управление доступом к сведениям о счетах Azure с помощью управления доступом на основе ролей](https://docs.microsoft.com/azure/billing/billing-manage-access).</span><span class="sxs-lookup"><span data-stu-id="4517a-107">See [Manage access to Azure billing using roles](https://docs.microsoft.com/azure/billing/billing-manage-access).</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4517a-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="4517a-108">Install the npm module</span></span> 

<span data-ttu-id="4517a-109">Установите модуль npm выставления счетов Azure.</span><span class="sxs-lookup"><span data-stu-id="4517a-109">Install the Azure Billing npm module</span></span> 

```bash
npm install azure-arm-billing
```
### <a name="example"></a><span data-ttu-id="4517a-110">Пример</span><span class="sxs-lookup"><span data-stu-id="4517a-110">Example</span></span> 
 
<span data-ttu-id="4517a-111">Этот пример печатает список всех предыдущих накладных.</span><span class="sxs-lookup"><span data-stu-id="4517a-111">This example prints a list of all of your past invoices.</span></span>
 
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


## <a name="samples"></a><span data-ttu-id="4517a-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="4517a-112">Samples</span></span>

<span data-ttu-id="4517a-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="4517a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
