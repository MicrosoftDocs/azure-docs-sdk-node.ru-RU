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
ms.sourcegitcommit: f830f2f37429b32bbcfa856ad82a817ae2658341
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "46213356"
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
