---
title: Модули Azure Cosmos DB для Node.js
description: Справочник по модулям Azure Cosmos DB для Node.js
author: SnehaGunda
ms.author: sngun
manager: kfile
ms.date: 03/20/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 4064f9f6c0e1369c8d6261a70709102e7492b340
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260760"
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a><span data-ttu-id="e0c48-103">Модули Azure Cosmos DB для Node.js</span><span class="sxs-lookup"><span data-stu-id="e0c48-103">Azure Cosmos DB Modules for Node.js</span></span>

<span data-ttu-id="e0c48-104">Azure Cosmos DB — это глобально распределенная многомодельная база данных Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="e0c48-104">Azure Cosmos DB is Microsoft's globally distributed, multi-model database.</span></span> <span data-ttu-id="e0c48-105">Azure Cosmos DB позволяет гибко и независимо масштабировать пропускную способность и ресурсы хранилища в любом количестве регионов Azure.</span><span class="sxs-lookup"><span data-stu-id="e0c48-105">Azure Cosmos DB enables you to elastically and independently scale throughput and storage across any number of Azure's geographic regions.</span></span> <span data-ttu-id="e0c48-106">Она гарантирует пропускную способность, задержку, доступность и согласованность в соответствии с соглашениями об уровне обслуживания (SLA), которые зачастую не могут предложить другие службы баз данных.</span><span class="sxs-lookup"><span data-stu-id="e0c48-106">It offers throughput, latency, availability, and consistency guarantees with comprehensive service level agreements (SLAs), something no other database service can offer.</span></span>

<span data-ttu-id="e0c48-107">Azure Cosmos DB содержит оптимизированное для записи, независящее от схемы ядро СУБД с регулировкой ресурсов, которое изначально поддерживает несколько моделей данных: модели данных документа, пар "ключ — значение", графы и модели данных столбцов.</span><span class="sxs-lookup"><span data-stu-id="e0c48-107">Azure Cosmos DB contains a write optimized, resource governed, schema-agnostic database engine that natively supports multiple data models: key-value, documents, graphs, and columnar.</span></span> <span data-ttu-id="e0c48-108">Служба также поддерживает многие API для доступа к данным, включая MongoDB, SQL, Gremlin/Graph, таблицы Azure и Cassandra (предварительную версию). Список поддерживаемых интерфейсов постоянно увеличивается.</span><span class="sxs-lookup"><span data-stu-id="e0c48-108">It also supports many APIs for accessing data including MongoDB, SQL, Gremlin/Graph, Azure Tables, and Cassandra (preview) in an extensible manner.</span></span>

## <a name="management-package"></a><span data-ttu-id="e0c48-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="e0c48-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e0c48-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="e0c48-110">Install the npm module</span></span> 

<span data-ttu-id="e0c48-111">Установите модуль npm для Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="e0c48-111">Install the Azure Cosmos DB npm module.</span></span>

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a><span data-ttu-id="e0c48-112">Пример</span><span class="sxs-lookup"><span data-stu-id="e0c48-112">Example</span></span>

<span data-ttu-id="e0c48-113">Этот пример перечисляет все учетные записи Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="e0c48-113">This example lists all Azure Cosmos DB accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e0c48-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="e0c48-114">Samples</span></span>

* [<span data-ttu-id="e0c48-115">Разработка приложения Node.js с помощью Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="e0c48-115">Developing a Node.js app using Azure Cosmos DB</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [<span data-ttu-id="e0c48-116">Разработка приложения Node.js с помощью Azure Cosmos DB — Gremlin</span><span class="sxs-lookup"><span data-stu-id="e0c48-116">Developing a Node.js app using Azure Cosmos DB - Gremlin</span></span>](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

<span data-ttu-id="e0c48-117">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="e0c48-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
