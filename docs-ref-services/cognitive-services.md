---
title: "Модули Azure Cognitive Services для Node.js"
description: "Справочник по модулям Azure Cognitive Services для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Модули Azure Cognitive Services для Node.js

Azure Cognitive Services — это набор API-интерфейсов, пакетов SDK и служб, которые помогают разработчикам сделать свои приложения более интеллектуальными, привлекательными и доступными. Microsoft Cognitive Services — часть растущего портфеля API машинного обучения корпорации Майкрософт. Используя эти службы, разработчики могут легко добавлять в свои приложения интеллектуальные функции, например определение эмоций и обнаружение видео, распознавание лиц, речи и компьютерное зрение, понимание речи и языка. Наша цель — персонализированные вычислительные среды и высокая производительность, обеспечиваемые системами, которые все лучше и лучше видят, слышат, говорят, понимают и даже начинают размышлять.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm Azure Cognitive Services.

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>Пример

Этот пример перечисляет все учетные записи Cognitive Services.

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
