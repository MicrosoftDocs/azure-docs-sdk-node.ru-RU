---
title: Модули Azure Logic Apps для Node.js
description: Справочник по модулям Azure Logic Apps для Node.js
author: ecfan
ms.author: estfan
manager: cfowler
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 2de867fdd0aa31b63b9680cc3f0c2e7f6301e632
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Модули Azure Logic Apps для Node.js

Приложения логики позволяют упростить и реализовать масштабируемые рабочие процессы и сценарии интеграции в облаке. Это визуальный конструктор для моделирования и автоматизации процессов в виде ряда операций, которые называются рабочим процессом. Для облачных и локальных сред доступно множество соединителей, которые позволяют быстро реализовать сценарии интеграции в службах и протоколах. Приложение логики запускается при срабатывании триггера (например, "When an account is added to Dynamics CRM" (При добавлении учетной записи в Dynamics CRM)), после чего могут выполняться разные комбинации действий, преобразования и условная логика.

Использование приложений логики связано со следующими преимуществами.
- Экономия времени при разработке сложных процессов с помощью простых в использовании средств проектирования.
- Относительно простая реализация шаблонов и рабочих процессов, которые иначе было бы трудно реализовать в коде.
- Быстрое начало работы с шаблонами.
- Настройка приложений логики с помощью собственных настраиваемых интерфейсов API, кода и действий.
- Подключение и синхронизация разрозненных систем в локальных и облачных средах.
- Сборка с использованием BizTalk Server, службы управления API, Функций Azure и служебной шины Azure при первоклассной поддержке интеграции.

Приложения логики — это полностью управляемые решения iPaaS (платформа интеграции как услуга), при разработке которых вам не нужно выполнять дополнительные действия для обеспечения размещения, масштабируемости, доступности и возможности управления. Приложения логики автоматически масштабируются в соответствии с требованиями.

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-module"></a>Установка модуля npm

Установите модуль Azure Logic Apps для Node.js.

```bash
npm install azure-arm-logic
```

### <a name="example"></a>Пример

```javascript
const msRestAzure = require('ms-rest-azure');
const LogicManagement = require('azure-arm-logic');

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const subscriptionId = 'subscription-id';
    const client = new LogicManagement(credentials, subscriptionId);
    return client.workflows.listBySubscription();
  })
  .then(workflows => console.log(workflows));
```

### <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
