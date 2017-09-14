---
title: "Модули Azure Key Vault для Node.js"
description: "Справочник по модулям Azure Key Vault для Node.js"
keywords: Azure,SDK,API,Key Vault, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Key Vault
ms.openlocfilehash: e497e1e0e369dfd975fe5a2d7759ec893fbf6aff
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-key-vault-modules-for-nodejs"></a><span data-ttu-id="a6797-104">Модули Azure Key Vault для Node.js</span><span class="sxs-lookup"><span data-stu-id="a6797-104">Azure Key Vault modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a6797-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="a6797-105">Overview</span></span>

<span data-ttu-id="a6797-106">Хранилище ключей Azure помогает защитить криптографические ключи и секреты, используемые облачными приложениями и службами.</span><span class="sxs-lookup"><span data-stu-id="a6797-106">Azure Key Vault helps safeguard cryptographic keys and secrets used by cloud applications and services.</span></span> <span data-ttu-id="a6797-107">С помощью хранилища ключей можно шифровать ключи и секреты (например, ключи аутентификации, ключи учетных записей хранения, ключи шифрования данных, PFX-файлы и пароли), используя ключи, защищенные аппаратными модулями безопасности.</span><span class="sxs-lookup"><span data-stu-id="a6797-107">By using Key Vault, you can encrypt keys and secrets (such as authentication keys, storage account keys, data encryption keys, .PFX files, and passwords) by using keys that are protected by hardware security modules (HSMs).</span></span> <span data-ttu-id="a6797-108">Чтобы обеспечить более высокий уровень защиты, ключи можно импортировать или создать в аппаратных модулях безопасности.</span><span class="sxs-lookup"><span data-stu-id="a6797-108">For added assurance, you can import or generate keys in HSMs.</span></span> <span data-ttu-id="a6797-109">Если вы выберете этот вариант, корпорация Майкрософт будет обрабатывать ключи в аппаратных модулях безопасности (оборудование и встроенное ПО), сертифицированных по стандарту FIPS 140-2 уровня 2.</span><span class="sxs-lookup"><span data-stu-id="a6797-109">If you choose to do this, Microsoft processes your keys in FIPS 140-2 Level 2 validated HSMs (hardware and firmware).</span></span>

<span data-ttu-id="a6797-110">Хранилище ключей упрощает управление ключами и позволяет поддерживать контроль над ключами, которые предоставляют доступ к вашим данным и шифруют их.</span><span class="sxs-lookup"><span data-stu-id="a6797-110">Key Vault streamlines the key management process and enables you to maintain control of keys that access and encrypt your data.</span></span> <span data-ttu-id="a6797-111">Разработчики могут за считанные минуты создавать ключи для разработки и тестирования, а затем с легкостью использовать их в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="a6797-111">Developers can create keys for development and testing in minutes, and then seamlessly migrate them to production keys.</span></span> <span data-ttu-id="a6797-112">По необходимости администраторы безопасности могут предоставлять (и отзывать) разрешения на использование ключей.</span><span class="sxs-lookup"><span data-stu-id="a6797-112">Security administrators can grant (and revoke) permission to keys, as needed.</span></span>

## <a name="management-package"></a><span data-ttu-id="a6797-113">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="a6797-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a6797-114">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="a6797-114">Install the npm module</span></span> 

<span data-ttu-id="a6797-115">Установите модуль npm Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="a6797-115">Install the Azure Key Vault npm module</span></span>

```bash
npm install azure-arm-keyvault
```

### <a name="example"></a><span data-ttu-id="a6797-116">Пример</span><span class="sxs-lookup"><span data-stu-id="a6797-116">Example</span></span>

<span data-ttu-id="a6797-117">Этот пример создает новую службу Key Vault в Azure.</span><span class="sxs-lookup"><span data-stu-id="a6797-117">This example creates a new Key Vault service in Azure.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a6797-118">Примеры</span><span class="sxs-lookup"><span data-stu-id="a6797-118">Samples</span></span>

- [<span data-ttu-id="a6797-119">Приступая к работе с Key Vault в Node.js</span><span class="sxs-lookup"><span data-stu-id="a6797-119">Getting started with Key Vault in Node.js</span></span>](https://azure.microsoft.com/resources/samples/key-vault-node-getting-started/)
- [<span data-ttu-id="a6797-120">Управление ресурсами и группами ресурсов Azure с помощью Node.js</span><span class="sxs-lookup"><span data-stu-id="a6797-120">Manage Azure resources and resource groups with Node.js</span></span>](https://azure.microsoft.com/resources/samples/resource-manager-node-resources-and-groups/) 
- [<span data-ttu-id="a6797-121">Интеграция Azure AD в веб-приложение NodeJS</span><span class="sxs-lookup"><span data-stu-id="a6797-121">Integrating Azure AD into a NodeJS web application</span></span>](https://azure.microsoft.com/resources/samples/active-directory-node-webapp-openidconnect/) 

<span data-ttu-id="a6797-122">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="a6797-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
