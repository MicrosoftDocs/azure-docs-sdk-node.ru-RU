---
title: Модули DNS Azure для Node.js
description: Справочник по модулям DNS Azure для Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 93eec1890fc15d19c0545086a53b751d0886988a
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51494868"
---
# <a name="azure-dns-modules-for-nodejs"></a><span data-ttu-id="60c10-103">Модули DNS Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="60c10-103">Azure DNS modules for Node.js</span></span>

<span data-ttu-id="60c10-104">Размещайте свои домены DNS в Azure с помощью Azure DNS.</span><span class="sxs-lookup"><span data-stu-id="60c10-104">Use Azure DNS to host your Domain Name System (DNS) domains in Azure.</span></span> <span data-ttu-id="60c10-105">Управляйте DNS-записями с помощью тех же учетных данных, данных для выставления счетов и контракта на поддержку, которые вы используете в других службах Azure.</span><span class="sxs-lookup"><span data-stu-id="60c10-105">Manage your DNS records using the same credentials and billing and support contract as your other Azure services.</span></span> <span data-ttu-id="60c10-106">Таким образом достигается безупречная интеграция служб на основе Azure с соответствующими обновлениями DNS и упрощается процесс сквозного развертывания.</span><span class="sxs-lookup"><span data-stu-id="60c10-106">Seamlessly integrate Azure-based services with corresponding DNS updates and streamline your end-to-end deployment process.</span></span>

## <a name="management-package"></a><span data-ttu-id="60c10-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="60c10-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="60c10-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="60c10-108">Install the npm module</span></span>

<span data-ttu-id="60c10-109">Установите модуль npm Azure DNS.</span><span class="sxs-lookup"><span data-stu-id="60c10-109">Install the Azure DNS npm module</span></span>

```bash
npm install azure-arm-dns
```

### <a name="example"></a><span data-ttu-id="60c10-110">Пример</span><span class="sxs-lookup"><span data-stu-id="60c10-110">Example</span></span>

<span data-ttu-id="60c10-111">Этот пример перечисляет зоны управления DNS.</span><span class="sxs-lookup"><span data-stu-id="60c10-111">This example lists the DNS Management zones.</span></span>

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

## <a name="samples"></a><span data-ttu-id="60c10-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="60c10-112">Samples</span></span>

<span data-ttu-id="60c10-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="60c10-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
