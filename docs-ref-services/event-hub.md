---
title: "Модули концентратора событий Azure для Node.js"
description: "Справочник по модулям концентратора событий Azure для Node.js"
keywords: Azure,SDK,API,Event Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="377cc-104">Модули концентратора событий Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="377cc-104">Azure Event Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="377cc-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="377cc-105">Overview</span></span>
<span data-ttu-id="377cc-106">Концентраторы событий Azure — это высокомасштабируемая платформа потоковой передачи данных и служба потребления событий, принимающая и обрабатывающая миллионы событий в секунду.</span><span class="sxs-lookup"><span data-stu-id="377cc-106">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="377cc-107">Концентраторы событий могут обрабатывать и сохранять события, данные и телеметрию, созданные распределенным программным обеспечением и устройствами.</span><span class="sxs-lookup"><span data-stu-id="377cc-107">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="377cc-108">Данные, отправляемые в концентратор событий, можно преобразовывать и сохранять с помощью любого поставщика аналитики в реальном времени, а также с помощью адаптеров пакетной обработки или хранения.</span><span class="sxs-lookup"><span data-stu-id="377cc-108">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="377cc-109">Благодаря возможности публикации и подписки с низкой задержкой и с неограниченным масштабированием концентраторы событий становятся "трамплином" для больших объемов данных.</span><span class="sxs-lookup"><span data-stu-id="377cc-109">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="377cc-110">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="377cc-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="377cc-111">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="377cc-111">Install the npm module</span></span> 

<span data-ttu-id="377cc-112">Используйте npm для установки модулей концентратора событий Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="377cc-112">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="377cc-113">Пример</span><span class="sxs-lookup"><span data-stu-id="377cc-113">Example</span></span>

<span data-ttu-id="377cc-114">Этот пример извлекает сведения о существующем концентраторе событий.</span><span class="sxs-lookup"><span data-stu-id="377cc-114">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="377cc-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="377cc-115">Samples</span></span>

<span data-ttu-id="377cc-116">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="377cc-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
