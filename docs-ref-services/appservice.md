---
title: "Модули службы приложений Azure для Node.js"
description: "Справочник по модулям службы приложений Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: b722344f056a52785aef6d853a797231dcafc699
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="5a889-103">Модули службы приложений Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="5a889-103">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="5a889-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="5a889-104">Overview</span></span>

<span data-ttu-id="5a889-105">Служба приложений Azure — это решение на основе модели "платформа как услуга" (PaaS) Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="5a889-105">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="5a889-106">Кроме того, с его помощью можно интегрировать приложения с решениями SaaS, подключаться к локальным приложениям и автоматизировать бизнес-процессы.</span><span class="sxs-lookup"><span data-stu-id="5a889-106">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="5a889-107">Azure запускает приложения на полностью управляемых виртуальных машинах.</span><span class="sxs-lookup"><span data-stu-id="5a889-107">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="5a889-108">При этом вы можете выбрать тип виртуальных машин, которые необходимо использовать для вашей нагрузки (общие или выделенные).</span><span class="sxs-lookup"><span data-stu-id="5a889-108">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="5a889-109">Служба приложений обладает возможностями для работы в сетевой и мобильной среде, которые ранее предлагались в составе отдельных решений Веб-сайты Azure и мобильные службы Azure.</span><span class="sxs-lookup"><span data-stu-id="5a889-109">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="5a889-110">Она также предусматривает новые возможности для автоматизации бизнес-процессов и размещения облачных API.</span><span class="sxs-lookup"><span data-stu-id="5a889-110">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="5a889-111">Интегрированная служба приложений позволяет легко создать единое решение, объединяющее несколько компонентов (например, веб-сайты, серверные части мобильных приложений, интерфейсы API RESTful и бизнес-процессы).</span><span class="sxs-lookup"><span data-stu-id="5a889-111">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="5a889-112">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="5a889-112">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="5a889-113">Установка пакета npm</span><span class="sxs-lookup"><span data-stu-id="5a889-113">Install the npm package</span></span>

<span data-ttu-id="5a889-114">Установите модуль службы приложения Azure для Node.js.</span><span class="sxs-lookup"><span data-stu-id="5a889-114">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="5a889-115">Пример</span><span class="sxs-lookup"><span data-stu-id="5a889-115">Example</span></span>

<span data-ttu-id="5a889-116">Этот пример создает веб-сайт в Azure с помощью Node.js.</span><span class="sxs-lookup"><span data-stu-id="5a889-116">This example creates a website on Azure using Node.js.</span></span>

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

## <a name="samples"></a><span data-ttu-id="5a889-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="5a889-117">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="5a889-118">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="5a889-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
