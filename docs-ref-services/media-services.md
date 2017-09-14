---
title: "Модули служб мультимедиа Azure для Node.js"
description: "Справочник по модулям служб мультимедиа Azure для Node.js"
keywords: Azure,SDK,API,Media Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="112da-104">Модули служб мультимедиа Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="112da-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="112da-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="112da-105">Overview</span></span>

<span data-ttu-id="112da-106">Службы мультимедиа Azure — это расширяемая облачная платформа, которая позволяет разработчикам создавать масштабируемые приложения для управления и доставки файлов мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="112da-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="112da-107">С помощью служб мультимедиа Azure можно безопасно передавать, сохранять, кодировать и упаковывать видео- или аудиосодержимое для потоковой трансляции разным клиентам (например, на ТВ, ПК и мобильные устройства) или для трансляции по требованию.</span><span class="sxs-lookup"><span data-stu-id="112da-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="112da-108">С помощью служб мультимедиа Azure вы можете:</span><span class="sxs-lookup"><span data-stu-id="112da-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="112da-109">Создавать сквозные рабочие процессы, полностью использующие службы мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="112da-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="112da-110">Использовать сторонние компоненты в качестве некоторых частей рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="112da-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="112da-111">Например, можно выполнять кодирование с помощью стороннего кодировщика.</span><span class="sxs-lookup"><span data-stu-id="112da-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="112da-112">А затем отправить, защитить, упаковать и доставить содержимое с использованием служб мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="112da-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="112da-113">Выполнять потоковую передачу содержимого динамически или доставлять содержимое по запросу.</span><span class="sxs-lookup"><span data-stu-id="112da-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="112da-114">В этом разделе также есть ссылки на другие разделы.</span><span class="sxs-lookup"><span data-stu-id="112da-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="112da-115">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="112da-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="112da-116">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="112da-116">Install the npm module</span></span>

<span data-ttu-id="112da-117">Установка модуля npm служб мультимедиа Azure</span><span class="sxs-lookup"><span data-stu-id="112da-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="112da-118">Пример</span><span class="sxs-lookup"><span data-stu-id="112da-118">Example</span></span>

<span data-ttu-id="112da-119">Этот пример перечисляет все службы мультимедиа для группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="112da-119">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="112da-120">Примеры</span><span class="sxs-lookup"><span data-stu-id="112da-120">Samples</span></span>

<span data-ttu-id="112da-121">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="112da-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
