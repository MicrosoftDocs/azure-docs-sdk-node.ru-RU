---
title: "Модули реестра контейнеров Azure для Node.js"
description: "Справочник по модулям реестра контейнеров Azure для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: dda0e9bbfaa8a3e060f3b8f820d5bab315662629
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-container-registry-modules-for-nodejs"></a>Модули реестра контейнеров Azure для Node.js

Реестр контейнеров Azure — это управляемая служба реестра Docker, основанная на реестре Docker 2.0 с открытым кодом. Создавайте и настраивайте реестры контейнеров Azure, чтобы хранить частные образы контейнеров Docker и управлять ими. Используйте реестры контейнеров Azure с имеющимися конвейерами разработки и развертывания контейнеров, изучив сведения, предоставленные сообществом Docker.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль npm реестра контейнеров Azure.

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a>Пример

Этот пример возвращает список доступных контейнеров.

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
