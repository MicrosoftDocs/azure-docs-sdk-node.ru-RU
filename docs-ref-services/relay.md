---
title: Модули ретранслятора Azure для Node.js
description: Справочник по ретрансляторам Azure для Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: e0bb24ac422d71bd8c957e94cceffd57bf121e48
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51465998"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="24dff-103">Модули ретранслятора Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="24dff-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="24dff-104">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="24dff-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="24dff-105">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="24dff-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="24dff-106">См. дополнительные сведения о [ретрансляторе Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="24dff-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="24dff-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="24dff-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="24dff-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="24dff-108">Install the npm module</span></span>

<span data-ttu-id="24dff-109">Установите модуль npm ретранслятора Azure.</span><span class="sxs-lookup"><span data-stu-id="24dff-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="24dff-110">Пример</span><span class="sxs-lookup"><span data-stu-id="24dff-110">Example</span></span>

<span data-ttu-id="24dff-111">Этот пример выводит список пространств имен для клиента ретрансляции.</span><span class="sxs-lookup"><span data-stu-id="24dff-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="24dff-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="24dff-112">Samples</span></span>

<span data-ttu-id="24dff-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="24dff-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
