---
title: "Модули службы хранилища Azure для Node.js"
description: "Справочник по модулям службы хранилища Azure для Node.js"
keywords: Azure, Node, SDK, API, Storage, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: storage
ms.openlocfilehash: 61d3f3bb49d10e63a353c474067a155223bb6c76
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-storage-modules-for-nodejs"></a><span data-ttu-id="919ce-104">Модули службы хранилища Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="919ce-104">Azure Storage modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="919ce-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="919ce-105">Overview</span></span>

<span data-ttu-id="919ce-106">Используете модуль клиента службы хранилища Azure для выполнения следующих задач:</span><span class="sxs-lookup"><span data-stu-id="919ce-106">Use the Azure Storage client module to:</span></span>

- <span data-ttu-id="919ce-107">Чтение и запись объектов и файлов из [хранилища BLOB-объектов Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage).</span><span class="sxs-lookup"><span data-stu-id="919ce-107">Read and write objects and files from [Azure Blob storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-blob-storage)</span></span>
- <span data-ttu-id="919ce-108">Отправка и получение сообщений между подключенными к облаку приложениями с помощью [хранилища очередей Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="919ce-108">Send and receive messages between cloud-connected applications with [Azure Queue storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-queues)</span></span>
- <span data-ttu-id="919ce-109">Чтение и запись больших объемов структурированных данных с помощью [хранилища таблиц Azure](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage).</span><span class="sxs-lookup"><span data-stu-id="919ce-109">Read and write large structured data with [Azure Table storage](https://docs.microsoft.com/azure/storage/storage-nodejs-how-to-use-table-storage)</span></span>

<span data-ttu-id="919ce-110">Модули управления позволяют создавать, обновлять и администрировать учетные записи службы хранилища Azure, а также запрашивать и повторно создавать ключи доступа в приложениях Node.js.</span><span class="sxs-lookup"><span data-stu-id="919ce-110">Create, update, and manage Azure Storage accounts and query and regenerate access keys from your Node.js apps with the management modules.</span></span>

## <a name="client-package"></a><span data-ttu-id="919ce-111">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="919ce-111">Client Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="919ce-112">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="919ce-112">Install the npm module</span></span>

<span data-ttu-id="919ce-113">Установите модуль npm клиента службы хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="919ce-113">Install the Azure storage client npm module</span></span>

```bash
npm install azure-storage
```

### <a name="example"></a><span data-ttu-id="919ce-114">Пример</span><span class="sxs-lookup"><span data-stu-id="919ce-114">Example</span></span>

<span data-ttu-id="919ce-115">Этот пример создает контейнер хранилища и отправляет в него локальный файл `data.txt`.</span><span class="sxs-lookup"><span data-stu-id="919ce-115">This example create a storage container and uploads a local file `data.txt` to it.</span></span>

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

## <a name="management-package"></a><span data-ttu-id="919ce-116">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="919ce-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="919ce-117">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="919ce-117">Install the npm module</span></span> 

<span data-ttu-id="919ce-118">Установите модуль npm управления службой хранилища Azure.</span><span class="sxs-lookup"><span data-stu-id="919ce-118">Install the Azure storage management npm module</span></span>

```bash
npm install azure-arm-storage
```

### <a name="example"></a><span data-ttu-id="919ce-119">Пример</span><span class="sxs-lookup"><span data-stu-id="919ce-119">Example</span></span>

<span data-ttu-id="919ce-120">Этот пример отображает список учетных записей хранения.</span><span class="sxs-lookup"><span data-stu-id="919ce-120">This example list the storage accounts.</span></span>

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

## <a name="samples"></a><span data-ttu-id="919ce-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="919ce-121">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/storage-samples.md)]

<span data-ttu-id="919ce-122">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="919ce-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
