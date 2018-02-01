---
title: "Модули Azure Analysis Services для Node.js"
description: "Справочник по модулям Azure Analysis Services для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 7dd9ac4a2a4939b66f5a91d048e49fb59cd547c0
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-analysis-services-modules-for-nodejs"></a><span data-ttu-id="a7912-103">Модули Azure Analysis Services для Node.js</span><span class="sxs-lookup"><span data-stu-id="a7912-103">Azure Analysis Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a7912-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="a7912-104">Overview</span></span>
<span data-ttu-id="a7912-105">Этот пакет содержит модуль Node.js, который упрощает управление Microsoft Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="a7912-105">This package provides a Node.js module that makes it easy to manage Microsoft Azure Analysis Services.</span></span>

## <a name="management-package"></a><span data-ttu-id="a7912-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="a7912-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a7912-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="a7912-107">Install the npm module</span></span>

<span data-ttu-id="a7912-108">Установите модуль npm Azure Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="a7912-108">Install the Azure Analysis Services npm module</span></span>

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a><span data-ttu-id="a7912-109">Пример</span><span class="sxs-lookup"><span data-stu-id="a7912-109">Example</span></span>

<span data-ttu-id="a7912-110">Этот пример содержит все доступные серверы Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="a7912-110">This example lists all available Analysis Service servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a7912-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="a7912-111">Samples</span></span>

<span data-ttu-id="a7912-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="a7912-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
