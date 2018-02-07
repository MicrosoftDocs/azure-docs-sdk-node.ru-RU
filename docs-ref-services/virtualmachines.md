---
title: "Использование модулей виртуальных машин для Node.js в Azure"
description: "Справочное руководство по модулям виртуальных машин Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
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

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
