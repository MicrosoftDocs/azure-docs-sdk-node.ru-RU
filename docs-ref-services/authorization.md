---
title: "Модули авторизации Azure для Node.js"
description: "Справочник по модулям авторизации Azure для Node.js"
keywords: Azure,SDK,API,Authorization, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: de843bf1afed77afdb9bde035962a1c151d9c1bb
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="58d08-104">Модули авторизации Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="58d08-104">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="58d08-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="58d08-105">Overview</span></span>

<span data-ttu-id="58d08-106">Проверка подлинности или авторизация службы приложений Azure — это функция, которая без изменений кода в серверной части приложения позволяет приложению выполнять вход пользователей.</span><span class="sxs-lookup"><span data-stu-id="58d08-106">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="58d08-107">Авторизация позволяет легко защитить приложение и работать с данными пользователей.</span><span class="sxs-lookup"><span data-stu-id="58d08-107">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="58d08-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="58d08-108">Management package</span></span>

<span data-ttu-id="58d08-109">Установите модули авторизации Azure для Node.js. с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="58d08-109">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="58d08-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="58d08-110">Install the npm module</span></span>

<span data-ttu-id="58d08-111">Установите модуль npm авторизации Azure.</span><span class="sxs-lookup"><span data-stu-id="58d08-111">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="58d08-112">Пример</span><span class="sxs-lookup"><span data-stu-id="58d08-112">Example</span></span>

<span data-ttu-id="58d08-113">Этот пример перечисляет все назначения ролей в запрошенной группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="58d08-113">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="58d08-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="58d08-114">Samples</span></span>

<span data-ttu-id="58d08-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="58d08-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
