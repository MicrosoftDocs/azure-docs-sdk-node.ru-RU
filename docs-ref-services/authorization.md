---
title: "Модули авторизации Azure для Node.js"
description: "Справочник по модулям авторизации Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 6fbaaeba28cac81d360e93c5066791adfa51bcd5
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-authorization-modules-for-nodejs"></a>Модули авторизации Azure для Node.js

## <a name="overview"></a>Обзор

Проверка подлинности или авторизация службы приложений Azure — это функция, которая без изменений кода в серверной части приложения позволяет приложению выполнять вход пользователей. Авторизация позволяет легко защитить приложение и работать с данными пользователей.

## <a name="management-package"></a>Пакет управления

Установите модули авторизации Azure для Node.js. с помощью npm.

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm авторизации Azure.

```bash
npm install azure-arm-authorization
```

### <a name="example"></a>Пример

Этот пример перечисляет все назначения ролей в запрошенной группе ресурсов.

```javascript
const msRestAzure = require('ms-rest-azure');
const authorizationManagement = require('azure-arm-authorization');

const resourceGroup = 'resource-group-name';
const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
 const client = new authorizationManagement(credentials, subscriptionId);
 client.roleAssignments.listForResourceGroup(resourceGroupName).then(result => {
   console.log(result);
 });
});
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
