---
title: Модули служебной шины Azure для Node.js
description: Справочник по модулям служебной шины Azure для Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2018
ms.locfileid: "51053703"
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Модули служебной шины Azure для Node.js

Служебная шина Azure — это облачная платформа асинхронного обмена сообщениями, которая позволяет отправлять данные между несвязанными системами.

Дополнительные сведения о [служебной шине Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль служебной шины Azure для Node.js с помощью npm.

```bash
npm install azure-arm-sb
```

### <a name="example"></a>Пример

Этот пример создает клиент и выводит список всех пространств имен служебной шины Azure для Node.js, связанных с данной подпиской.

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
