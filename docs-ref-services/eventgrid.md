---
title: Библиотеки службы "Сетка событий Azure" для Node.js
description: Справочник по библиотекам службы "Сетка событий Azure" для Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52040049"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="3b06e-103">Библиотеки службы "Сетка событий Azure" для Node.js</span><span class="sxs-lookup"><span data-stu-id="3b06e-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="3b06e-104">Создавайте управляемые событиями приложения, которые прослушивают события от служб Azure и пользовательских источников и реагируют на них, с помощью службы "Сетка событий Azure" и простых средств обработки событий на основе HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b06e-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="3b06e-105">См. дополнительные сведения о [службе "Сетка событий Azure"](/azure/event-grid/overview) и начните работу с помощью [краткого руководства по событиям хранилища BLOB-объектов Azure](/azure/storage/blobs/storage-blob-event-quickstart).</span><span class="sxs-lookup"><span data-stu-id="3b06e-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="3b06e-106">Пакет SDK для публикации</span><span class="sxs-lookup"><span data-stu-id="3b06e-106">Publish SDK</span></span>

<span data-ttu-id="3b06e-107">Создавайте события, выполняйте аутентификацию и публикацию в разделы с помощью пакета SDK для публикации службы "Сетка событий Azure".</span><span class="sxs-lookup"><span data-stu-id="3b06e-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="3b06e-108">Установка</span><span class="sxs-lookup"><span data-stu-id="3b06e-108">Installation</span></span>

<span data-ttu-id="3b06e-109">Добавьте модуль в проект с помощью npm:</span><span class="sxs-lookup"><span data-stu-id="3b06e-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="3b06e-110">Пример кода</span><span class="sxs-lookup"><span data-stu-id="3b06e-110">Example code</span></span>

<span data-ttu-id="3b06e-111">Следующий фрагмент кода публикует событие макета в раздел службы "Сетка событий".</span><span class="sxs-lookup"><span data-stu-id="3b06e-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="3b06e-112">Ключи доступа для конечной точки и раздела можно получить на портале Azure или с помощью Azure CLI:</span><span class="sxs-lookup"><span data-stu-id="3b06e-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

<span data-ttu-id="3b06e-113">В этом примере показано, как обрабатывать событие из службы хранилища Azure:</span><span class="sxs-lookup"><span data-stu-id="3b06e-113">This sample shows how to handle an event from Azure Storage:</span></span>

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b06e-114">Обзор клиентских API-интерфейсов</span><span class="sxs-lookup"><span data-stu-id="3b06e-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="3b06e-115">Пакет SDK для управления</span><span class="sxs-lookup"><span data-stu-id="3b06e-115">Management SDK</span></span>

<span data-ttu-id="3b06e-116">Создавайте, обновляйте и удаляйте экземпляры, разделы и подписки службы "Сетка событий" с помощью пакета SDK для управления.</span><span class="sxs-lookup"><span data-stu-id="3b06e-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="3b06e-117">Установка</span><span class="sxs-lookup"><span data-stu-id="3b06e-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="3b06e-118">Пример кода</span><span class="sxs-lookup"><span data-stu-id="3b06e-118">Example code</span></span>

<span data-ttu-id="3b06e-119">Следующий код создает раздел `topic1` службы "Сетка событий" и возвращает ключи доступа, связанные с созданным разделом.</span><span class="sxs-lookup"><span data-stu-id="3b06e-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b06e-120">Обзор API-интерфейсов управления</span><span class="sxs-lookup"><span data-stu-id="3b06e-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="3b06e-121">Подробнее</span><span class="sxs-lookup"><span data-stu-id="3b06e-121">Learn more</span></span>

- [<span data-ttu-id="3b06e-122">Получение событий с помощью пакета SDK службы "Сетка событий"</span><span class="sxs-lookup"><span data-stu-id="3b06e-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)
