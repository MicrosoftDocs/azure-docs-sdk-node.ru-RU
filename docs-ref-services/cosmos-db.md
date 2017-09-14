---
title: "Модули Azure Cosmos DB для Node.js"
description: "Справочник по модулям Azure Cosmos DB для Node.js"
keywords: Azure,SDK,API,Cosmos DB, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 1f545f89b5304b611dbe1ed9cb86052c112f13c1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="771e9-104">Модули Azure Cosmos DB для Node.js</span><span class="sxs-lookup"><span data-stu-id="771e9-104">Azure Cosmos DB Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="771e9-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="771e9-105">Overview</span></span>

<span data-ttu-id="771e9-106">Azure Cosmos DB — это глобально распределенная многомодельная база данных Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="771e9-106">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="771e9-107">Azure Cosmos DB позволяет гибко и независимо масштабировать пропускную способность и ресурсы хранилища в любом количестве регионов Azure.</span><span class="sxs-lookup"><span data-stu-id="771e9-107">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="771e9-108">Она гарантирует пропускную способность, задержку, доступность и согласованность в соответствии с соглашениями об уровне обслуживания (SLA), которые зачастую не могут предложить другие службы баз данных.</span><span class="sxs-lookup"><span data-stu-id="771e9-108">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="771e9-109">Azure Cosmos DB содержит оптимизированное для записи, независящее от схемы ядро СУБД с регулировкой ресурсов, которое изначально поддерживает несколько моделей данных: модели данных документа, пар "ключ — значение", графы и модели данных столбцов.</span><span class="sxs-lookup"><span data-stu-id="771e9-109">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="771e9-110">Она также поддерживает многие интерфейсы API для доступа к данным, включая MongoDB, DocumentDB SQL, Gremlin (предварительная версия) и таблицы Azure (предварительная версия). Список поддерживаемых интерфейсов постоянно увеличивается.</span><span class="sxs-lookup"><span data-stu-id="771e9-110">It also supports many APIs for accessing data including MongoDB, DocumentDB SQL, Gremlin (preview), and Azure Tables (preview), in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="771e9-111">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="771e9-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="771e9-112">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="771e9-112">Install the npm module</span></span> 

<span data-ttu-id="771e9-113">Установите модуль npm Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="771e9-113">Install the Azure Cosmos DB npm module</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="771e9-114">Пример</span><span class="sxs-lookup"><span data-stu-id="771e9-114">Example</span></span>

<span data-ttu-id="771e9-115">Этот пример перечисляет все учетные записи Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="771e9-115">This example lists all Cosmos DB accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a><span data-ttu-id="771e9-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="771e9-116">Samples</span></span>

* [<span data-ttu-id="771e9-117">Разработка приложения Node.js с помощью Azure Cosmos DB — DocumentDB</span><span class="sxs-lookup"><span data-stu-id="771e9-117">Developing a Node.js app using Azure Cosmos DB - DocumentDB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="771e9-118">Разработка приложения Node.js с помощью Azure Cosmos DB — Gremlin</span><span class="sxs-lookup"><span data-stu-id="771e9-118">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="771e9-119">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="771e9-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
