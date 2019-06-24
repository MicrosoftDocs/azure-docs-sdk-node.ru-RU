---
title: Модули Azure Data Lake Analytics для Node.js
description: Справочник по модулям Azure Data Lake Analytics для Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 97a846d9970310931e05e681b23b5787c97260b6
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52045109"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Модули Azure Data Lake Analytics для Node.js

Azure Data Lake Analytics — это служба обработки заданий аналитики по запросу, которая позволяет упростить анализ больших данных. Вы можете сосредоточиться на создании, запуске заданий и управлении ими, а не на управлении распределенной инфраструктурой. Вместо развертывания и настройки оборудования вы пишете запросы для преобразования данных и получения ценных выводов. Служба аналитики способна мгновенно выполнять задания любого масштаба, для чего нужно указать необходимый объем ресурсов. Вы оплачиваете только время выполнения задания, что приводит к значительной экономии средств. Служба аналитики поддерживает Azure Active Directory, что позволяет управлять доступом и ролями, интегрированными с локальной системой идентификации. Служба также включает U-SQL — язык, который объединяет преимущества SQL с выразительностью пользовательского кода. Масштабируемая распределенная среда выполнения U-SQL позволяет эффективно анализировать данные в хранилище и на серверах SQL Server в Azure, в Базе данных SQL Azure и хранилище данных SQL Azure.

### <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модули Azure Data Lake Analytics для Node.js с помощью npm.

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>Пример

Этот пример перечисляет все учетные записи службы аналитики в данной подписке.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
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
