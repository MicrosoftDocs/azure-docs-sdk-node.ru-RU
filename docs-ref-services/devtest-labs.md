---
title: "Модули Azure DevTest Labs для Node.js"
description: "Справочник по модулям Azure DevTest Labs для Node.js"
keywords: Azure,SDK,API,DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Модули Azure DevTest Labs для Node.js

## <a name="overview"></a>Обзор

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
