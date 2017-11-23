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
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="f4a28-104">Модули службы приложений Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="f4a28-104">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f4a28-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="f4a28-105">Overview</span></span>

<span data-ttu-id="f4a28-106">Служба приложений Azure — это решение на основе модели "платформа как услуга" (PaaS) Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f4a28-106">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="f4a28-107">Кроме того, с его помощью можно интегрировать приложения с решениями SaaS, подключаться к локальным приложениям и автоматизировать бизнес-процессы.</span><span class="sxs-lookup"><span data-stu-id="f4a28-107">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="f4a28-108">Azure запускает приложения на полностью управляемых виртуальных машинах.</span><span class="sxs-lookup"><span data-stu-id="f4a28-108">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="f4a28-109">При этом вы можете выбрать тип виртуальных машин, которые необходимо использовать для вашей нагрузки (общие или выделенные).</span><span class="sxs-lookup"><span data-stu-id="f4a28-109">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="f4a28-110">Служба приложений обладает возможностями для работы в сетевой и мобильной среде, которые ранее предлагались в составе отдельных решений Веб-сайты Azure и мобильные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="f4a28-110">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="f4a28-111">Она также предусматривает новые возможности для автоматизации бизнес-процессов и размещения облачных API.</span><span class="sxs-lookup"><span data-stu-id="f4a28-111">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="f4a28-112">Интегрированная служба приложений позволяет легко создать единое решение, объединяющее несколько компонентов (например, веб-сайты, серверные части мобильных приложений, интерфейсы API RESTful и бизнес-процессы).</span><span class="sxs-lookup"><span data-stu-id="f4a28-112">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="f4a28-113">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="f4a28-113">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="f4a28-114">Установка пакета npm</span><span class="sxs-lookup"><span data-stu-id="f4a28-114">Install the npm package</span></span>

<span data-ttu-id="f4a28-115">Установите модуль службы приложения Azure для Node.js.</span><span class="sxs-lookup"><span data-stu-id="f4a28-115">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="f4a28-116">Пример</span><span class="sxs-lookup"><span data-stu-id="f4a28-116">Example</span></span>

<span data-ttu-id="f4a28-117">Этот пример создает веб-сайт в Azure с помощью Node.js.</span><span class="sxs-lookup"><span data-stu-id="f4a28-117">This example creates a website on Azure using Node.js.</span></span>

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

## <a name="samples"></a><span data-ttu-id="f4a28-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="f4a28-118">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="f4a28-119">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="f4a28-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
