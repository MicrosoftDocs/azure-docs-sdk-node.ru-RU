---
title: Модули машинного обучения Azure для Node.js
description: Справочник по модулям машинного обучения Azure для Node.js
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7dfa6d8fa633863fe834ce73462584e79c312c5d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259893"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Модули машинного обучения Azure для Node.js

Машинное обучение — это метод обработки и анализа данных, который позволяет выполнить обучение компьютеров на основе имеющихся данных с целью прогнозирования будущего поведения, результатов и тенденций. Эти прогнозы машинного обучения позволяют сделать приложения и устройства эффективнее. При покупках через Интернет машинное обучение помогает рекомендовать другие продукты, которые могут вам понравиться, на основе уже приобретенных вами товаров. При проведении кредитной карты через терминал машинное обучение сравнивает транзакцию с базой данных и позволяет обнаружить мошенничество. Когда робот-пылесос убирает комнату, машинное обучение позволяет определить, когда этот процесс окончен.

## <a name="management-package"></a>Пакет управления


### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm машинного обучения Azure.

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>Пример

Этот пример перечисляет все планы обязательств машинного обучения.

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
