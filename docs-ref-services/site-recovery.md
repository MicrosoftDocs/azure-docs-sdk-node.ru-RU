---
title: Модули Azure Site Recovery для Node.js
description: Справочник по модулям Azure Site Recovery для Node.js
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: f8cddf806b921d5445cd0757b64aeb0dc5df03cf
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52040179"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="2ecab-103">Модули Azure Site Recovery для Node.js</span><span class="sxs-lookup"><span data-stu-id="2ecab-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="2ecab-104">Служба Site Recovery позволяет автоматизировать репликацию виртуальных машин Azure между регионами, репликацию локальных виртуальных машин и физических серверов в Azure и репликацию локальных компьютеров во вторичный центр обработки данных.</span><span class="sxs-lookup"><span data-stu-id="2ecab-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="2ecab-105">Дополнительные сведения об [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="2ecab-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="2ecab-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="2ecab-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="2ecab-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="2ecab-107">Install the npm module</span></span>

<span data-ttu-id="2ecab-108">Установите модуль npm службы Azure Site Recovery.</span><span class="sxs-lookup"><span data-stu-id="2ecab-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="2ecab-109">Пример</span><span class="sxs-lookup"><span data-stu-id="2ecab-109">Example</span></span>

<span data-ttu-id="2ecab-110">Этот пример перечисляет службы Site Recovery в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="2ecab-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2ecab-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="2ecab-111">Samples</span></span>

<span data-ttu-id="2ecab-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="2ecab-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
