---
title: Модули центров уведомлений Azure для Node.js
description: Справочник по модулям центров уведомлений Azure для Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52094388"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Модули центров уведомлений Azure для Node.js

Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ. Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.

Центры уведомлений отлично походят как для отдельных потребителей, так и для крупных предприятий. Вот некоторые примеры задач, для которых наши клиенты применяют Центры уведомлений:
- отправка (с низкой задержкой) уведомлений об экстренных новостях миллионам пользователей;
- отправка купонов целевым сегментам пользователей с учетом их местоположения;
- отправка уведомлений о событиях пользователям или группам пользователей в информационных, спортивных, финансовых и игровых приложениях;
- передача в приложения рекламного содержимого, которое помогает привлекать клиентов и продавать товары;
- уведомление пользователей о корпоративных событиях, новостях и рабочих задачах;
- отправка кодов для многофакторной идентификации.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль центров уведомлений Azure 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>Пример

Этот пример формирует список всех центров уведомлений.

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a>Примеры

* [Руководство по мобильным приложениям службы для серверной части .NET](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Отправка твита об аномальных вибрациях, обнаруженных службами Интернета вещей Azure на основе данных устройства Intel Edison с Node.js)

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
