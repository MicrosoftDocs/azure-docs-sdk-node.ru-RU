---
title: "Модули Azure PostgreSQL для Node.js"
description: "Справочник по модулям Azure PostgreSQL для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: d8a2c7fe90746def7e50a7af3a0f470213eed197
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-postgresql-modules-for-nodejs"></a><span data-ttu-id="f805f-103">Модули Azure PostgreSQL для Node.js</span><span class="sxs-lookup"><span data-stu-id="f805f-103">Azure PostgreSQL modules for Node.js</span></span>

<span data-ttu-id="f805f-104">Рекомендуемая клиентская библиотека для доступа к базе данных Azure для PostgreSQL с открытым кодом [Библиотека подключений Node.js для базы данных Azure для PostgreSQL](https://www.npmjs.com/package/pg).</span><span class="sxs-lookup"><span data-stu-id="f805f-104">The recommended client library for accessing Azure Database for PostgreSQL is the open-source [Node.js connection library for Azure Database for PostgreSQL](https://www.npmjs.com/package/pg).</span></span> <span data-ttu-id="f805f-105">Эта библиотека является клиентом PostgreSQL без блокировки для Node.js. Она поддерживает только JavaScript и необязательные собственные привязки libpq.</span><span class="sxs-lookup"><span data-stu-id="f805f-105">This library is a non-blocking PostgreSQL client for Node.js, supporting pure JavaScript and optional native libpq bindings.</span></span>

<span data-ttu-id="f805f-106">Дополнительные сведения о [базе данных Azure для PostgreSQL](https://docs.microsoft.com/azure/postgresql/).</span><span class="sxs-lookup"><span data-stu-id="f805f-106">Learn more about [Azure Database for PostgreSQL](https://docs.microsoft.com/azure/postgresql/)</span></span>

## <a name="client-package"></a><span data-ttu-id="f805f-107">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="f805f-107">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f805f-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="f805f-108">Install the npm module</span></span>

<span data-ttu-id="f805f-109">Установите модуль клиента PostgreSQL с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="f805f-109">Use npm to install the PostgreSQL client module.</span></span>

```bash
npm install pg
```   

### <a name="example"></a><span data-ttu-id="f805f-110">Пример</span><span class="sxs-lookup"><span data-stu-id="f805f-110">Example</span></span>

<span data-ttu-id="f805f-111">Этот пример открывает подключение клиента и выполняет простой запрос.</span><span class="sxs-lookup"><span data-stu-id="f805f-111">This example opens a client connection and executes a simple query.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f805f-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="f805f-112">Samples</span></span>

[!INCLUDE [node-postgresql-samples](../docs-ref-conceptual/includes/postgresql-samples.md)]

<span data-ttu-id="f805f-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="f805f-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
