---
title: "Аутентификация с использованием модулей управления Azure для Node.js"
description: "Аутентификация с помощью субъекта-службы в модулях управления Azure для Node.js"
keywords: Azure, Node, SDK, API, authentication, active directory, service principal
author: tomarcher
manager: douge
ms.author: tarcher
ms.date: 06/17/2017
ms.topic: article
ms.prod: azure
ms.devlang: nodejs
ms.service: azure-nodejs
ms.openlocfilehash: 3ad1f17435844852838d01115ad8326f141aa73c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="authenticate-with-the-azure-modules-for-nodejs"></a>Аутентификация с использованием модулей Azure для Node.js 

Все API-интерфейсы служб, для которых создаются экземпляры, должны пройти аутентификацию с использованием объекта `credentials`. Существует три способа аутентификации и создания необходимых учетных данных с использованием пакета Azure SDK для Node.js: 

- Обычная аутентификация
- Интерактивный вход
- Проверка подлинности субъекта-службы

## <a name="basic-authentication"></a>Обычная аутентификация

Чтобы выполнить аутентификацию программными средствами с помощью учетных данных учетной записи Azure, используйте функцию `loginWithUsernamePassword`. В следующем фрагменте кода JavaScript показано, как выполнять обычную аутентификацию с использованием учетных данных, которые хранятся как переменные среды. 

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.loginWithUsernamePassword(process.env.AZURE_USER, 
                                 process.env.AZURE_PASS, 
                                 (err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, 
                                                             '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="interactive-login"></a>Интерактивный вход

При интерактивном входе предоставляются ссылки и код, что позволяет пользователю выполнять аутентификацию в браузере. Применяйте этот метод, если в одном скрипте используется несколько учетных записей или если требуется вмешательство пользователя.

```javascript
const Azure = require('azure');
const MsRest = require('ms-rest-azure');

MsRest.interactiveLogin((err, credentials) => {
  if (err) throw err;

  let storageClient = Azure.createARMStorageManagementClient(credentials, '<azure-subscription-id>');

  // ..use the client instance to manage service resources.
});
```

## <a name="service-principal-authentication"></a>Проверка подлинности субъекта-службы

[Интерактивный вход](#interactive-login) — самый простой способ аутентификации. Но при использовании пакета SDK для Node.js может потребоваться использовать обычную аутентификацию субъекта-службы, а не предоставлять учетные данные учетной записи. В руководстве по [созданию субъекта-службы Azure с помощью Node.js](./node-sdk-azure-authenticate-principal.md) описаны разные способы создания и использования субъекта-службы. 