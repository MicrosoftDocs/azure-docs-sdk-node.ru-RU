---
title: "Модули помощника по Azure для Node.js"
description: "Справочник по модулям помощника по Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: aad3b292c6304159f68a81270e671cd335c972ec
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a>Модули помощника по Azure для Node.js

## <a name="overview"></a>Обзор

Azure Advisor — это персонализированный облачный консультант, который поможет следовать рекомендациям по оптимизации развернутых служб Azure. Помощник по Azure анализирует конфигурацию ресурсов и данные телеметрии их использования и рекомендует решения, которые помогут повысить эффективность затрат, производительность, уровень доступности и безопасности ресурсов Azure.

С помощью Помощника можно:
- получить упреждающие, действенные и персонализированные практические рекомендации;
- повысить производительность, безопасность и уровень доступности ресурсов, выявляя при этом любые возможности сократить общие затраты на Azure;
- получить рекомендации о доступных встроенных действиях.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm помощника по Azure.

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Пример

Этот пример отображает список рекомендаций помощника по Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
