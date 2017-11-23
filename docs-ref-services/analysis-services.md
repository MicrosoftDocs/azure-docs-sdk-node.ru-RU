---
title: "Модули Azure Analysis Services для Node.js"
description: "Справочник по модулям Azure Analysis Services для Node.js"
keywords: Azure,SDK,API,Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="ca602-104">Модули Azure Analysis Services для Node.js</span><span class="sxs-lookup"><span data-stu-id="ca602-104">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="ca602-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="ca602-105">Overview</span></span>
<span data-ttu-id="ca602-106">Этот пакет содержит модуль Node.js, который упрощает управление Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="ca602-106">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="ca602-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="ca602-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ca602-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="ca602-108">Install the npm module</span></span>

<span data-ttu-id="ca602-109">Установите модуль npm Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="ca602-109">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="ca602-110">Пример</span><span class="sxs-lookup"><span data-stu-id="ca602-110">Example</span></span>

<span data-ttu-id="ca602-111">Этот пример содержит все доступные серверы Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="ca602-111">This example lists all available Analysis Service servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a><span data-ttu-id="ca602-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="ca602-112">Samples</span></span>

<span data-ttu-id="ca602-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="ca602-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
