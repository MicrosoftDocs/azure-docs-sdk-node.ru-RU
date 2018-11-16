---
title: Модули Azure PowerBI Embedded для Node.js
description: Справочник по модулям Azure PowerBI Embedded для Node.js
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: PowerBI Embedded
ms.openlocfilehash: 58251dd1cd3a672a5167193f74d311952d70e84e
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51481398"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="3d1ac-103">Модули Azure PowerBI Embedded для Node.js</span><span class="sxs-lookup"><span data-stu-id="3d1ac-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="3d1ac-104">С помощью службы Power BI Embedded Azure вы можете интегрировать отчеты Power BI прямо в приложение Node для создания или изменения диаграмм и отчетов.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="3d1ac-105">Дополнительные сведения о [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="3d1ac-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="3d1ac-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="3d1ac-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="3d1ac-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="3d1ac-107">Install the npm module</span></span>

<span data-ttu-id="3d1ac-108">Установите модуль npm Azure Power BI</span><span class="sxs-lookup"><span data-stu-id="3d1ac-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="3d1ac-109">Пример</span><span class="sxs-lookup"><span data-stu-id="3d1ac-109">Example</span></span>

<span data-ttu-id="3d1ac-110">Этот пример создает коллекцию рабочей области в существующей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="3d1ac-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="3d1ac-111">Samples</span></span>

<span data-ttu-id="3d1ac-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="3d1ac-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
