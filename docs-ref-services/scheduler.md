---
title: "Модули планировщика Azure для Node.js"
description: "Справочник по модулям планировщика Azure для Node.js"
keywords: Azure,SDK,API,Scheduler, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="4a113-104">Модули планировщика Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="4a113-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4a113-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="4a113-105">Overview</span></span>

<span data-ttu-id="4a113-106">Планировщик Azure создает, хранит и вызывает запланированную работу через протоколы HTTP, HTTPS, очередь хранилища или [служебную шину Azure](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="4a113-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="4a113-107">Дополнительные сведения о [планировщике Azure](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="4a113-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="4a113-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="4a113-108">Management package</span></span>

<span data-ttu-id="4a113-109">Создание, сопровождение и вызов запланированной работы через различные коммуникационные каналы с помощью API управления.</span><span class="sxs-lookup"><span data-stu-id="4a113-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4a113-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="4a113-110">Install the npm module</span></span>

<span data-ttu-id="4a113-111">Установка модуля npm планировщика Azure</span><span class="sxs-lookup"><span data-stu-id="4a113-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="4a113-112">Пример</span><span class="sxs-lookup"><span data-stu-id="4a113-112">Example</span></span>

<span data-ttu-id="4a113-113">Это примеры содержат текущие планировщики.</span><span class="sxs-lookup"><span data-stu-id="4a113-113">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="4a113-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="4a113-114">Samples</span></span>

<span data-ttu-id="4a113-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="4a113-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
