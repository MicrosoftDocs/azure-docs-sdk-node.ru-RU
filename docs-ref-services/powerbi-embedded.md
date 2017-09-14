---
title: "Модули Azure PowerBI Embedded для Node.js"
description: "Справочник по модулям Azure PowerBI Embedded для Node.js"
keywords: Azure,SDK,API,PowerBI Embedded, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 74e69421d372ff4ccaebf2b811152dd83b9b4e7b
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="a1b75-104">Модули Azure PowerBI Embedded для Node.js</span><span class="sxs-lookup"><span data-stu-id="a1b75-104">Azure PowerBI Embedded modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a1b75-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="a1b75-105">Overview</span></span>

<span data-ttu-id="a1b75-106">С помощью службы Power BI Embedded Azure вы можете интегрировать отчеты Power BI прямо в приложение Node для создания или изменения диаграмм и отчетов.</span><span class="sxs-lookup"><span data-stu-id="a1b75-106">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="a1b75-107">Дополнительные сведения о [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="a1b75-107">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="a1b75-108">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="a1b75-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a1b75-109">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="a1b75-109">Install the npm module</span></span>

<span data-ttu-id="a1b75-110">Установите модуль npm Azure Power BI</span><span class="sxs-lookup"><span data-stu-id="a1b75-110">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="a1b75-111">Пример</span><span class="sxs-lookup"><span data-stu-id="a1b75-111">Example</span></span>

<span data-ttu-id="a1b75-112">Этот пример создает коллекцию рабочей области в существующей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="a1b75-112">This example creates a workspace collection in an existing resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const PowerBIEmbeddedManagementClient = require('azure-arm-powerbiembedded');

const creationOptions = {
  location: 'northcentralus',
  tags: {
    key1: 'value1',
    key2: 'value2'
  },
  sku: {
    name: 'S1',
    teir: 'Standard'
  }
};

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';
const workspace = 'workspace-collection-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new PowerBIEmbeddedManagementClient(
      credentials,
      subscriptionId
    );
    return client.workspaceCollections.create(
      resourceGroup,
      workspace,
      creationOptions
    );
  })
  .then(workspaces => console.dir(workspaces, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="a1b75-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="a1b75-113">Samples</span></span>

<span data-ttu-id="a1b75-114">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="a1b75-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
