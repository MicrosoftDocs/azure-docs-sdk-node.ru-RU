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
ms.openlocfilehash: 470124eb69a48486fa54be6628c028399f0c038e
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="60c7e-103">Модули Azure Site Recovery для Node.js</span><span class="sxs-lookup"><span data-stu-id="60c7e-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="60c7e-104">Служба Site Recovery позволяет автоматизировать репликацию виртуальных машин Azure между регионами, репликацию локальных виртуальных машин и физических серверов в Azure и репликацию локальных компьютеров во вторичный центр обработки данных.</span><span class="sxs-lookup"><span data-stu-id="60c7e-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="60c7e-105">Дополнительные сведения об [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="60c7e-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="60c7e-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="60c7e-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="60c7e-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="60c7e-107">Install the npm module</span></span>

<span data-ttu-id="60c7e-108">Установите модуль npm службы Azure Site Recovery.</span><span class="sxs-lookup"><span data-stu-id="60c7e-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="60c7e-109">Пример</span><span class="sxs-lookup"><span data-stu-id="60c7e-109">Example</span></span>

<span data-ttu-id="60c7e-110">Этот пример перечисляет службы Site Recovery в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="60c7e-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="60c7e-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="60c7e-111">Samples</span></span>

<span data-ttu-id="60c7e-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="60c7e-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
