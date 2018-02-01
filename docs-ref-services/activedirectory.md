---
title: "Модули Azure Active Directory для Node.js"
description: "Справочник по модулям Azure Active Directory для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="9f9a1-103">Модули Azure Active Directory для Node.js</span><span class="sxs-lookup"><span data-stu-id="9f9a1-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9f9a1-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="9f9a1-104">Overview</span></span>

<span data-ttu-id="9f9a1-105">[Библиотека проверки подлинности Active Directory (ADAL) для Node.js](https://www.npmjs.com/package/adal-node) позволяет приложениям Node.js проходить проверку подлинности в AAD, чтобы получить доступ к защищенным веб-ресурсам.</span><span class="sxs-lookup"><span data-stu-id="9f9a1-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="9f9a1-106">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="9f9a1-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="9f9a1-107">Установка модулей npm</span><span class="sxs-lookup"><span data-stu-id="9f9a1-107">Install the npm modules</span></span>

<span data-ttu-id="9f9a1-108">Установите модули клиента хранилища Azure или управления хранилищем Azure с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="9f9a1-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="9f9a1-109">Пример</span><span class="sxs-lookup"><span data-stu-id="9f9a1-109">Example</span></span>

<span data-ttu-id="9f9a1-110">Этот пример из [примера учетных данных клиента](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) иллюстрирует проверку подлинности между серверами с помощью учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="9f9a1-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a><span data-ttu-id="9f9a1-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="9f9a1-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="9f9a1-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="9f9a1-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
