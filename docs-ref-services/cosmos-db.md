---
title: "Модули Azure Cosmos DB для Node.js"
description: "Справочник по модулям Azure Cosmos DB для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cosmos DB
ms.openlocfilehash: 575c276ec755dabe8e7b9ed76ba98ef8073c4f1b
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cosmos-db-modules-for-nodejs"></a>Модули Azure Cosmos DB для Node.js

Azure Cosmos DB — это глобально распределенная многомодельная база данных Майкрософт. Azure Cosmos DB позволяет гибко и независимо масштабировать пропускную способность и ресурсы хранилища в любом количестве регионов Azure. Она гарантирует пропускную способность, задержку, доступность и согласованность в соответствии с соглашениями об уровне обслуживания (SLA), которые зачастую не могут предложить другие службы баз данных.

Azure Cosmos DB содержит оптимизированное для записи, независящее от схемы ядро СУБД с регулировкой ресурсов, которое изначально поддерживает несколько моделей данных: модели данных документа, пар "ключ — значение", графы и модели данных столбцов. Она также поддерживает многие интерфейсы API для доступа к данным, включая MongoDB, DocumentDB SQL, Gremlin (предварительная версия) и таблицы Azure (предварительная версия). Список поддерживаемых интерфейсов постоянно увеличивается.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm 

Установите модуль npm Azure Cosmos DB.

```bash
npm install azure-arm-documentdb
```

### <a name="example"></a>Пример

Этот пример перечисляет все учетные записи Cosmos DB.

```javascript
const msRestAzure = require('ms-rest-azure');
const documentDBManagementClient = require('azure-arm-documentdb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const documentDbClient = new documentDBManagementClient(credentials, subscriptionId);
  documentDbClient.databaseAccounts
    .list()
    .then(databaseAccounts => console.log('Retrieved database accounts: ', databaseAccounts));
});
```

## <a name="samples"></a>Примеры

* [Разработка приложения Node.js с помощью Azure Cosmos DB — DocumentDB](https://azure.microsoft.com/resources/samples/azure-cosmos-db-documentdb-nodejs-getting-started/)
* [Разработка приложения Node.js с помощью Azure Cosmos DB — Gremlin](https://azure.microsoft.com/resources/samples/azure-cosmos-db-graph-nodejs-getting-started/)

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
