---
title: Модули служебной шины Azure для Node.js
description: Справочник по модулям служебной шины Azure для Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "49761539"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="aa3ef-103">Модули служебной шины Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="aa3ef-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="aa3ef-104">Служебная шина Azure — это облачная платформа асинхронного обмена сообщениями, которая позволяет отправлять данные между несвязанными системами.</span><span class="sxs-lookup"><span data-stu-id="aa3ef-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="aa3ef-105">Дополнительные сведения о [служебной шине Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="aa3ef-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="aa3ef-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="aa3ef-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aa3ef-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="aa3ef-107">Install the npm module</span></span>

<span data-ttu-id="aa3ef-108">Установите модуль служебной шины Azure для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="aa3ef-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="aa3ef-109">Пример</span><span class="sxs-lookup"><span data-stu-id="aa3ef-109">Example</span></span>

<span data-ttu-id="aa3ef-110">Этот пример создает клиент и выводит список всех пространств имен служебной шины Azure для Node.js, связанных с данной подпиской.</span><span class="sxs-lookup"><span data-stu-id="aa3ef-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="aa3ef-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="aa3ef-111">Samples</span></span>

<span data-ttu-id="aa3ef-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="aa3ef-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
