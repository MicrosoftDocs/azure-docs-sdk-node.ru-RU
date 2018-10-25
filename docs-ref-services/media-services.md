---
title: Модули служб мультимедиа Azure для Node.js
description: Справочник по модулям служб мультимедиа Azure для Node.js
author: Juliako
ms.author: juliako
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: bfd4402c215a81c9ed8753cfe9ad9dbfaa52bd6f
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "49795049"
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="359c9-103">Модули служб мультимедиа Azure для Node.js</span><span class="sxs-lookup"><span data-stu-id="359c9-103">Azure Media Services modules for Node.js</span></span>

<span data-ttu-id="359c9-104">Службы мультимедиа Azure — это расширяемая облачная платформа, которая позволяет разработчикам создавать масштабируемые приложения для управления и доставки файлов мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="359c9-104">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="359c9-105">С помощью служб мультимедиа Azure можно безопасно передавать, сохранять, кодировать и упаковывать видео- или аудиосодержимое для потоковой трансляции разным клиентам (например, на ТВ, ПК и мобильные устройства) или для трансляции по требованию.</span><span class="sxs-lookup"><span data-stu-id="359c9-105">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="359c9-106">С помощью служб мультимедиа Azure вы можете:</span><span class="sxs-lookup"><span data-stu-id="359c9-106">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="359c9-107">Создавать сквозные рабочие процессы, полностью использующие службы мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="359c9-107">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="359c9-108">Использовать сторонние компоненты в качестве некоторых частей рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="359c9-108">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="359c9-109">Например, можно выполнять кодирование с помощью стороннего кодировщика.</span><span class="sxs-lookup"><span data-stu-id="359c9-109">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="359c9-110">А затем отправить, защитить, упаковать и доставить содержимое с использованием служб мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="359c9-110">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="359c9-111">Выполнять потоковую передачу содержимого динамически или доставлять содержимое по запросу.</span><span class="sxs-lookup"><span data-stu-id="359c9-111">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="359c9-112">В этом разделе также есть ссылки на другие разделы.</span><span class="sxs-lookup"><span data-stu-id="359c9-112">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="359c9-113">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="359c9-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="359c9-114">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="359c9-114">Install the npm module</span></span>

<span data-ttu-id="359c9-115">Установка модуля npm служб мультимедиа Azure</span><span class="sxs-lookup"><span data-stu-id="359c9-115">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="359c9-116">Пример</span><span class="sxs-lookup"><span data-stu-id="359c9-116">Example</span></span>

<span data-ttu-id="359c9-117">Этот пример перечисляет все службы мультимедиа для группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="359c9-117">This example lists all media services for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="359c9-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="359c9-118">Samples</span></span>

<span data-ttu-id="359c9-119">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="359c9-119">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
