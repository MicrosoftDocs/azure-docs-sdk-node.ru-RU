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
ms.openlocfilehash: 36bc5e97a5eea6e821f66bff9b3e8f610baa2dd0
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51388548"
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="15ca9-103">Модули Azure Key Vault для Node.js</span><span class="sxs-lookup"><span data-stu-id="15ca9-103">Azure Key Vault modules for Node.js</span></span>

<span data-ttu-id="15ca9-104">Хранилище ключей Azure помогает защитить криптографические ключи и секреты, используемые облачными приложениями и службами.</span><span class="sxs-lookup"><span data-stu-id="15ca9-104">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="15ca9-105">С помощью хранилища ключей можно шифровать ключи и секреты (например, ключи аутентификации, ключи учетных записей хранения, ключи шифрования данных, PFX-файлы и пароли), используя ключи, защищенные аппаратными модулями безопасности.</span><span class="sxs-lookup"><span data-stu-id="15ca9-105">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="15ca9-106">Чтобы обеспечить более высокий уровень защиты, ключи можно импортировать или создать в аппаратных модулях безопасности.</span><span class="sxs-lookup"><span data-stu-id="15ca9-106">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="15ca9-107">Если вы выберете этот вариант, корпорация Майкрософт будет обрабатывать ключи в аппаратных модулях безопасности (оборудование и встроенное ПО), сертифицированных по стандарту FIPS 140-2 уровня 2.</span><span class="sxs-lookup"><span data-stu-id="15ca9-107">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="15ca9-108">Хранилище ключей упрощает управление ключами и позволяет поддерживать контроль над ключами, которые предоставляют доступ к вашим данным и шифруют их.</span><span class="sxs-lookup"><span data-stu-id="15ca9-108">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="15ca9-109">Разработчики могут за считанные минуты создавать ключи для разработки и тестирования, а затем с легкостью использовать их в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="15ca9-109">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="15ca9-110">По необходимости администраторы безопасности могут предоставлять (и отзывать) разрешения на использование ключей.</span><span class="sxs-lookup"><span data-stu-id="15ca9-110">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="15ca9-111">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="15ca9-111">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="15ca9-112">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="15ca9-112">Install the npm module</span></span> 

<span data-ttu-id="15ca9-113">Установите модуль npm Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="15ca9-113">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="15ca9-114">Пример</span><span class="sxs-lookup"><span data-stu-id="15ca9-114">Example</span></span>

<span data-ttu-id="15ca9-115">Этот пример создает новую службу Key Vault в Azure.</span><span class="sxs-lookup"><span data-stu-id="15ca9-115">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="15ca9-116">Примеры</span><span class="sxs-lookup"><span data-stu-id="15ca9-116">Samples</span></span>

- [<span data-ttu-id="15ca9-117">Приступая к работе с Key Vault в Node.js</span><span class="sxs-lookup"><span data-stu-id="15ca9-117">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="15ca9-118">Управление ресурсами и группами ресурсов Azure с помощью Node.js</span><span class="sxs-lookup"><span data-stu-id="15ca9-118">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="15ca9-119">Интеграция Azure AD в веб-приложение NodeJS</span><span class="sxs-lookup"><span data-stu-id="15ca9-119">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="15ca9-120">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="15ca9-120">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
