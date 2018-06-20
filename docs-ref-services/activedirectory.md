---
title: Модули Azure Active Directory для Node.js
description: Справочник по модулям Azure Active Directory для Node.js
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: c356801500aa3ef9038fc27634c8a95debf152b3
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259923"
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="2ebf6-103">Модули Azure Active Directory для Node.js</span><span class="sxs-lookup"><span data-stu-id="2ebf6-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2ebf6-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="2ebf6-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ebf6-105">Мы настоятельно рекомендуем использовать для доступа к ресурсам Azure Active Directory [Microsoft Graph](https://graph.microsoft.io/) вместо API Azure AD Graph.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="2ebf6-106">В настоящее время усилия наших разработчиков направлены на Microsoft Graph, и дальнейшие усовершенствования API Azure AD Graph не планируются.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="2ebf6-107">Существует совсем немного сценариев, в которых по-прежнему можно использовать API Azure AD Graph. Дополнительные сведения см. в записи блога [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) (Microsoft Graph или Azure AD Graph) в Центре разработчика Office.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="2ebf6-108">[Библиотека проверки подлинности Active Directory (ADAL) для Node.js](https://www.npmjs.com/package/adal-node) позволяет приложениям Node.js проходить проверку подлинности в AAD, чтобы получить доступ к защищенным веб-ресурсам.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="2ebf6-109">Пакет клиента</span><span class="sxs-lookup"><span data-stu-id="2ebf6-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="2ebf6-110">Установка модулей npm</span><span class="sxs-lookup"><span data-stu-id="2ebf6-110">Install the npm modules</span></span>

<span data-ttu-id="2ebf6-111">Установите модули клиента хранилища Azure или управления хранилищем Azure с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="2ebf6-112">Пример</span><span class="sxs-lookup"><span data-stu-id="2ebf6-112">Example</span></span>

<span data-ttu-id="2ebf6-113">Этот пример из [примера учетных данных клиента](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) иллюстрирует проверку подлинности между серверами с помощью учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2ebf6-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="2ebf6-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="2ebf6-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="2ebf6-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
