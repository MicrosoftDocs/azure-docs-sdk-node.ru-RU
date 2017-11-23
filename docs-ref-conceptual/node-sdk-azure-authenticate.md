---
title: "Аутентификация с использованием модулей управления Azure для Node.js"
description: "Аутентификация с помощью субъекта-службы в модулях управления Azure для Node.js"
keywords: Azure, Node, SDK, API, authentication, active directory, service principal
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a><span data-ttu-id="06efd-104">Аутентификация с использованием модулей Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="06efd-104">Authenticate with the Azure modules for Node.js</span></span> 

<span data-ttu-id="06efd-105">Все API-интерфейсы служб, для которых создаются экземпляры, должны пройти аутентификацию с использованием объекта `credentials`.</span><span class="sxs-lookup"><span data-stu-id="06efd-105">All service APIs require authentication via a `credentials` object when being instantiated.</span></span> <span data-ttu-id="06efd-106">Существует три способа аутентификации и создания необходимых учетных данных с использованием пакета Azure SDK для Node.js:</span><span class="sxs-lookup"><span data-stu-id="06efd-106">There are three ways of authenticating and creating the required credentials via the Azure SDK for Node.js:</span></span> 

- <span data-ttu-id="06efd-107">Обычная аутентификация</span><span class="sxs-lookup"><span data-stu-id="06efd-107">Basic authentication</span></span>
- <span data-ttu-id="06efd-108">Интерактивный вход</span><span class="sxs-lookup"><span data-stu-id="06efd-108">Interactive login</span></span>
- <span data-ttu-id="06efd-109">Проверка подлинности субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="06efd-109">Service principal authentication</span></span>

## <a name="basic-authentication"></a><span data-ttu-id="06efd-110">Обычная аутентификация</span><span class="sxs-lookup"><span data-stu-id="06efd-110">Basic authentication</span></span>

<span data-ttu-id="06efd-111">Чтобы выполнить аутентификацию программными средствами с помощью учетных данных учетной записи Azure, используйте функцию `loginWithUsernamePassword`.</span><span class="sxs-lookup"><span data-stu-id="06efd-111">To programmatically authenticate using your Azure account credentials, use the `loginWithUsernamePassword` function.</span></span> <span data-ttu-id="06efd-112">В следующем фрагменте кода JavaScript показано, как выполнять обычную аутентификацию с использованием учетных данных, которые хранятся как переменные среды.</span><span class="sxs-lookup"><span data-stu-id="06efd-112">The following JavaScript code snippet illustrates how to use basic authentication using credentials that are stored as environment variables.</span></span> 

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

## <a name="interactive-login"></a><span data-ttu-id="06efd-113">Интерактивный вход</span><span class="sxs-lookup"><span data-stu-id="06efd-113">Interactive login</span></span>

<span data-ttu-id="06efd-114">При интерактивном входе предоставляются ссылки и код, что позволяет пользователю выполнять аутентификацию в браузере.</span><span class="sxs-lookup"><span data-stu-id="06efd-114">Interactive login provides a link and a code that allows the user to authenticate from a browser.</span></span> <span data-ttu-id="06efd-115">Применяйте этот метод, если в одном скрипте используется несколько учетных записей или если требуется вмешательство пользователя.</span><span class="sxs-lookup"><span data-stu-id="06efd-115">Use this method when multiple accounts are used by the same script or when user intervention is preferred.</span></span>

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a><span data-ttu-id="06efd-116">Проверка подлинности субъекта-службы</span><span class="sxs-lookup"><span data-stu-id="06efd-116">Service principal authentication</span></span>

<span data-ttu-id="06efd-117">[Интерактивный вход](#interactive-login) — самый простой способ аутентификации.</span><span class="sxs-lookup"><span data-stu-id="06efd-117">[Interactive login](#interactive-login) is the easiest way to authenticate.</span></span> <span data-ttu-id="06efd-118">Но при использовании пакета SDK для Node.js может потребоваться использовать обычную аутентификацию субъекта-службы, а не предоставлять учетные данные учетной записи.</span><span class="sxs-lookup"><span data-stu-id="06efd-118">However, when using the Node.js SDK, you may want to use service principal authentication rather than providing your account credentials.</span></span> <span data-ttu-id="06efd-119">В руководстве по [созданию субъекта-службы Azure с помощью Node.js](./node-sdk-azure-authenticate-principal.md) описаны разные способы создания и использования субъекта-службы.</span><span class="sxs-lookup"><span data-stu-id="06efd-119">The topic, [Create an Azure service principal with Node.js](./node-sdk-azure-authenticate-principal.md), explains various techniques for creating (and using) a service principal.</span></span> 