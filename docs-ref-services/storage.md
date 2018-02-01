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
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="b8f28-103">Модули службы хранилища Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="b8f28-103">Azure Storage modules for Node.js</span></span>

<span data-ttu-id="b8f28-104">Используете модуль клиента службы хранилища Azure для выполнения следующих задач:</span><span class="sxs-lookup"><span data-stu-id="b8f28-104">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="b8f28-105">Чтение и запись объектов и файлов из [хранилища BLOB-объектов Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage).</span><span class="sxs-lookup"><span data-stu-id="b8f28-105">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="b8f28-106">Отправка и получение сообщений между подключенными к облаку приложениями с помощью [хранилища очередей Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="b8f28-106">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="b8f28-107">Чтение и запись больших объемов структурированных данных с помощью [хранилища таблиц Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage).</span><span class="sxs-lookup"><span data-stu-id="b8f28-107">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="b8f28-108">Модули управления позволяют создавать, обновлять и администрировать учетные записи службы хранилища Azure, а также запрашивать и повторно создавать ключи доступа в приложениях Node.js.</span><span class="sxs-lookup"><span data-stu-id="b8f28-108">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="b8f28-109">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="b8f28-109">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b8f28-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="b8f28-110">Install the npm module</span></span>

<span data-ttu-id="b8f28-111">Установите модуль npm клиента службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="b8f28-111">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="b8f28-112">Пример</span><span class="sxs-lookup"><span data-stu-id="b8f28-112">Example</span></span>

<span data-ttu-id="b8f28-113">Этот пример создает контейнер хранилища и отправляет в него локальный файл `data.txt`.</span><span class="sxs-lookup"><span data-stu-id="b8f28-113">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="b8f28-114">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="b8f28-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b8f28-115">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="b8f28-115">Install the npm module</span></span> 

<span data-ttu-id="b8f28-116">Установите модуль npm управления службой хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="b8f28-116">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="b8f28-117">Пример</span><span class="sxs-lookup"><span data-stu-id="b8f28-117">Example</span></span>

<span data-ttu-id="b8f28-118">Этот пример отображает список учетных записей хранения.</span><span class="sxs-lookup"><span data-stu-id="b8f28-118">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b8f28-119">Примеры</span><span class="sxs-lookup"><span data-stu-id="b8f28-119">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="b8f28-120">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="b8f28-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
