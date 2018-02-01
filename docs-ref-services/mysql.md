---
title: "Модули Azure MySQL для Node.js"
description: "Справочник по модулям Azure MySQL для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: c78f61d0f76b6a40ad85ae0e7d9101349666eb0b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-mysql-modules-for-nodejs"></a>Модули Azure MySQL для Node.js

Рекомендуемая клиентская библиотека для доступа к базе данных Azure для MySQL с открытым кодом [Библиотека подключений Node.js для базы данных Azure для MySQL](https://github.com/sidorares/node-mysql2). 

Дополнительные сведения о [базе данных Azure для MySQL](https://docs.microsoft.com/azure/MySQL/).

## <a name="client-package"></a>Пакет клиента

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль клиента MySQL с помощью npm.

```bash
npm install mysql2
```   

### <a name="example"></a>Пример

Этот пример подключается к базе данных MySQL и выполняет простой запрос для получения всех клиентов.

```javascript
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'mysqldemo.mysql.database.azure.com',
  user: 'myadmin@mysqldemo',
  password: 'your_password',
  database: 'my_db',
  port: 3306,
  ssl: true
});

connection.connect();
const query = 'SELECT * FROM customers';
connection.query(query, (err, res) =>
  console.log(`We have ${res.length} customers`)
);

connection.end();
```

## <a name="samples"></a>Примеры

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
