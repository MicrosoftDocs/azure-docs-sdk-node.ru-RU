---
title: Модули Azure Backup для Node.js
description: Справочник по модулям Azure Backup для Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 9234285d32bc465eeb86d13514783e1de4e5ef1b
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052789"
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
