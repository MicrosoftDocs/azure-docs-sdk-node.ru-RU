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
ms.openlocfilehash: c91b8396dbfeb766887b650541044f7ce2e7bde6
ms.sourcegitcommit: 79213a25192d8913bf8ec16c19fbec6a8eb691f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/12/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Модули Azure Active Directory для Node.js

## <a name="overview"></a>Обзор

> [!IMPORTANT]
> Мы настоятельно рекомендуем использовать для доступа к ресурсам Azure Active Directory [Microsoft Graph](https://graph.microsoft.io/) вместо API Azure AD Graph. В настоящее время усилия наших разработчиков направлены на Microsoft Graph, и дальнейшие усовершенствования API Azure AD Graph не планируются. Существует совсем немного сценариев, в которых по-прежнему можно использовать API Azure AD Graph. Дополнительные сведения см. в записи блога [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) (Microsoft Graph или Azure AD Graph) в Центре разработчика Office.

[Библиотека проверки подлинности Active Directory (ADAL) для Node.js](https://www.npmjs.com/package/adal-node) позволяет приложениям Node.js проходить проверку подлинности в AAD, чтобы получить доступ к защищенным веб-ресурсам.

## <a name="client-package"></a>Пакет клиента

### <a name="install-the-npm-modules"></a>Установка модулей npm

Установите модули клиента хранилища Azure или управления хранилищем Azure с помощью npm.

```bash
npm install adal-node
```   

### <a name="example"></a>Пример

Этот пример из [примера учетных данных клиента](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) иллюстрирует проверку подлинности между серверами с помощью учетных данных клиента.

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

## <a name="samples"></a>Примеры

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
