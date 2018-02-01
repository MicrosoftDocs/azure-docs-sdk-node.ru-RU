---
title: "Модули планировщика Azure для Node.js"
description: "Справочник по модулям планировщика Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 539337abd2fff3830cb022a49aff374e877a08ee
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="bd5a8-103">Модули планировщика Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="bd5a8-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="bd5a8-104">Планировщик Azure создает, хранит и вызывает запланированную работу через протоколы HTTP, HTTPS, очередь хранилища или [служебную шину Azure](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="bd5a8-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="bd5a8-105">Дополнительные сведения о [планировщике Azure](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="bd5a8-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="bd5a8-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="bd5a8-106">Management package</span></span>

<span data-ttu-id="bd5a8-107">Создание, сопровождение и вызов запланированной работы через различные коммуникационные каналы с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bd5a8-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="bd5a8-108">Install the npm module</span></span>

<span data-ttu-id="bd5a8-109">Установка модуля npm планировщика Azure</span><span class="sxs-lookup"><span data-stu-id="bd5a8-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="bd5a8-110">Пример</span><span class="sxs-lookup"><span data-stu-id="bd5a8-110">Example</span></span>

<span data-ttu-id="bd5a8-111">Это примеры содержат текущие планировщики.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-111">This examples lists the current schedulers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a><span data-ttu-id="bd5a8-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="bd5a8-112">Samples</span></span>

<span data-ttu-id="bd5a8-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="bd5a8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
