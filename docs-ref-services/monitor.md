---
title: Модули Azure Monitor для Node.js
description: Справочник по модулям Azure Monitor для Node.js
author: rbouche
ms.author: robb
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8a9411b7979f3130a1aa24fd2a0b294fc7f67718
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-monitor-modules-for-nodejs"></a><span data-ttu-id="10d9b-103">Модули Azure Monitor для Node.js</span><span class="sxs-lookup"><span data-stu-id="10d9b-103">Azure Monitor modules for Node.js</span></span>

<span data-ttu-id="10d9b-104">Облачные приложения являются сложными и содержат множество подвижных частей.</span><span class="sxs-lookup"><span data-stu-id="10d9b-104">Cloud applications are complex with many moving parts.</span></span> <span data-ttu-id="10d9b-105">Мониторинг дает возможность отслеживать данные, чтобы обеспечить работоспособность приложения,</span><span class="sxs-lookup"><span data-stu-id="10d9b-105">Monitoring provides data to ensure that your application stays up and running in a healthy state.</span></span> <span data-ttu-id="10d9b-106">а также позволяет предотвратить потенциальные проблемы или устранить неполадки.</span><span class="sxs-lookup"><span data-stu-id="10d9b-106">It also helps you to stave off potential problems or troubleshoot past ones.</span></span> <span data-ttu-id="10d9b-107">Кроме того, данные мониторинга можно использовать для получения подробных сведений о приложении.</span><span class="sxs-lookup"><span data-stu-id="10d9b-107">In addition, you can use monitoring data to gain deep insights about your application.</span></span> <span data-ttu-id="10d9b-108">Эти знания могут помочь повысить его производительность и улучшить возможности обслуживания, а также автоматизировать действия, которые в противном случае выполнялись бы вручную.</span><span class="sxs-lookup"><span data-stu-id="10d9b-108">That knowledge can help you to improve application performance or maintainability, or automate actions that would otherwise require manual intervention.</span></span>

## <a name="management-package"></a><span data-ttu-id="10d9b-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="10d9b-109">Management Package</span></span>

### <a name="install-npm-module"></a><span data-ttu-id="10d9b-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="10d9b-110">Install npm module</span></span>

```bash
npm install azure-arm-monitor
```

### <a name="example"></a><span data-ttu-id="10d9b-111">Пример</span><span class="sxs-lookup"><span data-stu-id="10d9b-111">Example</span></span>

<span data-ttu-id="10d9b-112">Этот пример кода выводит все правила генерации оповещений, связанные с группой ресурсов.</span><span class="sxs-lookup"><span data-stu-id="10d9b-112">This code example prints all the alerting rules associated with a resource group.</span></span>

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

### <a name="samples"></a><span data-ttu-id="10d9b-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="10d9b-113">Samples</span></span>

<span data-ttu-id="10d9b-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="10d9b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
