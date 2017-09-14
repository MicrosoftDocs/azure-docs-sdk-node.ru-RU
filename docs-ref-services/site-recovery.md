---
title: "Модули Azure Site Recovery для Node.js"
description: "Справочник по модулям Azure Site Recovery для Node.js"
keywords: Azure,SDK,API,Site Recovery, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="fa078-104">Модули Azure Site Recovery для Node.js</span><span class="sxs-lookup"><span data-stu-id="fa078-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="fa078-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="fa078-105">Overview</span></span>

<span data-ttu-id="fa078-106">Служба Site Recovery позволяет автоматизировать репликацию виртуальных машин Azure между регионами, репликацию локальных виртуальных машин и физических серверов в Azure и репликацию локальных компьютеров во вторичный центр обработки данных.</span><span class="sxs-lookup"><span data-stu-id="fa078-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="fa078-107">Дополнительные сведения об [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="fa078-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="fa078-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="fa078-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="fa078-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="fa078-109">Install the npm module</span></span>

<span data-ttu-id="fa078-110">Установите модуль npm службы Azure Site Recovery.</span><span class="sxs-lookup"><span data-stu-id="fa078-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="fa078-111">Пример</span><span class="sxs-lookup"><span data-stu-id="fa078-111">Example</span></span>

<span data-ttu-id="fa078-112">Этот пример перечисляет службы Site Recovery в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fa078-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="fa078-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="fa078-113">Samples</span></span>

<span data-ttu-id="fa078-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="fa078-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
