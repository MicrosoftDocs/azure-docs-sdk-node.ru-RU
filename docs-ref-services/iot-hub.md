---
title: "Модули Центра Интернета вещей Azure для Node.js"
description: "Справочник по модулям Центра Интернета вещей Azure для Node.js"
keywords: Azure,SDK,API,IoT Hub, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 44d01ceb833d2acbef6f9f22b32d4ad66b1fd5ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="9cdb8-104">Модули Центра Интернета вещей Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="9cdb8-104">Azure IoT Hub modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9cdb8-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="9cdb8-105">Overview</span></span>

<span data-ttu-id="9cdb8-106">Центр IoT Azure — это полностью управляемая служба, которая обеспечивает надежный и защищенный двунаправленный обмен данными между миллионами устройств IoT и серверной частью решения.</span><span class="sxs-lookup"><span data-stu-id="9cdb8-106">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="9cdb8-107">Центр IoT Azure обеспечивает:</span><span class="sxs-lookup"><span data-stu-id="9cdb8-107">Azure IoT Hub:</span></span>
- <span data-ttu-id="9cdb8-108">несколько вариантов взаимодействия между устройствами и облаком, в том числе одностороннюю передачу сообщений, передачу файлов и методы "запрос — ответ";</span><span class="sxs-lookup"><span data-stu-id="9cdb8-108">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="9cdb8-109">встроенную декларативную маршрутизацию сообщений к другим службам Azure;</span><span class="sxs-lookup"><span data-stu-id="9cdb8-109">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="9cdb8-110">хранилище для метаданных устройств и информации о состоянии синхронизации с возможностью запрашивания данных;</span><span class="sxs-lookup"><span data-stu-id="9cdb8-110">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="9cdb8-111">безопасную связь и контроль доступа с использованием отдельных ключей безопасности или сертификатов X.509 для каждого устройства;</span><span class="sxs-lookup"><span data-stu-id="9cdb8-111">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="9cdb8-112">комплексный мониторинг взаимодействия, а также событий управления идентификацией устройств;</span><span class="sxs-lookup"><span data-stu-id="9cdb8-112">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="9cdb8-113">простое подключение устройств, так как используются библиотеки устройств для большинства популярных языков и платформ.</span><span class="sxs-lookup"><span data-stu-id="9cdb8-113">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="9cdb8-114">Используйте npm для установки модулей Центра Интернета вещей Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="9cdb8-114">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="9cdb8-115">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="9cdb8-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9cdb8-116">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="9cdb8-116">Install the npm module</span></span>

<span data-ttu-id="9cdb8-117">Установите модуль npm Центра Интернета вещей Azure.</span><span class="sxs-lookup"><span data-stu-id="9cdb8-117">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="9cdb8-118">Пример</span><span class="sxs-lookup"><span data-stu-id="9cdb8-118">Example</span></span>

<span data-ttu-id="9cdb8-119">Этот пример создает и называет Центр Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="9cdb8-119">This example creates and names an IoT hub.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

<span data-ttu-id="9cdb8-120">Этот пример получает существующий Центр Интернета вещей по имени.</span><span class="sxs-lookup"><span data-stu-id="9cdb8-120">This example gets the existing IoT hub, by name.</span></span>

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a><span data-ttu-id="9cdb8-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="9cdb8-121">Samples</span></span>

- [<span data-ttu-id="9cdb8-122">Начальный набор Интернета вещей Microsoft Azure для Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="9cdb8-122">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- <span data-ttu-id="9cdb8-123">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Отправка твита об аномальных вибрациях, обнаруженных службами Интернета вещей Azure на основе данных устройства Intel Edison с Node.js)</span><span class="sxs-lookup"><span data-stu-id="9cdb8-123">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span>

<span data-ttu-id="9cdb8-124">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="9cdb8-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
