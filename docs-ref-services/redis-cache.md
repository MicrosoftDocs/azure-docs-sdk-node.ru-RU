---
title: "Модули кэша Redis для Microsoft Azure для Node.js"
description: "Справочник по модулям кэша Redis для Microsoft Azure для Node.js"
keywords: Azure,SDK,API,Redis Cache, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: 8a10e522e39461697b740750b63fc82a6cc320ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="b5711-104">Модули кэша Redis для Microsoft Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="b5711-104">Azure Redis Cache modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b5711-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="b5711-105">Overview</span></span>

<span data-ttu-id="b5711-106">Кэш Redis для Azure основан на популярном проекте с открытым кодом Redis.</span><span class="sxs-lookup"><span data-stu-id="b5711-106">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="b5711-107">Он предоставляет доступ к безопасному выделенному экземпляру Redis, управляемому корпорацией Майкрософт и доступному из приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="b5711-107">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="b5711-108">Redis — это усовершенствованное хранилище пар "ключ — значение", где ключи могут содержать такие структуры данных, как строки, хэши, списки, наборы и сортируемые наборы.</span><span class="sxs-lookup"><span data-stu-id="b5711-108">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="b5711-109">Redis поддерживает ряд атомарных операций с этими типами данных.</span><span class="sxs-lookup"><span data-stu-id="b5711-109">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="b5711-110">Дополнительные сведения о [кэше Redis для Azure](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="b5711-110">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="b5711-111">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="b5711-111">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b5711-112">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="b5711-112">Install the npm module</span></span>

<span data-ttu-id="b5711-113">Установите модуль Redis для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="b5711-113">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="b5711-114">Пример</span><span class="sxs-lookup"><span data-stu-id="b5711-114">Example</span></span>

<span data-ttu-id="b5711-115">Этот пример кода подключается к экземпляру кэша Redis для Azure, сохраняет пару "ключ — значение", а затем считывает сохраненное значение по его ключу.</span><span class="sxs-lookup"><span data-stu-id="b5711-115">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

```javascript
const redis = require('redis');

const client = redis.createClient(6380, '<name>.redis.cache.windows.net', {
  auth_pass: '<key>',
  tls: { servername: '<name>.redis.cache.windows.net' }
});

client.set('key1', 'value', (err, reply) => {
  console.log(reply);
});

client.get('key1', (err, reply) => {
  console.log(reply);
});
```

## <a name="management-package"></a><span data-ttu-id="b5711-116">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="b5711-116">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b5711-117">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="b5711-117">Install the npm module</span></span>

<span data-ttu-id="b5711-118">Установите модули кэша Redis для Azure для Node.js. с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="b5711-118">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="b5711-119">Пример</span><span class="sxs-lookup"><span data-stu-id="b5711-119">Example</span></span>

<span data-ttu-id="b5711-120">Этот пример кода выполняет проверку подлинности в Azure и перечисляет все экземпляры кэша Redis в указанной группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="b5711-120">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AzureMgmtRedisCache = require('azure-arm-rediscache');

msRestAzure.interactiveLogin().then(credentials => {
  const client = new AzureMgmtRedisCache(credentials, 'my-subscription-id');
  client.redis.listByResourceGroup('testResourceGroup').then(result => {
    console.log(result);
  });
});
```


## <a name="samples"></a><span data-ttu-id="b5711-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="b5711-121">Samples</span></span>

* [<span data-ttu-id="b5711-122">Использование кэша Redis для Azure с Node.js</span><span class="sxs-lookup"><span data-stu-id="b5711-122">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="b5711-123">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="b5711-123">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
