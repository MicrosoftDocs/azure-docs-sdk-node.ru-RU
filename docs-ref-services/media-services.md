---
title: "Модули служб мультимедиа Azure для Node.js"
description: "Справочник по модулям служб мультимедиа Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 77a6716d4ef0d566690325a86e85d66c5ac234d6
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-media-services-modules-for-nodejs"></a>Модули служб мультимедиа Azure для Node.js

Службы мультимедиа Azure — это расширяемая облачная платформа, которая позволяет разработчикам создавать масштабируемые приложения для управления и доставки файлов мультимедиа. С помощью служб мультимедиа Azure можно безопасно передавать, сохранять, кодировать и упаковывать видео- или аудиосодержимое для потоковой трансляции разным клиентам (например, на ТВ, ПК и мобильные устройства) или для трансляции по требованию.

С помощью служб мультимедиа Azure вы можете:
- Создавать сквозные рабочие процессы, полностью использующие службы мультимедиа. 
- Использовать сторонние компоненты в качестве некоторых частей рабочего процесса. Например, можно выполнять кодирование с помощью стороннего кодировщика. А затем отправить, защитить, упаковать и доставить содержимое с использованием служб мультимедиа.
- Выполнять потоковую передачу содержимого динамически или доставлять содержимое по запросу. В этом разделе также есть ссылки на другие разделы.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установка модуля npm служб мультимедиа Azure

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a>Пример

Этот пример перечисляет все службы мультимедиа для группы ресурсов.

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
