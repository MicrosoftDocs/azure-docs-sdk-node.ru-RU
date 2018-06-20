---
title: Модули Azure PostgreSQL для Node.js
description: Справочник по модулям Azure PostgreSQL для Node.js
author: rachel-msft
ms.author: raagyema
manager: sukamat
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: postgresql
ms.openlocfilehash: 706f636a89e5e89c1dbf760e01c684bcc9588f1f
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262058"
---
# <a name="azure-postgresql-modules-for-nodejs"></a>Модули Azure PostgreSQL для Node.js

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
