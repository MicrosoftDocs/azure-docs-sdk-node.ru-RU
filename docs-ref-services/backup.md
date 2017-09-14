---
title: "Модули Azure Backup для Node.js"
description: "Справочник по модулям Azure Backup для Node.js"
keywords: Azure,SDK,API,Backup, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 3ff9bff16a520bca461198531fd4c02139d2b293
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-backup-modules-for-nodejs"></a>Модули Azure Backup для Node.js

## <a name="overview"></a>Обзор

Служба архивации Azure — это служба на платформе Azure, используемая для резервного копирования (защиты) и восстановления данных в Microsoft Cloud. Служба архивации Azure позволяет заменить существующее локальное или автономное решение для резервного копирования на надежное, безопасное и экономичное облачное решение. Служба архивации Azure включает несколько компонентов, которые можно загрузить и установить на соответствующем компьютере, сервере или в облаке. В зависимости от того, что вам нужно защитить, развертываются различные компоненты или агенты. Все компоненты службы архивации Azure можно использовать для резервного копирования данных в хранилище служб восстановления Azure, независимо от того, защищаются ли локальные или облачные данные. 

## <a name="management-package"></a>Пакет управления

### <a name="install-the-modules-with-npm"></a>Установка модулей с помощью npm

Используйте npm для установки модулей Azure Backup для Node.js

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>Пример

Этот пример перечисляет задания восстановления для данного хранилища и группы ресурсов.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
