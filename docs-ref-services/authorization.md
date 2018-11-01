---
title: Модули авторизации Azure для Node.js
description: Справочник по модулям авторизации Azure для Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Authorization
ms.openlocfilehash: 0b0ecd088d8b7728e56f352597e2db038678945f
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50340022"
---
# <a name="azure-authorization-modules-for-nodejs"></a><span data-ttu-id="43f46-103">Модули авторизации Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="43f46-103">Azure Authorization modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="43f46-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="43f46-104">Overview</span></span>

<span data-ttu-id="43f46-105">Проверка подлинности или авторизация службы приложений Azure — это функция, которая без изменений кода в серверной части приложения позволяет приложению выполнять вход пользователей.</span><span class="sxs-lookup"><span data-stu-id="43f46-105">Azure App Service Authentication / Authorization is a feature that provides a way for your application to sign in users so that code doesn't have to be changed on the app backend.</span></span> <span data-ttu-id="43f46-106">Авторизация позволяет легко защитить приложение и работать с данными пользователей.</span><span class="sxs-lookup"><span data-stu-id="43f46-106">Authorization provides an easy way to protect your application and work with per-user data.</span></span>

## <a name="management-package"></a><span data-ttu-id="43f46-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="43f46-107">Management package</span></span>

<span data-ttu-id="43f46-108">Установите модули авторизации Azure для Node.js. с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="43f46-108">Use npm to install the Azure Authorization modules for Node.js</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="43f46-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="43f46-109">Install the npm module</span></span>

<span data-ttu-id="43f46-110">Установите модуль npm авторизации Azure.</span><span class="sxs-lookup"><span data-stu-id="43f46-110">Install the Azure authorization npm module</span></span>

```bash
npm install azure-arm-authorization
```

### <a name="example"></a><span data-ttu-id="43f46-111">Пример</span><span class="sxs-lookup"><span data-stu-id="43f46-111">Example</span></span>

<span data-ttu-id="43f46-112">Этот пример перечисляет все назначения ролей в запрошенной группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="43f46-112">This example lists all role assignments for the requested resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="43f46-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="43f46-113">Samples</span></span>

<span data-ttu-id="43f46-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="43f46-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
