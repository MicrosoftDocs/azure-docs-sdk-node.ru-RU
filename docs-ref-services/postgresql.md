---
title: "Модули Azure PostgreSQL для Node.js"
description: "Справочник по модулям Azure PostgreSQL для Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, database, PostgreSQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: a5130c96b3ae922358b6898c15510282fbaa97f0
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Модули Azure PostgreSQL для Node.js

## <a name="overview"></a>Обзор

Рекомендуемая клиентская библиотека для доступа к базе данных Azure для PostgreSQL с открытым кодом [Библиотека подключений Node.js для базы данных Azure для PostgreSQL](https://www.npmjs.com/package/pg). Эта библиотека является клиентом PostgreSQL без блокировки для Node.js. Она поддерживает только JavaScript и необязательные собственные привязки libpq.

Дополнительные сведения о [базе данных Azure для PostgreSQL](https://docs.microsoft.com/azure/postgresql/).

## <a name="client-package"></a>Пакет клиента

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль клиента PostgreSQL с помощью npm.

```bash
npm install pg
```   

### <a name="example"></a>Пример

Этот пример открывает подключение клиента и выполняет простой запрос.

```javascript
const pg = require('pg');

const connectionString =
  'postgres://{username}@{server-name}:{password}@{server-name}.postgres.database.azure.com:5432/{database-name}?ssl=true';

const client = new pg.Client(connectionString);
client.connect();

const query = 'SELECT * FROM {table-name}';
client.query(query, (err, res) => {
  console.log(res);
});
```

## <a name="samples"></a>Примеры

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
