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
# <a name="azure-monitor-modules-for-nodejs"></a>Модули Azure Monitor для Node.js

Облачные приложения являются сложными и содержат множество подвижных частей. Мониторинг дает возможность отслеживать данные, чтобы обеспечить работоспособность приложения, а также позволяет предотвратить потенциальные проблемы или устранить неполадки. Кроме того, данные мониторинга можно использовать для получения подробных сведений о приложении. Эти знания могут помочь повысить его производительность и улучшить возможности обслуживания, а также автоматизировать действия, которые в противном случае выполнялись бы вручную.

## <a name="management-package"></a>Пакет управления

### <a name="install-npm-module"></a>Установка модуля npm

```bash
npm install azure-arm-monitor
```

### <a name="example"></a>Пример

Этот пример кода выводит все правила генерации оповещений, связанные с группой ресурсов.

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

### <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
