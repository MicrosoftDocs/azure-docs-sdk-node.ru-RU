---
title: "Модули Azure CDN для Node.js"
description: "Справочник по модулям Azure CDN для Node.js"
keywords: Azure,SDK,API,CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a>Модули Azure CDN для Node.js

## <a name="overview"></a>Обзор

Сеть доставки содержимого (CDN) Azure предлагает разработчикам глобальное решение по доставке содержимого, размещенного в Azure или любом другом расположении, по сети с высокой пропускной способностью. Используя CDN, вы можете кэшировать общедоступные объекты, загруженные из хранилища BLOB-объектов, веб-приложения, виртуальной машины, папки приложения или другого расположения HTTP или HTTPS. Кэш CDN может храниться в стратегически важных местах для обеспечения максимальной пропускной способности при доставке содержимого пользователям. CDN обычно используется для доставки статического содержимого, например изображений, таблиц стилей, документов, файлов, клиентских скриптов и HTML-страниц.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm Azure CDN.

```bash
npm install azure-arm-cdn
```

### <a name="example"></a>Пример

Этот пример перечисляет все профили CDN.

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
