---
title: Модули Azure Data Lake Store для Node.js
description: Справочник по модулям Azure Data Lake Store для Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: da7e71a9ee1f6936924b1ec966b441756e9b0dfe
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2018
ms.locfileid: "51185143"
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a>Модули Azure Data Lake Store для Node.js

Хранилище озера данных Azure — это крупномасштабный репозиторий корпоративного уровня для рабочих нагрузок анализа больших данных. Azure Data Lake позволяет сохранять данные с любым размером, типом и скоростью приема в одном месте для эксплуатационной и исследовательской аналитики.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модули Azure Data Lake Store для Node.js с помощью npm.

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a>Пример

С помощью этого примера можно получить список всех учетных записей Data Lake Store в рамках определенной подписки Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
