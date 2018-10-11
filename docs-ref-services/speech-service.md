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
ms.sourcegitcommit: 0d439a88f38a085e2be0616c8bdb0ffcca2e54ad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/11/2018
ms.locfileid: "49027438"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Пакет SDK службы "Речь" в Cognitive Services для JavaScript

## <a name="overview"></a>Обзор

Чтобы упростить разработку приложений с поддержкой речевых функций, корпорация Майкрософт предоставляет пакет SDK [службы "Речь"](https://aka.ms/csspeech).
Пакет SDK службы "Речь" предоставляет согласованные собственные API для перевода речи и преобразования речи в текст.

> [!NOTE]
> Пакет SDK службы "Речь" сейчас доступен только в браузерной версии.
> Пакет npm появится в ближайшее время.

### <a name="install-the-speech-sdk"></a>Установка пакета SDK службы "Речь"

Скачайте пакет SDK службы "Речь" как [ZIP-файл](https://aka.ms/csspeech/jsbrowserpackage) и распакуйте его.
Будет распаковано несколько файлов, включая файл с именем `microsoft.cognitiveservices.speech.sdk.bundle.js`.
Загрузите этот файл как ресурс скрипта на веб-страницу, чтобы начать использовать пакет SDK службы "Речь":

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>Пример 

В следующих фрагментах кода показано, как выполнить простое распознавание речи в браузере:

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

Ознакомьтесь с нашим [пошаговым кратким руководством](/azure/cognitive-services/speech-service/quickstart-js-browser).

## <a name="samples"></a>Примеры

Другие примеры доступны в нашем [репозитории примеров для пакета SDK службы "Речь"](https://aka.ms/csspeech/samples).
