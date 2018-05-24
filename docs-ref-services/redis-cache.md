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
---
# <a name="azure-redis-cache-modules-for-nodejs"></a>Модули кэша Redis для Microsoft Azure для Node.js

Кэш Redis для Azure основан на популярном проекте с открытым кодом Redis. Он предоставляет доступ к безопасному выделенному экземпляру Redis, управляемому корпорацией Майкрософт и доступному из приложений Azure.

Redis — это усовершенствованное хранилище пар "ключ — значение", где ключи могут содержать такие структуры данных, как строки, хэши, списки, наборы и сортируемые наборы. Redis поддерживает ряд атомарных операций с этими типами данных.

Дополнительные сведения о [кэше Redis для Azure](https://docs.microsoft.com/azure/redis-cache/).

## <a name="client-package"></a>Пакет клиента

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль Redis для Node.js с помощью npm.

```bash
npm install redis
```

### <a name="example"></a>Пример

Этот пример кода подключается к экземпляру кэша Redis для Azure, сохраняет пару "ключ — значение", а затем считывает сохраненное значение по его ключу.

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

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модули кэша Redis для Azure для Node.js. с помощью npm.

```bash
npm install azure-arm-rediscache
```

### <a name="example"></a>Пример

Этот пример кода выполняет проверку подлинности в Azure и перечисляет все экземпляры кэша Redis в указанной группе ресурсов.

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


## <a name="samples"></a>Примеры

* [Использование кэша Redis для Azure с Node.js](https://docs.microsoft.com/azure/redis-cache/cache-nodejs-get-started)

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
