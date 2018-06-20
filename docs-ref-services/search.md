---
title: Модули Поиска Azure для Node.js
description: Справочник по модулям Поиска Azure для Node.js
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: 895281acd2359240f3d483e4205c628e1f85f724
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264991"
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="22940-103">Модули Поиска Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="22940-103">Azure Search modules for Node.js</span></span>

<span data-ttu-id="22940-104">Поиск Azure — это облачное решение (поиск как услуга), которое делегирует корпорации Майкрософт управление сервером и инфраструктурой. Вы получаете готовое к работе решение, которое можно заполнить своими данными и затем использовать для добавления поиска в свое приложение.</span><span class="sxs-lookup"><span data-stu-id="22940-104">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="22940-105">Дополнительные сведения о [Поиске Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="22940-105">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="22940-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="22940-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="22940-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="22940-107">Install the npm module</span></span>

<span data-ttu-id="22940-108">Установите модуль npm Поиска Azure.</span><span class="sxs-lookup"><span data-stu-id="22940-108">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="22940-109">Пример</span><span class="sxs-lookup"><span data-stu-id="22940-109">Example</span></span>

<span data-ttu-id="22940-110">Этот пример создает новую службу поиска в Azure, а также выводит список ресурсов в группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="22940-110">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="22940-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="22940-111">Samples</span></span>

<span data-ttu-id="22940-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="22940-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
