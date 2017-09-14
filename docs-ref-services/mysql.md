---
title: "Модули Azure MySQL для Node.js"
description: "Справочник по модулям Azure MySQL для Node.js"
keywords: Azure, Node, SDK, API, nodejs, javascript, database, MySQL
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: mysql
ms.openlocfilehash: 3efc0fcccb7cb01711ad1ce98e9ff9a2d87b77fe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-mysql-modules-for-nodejs"></a><span data-ttu-id="dd96b-104">Модули Azure MySQL для Node.js</span><span class="sxs-lookup"><span data-stu-id="dd96b-104">Azure MySQL modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dd96b-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="dd96b-105">Overview</span></span>

<span data-ttu-id="dd96b-106">Рекомендуемая клиентская библиотека для доступа к базе данных Azure для MySQL с открытым кодом [Библиотека подключений Node.js для базы данных Azure для MySQL](https://github.com/sidorares/node-mysql2).</span><span class="sxs-lookup"><span data-stu-id="dd96b-106">The recommended client library for accessing Azure Database for MySQL is the open-source [Node.js connection library for Azure Database for MySQL](https://github.com/sidorares/node-mysql2).</span></span> 

<span data-ttu-id="dd96b-107">Дополнительные сведения о [базе данных Azure для MySQL](https://docs.microsoft.com/azure/MySQL/).</span><span class="sxs-lookup"><span data-stu-id="dd96b-107">Learn more about [Azure Database for MySQL](https://docs.microsoft.com/azure/MySQL/)</span></span>

## <a name="client-package"></a><span data-ttu-id="dd96b-108">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="dd96b-108">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dd96b-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="dd96b-109">Install the npm module</span></span>

<span data-ttu-id="dd96b-110">Установите модуль клиента MySQL с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="dd96b-110">Use npm to install the MySQL client module.</span></span>

```bash
npm install mysql2
```   

### <a name="example"></a><span data-ttu-id="dd96b-111">Пример</span><span class="sxs-lookup"><span data-stu-id="dd96b-111">Example</span></span>

<span data-ttu-id="dd96b-112">Этот пример подключается к базе данных MySQL и выполняет простой запрос для получения всех клиентов.</span><span class="sxs-lookup"><span data-stu-id="dd96b-112">This example connects to a MySQL database and performs a simple query to retrieve all customers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="dd96b-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="dd96b-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/mysql-samples.md)]

<span data-ttu-id="dd96b-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="dd96b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
