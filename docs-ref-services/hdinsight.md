---
title: "Модули Azure HDInsight для Node.js"
description: "Справочник по модулям Azure HDInsight для Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 897ef2e3d2316a1f6f5637027ac2a2211c556f7a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2018
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="df3b0-103">Модули Azure HDInsight для Node.js</span><span class="sxs-lookup"><span data-stu-id="df3b0-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="df3b0-104">Azure HDInsight является облачным распределением компонентов Hadoop из платформы данных Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="df3b0-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="df3b0-105">Первоначально технология Apache Hadoop была платформой с открытым кодом для распределенной обработки и анализа наборов больших данных в кластерах компьютеров.</span><span class="sxs-lookup"><span data-stu-id="df3b0-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="df3b0-106">Благодаря HDInsight технологии Hadoop просты в использовании. Теперь вам доступно следующее:</span><span class="sxs-lookup"><span data-stu-id="df3b0-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="df3b0-107">Упрощенная настройка и установка.</span><span class="sxs-lookup"><span data-stu-id="df3b0-107">Less setup and configuration.</span></span> <span data-ttu-id="df3b0-108">Дополнительные сведения см. в статье о подготовке кластеров Hadoop в HDInsight.</span><span class="sxs-lookup"><span data-stu-id="df3b0-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="df3b0-109">Максимальная доступность и надежность.</span><span class="sxs-lookup"><span data-stu-id="df3b0-109">High availability and reliability.</span></span> <span data-ttu-id="df3b0-110">Дополнительные сведения см. в статье о доступности и надежности HDInsight.</span><span class="sxs-lookup"><span data-stu-id="df3b0-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="df3b0-111">Функции безопасности и управления за счет интеграции с Active Directory.</span><span class="sxs-lookup"><span data-stu-id="df3b0-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="df3b0-112">Дополнительные сведения см. в статье о присоединенных к домену кластерах.</span><span class="sxs-lookup"><span data-stu-id="df3b0-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="df3b0-113">Динамическое масштабирование без прерывания заданий.</span><span class="sxs-lookup"><span data-stu-id="df3b0-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="df3b0-114">Обновление компонентов и доступность текущих версий.</span><span class="sxs-lookup"><span data-stu-id="df3b0-114">Component updates and current versions.</span></span> <span data-ttu-id="df3b0-115">Дополнительные сведения см. в статье о компонентах и версиях, доступных в HDInsight.</span><span class="sxs-lookup"><span data-stu-id="df3b0-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="df3b0-116">Интеграция с другими службами Azure, включая веб-приложения и базу данных SQL.</span><span class="sxs-lookup"><span data-stu-id="df3b0-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="df3b0-117">Технологическая платформа Hadoop включает связанные программное обеспечение и служебные программы, включая Apache Hive, HBase, Spark, Kafka и т. д.</span><span class="sxs-lookup"><span data-stu-id="df3b0-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="df3b0-118">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="df3b0-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="df3b0-119">Установка модулей npm</span><span class="sxs-lookup"><span data-stu-id="df3b0-119">Install the npm modules</span></span>

<span data-ttu-id="df3b0-120">Установите модули Azure HDInsight для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="df3b0-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="df3b0-121">Пример</span><span class="sxs-lookup"><span data-stu-id="df3b0-121">Example</span></span> 

<span data-ttu-id="df3b0-122">Этот пример создает клиент HD Insight и выводит список всех доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="df3b0-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="df3b0-123">Примеры</span><span class="sxs-lookup"><span data-stu-id="df3b0-123">Samples</span></span>

<span data-ttu-id="df3b0-124">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="df3b0-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
