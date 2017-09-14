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
# <a name="azure-billing-modules-for-nodejs"></a>Модули выставления счетов Azure для Node.js

## <a name="overview"></a>Обзор
API-интерфейсы выставления счетов Azure предоставляют доступ к счетам и сведениям об их выставлении в Azure.

Чтобы использовать этот API, администратор учетной записи должен дать согласие на портале Azure. См. статью [Управление доступом к сведениям о счетах Azure с помощью управления доступом на основе ролей](https://docs.microsoft.com/azure/billing/billing-manage-access).

### <a name="install-the-npm-module"></a>Установка модуля npm 

Установите модуль npm выставления счетов Azure. 

```bash
npm install azure-arm-billing
```
### <a name="example"></a>Пример 
 
Этот пример печатает список всех предыдущих накладных.
 
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


## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
