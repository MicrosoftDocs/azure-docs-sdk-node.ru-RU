---
title: "Модули Поиска Azure для Node.js"
description: "Справочник по модулям Поиска Azure для Node.js"
keywords: Azure,SDK,API,Search, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a>Модули Поиска Azure для Node.js

## <a name="overview"></a>Обзор

Поиск Azure — это облачное решение (поиск как услуга), которое делегирует корпорации Майкрософт управление сервером и инфраструктурой. Вы получаете готовое к работе решение, которое можно заполнить своими данными и затем использовать для добавления поиска в свое приложение.

Дополнительные сведения о [Поиске Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm Поиска Azure.

```bash
npm install azure-arm-search
```

### <a name="example"></a>Пример

Этот пример создает новую службу поиска в Azure, а также выводит список ресурсов в группе ресурсов.

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
