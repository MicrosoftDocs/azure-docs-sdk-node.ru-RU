---
title: "Модули центров уведомлений Azure для Node.js"
description: "Справочник по модулям центров уведомлений Azure для Node.js"
keywords: Azure,SDK,API,Notification Hubs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 0141760cb93c77faed4a04893fe1376e4e75c361
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="dde93-104">Модули центров уведомлений Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="dde93-104">Azure Notification Hubs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="dde93-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="dde93-105">Overview</span></span>

<span data-ttu-id="dde93-106">Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ.</span><span class="sxs-lookup"><span data-stu-id="dde93-106">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="dde93-107">Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.</span><span class="sxs-lookup"><span data-stu-id="dde93-107">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="dde93-108">Центры уведомлений отлично походят как для отдельных потребителей, так и для крупных предприятий.</span><span class="sxs-lookup"><span data-stu-id="dde93-108">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="dde93-109">Вот некоторые примеры задач, для которых наши клиенты применяют Центры уведомлений:</span><span class="sxs-lookup"><span data-stu-id="dde93-109">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="dde93-110">отправка (с низкой задержкой) уведомлений об экстренных новостях миллионам пользователей;</span><span class="sxs-lookup"><span data-stu-id="dde93-110">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="dde93-111">отправка купонов целевым сегментам пользователей с учетом их местоположения;</span><span class="sxs-lookup"><span data-stu-id="dde93-111">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="dde93-112">отправка уведомлений о событиях пользователям или группам пользователей в информационных, спортивных, финансовых и игровых приложениях;</span><span class="sxs-lookup"><span data-stu-id="dde93-112">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="dde93-113">передача в приложения рекламного содержимого, которое помогает привлекать клиентов и продавать товары;</span><span class="sxs-lookup"><span data-stu-id="dde93-113">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="dde93-114">уведомление пользователей о корпоративных событиях, новостях и рабочих задачах;</span><span class="sxs-lookup"><span data-stu-id="dde93-114">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="dde93-115">отправка кодов для многофакторной идентификации.</span><span class="sxs-lookup"><span data-stu-id="dde93-115">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="dde93-116">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="dde93-116">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="dde93-117">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="dde93-117">Install the npm module</span></span>

<span data-ttu-id="dde93-118">Установите модуль центров уведомлений Azure</span><span class="sxs-lookup"><span data-stu-id="dde93-118">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="dde93-119">Пример</span><span class="sxs-lookup"><span data-stu-id="dde93-119">Example</span></span>

<span data-ttu-id="dde93-120">Этот пример формирует список всех центров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="dde93-120">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="dde93-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="dde93-121">Samples</span></span>

* [<span data-ttu-id="dde93-122">Руководство по мобильным приложениям службы для серверной части .NET</span><span class="sxs-lookup"><span data-stu-id="dde93-122">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* <span data-ttu-id="dde93-123">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Отправка твита об аномальных вибрациях, обнаруженных службами Интернета вещей Azure на основе данных устройства Intel Edison с Node.js)</span><span class="sxs-lookup"><span data-stu-id="dde93-123">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="dde93-124">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="dde93-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
