---
title: "Модули Azure Data Lake Store для Node.js"
description: "Справочник по модулям Azure Data Lake Store для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: a108cc6d184b72d2d4227f9e60da6b7a535f92ae
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="bf1cd-103">Модули Azure Data Lake Store для Node.js</span><span class="sxs-lookup"><span data-stu-id="bf1cd-103">Azure Data Lake Store modules for Node.js</span></span>

<span data-ttu-id="bf1cd-104">Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных.</span><span class="sxs-lookup"><span data-stu-id="bf1cd-104">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="bf1cd-105">Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.</span><span class="sxs-lookup"><span data-stu-id="bf1cd-105">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="bf1cd-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bf1cd-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bf1cd-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bf1cd-107">Install the npm module</span></span>

<span data-ttu-id="bf1cd-108">Установите модули Azure Data Lake Store для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="bf1cd-108">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="bf1cd-109">Пример</span><span class="sxs-lookup"><span data-stu-id="bf1cd-109">Example</span></span>

<span data-ttu-id="bf1cd-110">С помощью этого примера можно получить список всех учетных записей Data Lake Store в рамках определенной подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="bf1cd-110">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="bf1cd-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="bf1cd-111">Samples</span></span>

<span data-ttu-id="bf1cd-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bf1cd-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
