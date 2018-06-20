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
ms.openlocfilehash: 4d0a1ebf75591a9a3575172f325309ddbac7885c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260892"
---
# <a name="azure-powerbi-embedded-modules-for-nodejs"></a><span data-ttu-id="76a67-103">Модули Azure PowerBI Embedded для Node.js</span><span class="sxs-lookup"><span data-stu-id="76a67-103">Azure PowerBI Embedded modules for Node.js</span></span>

<span data-ttu-id="76a67-104">С помощью службы Power BI Embedded Azure вы можете интегрировать отчеты Power BI прямо в приложение Node для создания или изменения диаграмм и отчетов.</span><span class="sxs-lookup"><span data-stu-id="76a67-104">With the Power BI Embedded Azure service, you can integrate Power BI reports right into your node application to create or edit charts and reports.</span></span>

<span data-ttu-id="76a67-105">Дополнительные сведения о [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span><span class="sxs-lookup"><span data-stu-id="76a67-105">Learn more about [Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding/).</span></span>

## <a name="management-package"></a><span data-ttu-id="76a67-106">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="76a67-106">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="76a67-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="76a67-107">Install the npm module</span></span>

<span data-ttu-id="76a67-108">Установите модуль npm Azure Power BI</span><span class="sxs-lookup"><span data-stu-id="76a67-108">Install the Azure Power BI npm module</span></span>

```bash
npm install azure-arm-powerbiembedded
```

### <a name="example"></a><span data-ttu-id="76a67-109">Пример</span><span class="sxs-lookup"><span data-stu-id="76a67-109">Example</span></span>

<span data-ttu-id="76a67-110">Этот пример создает коллекцию рабочей области в существующей группе ресурсов.</span><span class="sxs-lookup"><span data-stu-id="76a67-110">This example creates a workspace collection in an existing resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="76a67-111">Примеры</span><span class="sxs-lookup"><span data-stu-id="76a67-111">Samples</span></span>

<span data-ttu-id="76a67-112">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="76a67-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
