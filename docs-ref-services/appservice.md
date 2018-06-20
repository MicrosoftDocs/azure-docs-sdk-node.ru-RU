---
title: Модули службы приложений Azure для Node.js
description: Справочник по модулям службы приложений Azure для Node.js
author: SyntaxC4
ms.author: cfowler
manager: jhubbard
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: d9cb33e9aead2878fc9571b1ccb3a34b8990af74
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266615"
---
# <a name="azure-app-service-modules-for-nodejs"></a>Модули службы приложений Azure для Node.js

## <a name="overview"></a>Обзор

Служба приложений Azure — это решение на основе модели "платформа как услуга" (PaaS) Microsoft Azure. Кроме того, с его помощью можно интегрировать приложения с решениями SaaS, подключаться к локальным приложениям и автоматизировать бизнес-процессы. Azure запускает приложения на полностью управляемых виртуальных машинах. При этом вы можете выбрать тип виртуальных машин, которые необходимо использовать для вашей нагрузки (общие или выделенные).

Служба приложений обладает возможностями для работы в сетевой и мобильной среде, которые ранее предлагались в составе отдельных решений Веб-сайты Azure и мобильные службы Azure. Она также предусматривает новые возможности для автоматизации бизнес-процессов и размещения облачных API. Интегрированная служба приложений позволяет легко создать единое решение, объединяющее несколько компонентов (например, веб-сайты, серверные части мобильных приложений, интерфейсы API RESTful и бизнес-процессы).

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-package"></a>Установка пакета npm

Установите модуль службы приложения Azure для Node.js.

```bash
npm install azure-arm-website
```

### <a name="example"></a>Пример

Этот пример создает веб-сайт в Azure с помощью Node.js.

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>Примеры

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
