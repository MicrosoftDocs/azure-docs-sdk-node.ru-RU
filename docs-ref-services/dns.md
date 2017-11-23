---
title: "Модули DNS Azure для Node.js"
description: "Справочник по модулям DNS Azure для Node.js"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="a731a-104">Модули DNS Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="a731a-104">Azure DNS modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a731a-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="a731a-105">Overview</span></span>

<span data-ttu-id="a731a-106">Размещайте свои домены DNS в Azure с помощью Azure DNS.</span><span class="sxs-lookup"><span data-stu-id="a731a-106">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="a731a-107">Управляйте DNS-записями с помощью тех же учетных данных, данных для выставления счетов и контракта на поддержку, которые вы используете в других службах Azure.</span><span class="sxs-lookup"><span data-stu-id="a731a-107">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="a731a-108">Таким образом достигается безупречная интеграция служб на основе Azure с соответствующими обновлениями DNS и упрощается процесс сквозного развертывания.</span><span class="sxs-lookup"><span data-stu-id="a731a-108">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="a731a-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="a731a-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a731a-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="a731a-110">Install the npm module</span></span>

<span data-ttu-id="a731a-111">Установите модуль npm Azure DNS.</span><span class="sxs-lookup"><span data-stu-id="a731a-111">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="a731a-112">Пример</span><span class="sxs-lookup"><span data-stu-id="a731a-112">Example</span></span>

<span data-ttu-id="a731a-113">Этот пример перечисляет зоны управления DNS.</span><span class="sxs-lookup"><span data-stu-id="a731a-113">This example lists the DNS Management zones.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="a731a-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="a731a-114">Samples</span></span>

<span data-ttu-id="a731a-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="a731a-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
