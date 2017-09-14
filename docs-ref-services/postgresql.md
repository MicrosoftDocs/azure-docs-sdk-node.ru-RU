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
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="73dc2-104">Модули Azure PostgreSQL для Node.js</span><span class="sxs-lookup"><span data-stu-id="73dc2-104">Azure PostgreSQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="73dc2-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="73dc2-105">Overview</span></span>

<span data-ttu-id="73dc2-106">Рекомендуемая клиентская библиотека для доступа к базе данных Azure для PostgreSQL с открытым кодом [Библиотека подключений Node.js для базы данных Azure для PostgreSQL](https://www.npmjs.com/package/pg).</span><span class="sxs-lookup"><span data-stu-id="73dc2-106">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="73dc2-107">Эта библиотека является клиентом PostgreSQL без блокировки для Node.js. Она поддерживает только JavaScript и необязательные собственные привязки libpq.</span><span class="sxs-lookup"><span data-stu-id="73dc2-107">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="73dc2-108">Дополнительные сведения о [базе данных Azure для PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span><span class="sxs-lookup"><span data-stu-id="73dc2-108">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="73dc2-109">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="73dc2-109">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="73dc2-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="73dc2-110">Install the npm module</span></span>

<span data-ttu-id="73dc2-111">Установите модуль клиента PostgreSQL с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="73dc2-111">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="73dc2-112">Пример</span><span class="sxs-lookup"><span data-stu-id="73dc2-112">Example</span></span>

<span data-ttu-id="73dc2-113">Этот пример открывает подключение клиента и выполняет простой запрос.</span><span class="sxs-lookup"><span data-stu-id="73dc2-113">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="73dc2-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="73dc2-114">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="73dc2-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="73dc2-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
