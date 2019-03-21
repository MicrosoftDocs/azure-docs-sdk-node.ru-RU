---
title: Пакет SDK службы "Речь" в Cognitive Services для JavaScript
description: Справочные материалы по пакету SDK службы "Речь" в Cognitive Services для JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.subservice: speech-service
ms.openlocfilehash: b1375b6beb478cab2475539c03b6bac9f0ea99e0
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052580"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="ea163-103">Пакет SDK службы "Речь" в Cognitive Services для JavaScript</span><span class="sxs-lookup"><span data-stu-id="ea163-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="ea163-104">Обзор</span><span class="sxs-lookup"><span data-stu-id="ea163-104">Overview</span></span>

<span data-ttu-id="ea163-105">Чтобы упростить разработку приложений с поддержкой речевых функций, корпорация Майкрософт предоставляет пакет SDK [службы "Речь"](https://aka.ms/csspeech).</span><span class="sxs-lookup"><span data-stu-id="ea163-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="ea163-106">Пакет SDK службы "Речь" предоставляет согласованные собственные API для перевода речи и преобразования речи в текст.</span><span class="sxs-lookup"><span data-stu-id="ea163-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="ea163-107">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="ea163-107">Install the npm module</span></span>

<span data-ttu-id="ea163-108">Установка модуля npm для пакета SDK службы "Речь" Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="ea163-108">Install the Cognitive Services Speech SDK npm module</span></span>

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a><span data-ttu-id="ea163-109">Пример</span><span class="sxs-lookup"><span data-stu-id="ea163-109">Example</span></span> 

<span data-ttu-id="ea163-110">В следующих фрагментах кода показано, как выполнить простое распознавание речи в файле:</span><span class="sxs-lookup"><span data-stu-id="ea163-110">The following code snippets illustrates how to do simple speech recognition from a file:</span></span>

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

<span data-ttu-id="ea163-111">Ознакомьтесь с нашим [пошаговым кратким руководством](/azure/cognitive-services/speech-service/quickstart-js-node).</span><span class="sxs-lookup"><span data-stu-id="ea163-111">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>

## <a name="samples"></a><span data-ttu-id="ea163-112">Примеры</span><span class="sxs-lookup"><span data-stu-id="ea163-112">Samples</span></span>

* <span data-ttu-id="ea163-113">[Краткое пошаговое руководство по распознаванию речи в Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span><span class="sxs-lookup"><span data-stu-id="ea163-113">[Step-by-step quickstart for Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).</span></span>
* <span data-ttu-id="ea163-114">[Краткое пошаговое руководство по распознаванию речи в браузере](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="ea163-114">[Step-by-step quickstart for the browser](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>
* <span data-ttu-id="ea163-115">Другие примеры можно найти в нашем [репозитории примеров для пакета SDK службы "Речь"](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="ea163-115">More samples can be found in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
