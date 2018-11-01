---
title: Пакет SDK службы "Речь" в Cognitive Services для JavaScript
description: Справочные материалы по пакету SDK службы "Речь" в Cognitive Services для JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50402390"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="77362-103">Пакет SDK службы "Речь" в Cognitive Services для JavaScript</span><span class="sxs-lookup"><span data-stu-id="77362-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="77362-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="77362-104">Overview</span></span>

<span data-ttu-id="77362-105">Чтобы упростить разработку приложений с поддержкой речевых функций, корпорация Майкрософт предоставляет пакет SDK [службы "Речь"](https://aka.ms/csspeech).</span><span class="sxs-lookup"><span data-stu-id="77362-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="77362-106">Пакет SDK службы "Речь" предоставляет согласованные собственные API для перевода речи и преобразования речи в текст.</span><span class="sxs-lookup"><span data-stu-id="77362-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="77362-107">Пакет SDK службы "Речь" сейчас доступен только в браузерной версии.</span><span class="sxs-lookup"><span data-stu-id="77362-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="77362-108">Пакет npm появится в ближайшее время.</span><span class="sxs-lookup"><span data-stu-id="77362-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="77362-109">Установка пакета SDK службы "Речь"</span><span class="sxs-lookup"><span data-stu-id="77362-109">Install the Speech SDK</span></span>

<span data-ttu-id="77362-110">Скачайте пакет SDK службы "Речь" как [ZIP-файл](https://aka.ms/csspeech/jsbrowserpackage) и распакуйте его.</span><span class="sxs-lookup"><span data-stu-id="77362-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="77362-111">Будет распаковано несколько файлов, включая файл с именем `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span><span class="sxs-lookup"><span data-stu-id="77362-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="77362-112">Загрузите этот файл как ресурс скрипта на веб-страницу, чтобы начать использовать пакет SDK службы "Речь":</span><span class="sxs-lookup"><span data-stu-id="77362-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="77362-113">Пример</span><span class="sxs-lookup"><span data-stu-id="77362-113">Example</span></span> 

<span data-ttu-id="77362-114">В следующих фрагментах кода показано, как выполнить простое распознавание речи в браузере:</span><span class="sxs-lookup"><span data-stu-id="77362-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

<span data-ttu-id="77362-115">Ознакомьтесь с нашим [пошаговым кратким руководством](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="77362-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="77362-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="77362-116">Samples</span></span>

<span data-ttu-id="77362-117">Другие примеры доступны в нашем [репозитории примеров для пакета SDK службы "Речь"](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="77362-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
