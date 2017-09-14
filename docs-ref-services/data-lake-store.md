---
title: "Модули Azure Data Lake Store для Node.js"
description: "Справочник по модулям Azure Data Lake Store для Node.js"
keywords: Azure,SDK,API,Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a><span data-ttu-id="bb691-104">Модули Azure Data Lake Store для Node.js</span><span class="sxs-lookup"><span data-stu-id="bb691-104">Azure Data Lake Store modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bb691-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="bb691-105">Overview</span></span>
<span data-ttu-id="bb691-106">Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных.</span><span class="sxs-lookup"><span data-stu-id="bb691-106">Azure Data Lake Store is an enterprise-wide hyper-scale repository for big data analytic workloads.</span></span> <span data-ttu-id="bb691-107">Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.</span><span class="sxs-lookup"><span data-stu-id="bb691-107">Azure Data Lake enables you to capture data of any size, type, and ingestion speed in one single place for operational and exploratory analytics.</span></span>

## <a name="management-package"></a><span data-ttu-id="bb691-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bb691-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bb691-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bb691-109">Install the npm module</span></span>

<span data-ttu-id="bb691-110">Установите модули Azure Data Lake Store для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="bb691-110">Use npm to install the Azure Data Lake Store modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a><span data-ttu-id="bb691-111">Пример</span><span class="sxs-lookup"><span data-stu-id="bb691-111">Example</span></span>

<span data-ttu-id="bb691-112">С помощью этого примера можно получить список всех учетных записей Data Lake Store в рамках определенной подписки Azure.</span><span class="sxs-lookup"><span data-stu-id="bb691-112">This example lists all Data Lake Store accounts within a given Azure subscription</span></span>

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

## <a name="samples"></a><span data-ttu-id="bb691-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="bb691-113">Samples</span></span>

<span data-ttu-id="bb691-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bb691-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
