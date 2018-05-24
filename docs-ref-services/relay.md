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
ms.openlocfilehash: 1f9b4263b8ffae78fcf9f35b8ef0160095059693
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="466a3-103">Модули ретранслятора Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="466a3-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="466a3-104">Служба ретранслятора Azure помогает создавать гибридные приложения и позволяет безопасно предоставлять в общедоступном облаке службы, используемые в корпоративной сети предприятия. Для этого вам не нужно открывать подключения брандмауэра или вносить значительные изменения в инфраструктуру корпоративной сети.</span><span class="sxs-lookup"><span data-stu-id="466a3-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="466a3-105">Ретранслятор поддерживает множество различных транспортных протоколов и стандартов веб-служб.</span><span class="sxs-lookup"><span data-stu-id="466a3-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="466a3-106">См. дополнительные сведения о [ретрансляторе Azure](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="466a3-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="466a3-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="466a3-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="466a3-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="466a3-108">Install the npm module</span></span>

<span data-ttu-id="466a3-109">Установите модуль npm ретранслятора Azure.</span><span class="sxs-lookup"><span data-stu-id="466a3-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="466a3-110">Пример</span><span class="sxs-lookup"><span data-stu-id="466a3-110">Example</span></span>

<span data-ttu-id="466a3-111">Этот пример выводит список пространств имен для клиента ретрансляции.</span><span class="sxs-lookup"><span data-stu-id="466a3-111">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="466a3-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="466a3-112">Samples</span></span>

<span data-ttu-id="466a3-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="466a3-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
