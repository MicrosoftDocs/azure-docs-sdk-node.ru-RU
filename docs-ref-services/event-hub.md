---
title: "Модули концентратора событий Azure для Node.js"
description: "Справочник по модулям концентратора событий Azure для Node.js"
keywords: Azure,SDK,API,Event Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 5ac6fc3f86419602756c354393078b399a6cba23
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-event-hub-modules-for-nodejs"></a>Модули концентратора событий Azure для Node.js

## <a name="overview"></a>Обзор
Концентраторы событий Azure — это высокомасштабируемая платформа потоковой передачи данных и служба потребления событий, принимающая и обрабатывающая миллионы событий в секунду. Концентраторы событий могут обрабатывать и сохранять события, данные и телеметрию, созданные распределенным программным обеспечением и устройствами. Данные, отправляемые в концентратор событий, можно преобразовывать и сохранять с помощью любого поставщика аналитики в реальном времени, а также с помощью адаптеров пакетной обработки или хранения. Благодаря возможности публикации и подписки с низкой задержкой и с неограниченным масштабированием концентраторы событий становятся "трамплином" для больших объемов данных.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm 

Используйте npm для установки модулей концентратора событий Azure для Node.js

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a>Пример

Этот пример извлекает сведения о существующем концентраторе событий.

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
