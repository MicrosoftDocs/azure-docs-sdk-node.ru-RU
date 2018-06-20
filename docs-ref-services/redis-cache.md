---
title: Модули кэша Redis для Microsoft Azure для Node.js
description: Справочник по модулям кэша Redis для Microsoft Azure для Node.js
author: wesmc7777
ms.author: wesmc
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Redis Cache
ms.openlocfilehash: afeee19cb79b54561b6cbef4a79de8b1606adb4d
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34265065"
---
# <a name="azure-redis-cache-modules-for-nodejs"></a><span data-ttu-id="9ff86-103">Модули кэша Redis для Microsoft Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="9ff86-103">Azure Redis Cache modules for Node.js</span></span>

<span data-ttu-id="9ff86-104">Кэш Redis для Azure основан на популярном проекте с открытым кодом Redis.</span><span class="sxs-lookup"><span data-stu-id="9ff86-104">Azure Redis Cache is based on the popular open source Redis project.</span></span> <span data-ttu-id="9ff86-105">Он предоставляет доступ к безопасному выделенному экземпляру Redis, управляемому корпорацией Майкрософт и доступному из приложений Azure.</span><span class="sxs-lookup"><span data-stu-id="9ff86-105">It gives you access to a secure, dedicated Redis instance, managed by Microsoft and accessible from your Azure apps.</span></span>

<span data-ttu-id="9ff86-106">Redis — это усовершенствованное хранилище пар "ключ — значение", где ключи могут содержать такие структуры данных, как строки, хэши, списки, наборы и сортируемые наборы.</span><span class="sxs-lookup"><span data-stu-id="9ff86-106">Redis is an advanced key-value store, where keys can contain data structures such as strings, hashes, lists, sets, and sorted sets.</span></span> <span data-ttu-id="9ff86-107">Redis поддерживает ряд атомарных операций с этими типами данных.</span><span class="sxs-lookup"><span data-stu-id="9ff86-107">Redis supports a set of atomic operations on these data types.</span></span>

<span data-ttu-id="9ff86-108">Дополнительные сведения о [кэше Redis для Azure](https://docs.microsoft.com/azure/redis-cache/).</span><span class="sxs-lookup"><span data-stu-id="9ff86-108">Learn more about [Azure Redis Cache](https://docs.microsoft.com/azure/redis-cache/).</span></span>

## <a name="client-package"></a><span data-ttu-id="9ff86-109">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="9ff86-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9ff86-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="9ff86-110">Install the npm module</span></span>

<span data-ttu-id="9ff86-111">Установите модуль Redis для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="9ff86-111">Use npm to install the Redis module for Node.js</span></span>

```bash
npm install redis
```

### <a name="example"></a><span data-ttu-id="9ff86-112">Пример</span><span class="sxs-lookup"><span data-stu-id="9ff86-112">Example</span></span>

<span data-ttu-id="9ff86-113">Этот пример кода подключается к экземпляру кэша Redis для Azure, сохраняет пару "ключ — значение", а затем считывает сохраненное значение по его ключу.</span><span class="sxs-lookup"><span data-stu-id="9ff86-113">This example connects to an Azure Redis Cache instance, stores a key/value pair and then reads the stored value by its key.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="9ff86-114">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="9ff86-114">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9ff86-115">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="9ff86-115">Install the npm module</span></span>

<span data-ttu-id="9ff86-116">Установите модули кэша Redis для Azure для Node.js. с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="9ff86-116">Use npm to install the Azure Redis Cache modules for Node.js</span></span>

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a><span data-ttu-id="9ff86-117">Пример</span><span class="sxs-lookup"><span data-stu-id="9ff86-117">Example</span></span>

<span data-ttu-id="9ff86-118">Этот пример кода выполняет проверку подлинности в Azure и перечисляет все экземпляры кэша Redis в указанной группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="9ff86-118">This example authenticates to Azure and lists all Redis Cache instances in a specified resource group.</span></span>

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


## <a name="samples"></a><span data-ttu-id="9ff86-119">Примеры</span><span class="sxs-lookup"><span data-stu-id="9ff86-119">Samples</span></span>

* [<span data-ttu-id="9ff86-120">Использование кэша Redis для Azure с Node.js</span><span class="sxs-lookup"><span data-stu-id="9ff86-120">How to use Azure Redis Cache with Node.js</span></span>](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

<span data-ttu-id="9ff86-121">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="9ff86-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
