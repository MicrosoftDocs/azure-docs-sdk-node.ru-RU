---
title: "Модули виртуальных машин Azure для Node.js"
description: "Справочник по модулям виртуальных машин Azure для Node.js"
keywords: Azure, Node, SDK, API, virtual machine, vm, nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a>Модули виртуальных машин Azure для Node.js

## <a name="overview"></a>Обзор

Определите, настройте и разверните новые виртуальные машины Windows и Linux и масштабируемые наборы виртуальных машин из кода с помощью модулей управления Azure для Node.js. С помощью этих модулей можно запускать и останавливать существующие виртуальные машины, а также подключать и отключать диски остановленной виртуальной машины в подписке Azure.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm служб вычислений Azure.

```bash
npm install azure-arm-compute
```   

### <a name="example"></a>Пример

Следующий пример показывает, как войти в Azure, создать клиент управления и перечислить все образы виртуальных машин для указанного расположения, издателя, предложения и SKU.

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Примеры

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
