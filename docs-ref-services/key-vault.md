---
title: Модули Azure Key Vault для Node.js
description: Справочник по модулям Azure Key Vault для Node.js
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: 72bf4bc5443618f5f1bb9b4d1bb4d905669ff8c8
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266601"
---
# <a name="azure-key-vault-modules-for-nodejs"></a>Модули Azure Key Vault для Node.js

Хранилище ключей Azure помогает защитить криптографические ключи и секреты, используемые облачными приложениями и службами. С помощью хранилища ключей можно шифровать ключи и секреты (например, ключи аутентификации, ключи учетных записей хранения, ключи шифрования данных, PFX-файлы и пароли), используя ключи, защищенные аппаратными модулями безопасности. Чтобы обеспечить более высокий уровень защиты, ключи можно импортировать или создать в аппаратных модулях безопасности. Если вы выберете этот вариант, корпорация Майкрософт будет обрабатывать ключи в аппаратных модулях безопасности (оборудование и встроенное ПО), сертифицированных по стандарту FIPS 140-2 уровня 2.

Хранилище ключей упрощает управление ключами и позволяет поддерживать контроль над ключами, которые предоставляют доступ к вашим данным и шифруют их. Разработчики могут за считанные минуты создавать ключи для разработки и тестирования, а затем с легкостью использовать их в рабочей среде. По необходимости администраторы безопасности могут предоставлять (и отзывать) разрешения на использование ключей.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm 

Установите модуль npm Azure Key Vault.

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a>Пример

Этот пример создает новую службу Key Vault в Azure.

```javascript
const msRestAzure = require('ms-rest-azure');
const KeyVaultManagementClient = require('azure-arm-keyvault');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const vaultName = 'your-new-vault';
const tenantGUID = 'your-tenant-guid';

// Interactive Login
let client;
msRestAzure
  .interactiveLogin()
  .then(credentials => {
    client = new KeyVaultManagementClient(credentials, subscriptionId);
    return client.vaults.list();
  })
  .then(vaults => {
    console.dir(vaults, { depth: null, colors: true });
    const parameters = {
      location: 'East US',
      properties: {
        sku: { family: 'A', name: 'standard' },
        accessPolicies: [],
        enabledForDeployment: false,
        tenantId: tenantGUID
      }
    };
    console.info('Creating vault ${vaultName} ...');
    return client.vaults.createOrUpdate(resourceGroup, vaultName, parameters);
  })
  .then(vault => console.dir(vault, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error occured');
    console.dir(err, { depth: null, colors: true });
    return err;
  });
```

## <a name="samples"></a>Примеры

- [Приступая к работе с Key Vault в Node.js](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [Управление ресурсами и группами ресурсов Azure с помощью Node.js](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [Интеграция Azure AD в веб-приложение NodeJS](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
