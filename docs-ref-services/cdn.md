---
title: Модули Azure CDN для Node.js
description: Справочник по модулям Azure CDN для Node.js
author: dksimpson
ms.author: v-deasim
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: 1117f8fabfe364d3e5602ee89f652fe98851fef4
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52021978"
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="4c297-103">Модули Azure CDN для Node.js</span><span class="sxs-lookup"><span data-stu-id="4c297-103">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="4c297-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="4c297-104">Overview</span></span>

<span data-ttu-id="4c297-105">Сеть доставки содержимого (CDN) Azure предлагает разработчикам глобальное решение по доставке содержимого, размещенного в Azure или любом другом расположении, по сети с высокой пропускной способностью.</span><span class="sxs-lookup"><span data-stu-id="4c297-105">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="4c297-106">Используя CDN, вы можете кэшировать общедоступные объекты, загруженные из хранилища BLOB-объектов, веб-приложения, виртуальной машины, папки приложения или другого расположения HTTP или HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4c297-106">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="4c297-107">Кэш CDN может храниться в стратегически важных местах для обеспечения максимальной пропускной способности при доставке содержимого пользователям.</span><span class="sxs-lookup"><span data-stu-id="4c297-107">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="4c297-108">CDN обычно используется для доставки статического содержимого, например изображений, таблиц стилей, документов, файлов, клиентских скриптов и HTML-страниц.</span><span class="sxs-lookup"><span data-stu-id="4c297-108">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="4c297-109">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="4c297-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="4c297-110">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="4c297-110">Install the npm module</span></span>

<span data-ttu-id="4c297-111">Установите модуль npm Azure CDN.</span><span class="sxs-lookup"><span data-stu-id="4c297-111">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="4c297-112">Пример</span><span class="sxs-lookup"><span data-stu-id="4c297-112">Example</span></span>

<span data-ttu-id="4c297-113">Этот пример перечисляет все профили CDN.</span><span class="sxs-lookup"><span data-stu-id="4c297-113">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="4c297-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="4c297-114">Samples</span></span>

<span data-ttu-id="4c297-115">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="4c297-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
