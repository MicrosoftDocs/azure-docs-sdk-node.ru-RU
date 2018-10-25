---
title: Модули Azure Cognitive Services для Node.js
description: Справочник по модулям Azure Cognitive Services для Node.js
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "49714629"
---
# <a name="javascript-azure-cognitive-services-modules"></a><span data-ttu-id="df720-103">Модули Azure Cognitive Services для JavaScript</span><span class="sxs-lookup"><span data-stu-id="df720-103">JavaScript Azure Cognitive Services modules</span></span>

## <a name="vision-modules"></a><span data-ttu-id="df720-104">Модули визуального распознавания</span><span class="sxs-lookup"><span data-stu-id="df720-104">Vision modules</span></span>

### <a name="computer-vision"></a><span data-ttu-id="df720-105">API компьютерного зрения</span><span class="sxs-lookup"><span data-stu-id="df720-105">Computer Vision</span></span> 

<span data-ttu-id="df720-106">Предоставляет информацию о визуальном содержимом изображений:</span><span class="sxs-lookup"><span data-stu-id="df720-106">Returns information about visual content found in an image:</span></span>

- <span data-ttu-id="df720-107">Используйте добавление тегов, описания и модели, предназначенные для определенных сфер, для безошибочного определения и обозначения содержимого.</span><span class="sxs-lookup"><span data-stu-id="df720-107">Use tagging, descriptions, and domain-specific models to identify content and label it with confidence.</span></span>
- <span data-ttu-id="df720-108">Используйте параметры для определения непристойных материалов и содержимого для взрослых, чтобы включить автоматическое ограничение такого содержимого.</span><span class="sxs-lookup"><span data-stu-id="df720-108">Apply adult/racy settings to enable automated restriction of adult content.</span></span>
- <span data-ttu-id="df720-109">Определяйте типы изображений и цветовые схемы на фотографиях.</span><span class="sxs-lookup"><span data-stu-id="df720-109">Identify image types and color schemes in pictures.</span></span>

<span data-ttu-id="df720-110">[Попробуйте средства компьютерного зрения](https://azure.microsoft.com/services/cognitive-services/computer-vision/) в браузере бесплатно.</span><span class="sxs-lookup"><span data-stu-id="df720-110">[Try Computer Vision](https://azure.microsoft.com/services/cognitive-services/computer-vision/) for free in your browser.</span></span>

<span data-ttu-id="df720-111">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-111">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-computervision
```

<span data-ttu-id="df720-112">См. дополнительные сведения об [API компьютерного зрения](/azure/cognitive-services/computer-vision/home) и начните работу с помощью [краткого руководства по API компьютерного зрения для JavaScript](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="df720-112">[Learn more](/azure/cognitive-services/computer-vision/home) about the Computer Vision API and get started with the [Computer Vision API JavaScript quickstart](/azure/cognitive-services/computer-vision/quickstarts/javascript).</span></span>

### <a name="content-moderator"></a><span data-ttu-id="df720-113">Content Moderator</span><span class="sxs-lookup"><span data-stu-id="df720-113">Content Moderator</span></span>

<span data-ttu-id="df720-114">Машинная модерация текста, видео и изображений, улучшенная с помощью средств пользовательской проверки.</span><span class="sxs-lookup"><span data-stu-id="df720-114">Machine-assisted moderation of text, video and images, augmented with human review tools.</span></span>

<span data-ttu-id="df720-115">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-115">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-contentmoderator
```

<span data-ttu-id="df720-116">См. дополнительные сведения о [Content Moderator](/azure/cognitive-services/content-moderator/overview).</span><span class="sxs-lookup"><span data-stu-id="df720-116">[Learn more](/azure/cognitive-services/content-moderator/overview) about the Content Moderator service.</span></span>

### <a name="face-api"></a><span data-ttu-id="df720-117">API распознавания лиц</span><span class="sxs-lookup"><span data-stu-id="df720-117">Face API</span></span>

<span data-ttu-id="df720-118">Распознавание, идентификация, анализ и группировка лиц, а также добавление к ним тегов на фотографиях.</span><span class="sxs-lookup"><span data-stu-id="df720-118">Detect, identify, analyze, organize, and tag faces in photos.</span></span> 

<span data-ttu-id="df720-119">[Попробуйте API распознавания лиц](https://azure.microsoft.com/services/cognitive-services/face/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-119">[Try the Face API](https://azure.microsoft.com/services/cognitive-services/face/) in your browser.</span></span>

<span data-ttu-id="df720-120">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-120">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-face
```

<span data-ttu-id="df720-121">См. дополнительные сведения об [API распознавания лиц](/azure/cognitive-services/face/overview) в [кратком руководстве по API распознавания лиц для JavaScript](/azure/cognitive-services/Face/quickstarts/javascript).</span><span class="sxs-lookup"><span data-stu-id="df720-121">[Learn more](/azure/cognitive-services/face/overview) about the Face API and get started with the [Face API JavaScript quickstart](/azure/cognitive-services/Face/quickstarts/javascript).</span></span>

## <a name="search-modules"></a><span data-ttu-id="df720-122">Поиск модулей</span><span class="sxs-lookup"><span data-stu-id="df720-122">Search modules</span></span>

### <a name="web-search"></a><span data-ttu-id="df720-123">Поиск в Интернете</span><span class="sxs-lookup"><span data-stu-id="df720-123">Web search</span></span>

<span data-ttu-id="df720-124">Получайте веб-документы, индексированные с помощью API Bing для поиска в Интернете, и ограничивайте результаты по типу, дате создания и другим критериям.</span><span class="sxs-lookup"><span data-stu-id="df720-124">Retrieve web documents indexed by the Bing Web Search API and narrow down the results by result type, freshness and more.</span></span> 

<span data-ttu-id="df720-125">[Попробуйте API Поиска в Интернете](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-125">[Try the Web Search API](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) in your browser.</span></span>

<span data-ttu-id="df720-126">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-126">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-websearch
```

<span data-ttu-id="df720-127">См. дополнительные сведения об [API Bing для поиска в Интернете](/azure/cognitive-services/bing-web-search/overview) и начните работу с помощью [краткого руководства по API Поиска в Интернете для Node.js](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-127">[Learn more](/azure/cognitive-services/bing-web-search/overview) about the Bing Web Search API and get started with the [Web Search API Node.js quickstart](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).</span></span>

### <a name="image-search"></a><span data-ttu-id="df720-128">Поиск изображений</span><span class="sxs-lookup"><span data-stu-id="df720-128">Image search</span></span>

<span data-ttu-id="df720-129">Выполняйте поиск изображений и получайте эскизы, полные URL-адреса изображений, метаданные изображения и другие сведения в качестве результатов.</span><span class="sxs-lookup"><span data-stu-id="df720-129">Search for images and get thumbnails, full image URLs, image metadata and more in your results.</span></span>

<span data-ttu-id="df720-130">[Попробуйте API Поиска изображений](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-130">[Try the Image Search API](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) in your browser.</span></span>

<span data-ttu-id="df720-131">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-131">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-imagesearch
```

<span data-ttu-id="df720-132">См. дополнительные сведения об [API Bing для поиска изображений](/azure/cognitive-services/bing-image-search/overview) и начните работу с помощью [краткого руководства по API Bing для поиска изображений для Node.js](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-132">[Learn more](/azure/cognitive-services/bing-image-search/overview) about the Bing Image Search API and get started with the [Image Search API Node.js quickstart](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).</span></span>


### <a name="entity-search"></a><span data-ttu-id="df720-133">Поиск сущностей</span><span class="sxs-lookup"><span data-stu-id="df720-133">Entity search</span></span>

<span data-ttu-id="df720-134">Выполняйте поиск наиболее важных сущностей (мест, лиц или вещей) по заданному условию поиска или расположению.</span><span class="sxs-lookup"><span data-stu-id="df720-134">Search for the most relevant entity (place, person, or thing) for a given search term or location.</span></span>

<span data-ttu-id="df720-135">[Попробуйте API Поиска сущностей](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-135">[Try the Entity Search API](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) in your browser.</span></span>

<span data-ttu-id="df720-136">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-136">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-entitysearch
```

<span data-ttu-id="df720-137">См. дополнительные сведения об [API Bing для поиска сущностей](/azure/cognitive-services/bing-entities-search/search-the-web) и начните работу с помощью [краткого руководства по API Bing для поиска сущностей для Node.js](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-137">[Learn more](/azure/cognitive-services/bing-entities-search/search-the-web) about the Bing Entity Search API and get started with the [Entity Search API Node.js quickstart](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).</span></span>

### <a name="custom-search"></a><span data-ttu-id="df720-138">Пользовательский поиск</span><span class="sxs-lookup"><span data-stu-id="df720-138">Custom search</span></span>

<span data-ttu-id="df720-139">Выполняйте пользовательский поиск в Интернете в соответствии с конкретным доменом поиска.</span><span class="sxs-lookup"><span data-stu-id="df720-139">Build and a custom web search that meets your specific search domain.</span></span>

<span data-ttu-id="df720-140">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-140">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-customsearch
```

<span data-ttu-id="df720-141">См. дополнительные сведения о [Пользовательском поиске Bing](/azure/cognitive-services/bing-custom-search/) и начните работу с помощью [краткого руководства по API пользовательского поиска Bing для Node.js](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-141">[Learn more](/azure/cognitive-services/bing-custom-search/) about the Bing Custom Search service and get started with querying your custom search from your apps with the [Custom Search API Node.js quickstart](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).</span></span>

### <a name="video-search"></a><span data-ttu-id="df720-142">Поиск видео</span><span class="sxs-lookup"><span data-stu-id="df720-142">Video search</span></span>

<span data-ttu-id="df720-143">Выполняйте поиск видео в Интернете и получайте в результатах метаданные со сведениями об авторе, кодировке, длительности и числу просмотров.</span><span class="sxs-lookup"><span data-stu-id="df720-143">Find videos across the web and get results with creator, encoding, length, and view count metadata.</span></span>

<span data-ttu-id="df720-144">[Попробуйте API Bing для поиска видео](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-144">[Try the Video Search API](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) in your browser.</span></span>

<span data-ttu-id="df720-145">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-145">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-videosearch
```

<span data-ttu-id="df720-146">См. дополнительные сведения об [API Bing для поиска видео](/azure/cognitive-services/bing-video-search/search-the-web) и начните работу с помощью [краткого руководства по API Bing для поиска видео для Node.js](/azure/cognitive-services/bing-video-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-146">[Learn more](/azure/cognitive-services/bing-video-search/search-the-web) about the Bing Video Search service and get started with the [Video Search API Node.js quickstart](/azure/cognitive-services/bing-video-search/nodejs).</span></span>


### <a name="news-search"></a><span data-ttu-id="df720-147">Поиск новостей</span><span class="sxs-lookup"><span data-stu-id="df720-147">News search</span></span>

<span data-ttu-id="df720-148">Выполняйте поиск новостей в Интернете и работайте со статьями, связанными новостями, изображениями, а также метаданными, содержащими сведения о поставщике.</span><span class="sxs-lookup"><span data-stu-id="df720-148">Search the web for news articles and work with article, related news, images, and provider info metadata.</span></span>

<span data-ttu-id="df720-149">[Попробуйте API Bing для поиска новостей](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-149">[Try the News Search API](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) in your browser.</span></span>

<span data-ttu-id="df720-150">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-150">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-newssearch
```

<span data-ttu-id="df720-151">См. дополнительные сведения об [API Bing для поиска новостей](/azure/cognitive-services/bing-news-search/search-the-web) и начните работу с помощью [краткого руководства по API Bing для поиска новостей для JavaScript](/azure/cognitive-services/bing-news-search/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-151">[Learn more](/azure/cognitive-services/bing-news-search/search-the-web) about the Bing News Search service and get started with the [News Search API JavaScript quickstart](/azure/cognitive-services/bing-news-search/nodejs).</span></span>


## <a name="language-modules"></a><span data-ttu-id="df720-152">Модули языка</span><span class="sxs-lookup"><span data-stu-id="df720-152">Language modules</span></span>

### <a name="text-analytics"></a><span data-ttu-id="df720-153">Текстовая аналитика</span><span class="sxs-lookup"><span data-stu-id="df720-153">Text Analytics</span></span> 

<span data-ttu-id="df720-154">API анализа текста — это облачная служба, которая предоставляет возможности обработки естественного языка в необработанном тексте.</span><span class="sxs-lookup"><span data-stu-id="df720-154">The Text Analytics API is a cloud-based service that provides  natural language processing over raw text.</span></span> <span data-ttu-id="df720-155">API включает три основные функции:</span><span class="sxs-lookup"><span data-stu-id="df720-155">The API includes three main functions:</span></span>

- <span data-ttu-id="df720-156">Анализ мнений</span><span class="sxs-lookup"><span data-stu-id="df720-156">Sentiment analysis</span></span>
- <span data-ttu-id="df720-157">Извлечение ключевой фразы</span><span class="sxs-lookup"><span data-stu-id="df720-157">Key phrase extraction</span></span>
- <span data-ttu-id="df720-158">Определение языка</span><span class="sxs-lookup"><span data-stu-id="df720-158">Language detection</span></span>

<span data-ttu-id="df720-159">[Попробуйте API анализа текста](https://azure.microsoft.com/services/cognitive-services/text-analytics/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-159">[Try the Text Analytics API](https://azure.microsoft.com/services/cognitive-services/text-analytics/) in your browser.</span></span>

<span data-ttu-id="df720-160">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-160">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-textanalytics
```

<span data-ttu-id="df720-161">См. дополнительные сведения об [API анализа текста](/azure/cognitive-services/text-analytics/overview) и начните работу с помощью [краткого руководства по API анализа текста для Node.js](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-161">[Learn more](/azure/cognitive-services/text-analytics/overview) about the Text Analytics API and get started with the [Text Analytics API Node.js quickstart](/azure/cognitive-services/text-analytics/quickstarts/nodejs).</span></span>


### <a name="spell-check"></a><span data-ttu-id="df720-162">Проверка орфографии</span><span class="sxs-lookup"><span data-stu-id="df720-162">Spell Check</span></span>

<span data-ttu-id="df720-163">Выполняйте контекстные проверки грамматики и орфографии с помощью API проверки орфографии Bing.</span><span class="sxs-lookup"><span data-stu-id="df720-163">Perform contextual grammar and spell checking with the Bing Spell Check API.</span></span>

<span data-ttu-id="df720-164">[Попробуйте API проверки орфографии](https://azure.microsoft.com/services/cognitive-services/spell-check/) в браузере.</span><span class="sxs-lookup"><span data-stu-id="df720-164">[Try the Spell Check API](https://azure.microsoft.com/services/cognitive-services/spell-check/) in your browser.</span></span>

<span data-ttu-id="df720-165">Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span><span class="sxs-lookup"><span data-stu-id="df720-165">Get the JavaScript module with [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):</span></span>

```
npm install azure-cognitiveservices-spellcheck
```

<span data-ttu-id="df720-166">См. дополнительные сведения об [API проверки орфографии](/azure/cognitive-services/bing-spell-check/proof-text) в [кратком руководстве по API проверки орфографии для Node.js](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span><span class="sxs-lookup"><span data-stu-id="df720-166">[Learn more](/azure/cognitive-services/bing-spell-check/proof-text) about the Spell Check API and get started with the [Spell Check API Node.js quickstart](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).</span></span>

## <a name="samples"></a><span data-ttu-id="df720-167">Примеры</span><span class="sxs-lookup"><span data-stu-id="df720-167">Samples</span></span>

<span data-ttu-id="df720-168">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="df720-168">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
