---
title: "Модули Azure Backup для Node.js"
description: "Справочник по модулям Azure Backup для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 83ccd48d6f66c49ed6be837384a39cb32919b83c
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="84960-103">Модули Azure Backup для Node.js</span><span class="sxs-lookup"><span data-stu-id="84960-103">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="84960-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="84960-104">Overview</span></span>

<span data-ttu-id="84960-105">Служба архивации Azure — это служба на платформе Azure, используемая для резервного копирования (защиты) и восстановления данных в Microsoft Cloud.</span><span class="sxs-lookup"><span data-stu-id="84960-105">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="84960-106">Служба архивации Azure позволяет заменить существующее локальное или автономное решение для резервного копирования на надежное, безопасное и экономичное облачное решение.</span><span class="sxs-lookup"><span data-stu-id="84960-106">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="84960-107">Служба архивации Azure включает несколько компонентов, которые можно загрузить и установить на соответствующем компьютере, сервере или в облаке.</span><span class="sxs-lookup"><span data-stu-id="84960-107">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="84960-108">В зависимости от того, что вам нужно защитить, развертываются различные компоненты или агенты.</span><span class="sxs-lookup"><span data-stu-id="84960-108">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="84960-109">Все компоненты службы архивации Azure можно использовать для резервного копирования данных в хранилище служб восстановления Azure, независимо от того, защищаются ли локальные или облачные данные.</span><span class="sxs-lookup"><span data-stu-id="84960-109">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="84960-110">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="84960-110">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="84960-111">Установка модулей с помощью npm</span><span class="sxs-lookup"><span data-stu-id="84960-111">Install the modules with npm</span></span>

<span data-ttu-id="84960-112">Используйте npm для установки модулей Azure Backup для Node.js</span><span class="sxs-lookup"><span data-stu-id="84960-112">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="84960-113">Пример</span><span class="sxs-lookup"><span data-stu-id="84960-113">Example</span></span>

<span data-ttu-id="84960-114">Этот пример перечисляет задания восстановления для данного хранилища и группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="84960-114">This example lists the recovery jobs for a given vault and resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="84960-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="84960-115">Samples</span></span>

<span data-ttu-id="84960-116">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="84960-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
