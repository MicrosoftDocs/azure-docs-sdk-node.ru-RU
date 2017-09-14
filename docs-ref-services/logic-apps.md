---
title: "Модули Azure Logic Apps для Node.js"
description: "Справочник по модулям Azure Logic Apps для Node.js"
keywords: Azure,SDK,API,Logic Apps, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Logic Apps
ms.openlocfilehash: 70380dbf1fd199ba4909975b05ade72efaa4e0ec
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-logic-apps-modules-for-nodejs"></a>Модули Azure Logic Apps для Node.js

## <a name="overview"></a>Обзор
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
