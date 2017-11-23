---
title: "Модули служебной шины Azure для Node.js"
description: "Справочник по модулям служебной шины Azure для Node.js"
keywords: Azure,SDK,API,Service Bus, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="22253-104">Модули служебной шины Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="22253-104">Azure Service Bus Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="22253-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="22253-105">Overview</span></span>

<span data-ttu-id="22253-106">Служебная шина Azure — это облачная платформа асинхронного обмена сообщениями, которая позволяет отправлять данные между несвязанными системами.</span><span class="sxs-lookup"><span data-stu-id="22253-106">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="22253-107">Дополнительные сведения о [служебной шине Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="22253-107">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="22253-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="22253-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="22253-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="22253-109">Install the npm module</span></span>

<span data-ttu-id="22253-110">Установите модуль служебной шины Azure для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="22253-110">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="22253-111">Пример</span><span class="sxs-lookup"><span data-stu-id="22253-111">Example</span></span>

<span data-ttu-id="22253-112">Этот пример создает клиент и выводит список всех пространств имен служебной шины Azure для Node.js, связанных с данной подпиской.</span><span class="sxs-lookup"><span data-stu-id="22253-112">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a><span data-ttu-id="22253-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="22253-113">Samples</span></span>

<span data-ttu-id="22253-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="22253-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
