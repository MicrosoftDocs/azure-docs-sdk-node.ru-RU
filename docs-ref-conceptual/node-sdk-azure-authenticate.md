---
title: "Аутентификация с использованием модулей управления Azure для Node.js"
description: "Аутентификация с помощью субъекта-службы в модулях управления Azure для Node.js"
author: craigshoemaker
manager: routlaw
ms.author: cshoe
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: c93e5205c43c78d1c9e94d59a362cda336cd8310
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="4d8b8-103">Аутентификация с использованием модулей Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="4d8b8-103">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="4d8b8-104">Все API-интерфейсы служб, для которых создаются экземпляры, должны пройти аутентификацию с использованием объекта `credentials`.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-104">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="4d8b8-105">Существует три способа аутентификации и создания необходимых учетных данных с использованием пакета Azure SDK для Node.js:</span><span class="sxs-lookup"><span data-stu-id="4d8b8-105">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="4d8b8-106">Обычная аутентификация</span><span class="sxs-lookup"><span data-stu-id="4d8b8-106">Basic authentication</span></span>
- <span data-ttu-id="4d8b8-107">Интерактивный вход</span><span class="sxs-lookup"><span data-stu-id="4d8b8-107">Interactive login</span></span>
- <span data-ttu-id="4d8b8-108">Проверка подлинности субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="4d8b8-108">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="4d8b8-109">Обычная аутентификация</span><span class="sxs-lookup"><span data-stu-id="4d8b8-109">Basic authentication</span></span>

<span data-ttu-id="4d8b8-110">Чтобы выполнить аутентификацию программными средствами с помощью учетных данных учетной записи Azure, используйте функцию `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-110">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="4d8b8-111">В следующем фрагменте кода JavaScript показано, как выполнять обычную аутентификацию с использованием учетных данных, которые хранятся как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-111">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a><span data-ttu-id="4d8b8-112">Интерактивный вход</span><span class="sxs-lookup"><span data-stu-id="4d8b8-112">Interactive login</span></span>

<span data-ttu-id="4d8b8-113">При интерактивном входе предоставляются ссылки и код, что позволяет пользователю выполнять аутентификацию в браузере.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-113">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="4d8b8-114">Применяйте этот метод, если в одном скрипте используется несколько учетных записей или если требуется вмешательство пользователя.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-114">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="4d8b8-115">Проверка подлинности субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="4d8b8-115">Service principal authentication</span></span>

<span data-ttu-id="4d8b8-116">[Интерактивный вход](#interactive-login) — самый простой способ аутентификации.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-116">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="4d8b8-117">Но при использовании пакета SDK для Node.js может потребоваться использовать обычную аутентификацию субъекта-службы, а не предоставлять учетные данные учетной записи.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-117">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="4d8b8-118">В руководстве по [созданию субъекта-службы Azure с помощью Node.js](./node-sdk-azure-authenticate-principal.md) описаны разные способы создания и использования субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="4d8b8-118">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 