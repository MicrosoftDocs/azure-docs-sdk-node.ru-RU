---
title: Примеры кода для работы со службой сообщений Azure и Интернетом вещей с помощью Node.js
description: Пример кода, в котором показано, как работать со службой сообщений Azure и Интернетом вещей с помощью Node.js.
author: rloutlaw
manager: routlaw
ms.devlang: nodejs
ms.topic: article
ms.service: azure-nodejs
ms.date: 06/17/2017
ms.author: routlaw
ms.openlocfilehash: 3169c3ef0d204e902db47d81ba02b638a5eb02f5
ms.sourcegitcommit: c332a32a1a850aa62405776bfe0e14251f722888
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="sample-code-for-using-azure-messaging-and-iot-with-nodejs"></a><span data-ttu-id="414f5-103">Примеры кода: использование службы сообщений Azure и Интернета вещей с Node.js</span><span class="sxs-lookup"><span data-stu-id="414f5-103">Sample code for using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="414f5-104">Примеры кода в этой статье иллюстрируют использование службы сообщений Azure и Интернета вещей с Node.js</span><span class="sxs-lookup"><span data-stu-id="414f5-104">The following sample code illustrates using Azure messaging and IoT with Node.js</span></span>

<span data-ttu-id="414f5-105">Если вам нужен код для выполнения других задач, см. полный список [примеров кода Node.js для Azure](https://azure.microsoft.com/resources/samples/?term=nodejs).</span><span class="sxs-lookup"><span data-stu-id="414f5-105">If you need code for other tasks, you can browse the full list of [Azure Node.js samples](https://azure.microsoft.com/resources/samples/?term=nodejs).</span></span>

| | |
|---|---|
| <span data-ttu-id="414f5-106">**Центр Интернета вещей Azure**</span><span class="sxs-lookup"><span data-stu-id="414f5-106">**Azure IoT Hub**</span></span> ||
| [<span data-ttu-id="414f5-107">Проверка связи с Центром Интернета вещей Azure</span><span class="sxs-lookup"><span data-stu-id="414f5-107">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping) | <span data-ttu-id="414f5-108">Простое решение для проверки связи, которое позволяет проверить возможность подключения устройств к Центру Интернета вещей Azure.</span><span class="sxs-lookup"><span data-stu-id="414f5-108">Simple ping solution to help validate a device connectivity to Azure IoT Hub.</span></span> |
| <span data-ttu-id="414f5-109">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/) (Отправка твита об аномальных вибрациях, обнаруженных службами Интернета вещей Azure на основе данных устройства Intel Edison с Node.js)</span><span class="sxs-lookup"><span data-stu-id="414f5-109">[Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)</span></span> | <span data-ttu-id="414f5-110">Проект Интернета вещей, который реализуется с помощью Центра Интернета вещей Azure и демонстрирует использование устройства с Node.js для отправки данных телеметрии, анализируемых службами Центра Интернета вещей Azure.</span><span class="sxs-lookup"><span data-stu-id="414f5-110">IoT project using Azure IoT Hub and showing a device running node to send telemetry data and that is analyzed by Azure IoT services.</span></span> |
| <span data-ttu-id="414f5-111">**Интернет вещей для Intel Edison**</span><span class="sxs-lookup"><span data-stu-id="414f5-111">**Intel Edison IoT**</span></span> ||
| [<span data-ttu-id="414f5-112">Приступая к работе с начальным набором Интернета вещей Azure для Intel Edison</span><span class="sxs-lookup"><span data-stu-id="414f5-112">Get started with Intel Edison Azure IoT Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-intel-edison-getstartedkit) | <span data-ttu-id="414f5-113">Пример работы Интернета вещей Azure с использованием начального набора Интернета вещей Azure для Intel Edison.</span><span class="sxs-lookup"><span data-stu-id="414f5-113">Demonstrates Azure IoT using the Azure IoT Starter Kit - Intel Edison.</span></span> |
| <span data-ttu-id="414f5-114">**MQTT**</span><span class="sxs-lookup"><span data-stu-id="414f5-114">**MQTT**</span></span> ||
| [<span data-ttu-id="414f5-115">Примеры модулей шлюзов MQTT и HTTP</span><span class="sxs-lookup"><span data-stu-id="414f5-115">Sample MQTT and HTTP Gateway modules</span></span>](https://github.com/Azure-Samples/iot-gateway-mqtt-http) | <span data-ttu-id="414f5-116">Пример использования двух модулей шлюзов, которые предоставляют конечные точки MQTT и HTTPS в формате Центра Интернета вещей, используемые для отправки данных телеметрии, а в случае с модулем MQTT — и службу передачи сообщений из облака на устройство.</span><span class="sxs-lookup"><span data-stu-id="414f5-116">Provides two Gateway modules that expose IoTHub-style MQTT and HTTPS endpoints for telemetry upload, and in the case of MQTT module also C2D messaging.</span></span> |
| <span data-ttu-id="414f5-117">**Raspberry Pi**</span><span class="sxs-lookup"><span data-stu-id="414f5-117">**Raspberry Pi**</span></span> ||
| [<span data-ttu-id="414f5-118">Приступая к работе с начальным набором Интернета вещей Microsoft Azure для Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="414f5-118">Get Started with Microsoft Azure IoT Raspberry Pi Starter Kit</span></span>](https://github.com/Azure-Samples/iot-hub-node-raspberrypi-getting-started) | <span data-ttu-id="414f5-119">В этом руководстве объясняется, как использовать начальный набор Интернета вещей Microsoft Azure для Raspberry Pi.</span><span class="sxs-lookup"><span data-stu-id="414f5-119">Illustrates using the Azure IoT Raspberry Pi Starter Kit.</span></span> |
| [<span data-ttu-id="414f5-120">Подключение начального набора Интернета вещей Microsoft Azure для устройств Raspberry Pi 3 к решению для удаленного мониторинга</span><span class="sxs-lookup"><span data-stu-id="414f5-120">Connect your Microsoft Azure IoT Raspberry Pi 3 Starter Kit to the remote monitoring solution</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/) | <span data-ttu-id="414f5-121">Сведения о подключении устройства Raspberry Pi 3 к решению для удаленного мониторинга Azure IoT Suite.</span><span class="sxs-lookup"><span data-stu-id="414f5-121">Learn how to connect a Raspberry Pi 3 device to the Azure IoT Suite remote monitoring solution.</span></span> |
