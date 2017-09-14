---
title: "Модули службы приложений Azure для Node.js"
description: "Справочник по модулям службы приложений Azure для Node.js"
keywords: Azure, Node, SDK, API, web apps , mobile , nodejs, javascript
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: c695ae6d523ea731b18382ba0906f78b40ce301f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
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
