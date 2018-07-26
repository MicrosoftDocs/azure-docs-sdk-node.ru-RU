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
ms.openlocfilehash: 7941d3850ef6c3518ff0ab13fe1b1ea239ab1828
ms.sourcegitcommit: 99a36d08455760a0436fb6a8fffb542518e3cb2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2018
ms.locfileid: "39189000"
---
# <a name="javascript-azure-cognitive-services-modules"></a>Модули Azure Cognitive Services для JavaScript

## <a name="vision-modules"></a>Модули визуального распознавания

### <a name="computer-vision"></a>API компьютерного зрения 

Предоставляет информацию о визуальном содержимом изображений:

- Используйте добавление тегов, описания и модели, предназначенные для определенных сфер, для безошибочного определения и обозначения содержимого.
- Используйте параметры для определения непристойных материалов и содержимого для взрослых, чтобы включить автоматическое ограничение такого содержимого.
- Определяйте типы изображений и цветовые схемы на фотографиях.

[Попробуйте средства компьютерного зрения](https://azure.microsoft.com/services/cognitive-services/computer-vision/) в браузере бесплатно.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-computervision
```

См. дополнительные сведения об [API компьютерного зрения](/azure/cognitive-services/computer-vision/home) и начните работу с помощью [краткого руководства по API компьютерного зрения для JavaScript](/azure/cognitive-services/computer-vision/quickstarts/javascript).

### <a name="content-moderator"></a>Content Moderator

Машинная модерация текста, видео и изображений, улучшенная с помощью средств пользовательской проверки.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-contentmoderator
```

См. дополнительные сведения о [Content Moderator](/azure/cognitive-services/content-moderator/overview).

### <a name="face-api"></a>API распознавания лиц

Распознавание, идентификация, анализ и группировка лиц, а также добавление к ним тегов на фотографиях. 

[Попробуйте API распознавания лиц](https://azure.microsoft.com/services/cognitive-services/face/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-face
```

См. дополнительные сведения об [API распознавания лиц](/azure/cognitive-services/face/overview) в [кратком руководстве по API распознавания лиц для JavaScript](/azure/cognitive-services/Face/quickstarts/javascript).

## <a name="search-modules"></a>Поиск модулей

### <a name="web-search"></a>Поиск в Интернете

Получайте веб-документы, индексированные с помощью API Bing для поиска в Интернете, и ограничивайте результаты по типу, дате создания и другим критериям. 

[Попробуйте API Поиска в Интернете](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-websearch
```

См. дополнительные сведения об [API Bing для поиска в Интернете](/azure/cognitive-services/bing-web-search/overview) и начните работу с помощью [краткого руководства по API Поиска в Интернете для Node.js](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).

### <a name="image-search"></a>Поиск изображений

Выполняйте поиск изображений и получайте эскизы, полные URL-адреса изображений, метаданные изображения и другие сведения в качестве результатов.

[Попробуйте API Поиска изображений](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-imagesearch
```

См. дополнительные сведения об [API Bing для поиска изображений](/azure/cognitive-services/bing-image-search/overview) и начните работу с помощью [краткого руководства по API Bing для поиска изображений для Node.js](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).


### <a name="entity-search"></a>Поиск сущностей

Выполняйте поиск наиболее важных сущностей (мест, лиц или вещей) по заданному условию поиска или расположению.

[Попробуйте API Поиска сущностей](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-entitysearch
```

См. дополнительные сведения об [API Bing для поиска сущностей](/azure/cognitive-services/bing-entities-search/search-the-web) и начните работу с помощью [краткого руководства по API Bing для поиска сущностей для Node.js](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).

### <a name="custom-search"></a>Пользовательский поиск

Выполняйте пользовательский поиск в Интернете в соответствии с конкретным доменом поиска.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-customsearch
```

См. дополнительные сведения о [Пользовательском поиске Bing](/azure/cognitive-services/bing-custom-search/) и начните работу с помощью [краткого руководства по API пользовательского поиска Bing для Node.js](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).

### <a name="video-search"></a>Поиск видео

Выполняйте поиск видео в Интернете и получайте в результатах метаданные со сведениями об авторе, кодировке, длительности и числу просмотров.

[Попробуйте API Bing для поиска видео](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-videosearch
```

См. дополнительные сведения об [API Bing для поиска видео](/azure/cognitive-services/bing-video-search/search-the-web) и начните работу с помощью [краткого руководства по API Bing для поиска видео для Node.js](/azure/cognitive-services/bing-video-search/nodejs).


### <a name="news-search"></a>Поиск новостей

Выполняйте поиск новостей в Интернете и работайте со статьями, связанными новостями, изображениями, а также метаданными, содержащими сведения о поставщике.

[Попробуйте API Bing для поиска новостей](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-newssearch
```

См. дополнительные сведения об [API Bing для поиска новостей](/azure/cognitive-services/bing-news-search/search-the-web) и начните работу с помощью [краткого руководства по API Bing для поиска новостей для JavaScript](/azure/cognitive-services/bing-news-search/nodejs).


## <a name="language-modules"></a>Модули языка

### <a name="text-analytics"></a>Текстовая аналитика 

API анализа текста — это облачная служба, которая предоставляет возможности обработки естественного языка в необработанном тексте. API включает три основные функции:

- Анализ мнений
- Извлечение ключевой фразы
- Определение языка

[Попробуйте API анализа текста](https://azure.microsoft.com/services/cognitive-services/text-analytics/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-textanalytics
```

См. дополнительные сведения об [API анализа текста](/azure/cognitive-services/text-analytics/overview) и начните работу с помощью [краткого руководства по API анализа текста для Node.js](/azure/cognitive-services/text-analytics/quickstarts/nodejs).


### <a name="spell-check"></a>Проверка орфографии

Выполняйте контекстные проверки грамматики и орфографии с помощью API проверки орфографии Bing.

[Попробуйте API проверки орфографии](https://azure.microsoft.com/services/cognitive-services/spell-check/) в браузере.

Получите модуль JavaScript с помощью [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```
npm install azure-cognitiveservices-spellcheck
```

См. дополнительные сведения об [API проверки орфографии](/azure/cognitive-services/bing-spell-check/proof-text) в [кратком руководстве по API проверки орфографии для Node.js](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
