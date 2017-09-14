---
title: "Модули машинного обучения Azure для Node.js"
description: "Справочник по модулям машинного обучения Azure для Node.js"
keywords: Azure,SDK,API,Machine Learning, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="c09e3-104">Модули машинного обучения Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="c09e3-104">Azure Machine Learning modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c09e3-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c09e3-105">Overview</span></span>

<span data-ttu-id="c09e3-106">Машинное обучение — это метод обработки и анализа данных, который позволяет выполнить обучение компьютеров на основе имеющихся данных с целью прогнозирования будущего поведения, результатов и тенденций.</span><span class="sxs-lookup"><span data-stu-id="c09e3-106">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="c09e3-107">Эти прогнозы машинного обучения позволяют сделать приложения и устройства эффективнее.</span><span class="sxs-lookup"><span data-stu-id="c09e3-107">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="c09e3-108">При покупках через Интернет машинное обучение помогает рекомендовать другие продукты, которые могут вам понравиться, на основе уже приобретенных вами товаров.</span><span class="sxs-lookup"><span data-stu-id="c09e3-108">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="c09e3-109">При проведении кредитной карты через терминал машинное обучение сравнивает транзакцию с базой данных и позволяет обнаружить мошенничество.</span><span class="sxs-lookup"><span data-stu-id="c09e3-109">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="c09e3-110">Когда робот-пылесос убирает комнату, машинное обучение позволяет определить, когда этот процесс окончен.</span><span class="sxs-lookup"><span data-stu-id="c09e3-110">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="c09e3-111">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="c09e3-111">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="c09e3-112">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="c09e3-112">Install the npm module</span></span>

<span data-ttu-id="c09e3-113">Установите модуль npm машинного обучения Azure.</span><span class="sxs-lookup"><span data-stu-id="c09e3-113">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="c09e3-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c09e3-114">Example</span></span>

<span data-ttu-id="c09e3-115">Этот пример перечисляет все планы обязательств машинного обучения.</span><span class="sxs-lookup"><span data-stu-id="c09e3-115">This example lists all machine learning committment plans.</span></span>

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

## <a name="samples"></a><span data-ttu-id="c09e3-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="c09e3-116">Samples</span></span>

<span data-ttu-id="c09e3-117">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="c09e3-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
