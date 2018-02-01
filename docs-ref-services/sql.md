---
title: "Модули SQL Azure для Node.js"
description: "Справочник по модулям SQL Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: sql-database
ms.openlocfilehash: 8ebcfbcbf39def1774a702c9f18a4e3f5ab86931
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-sql-modules-for-nodejs"></a><span data-ttu-id="3a925-103">Модули SQL Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="3a925-103">Azure SQL modules for Node.js</span></span>

<span data-ttu-id="3a925-104">Работа с данными, хранящимися в [базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), из Node.js.</span><span class="sxs-lookup"><span data-stu-id="3a925-104">Work with data stored in [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview) from Node.js.</span></span>
<span data-ttu-id="3a925-105">Библиотека управления предоставляет интерфейс для простого управления базами данных SQL Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3a925-105">The management library provides an interface to make it easy to manage Microsoft Azure SQL databases.</span></span>

## <a name="client-package"></a><span data-ttu-id="3a925-106">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="3a925-106">Client package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3a925-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="3a925-107">Install the npm module</span></span>

<span data-ttu-id="3a925-108">Установите модуль npm клиента SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a925-108">Install the SQL Server client npm module</span></span>

```bash
npm install tedious
```

### <a name="example"></a><span data-ttu-id="3a925-109">Пример</span><span class="sxs-lookup"><span data-stu-id="3a925-109">Example</span></span>

<span data-ttu-id="3a925-110">Этот пример подключается к базе данных SQL Server и выполняет простой запрос.</span><span class="sxs-lookup"><span data-stu-id="3a925-110">This example connects to a SQL Server database and perform a simple query.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="3a925-111">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="3a925-111">Management package</span></span>

### <a name="install-npm-modules"></a><span data-ttu-id="3a925-112">Установка модулей npm</span><span class="sxs-lookup"><span data-stu-id="3a925-112">Install npm modules</span></span>

<span data-ttu-id="3a925-113">Установите модуль npm управления Azure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3a925-113">Install the Azure SQL Server management npm module</span></span>

```
npm install azure-arm-sql
```   

### <a name="example"></a><span data-ttu-id="3a925-114">Пример</span><span class="sxs-lookup"><span data-stu-id="3a925-114">Example</span></span>

<span data-ttu-id="3a925-115">Проверка подлинности, создание клиента и отображение списка всех серверов.</span><span class="sxs-lookup"><span data-stu-id="3a925-115">Authenticate, create a client, and list all servers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="3a925-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="3a925-116">Samples</span></span>

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

<span data-ttu-id="3a925-117">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="3a925-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
