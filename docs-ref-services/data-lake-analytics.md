---
title: "Модули Azure Data Lake Analytics для Node.js"
description: "Справочник по модулям Azure Data Lake Analytics для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 28dae604ae9977eb33470757e207ac12a592c676
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a><span data-ttu-id="33331-103">Модули Azure Data Lake Analytics для Node.js</span><span class="sxs-lookup"><span data-stu-id="33331-103">Azure Data Lake Analytics modules for Node.js</span></span>

<span data-ttu-id="33331-104">Azure Data Lake Analytics — это служба обработки заданий аналитики по запросу, которая позволяет упростить анализ больших данных.</span><span class="sxs-lookup"><span data-stu-id="33331-104">Azure Data Lake Analytics is an on-demand analytics job service to simplify big data analytics.</span></span> <span data-ttu-id="33331-105">Вы можете сосредоточиться на создании, запуске заданий и управлении ими, а не на управлении распределенной инфраструктурой.</span><span class="sxs-lookup"><span data-stu-id="33331-105">You can focus on writing, running, and managing jobs rather than on operating distributed infrastructure.</span></span> <span data-ttu-id="33331-106">Вместо развертывания и настройки оборудования вы пишете запросы для преобразования данных и получения ценных выводов.</span><span class="sxs-lookup"><span data-stu-id="33331-106">Instead of deploying, configuring, and tuning hardware, you write queries to transform your data and extract valuable insights.</span></span> <span data-ttu-id="33331-107">Служба аналитики способна мгновенно выполнять задания любого масштаба, для чего нужно указать необходимый объем ресурсов.</span><span class="sxs-lookup"><span data-stu-id="33331-107">The analytics service can handle jobs of any scale instantly by setting the dial for how much power you need.</span></span> <span data-ttu-id="33331-108">Вы оплачиваете только время выполнения задания, что приводит к значительной экономии средств.</span><span class="sxs-lookup"><span data-stu-id="33331-108">You only pay for your job when it is running, making it cost-effective.</span></span> <span data-ttu-id="33331-109">Служба аналитики поддерживает Azure Active Directory, что позволяет управлять доступом и ролями, интегрированными с локальной системой идентификации.</span><span class="sxs-lookup"><span data-stu-id="33331-109">The analytics service supports Azure Active Directory letting you manage access and roles, integrated with your on-premises identity system.</span></span> <span data-ttu-id="33331-110">Служба также включает U-SQL — язык, который объединяет преимущества SQL с выразительностью пользовательского кода.</span><span class="sxs-lookup"><span data-stu-id="33331-110">It also includes U-SQL, a language that unifies the benefits of SQL with the expressive power of user code.</span></span> <span data-ttu-id="33331-111">Масштабируемая распределенная среда выполнения U-SQL позволяет эффективно анализировать данные в хранилище и на серверах SQL Server в Azure, в базе данных SQL Azure и хранилище данных SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="33331-111">U-SQL’s scalable distributed runtime enables you to efficiently analyze data in the store and across SQL Servers in Azure, Azure SQL Database, and Azure SQL Data Warehouse.</span></span>

### <a name="management-package"></a><span data-ttu-id="33331-112">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="33331-112">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="33331-113">Установка модуля npm</span><span class="sxs-lookup"><span data-stu-id="33331-113">Install the npm module</span></span>

<span data-ttu-id="33331-114">Установите модули Azure Data Lake Analytics для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="33331-114">Use npm to install the Azure Data Lake Analytics modules for Node.js</span></span>

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a><span data-ttu-id="33331-115">Пример</span><span class="sxs-lookup"><span data-stu-id="33331-115">Example</span></span>

<span data-ttu-id="33331-116">Этот пример перечисляет все учетные записи службы аналитики в данной подписке.</span><span class="sxs-lookup"><span data-stu-id="33331-116">This example lists all of the analytics accounts for a given subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a><span data-ttu-id="33331-117">Примеры</span><span class="sxs-lookup"><span data-stu-id="33331-117">Samples</span></span>

<span data-ttu-id="33331-118">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="33331-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
