---
title: Модули концентратора событий Azure для Node.js
description: Справочник по модулям концентратора событий Azure для Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: ff167e911b68b82b880e792e7ff2649cbe5af342
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="77941-103">Модули концентратора событий Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="77941-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="77941-104">Концентраторы событий Azure — это высокомасштабируемая платформа потоковой передачи данных и служба потребления событий, принимающая и обрабатывающая миллионы событий в секунду.</span><span class="sxs-lookup"><span data-stu-id="77941-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="77941-105">Концентраторы событий могут обрабатывать и сохранять события, данные и телеметрию, созданные распределенным программным обеспечением и устройствами.</span><span class="sxs-lookup"><span data-stu-id="77941-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="77941-106">Данные, отправляемые в концентратор событий, можно преобразовывать и сохранять с помощью любого поставщика аналитики в реальном времени, а также с помощью адаптеров пакетной обработки или хранения.</span><span class="sxs-lookup"><span data-stu-id="77941-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="77941-107">Благодаря возможности публикации и подписки с низкой задержкой и с неограниченным масштабированием концентраторы событий становятся "трамплином" для больших объемов данных.</span><span class="sxs-lookup"><span data-stu-id="77941-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="77941-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="77941-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="77941-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="77941-109">Install the npm module</span></span> 

<span data-ttu-id="77941-110">Используйте npm для установки модулей концентратора событий Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="77941-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="77941-111">Пример</span><span class="sxs-lookup"><span data-stu-id="77941-111">Example</span></span>

<span data-ttu-id="77941-112">Этот пример извлекает сведения о существующем концентраторе событий.</span><span class="sxs-lookup"><span data-stu-id="77941-112">This example retrieves information about an existing event hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="77941-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="77941-113">Samples</span></span>

<span data-ttu-id="77941-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="77941-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
