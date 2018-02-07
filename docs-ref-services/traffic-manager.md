---
title: "Модули диспетчера трафика Azure для Node.js"
description: "Справочник по модулям диспетчера трафика Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: cf0834a0eadc67868efb165d60d39c681d4435eb
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Модули диспетчера трафика Azure для Node.js

## <a name="overview"></a>Обзор

Диспетчер трафика Microsoft Azure позволяет управлять распределением пользовательского трафика между конечными точками службы в разных центрах обработки данных. К конечным точкам службы, поддерживаемым диспетчером трафика Azure, относятся виртуальные машины, веб-приложения и облачные службы Azure. Можно также использовать диспетчер трафика Azure для внешних конечных точек, не относящихся к среде Azure.

См. дополнительные сведения о [диспетчере трафика Azure](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm диспетчера трафика Azure.

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>Пример

Этот пример перечисляет все диспетчеры трафика для данной группы ресурсов.

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
