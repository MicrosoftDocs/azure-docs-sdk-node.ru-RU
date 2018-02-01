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
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="fbece-103">Модули Azure Cognitive Services для Node.js</span><span class="sxs-lookup"><span data-stu-id="fbece-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="fbece-104">Azure Cognitive Services — это набор API-интерфейсов, пакетов SDK и служб, которые помогают разработчикам сделать свои приложения более интеллектуальными, привлекательными и доступными.</span><span class="sxs-lookup"><span data-stu-id="fbece-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="fbece-105">Microsoft Cognitive Services — часть растущего портфеля API машинного обучения корпорации Майкрософт. Используя эти службы, разработчики могут легко добавлять в свои приложения интеллектуальные функции, например определение эмоций и обнаружение видео, распознавание лиц, речи и компьютерное зрение, понимание речи и языка.</span><span class="sxs-lookup"><span data-stu-id="fbece-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="fbece-106">Наша цель — персонализированные вычислительные среды и высокая производительность, обеспечиваемые системами, которые все лучше и лучше видят, слышат, говорят, понимают и даже начинают размышлять.</span><span class="sxs-lookup"><span data-stu-id="fbece-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="fbece-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="fbece-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fbece-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="fbece-108">Install the npm module</span></span>

<span data-ttu-id="fbece-109">Установите модуль npm Azure Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="fbece-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="fbece-110">Пример</span><span class="sxs-lookup"><span data-stu-id="fbece-110">Example</span></span>

<span data-ttu-id="fbece-111">Этот пример перечисляет все учетные записи Cognitive Services.</span><span class="sxs-lookup"><span data-stu-id="fbece-111">This example lists all cognitive service accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="fbece-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="fbece-112">Samples</span></span>

<span data-ttu-id="fbece-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="fbece-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
