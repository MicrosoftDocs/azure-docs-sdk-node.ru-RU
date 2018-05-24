---
title: Модули службы автоматизации Azure для Node.js
description: Справочник по модулям службы автоматизации Azure для Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 5efe0c0633313bcf489b05b8a54f71bba9a00da5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-automation-modules-for-nodejs"></a>Модули службы автоматизации Azure для Node.js

## <a name="overview"></a>Обзор

Служба автоматизации Azure позволяет пользователям автоматизировать стандартные задачи в облачной среде и среде предприятия. Такие задачи обычно выполняются вручную, занимают много времени, подвержены ошибкам и часто повторяются. Служба автоматизации экономит время и повышает надежность обычных административных задач и даже планирует их автоматическое выполнение через определенные интервалы. Можно автоматизировать процессы, используя модули Runbook, или автоматизировать управление конфигурацией, используя службу настройки требуемого состояния (DSC).

## <a name="management-package"></a>Пакет управления

### <a name="install-the-modules-with-npm"></a>Установка модулей с помощью npm

Установите модули службы автоматизации Azure для Node.js. с помощью npm.

```bash
npm install azure-arm-automation
```

### <a name="example"></a>Пример

Этот пример перечисляет учетные записи службы автоматизации.

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

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
