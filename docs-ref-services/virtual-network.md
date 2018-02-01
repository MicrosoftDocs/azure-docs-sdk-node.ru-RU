---
title: "Модули виртуальной сети Azure для Node.js"
description: "Справочник по модулям виртуальной сети Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: f073c700c8df7f7aa05c93d725051d3a9976bebc
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Модули виртуальной сети Azure для Node.js

## <a name="overview"></a>Обзор

Служба виртуальной сети Azure позволяет безопасно подключать ресурсы Azure между собой с помощью виртуальных сетей. Виртуальная сеть — это представление вашей собственной сети в облаке. Это логическая изоляция облака Azure, выделенного для вашей подписки. Виртуальные сети можно также подключать к локальной сети.

Дополнительные сведения о [виртуальной сети Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm виртуальной сети Azure

```bash
npm install azure-arm-network
```

### <a name="example"></a>Пример

Этот пример извлекает и печатает список виртуальных сетей.

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
