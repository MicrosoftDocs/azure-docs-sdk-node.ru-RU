---
title: "Модули ретранслятора Azure для Node.js"
description: "Справочник по ретрансляторам Azure для Node.js"
keywords: Azure,SDK,API,Relay, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="11e08-104">Модули ретранслятора Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="11e08-104">Azure Relay modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="11e08-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="11e08-105">Overview</span></span>

<span data-ttu-id="11e08-106">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="11e08-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="11e08-107">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="11e08-107">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="11e08-108">См. дополнительные сведения о [ретрансляторе Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="11e08-108">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="11e08-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="11e08-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="11e08-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="11e08-110">Install the npm module</span></span>

<span data-ttu-id="11e08-111">Установите модуль npm ретранслятора Azure.</span><span class="sxs-lookup"><span data-stu-id="11e08-111">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="11e08-112">Пример</span><span class="sxs-lookup"><span data-stu-id="11e08-112">Example</span></span>

<span data-ttu-id="11e08-113">Этот пример выводит список пространств имен для клиента ретрансляции.</span><span class="sxs-lookup"><span data-stu-id="11e08-113">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="11e08-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="11e08-114">Samples</span></span>

<span data-ttu-id="11e08-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="11e08-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
