---
title: Модули DNS Azure для Node.js
description: Справочник по модулям DNS Azure для Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DNS
ms.openlocfilehash: 610bc878acba978b7be25ea2caee4000cef3b452
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34262221"
---
# <a name="azure-dns-modules-for-nodejs"></a>Модули DNS Azure для Node.js

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
