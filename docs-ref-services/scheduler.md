---
title: Модули планировщика Azure для Node.js
description: Справочник по модулям планировщика Azure для Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50406480"
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Модули планировщика Azure для Node.js

Планировщик Azure создает, хранит и вызывает запланированную работу через протоколы HTTP, HTTPS, очередь хранилища или [служебную шину Azure](/azure/service-bus-messaging/service-bus-messaging-overview).

Дополнительные сведения о [планировщике Azure](/azure/scheduler/scheduler-intro).

## <a name="management-package"></a>Пакет управления

Создание, сопровождение и вызов запланированной работы через различные коммуникационные каналы с помощью API управления.

### <a name="install-the-npm-module"></a>Установка модуля npm

Установка модуля npm планировщика Azure

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>Пример

Это примеры содержат текущие планировщики.

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
