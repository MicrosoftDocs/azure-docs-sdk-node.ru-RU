---
title: Модули сопоставления служб Azure для Node.js
description: Справочник по модулям сопоставления служб Azure для Node.js
author: bwren
ms.author: bwren
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 494d948896d65dd67b06f455386f500346862beb
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "49761899"
---
# <a name="azure-service-map-modules-for-nodejs"></a><span data-ttu-id="aa4ea-103">Модули сопоставления служб Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="aa4ea-103">Azure Service Map modules for Node.js</span></span>

<span data-ttu-id="aa4ea-104">Служба схемы услуги автоматически обнаруживает компоненты приложений в системах Windows и Linux и сопоставляет взаимодействие между службами.</span><span class="sxs-lookup"><span data-stu-id="aa4ea-104">Service Map automatically discovers application components on Windows and Linux systems and maps the communication between services.</span></span> <span data-ttu-id="aa4ea-105">Схема услуги отображает сведения о подключениях между серверами, процессами и портами в любой подключенной по протоколу TCP архитектуре без дополнительной настройки. Пользователям требуется только установить агент.</span><span class="sxs-lookup"><span data-stu-id="aa4ea-105">Service Map shows connections between servers, processes, and ports across any TCP-connected architecture, with no configuration required other than the installation of an agent.</span></span>

<span data-ttu-id="aa4ea-106">Дополнительные сведения о [сопоставлении служб Azure](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span><span class="sxs-lookup"><span data-stu-id="aa4ea-106">Learn more about [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).</span></span>

## <a name="management-package"></a><span data-ttu-id="aa4ea-107">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="aa4ea-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aa4ea-108">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="aa4ea-108">Install the npm module</span></span>

<span data-ttu-id="aa4ea-109">Установите модуль npm сопоставления служб Azure.</span><span class="sxs-lookup"><span data-stu-id="aa4ea-109">Install the Azure Service Map npm module</span></span>

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a><span data-ttu-id="aa4ea-110">Пример</span><span class="sxs-lookup"><span data-stu-id="aa4ea-110">Example</span></span>

<span data-ttu-id="aa4ea-111">Этот пример перечисляет все сопоставления служб для указанной группы ресурсов и рабочей области.</span><span class="sxs-lookup"><span data-stu-id="aa4ea-111">This example lists all service maps for the specified resource group and workspace.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a><span data-ttu-id="aa4ea-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="aa4ea-112">Samples</span></span>

<span data-ttu-id="aa4ea-113">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="aa4ea-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
