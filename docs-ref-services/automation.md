---
title: "Модули службы автоматизации Azure для Node.js"
description: "Справочник по модулям службы автоматизации Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 09e9d2675d49b29881d332e7bbf251a5031e3483
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="9cd41-103">Модули службы автоматизации Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="9cd41-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9cd41-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="9cd41-104">Overview</span></span>

<span data-ttu-id="9cd41-105">Служба автоматизации Azure позволяет пользователям автоматизировать стандартные задачи в облачной среде и среде предприятия. Такие задачи обычно выполняются вручную, занимают много времени, подвержены ошибкам и часто повторяются.</span><span class="sxs-lookup"><span data-stu-id="9cd41-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="9cd41-106">Служба автоматизации экономит время и повышает надежность обычных административных задач и даже планирует их автоматическое выполнение через определенные интервалы.</span><span class="sxs-lookup"><span data-stu-id="9cd41-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="9cd41-107">Можно автоматизировать процессы, используя модули Runbook, или автоматизировать управление конфигурацией, используя службу настройки требуемого состояния (DSC).</span><span class="sxs-lookup"><span data-stu-id="9cd41-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="9cd41-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="9cd41-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="9cd41-109">Установка модулей с помощью npm</span><span class="sxs-lookup"><span data-stu-id="9cd41-109">Install the modules with npm</span></span>

<span data-ttu-id="9cd41-110">Установите модули службы автоматизации Azure для Node.js. с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="9cd41-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="9cd41-111">Пример</span><span class="sxs-lookup"><span data-stu-id="9cd41-111">Example</span></span>

<span data-ttu-id="9cd41-112">Этот пример перечисляет учетные записи службы автоматизации.</span><span class="sxs-lookup"><span data-stu-id="9cd41-112">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="9cd41-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="9cd41-113">Samples</span></span>

<span data-ttu-id="9cd41-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="9cd41-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
