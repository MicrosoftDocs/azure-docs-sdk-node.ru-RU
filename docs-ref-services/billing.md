---
title: "Модули выставления счетов Azure для Node.js"
description: "Справочник по выставления счетов Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Billing
ms.openlocfilehash: 58eed8996f543e845a53a741f8684d9e7f6cc1e4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
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
