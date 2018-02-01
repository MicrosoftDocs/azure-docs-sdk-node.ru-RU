---
title: "Модули службы хранилища Azure для Node.js"
description: "Справочник по модулям службы хранилища Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: b94c6fbb50e656e0dcc542236afe791c7ddc9be4
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-storage-modules-for-nodejs"></a>Модули службы хранилища Azure для Node.js

Используете модуль клиента службы хранилища Azure для выполнения следующих задач:

- Чтение и запись объектов и файлов из [хранилища BLOB-объектов Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage).
- Отправка и получение сообщений между подключенными к облаку приложениями с помощью [хранилища очередей Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues).
- Чтение и запись больших объемов структурированных данных с помощью [хранилища таблиц Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage).

Модули управления позволяют создавать, обновлять и администрировать учетные записи службы хранилища Azure, а также запрашивать и повторно создавать ключи доступа в приложениях Node.js.

## <a name="client-package"></a>Пакет клиента

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm клиента службы хранилища Azure.

```bash
npm install azure-storage
```

### <a name="example"></a>Пример

Этот пример создает контейнер хранилища и отправляет в него локальный файл `data.txt`.

```javascript
const azure = require('azure-storage');
const blobService = azure.createBlobService(storageConnectionString);

const container = 'taskcontainer';
const task = 'taskblob';
const filename = 'data.txt';

blobService.createContainerIfNotExists(container, error => {
  if (error) return console.log(error);
  blobService.createBlockBlobFromLocalFile(
    container,
    task,
    filename,
    (error, result) => {
      if (error) return console.log(error);
      console.dir(result, { depth: null, colors: true });
    }
  );
});
```

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm 

Установите модуль npm управления службой хранилища Azure.

```bash
npm install azure-arm-storage
```

### <a name="example"></a>Пример

Этот пример отображает список учетных записей хранения.

```javascript
const msRestAzure = require('ms-rest-azure');
const storageManagementClient = require('azure-arm-storage');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new storageManagementClient(
      credentials,
      subscriptionId
    );
    return client.storageAccounts.list();
  })
  .then(accounts => console.dir(accounts, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Примеры

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
