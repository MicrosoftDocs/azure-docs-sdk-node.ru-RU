---
title: "Модули Azure Monitor для Node.js"
description: "Справочник по модулям Azure Monitor для Node.js"
keywords: Azure,SDK,API,Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="2899e-104">Модули Azure Monitor для Node.js</span><span class="sxs-lookup"><span data-stu-id="2899e-104">Azure Monitor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2899e-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="2899e-105">Overview</span></span>
<span data-ttu-id="2899e-106">Облачные приложения являются сложными и содержат множество подвижных частей.</span><span class="sxs-lookup"><span data-stu-id="2899e-106">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="2899e-107">Мониторинг дает возможность отслеживать данные, чтобы обеспечить работоспособность приложения,</span><span class="sxs-lookup"><span data-stu-id="2899e-107">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="2899e-108">а также позволяет предотвратить потенциальные проблемы или устранить неполадки.</span><span class="sxs-lookup"><span data-stu-id="2899e-108">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="2899e-109">Кроме того, данные мониторинга можно использовать для получения подробных сведений о приложении.</span><span class="sxs-lookup"><span data-stu-id="2899e-109">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="2899e-110">Эти знания могут помочь повысить его производительность и улучшить возможности обслуживания, а также автоматизировать действия, которые в противном случае выполнялись бы вручную.</span><span class="sxs-lookup"><span data-stu-id="2899e-110">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="2899e-111">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="2899e-111">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="2899e-112">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="2899e-112">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="2899e-113">Пример</span><span class="sxs-lookup"><span data-stu-id="2899e-113">Example</span></span>

<span data-ttu-id="2899e-114">Этот пример кода выводит все правила генерации оповещений, связанные с группой ресурсов.</span><span class="sxs-lookup"><span data-stu-id="2899e-114">This code example prints all the alerting rules associated with a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a><span data-ttu-id="2899e-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="2899e-115">Samples</span></span>

<span data-ttu-id="2899e-116">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="2899e-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
