---
title: Модули Azure MySQL для Node.js
description: Справочник по модулям Azure MySQL для Node.js
author: ajlam
ms.author: andrela
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 557645774ecb0ea5e774f99d03251a303ad19660
ms.sourcegitcommit: 286f52ea38c9eff2ec9d4f8cabeb86f62fd9c406
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/23/2018
ms.locfileid: "41691774"
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="1615b-103">Модули Azure MySQL для Node.js</span><span class="sxs-lookup"><span data-stu-id="1615b-103">Azure MySQL modules for Node.js</span></span>

<span data-ttu-id="1615b-104">Рекомендуемая клиентская библиотека для доступа к базе данных Azure для MySQL с открытым кодом [Библиотека подключений Node.js для базы данных Azure для MySQL](https://github.com/sidorares/node-mysql2).</span><span class="sxs-lookup"><span data-stu-id="1615b-104">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="1615b-105">Дополнительные сведения о [базе данных Azure для MySQL](https://docs.microsoft.com/azure/MySQL/).</span><span class="sxs-lookup"><span data-stu-id="1615b-105">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="1615b-106">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="1615b-106">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1615b-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="1615b-107">Install the npm module</span></span>

<span data-ttu-id="1615b-108">Установите модуль клиента MySQL с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="1615b-108">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="1615b-109">Пример</span><span class="sxs-lookup"><span data-stu-id="1615b-109">Example</span></span>

<span data-ttu-id="1615b-110">Этот пример подключается к базе данных MySQL и выполняет простой запрос для получения всех клиентов.</span><span class="sxs-lookup"><span data-stu-id="1615b-110">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="1615b-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="1615b-111">Samples</span></span>

[!INCLUDE [node-mysql-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="1615b-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="1615b-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
