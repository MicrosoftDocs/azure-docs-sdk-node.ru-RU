---
title: Модули Службы контейнеров Azure для Node.js
description: Справочник по модулям Службы контейнеров Azure для Node.js
author: mmacy
ms.author: marsma
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Service
ms.openlocfilehash: 2d0aac2f7f6cc70ab3e40f7b3ccee6f64a011b55
ms.sourcegitcommit: 702a716434eb42f55d8782feb62ae2c6d8147aa9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34689834"
---
# <a name="microsoft-azure-sdk-for-nodejs---containerserviceclient"></a>Пакет Microsoft Azure SDK для Node.js — ContainerServiceClient
В этом проекте содержится пакет Node.js для доступа к службам Azure. Сейчас он поддерживает:
- **Node.js версии 6.x.x или выше**

## <a name="features"></a>Функции


## <a name="how-to-install"></a>Установка

```bash
npm install azure-arm-containerservice
```

## <a name="how-to-use"></a>Использование

### <a name="authentication-client-creation-and-list-containerservices-as-an-example"></a>Пример выполнения аутентификации, создания клиента и перечисления containerServices.

```javascript
const msRestAzure = require("ms-rest-azure");
const ContainerServiceClient = require("azure-arm-containerservice");
msRestAzure.interactiveLogin().then((creds) => {
    const subscriptionId = "<Subscription_Id>";
    const client = new ContainerServiceClient(creds, subscriptionId);
    return client.containerServices.list().then((result) => {
      console.log("The result is:");
      console.log(result);
    });
}).catch((err) => {
  console.log('An error ocurred:');
  console.dir(err, {depth: null, colors: true});
});
```

## <a name="related-projects"></a>Связанные проекты

- [Пакет Microsoft Azure SDK для Node.js](https://github.com/Azure/azure-sdk-for-node)