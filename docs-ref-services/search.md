---
title: "Модули Поиска Azure для Node.js"
description: "Справочник по модулям Поиска Azure для Node.js"
keywords: Azure,SDK,API,Search, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="c7397-104">Модули Поиска Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="c7397-104">Azure Search modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c7397-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c7397-105">Overview</span></span>

<span data-ttu-id="c7397-106">Поиск Azure — это облачное решение (поиск как услуга), которое делегирует корпорации Майкрософт управление сервером и инфраструктурой. Вы получаете готовое к работе решение, которое можно заполнить своими данными и затем использовать для добавления поиска в свое приложение.</span><span class="sxs-lookup"><span data-stu-id="c7397-106">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="c7397-107">Дополнительные сведения о [Поиске Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="c7397-107">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="c7397-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="c7397-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="c7397-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="c7397-109">Install the npm module</span></span>

<span data-ttu-id="c7397-110">Установите модуль npm Поиска Azure.</span><span class="sxs-lookup"><span data-stu-id="c7397-110">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="c7397-111">Пример</span><span class="sxs-lookup"><span data-stu-id="c7397-111">Example</span></span>

<span data-ttu-id="c7397-112">Этот пример создает новую службу поиска в Azure, а также выводит список ресурсов в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="c7397-112">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="c7397-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="c7397-113">Samples</span></span>

<span data-ttu-id="c7397-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="c7397-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
