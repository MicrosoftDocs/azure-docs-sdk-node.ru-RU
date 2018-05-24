---
title: Модули SQL Azure для Node.js
description: Справочник по модулям SQL Azure для Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 095a54a0919b237891ea89f4c826be0fc3060bbe
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="da2e0-103">Модули SQL Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="da2e0-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="da2e0-104">Работа с данными, хранящимися в [базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), из Node.js.</span><span class="sxs-lookup"><span data-stu-id="da2e0-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="da2e0-105">Библиотека управления предоставляет интерфейс для простого управления базами данных SQL Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="da2e0-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="da2e0-106">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="da2e0-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="da2e0-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="da2e0-107">Install the npm module</span></span>

<span data-ttu-id="da2e0-108">Установите модуль npm клиента SQL Server.</span><span class="sxs-lookup"><span data-stu-id="da2e0-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="da2e0-109">Пример</span><span class="sxs-lookup"><span data-stu-id="da2e0-109">Example</span></span>

<span data-ttu-id="da2e0-110">Этот пример подключается к базе данных SQL Server и выполняет простой запрос.</span><span class="sxs-lookup"><span data-stu-id="da2e0-110">This example connects to a SQL Server database and perform a simple query.</span></span>

```javascript
const Connection = require('tedious').Connection;
const Request = require('tedious').Request;

const config = {
  userName: 'your-username',
  password: 'your-password',
  server: 'path-to-server',
  options: {
    database: 'database-name',
    encrypt: true
  }
};

const connection = new Connection(config);
connection.on('connect', err => {
  err ? console.log(err) : executeStatement();
});

const query = 'SELECT * from TableName';
const executeStatement = () => {
  const request = new Request(query, (err, rowCount) => {
    err ? console.log(err) : console.log(rowCount);
  });

  request.on('row', columns => {
    columns.forEach(column => console.log(column.value));
  });

  connection.execSql(request);
};
```

## <a name="management-package"></a><span data-ttu-id="da2e0-111">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="da2e0-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="da2e0-112">Установка модулей npm</span><span class="sxs-lookup"><span data-stu-id="da2e0-112">Install npm modules</span></span>

<span data-ttu-id="da2e0-113">Установите модуль npm управления Azure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="da2e0-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="da2e0-114">Пример</span><span class="sxs-lookup"><span data-stu-id="da2e0-114">Example</span></span>

<span data-ttu-id="da2e0-115">Проверка подлинности, создание клиента и отображение списка всех серверов.</span><span class="sxs-lookup"><span data-stu-id="da2e0-115">Authenticate, create a client, and list all servers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SQLManagement = require('azure-arm-sql');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SQLManagement(credentials, 'your-subscription-id');
    return client.servers.list();
  })
  .then(servers => console.dir(servers, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="da2e0-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="da2e0-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="da2e0-117">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="da2e0-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
