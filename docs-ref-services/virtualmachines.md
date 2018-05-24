---
title: Использование модулей виртуальных машин для Node.js в Azure
description: Справочное руководство по модулям виртуальных машин Azure для Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
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
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a>Примеры

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
