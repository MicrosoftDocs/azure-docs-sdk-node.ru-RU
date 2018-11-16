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
ms.openlocfilehash: 021f57c7f4f1b86a3c0e97f345d2f934351669b8
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51494808"
---
# <a name="azure-logic-apps-modules-for-nodejs"></a><span data-ttu-id="e58fd-103">Модули Azure Logic Apps для Node.js</span><span class="sxs-lookup"><span data-stu-id="e58fd-103">Azure Logic Apps modules for Node.js</span></span>

<span data-ttu-id="e58fd-104">Приложения логики позволяют упростить и реализовать масштабируемые рабочие процессы и сценарии интеграции в облаке.</span><span class="sxs-lookup"><span data-stu-id="e58fd-104">Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud.</span></span> <span data-ttu-id="e58fd-105">Это визуальный конструктор для моделирования и автоматизации процессов в виде ряда операций, которые называются рабочим процессом.</span><span class="sxs-lookup"><span data-stu-id="e58fd-105">It provides a visual designer to model and automate your process as a series of steps known as a workflow.</span></span> <span data-ttu-id="e58fd-106">Для облачных и локальных сред доступно множество соединителей, которые позволяют быстро реализовать сценарии интеграции в службах и протоколах.</span><span class="sxs-lookup"><span data-stu-id="e58fd-106">There are many connectors across the cloud and on-premises to quickly integrate across services and protocols.</span></span> <span data-ttu-id="e58fd-107">Приложение логики запускается при срабатывании триггера (например, "When an account is added to Dynamics CRM" (При добавлении учетной записи в Dynamics CRM)), после чего могут выполняться разные комбинации действий, преобразования и условная логика.</span><span class="sxs-lookup"><span data-stu-id="e58fd-107">A logic app begins with a trigger (like 'When an account is added to Dynamics CRM') and after firing can begin many combinations of actions, conversions, and condition logic.</span></span>

<span data-ttu-id="e58fd-108">Использование приложений логики связано со следующими преимуществами.</span><span class="sxs-lookup"><span data-stu-id="e58fd-108">The advantages of using Logic Apps include the following:</span></span>
- <span data-ttu-id="e58fd-109">Экономия времени при разработке сложных процессов с помощью простых в использовании средств проектирования.</span><span class="sxs-lookup"><span data-stu-id="e58fd-109">Saving time by designing complex processes using easy to understand design tools</span></span>
- <span data-ttu-id="e58fd-110">Относительно простая реализация шаблонов и рабочих процессов, которые иначе было бы трудно реализовать в коде.</span><span class="sxs-lookup"><span data-stu-id="e58fd-110">Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code</span></span>
- <span data-ttu-id="e58fd-111">Быстрое начало работы с шаблонами.</span><span class="sxs-lookup"><span data-stu-id="e58fd-111">Getting started quickly from templates</span></span>
- <span data-ttu-id="e58fd-112">Настройка приложений логики с помощью собственных настраиваемых интерфейсов API, кода и действий.</span><span class="sxs-lookup"><span data-stu-id="e58fd-112">Customizing your logic app with your own custom APIs, code, and actions</span></span>
- <span data-ttu-id="e58fd-113">Подключение и синхронизация разрозненных систем в локальных и облачных средах.</span><span class="sxs-lookup"><span data-stu-id="e58fd-113">Connect and synchronise disparate systems across on-premises and the cloud</span></span>
- <span data-ttu-id="e58fd-114">Сборка с использованием BizTalk Server, службы управления API, Функций Azure и служебной шины Azure при первоклассной поддержке интеграции.</span><span class="sxs-lookup"><span data-stu-id="e58fd-114">Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support</span></span>

<span data-ttu-id="e58fd-115">Приложения логики — это полностью управляемые решения iPaaS (платформа интеграции как услуга), при разработке которых вам не нужно выполнять дополнительные действия для обеспечения размещения, масштабируемости, доступности и возможности управления.</span><span class="sxs-lookup"><span data-stu-id="e58fd-115">Logic Apps is a fully managed iPaaS (integration Platform as a Service) allowing developers not to have to worry about building hosting, scalability, availability and management.</span></span> <span data-ttu-id="e58fd-116">Приложения логики автоматически масштабируются в соответствии с требованиями.</span><span class="sxs-lookup"><span data-stu-id="e58fd-116">Logic Apps will scale up automatically to meet demand.</span></span>

## <a name="management-package"></a><span data-ttu-id="e58fd-117">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="e58fd-117">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e58fd-118">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="e58fd-118">Install the npm module</span></span>

<span data-ttu-id="e58fd-119">Установите модуль Azure Logic Apps для Node.js.</span><span class="sxs-lookup"><span data-stu-id="e58fd-119">Install the Azure logic module for Node.js</span></span>

```bash
npm install azure-arm-logic
```

### <a name="example"></a><span data-ttu-id="e58fd-120">Пример</span><span class="sxs-lookup"><span data-stu-id="e58fd-120">Example</span></span>

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

### <a name="samples"></a><span data-ttu-id="e58fd-121">Примеры</span><span class="sxs-lookup"><span data-stu-id="e58fd-121">Samples</span></span>

<span data-ttu-id="e58fd-122">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="e58fd-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
