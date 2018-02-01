---
title: "Модули Azure DevTest Labs для Node.js"
description: "Справочник по модулям Azure DevTest Labs для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 7754280741c09d47e138518d33628c667944c651
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Модули Azure DevTest Labs для Node.js

Azure DevTest Labs — это служба, помогающая разработчикам и тест-инженерам быстро создавать среды в Azure при минимальных потерях и контроле издержек. Для проверки последней версии вашего приложения вы можете быстро развернуть среду Windows и Linux, используя многоразовые шаблоны и артефакты. Для подготовки сред по запросу интегрируйте с DevTest Labs конвейер развертывания. Масштабируйте нагрузочное тестирование, подготавливая несколько агентов тестирования, и создавайте подготовленные среды для обучения и демонстраций.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm Azure DevTest Labs.

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>Пример

Этот пример извлекает и печатает сведения лаборатории.

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
