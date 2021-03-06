---
title: Модули SQL Azure для Node.js
description: Справочник по модулям SQL Azure для Node.js
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: sql-database
ms.subservice: development
ms.openlocfilehash: 00ba5984b5f8aef85570c54f23efefd1d741ca57
ms.sourcegitcommit: 0e294f7c4dcdfae9df18ff3e82b6563680ef2519
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55046434"
---
# <a name="azure-sql-modules-for-nodejs"></a>Модули SQL Azure для Node.js

Работа с данными, хранящимися в [базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview), из Node.js.
Библиотека управления предоставляет интерфейс для простого управления базами данных SQL Microsoft Azure.

## <a name="client-package"></a>Пакет клиента

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm клиента SQL Server.

```bash
npm install tedious
```

### <a name="example"></a>Пример

Этот пример подключается к базе данных SQL Server и выполняет простой запрос.

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

## <a name="management-package"></a>Пакет управления

### <a name="install-npm-modules"></a>Установка модулей npm

Установите модуль npm управления Azure SQL Server.

```
npm install azure-arm-sql
```   

### <a name="example"></a>Пример

Проверка подлинности, создание клиента и отображение списка всех серверов.

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

## <a name="samples"></a>Примеры

[!INCLUDE [node-sql-samples](../docs-ref-conceptual/includes/sql-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
