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
ms.openlocfilehash: 33e290343f9188a1f78e53f6b8ed89594e2d9b46
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-commerce-modules-for-nodejs"></a>Модули коммерческих предложений Azure для Node.js

## <a name="overview"></a>Обзор

Используйте API коммерческих предложений Azure для извлечения данных об использовании и ресурсах в предпочитаемые средства анализа данных. API использования ресурсов и RateCard в Azure позволяют точно прогнозировать расходы и управлять ими. Интерфейсы API реализованы в виде поставщика ресурсов и относятся к семейству API, предоставляемых Azure Resource Manager.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm коммерческих предложений Azure.

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Пример

Этот пример извлекает предполагаемое использование данных в Azure за последний месяц.

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

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
