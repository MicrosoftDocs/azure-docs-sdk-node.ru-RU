---
title: "Модули DNS Azure для Node.js"
description: "Справочник по модулям DNS Azure для Node.js"
keywords: Azure,SDK,API,DNS, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 679c2d494b99244961f2fee61b0813c81eb8a8de
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-dns-modules-for-nodejs"></a>Модули DNS Azure для Node.js

## <a name="overview"></a>Обзор

Размещайте свои домены DNS в Azure с помощью Azure DNS. Управляйте DNS-записями с помощью тех же учетных данных, данных для выставления счетов и контракта на поддержку, которые вы используете в других службах Azure. Таким образом достигается безупречная интеграция служб на основе Azure с соответствующими обновлениями DNS и упрощается процесс сквозного развертывания.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm Azure DNS.

```bash
npm install azure-arm-dns
```

### <a name="example"></a>Пример

Этот пример перечисляет зоны управления DNS.

```javascript
const msRestAzure = require('ms-rest-azure');
const DNSManagement = require('azure-arm-dns');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DNSManagement(credentials, subscriptionId);
    return client.zones.list();
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
