---
title: Модули центров уведомлений Azure для Node.js
description: Справочник по модулям центров уведомлений Azure для Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 30b8caa07111f9ceb5fa58f92649e4670aa6bee6
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34261723"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="aa329-103">Модули центров уведомлений Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="aa329-103">Azure Notification Hubs modules for Node.js</span></span>

<span data-ttu-id="aa329-104">Центры уведомлений Azure предлагают удобный и масштабируемый механизм для push-уведомлений с поддержкой разных платформ.</span><span class="sxs-lookup"><span data-stu-id="aa329-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="aa329-105">Один вызов API, единый для всех платформ, позволяет легко отправлять целевые персонализированные push-уведомления на любую мобильную платформу с любого облачного или локального сервера.</span><span class="sxs-lookup"><span data-stu-id="aa329-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="aa329-106">Центры уведомлений отлично походят как для отдельных потребителей, так и для крупных предприятий.</span><span class="sxs-lookup"><span data-stu-id="aa329-106">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="aa329-107">Вот некоторые примеры задач, для которых наши клиенты применяют Центры уведомлений:</span><span class="sxs-lookup"><span data-stu-id="aa329-107">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="aa329-108">отправка (с низкой задержкой) уведомлений об экстренных новостях миллионам пользователей;</span><span class="sxs-lookup"><span data-stu-id="aa329-108">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="aa329-109">отправка купонов целевым сегментам пользователей с учетом их местоположения;</span><span class="sxs-lookup"><span data-stu-id="aa329-109">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="aa329-110">отправка уведомлений о событиях пользователям или группам пользователей в информационных, спортивных, финансовых и игровых приложениях;</span><span class="sxs-lookup"><span data-stu-id="aa329-110">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="aa329-111">передача в приложения рекламного содержимого, которое помогает привлекать клиентов и продавать товары;</span><span class="sxs-lookup"><span data-stu-id="aa329-111">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="aa329-112">уведомление пользователей о корпоративных событиях, новостях и рабочих задачах;</span><span class="sxs-lookup"><span data-stu-id="aa329-112">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="aa329-113">отправка кодов для многофакторной идентификации.</span><span class="sxs-lookup"><span data-stu-id="aa329-113">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="aa329-114">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="aa329-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="aa329-115">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="aa329-115">Install the npm module</span></span>

<span data-ttu-id="aa329-116">Установите модуль центров уведомлений Azure</span><span class="sxs-lookup"><span data-stu-id="aa329-116">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="aa329-117">Пример</span><span class="sxs-lookup"><span data-stu-id="aa329-117">Example</span></span>

<span data-ttu-id="aa329-118">Этот пример формирует список всех центров уведомлений.</span><span class="sxs-lookup"><span data-stu-id="aa329-118">This example lists all notification hubs.</span></span>

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

## <a name="samples"></a><span data-ttu-id="aa329-119">Примеры</span><span class="sxs-lookup"><span data-stu-id="aa329-119">Samples</span></span>

* [<span data-ttu-id="aa329-120">Руководство по мобильным приложениям службы для серверной части .NET</span><span class="sxs-lookup"><span data-stu-id="aa329-120">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* <span data-ttu-id="aa329-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Отправка твита об аномальных вибрациях, обнаруженных службами Интернета вещей Azure на основе данных устройства Intel Edison с Node.js)</span><span class="sxs-lookup"><span data-stu-id="aa329-121">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="aa329-122">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="aa329-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
