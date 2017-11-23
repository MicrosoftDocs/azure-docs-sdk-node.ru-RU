---
title: "Модули Azure HDInsight для Node.js"
description: "Справочник по модулям Azure HDInsight для Node.js"
keywords: Azure,SDK,API,HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="c68b8-104">Модули Azure HDInsight для Node.js</span><span class="sxs-lookup"><span data-stu-id="c68b8-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="c68b8-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="c68b8-105">Overview</span></span>

<span data-ttu-id="c68b8-106">Azure HDInsight является облачным распределением компонентов Hadoop из платформы данных Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="c68b8-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="c68b8-107">Первоначально технология Apache Hadoop была платформой с открытым кодом для распределенной обработки и анализа наборов больших данных в кластерах компьютеров.</span><span class="sxs-lookup"><span data-stu-id="c68b8-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="c68b8-108">Благодаря HDInsight технологии Hadoop просты в использовании. Теперь вам доступно следующее:</span><span class="sxs-lookup"><span data-stu-id="c68b8-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="c68b8-109">Упрощенная настройка и установка.</span><span class="sxs-lookup"><span data-stu-id="c68b8-109">Less setup and configuration.</span></span> <span data-ttu-id="c68b8-110">Дополнительные сведения см. в статье о подготовке кластеров Hadoop в HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c68b8-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="c68b8-111">Максимальная доступность и надежность.</span><span class="sxs-lookup"><span data-stu-id="c68b8-111">High availability and reliability.</span></span> <span data-ttu-id="c68b8-112">Дополнительные сведения см. в статье о доступности и надежности HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c68b8-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="c68b8-113">Функции безопасности и управления за счет интеграции с Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c68b8-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="c68b8-114">Дополнительные сведения см. в статье о присоединенных к домену кластерах.</span><span class="sxs-lookup"><span data-stu-id="c68b8-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="c68b8-115">Динамическое масштабирование без прерывания заданий.</span><span class="sxs-lookup"><span data-stu-id="c68b8-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="c68b8-116">Обновление компонентов и доступность текущих версий.</span><span class="sxs-lookup"><span data-stu-id="c68b8-116">Component updates and current versions.</span></span> <span data-ttu-id="c68b8-117">Дополнительные сведения см. в статье о компонентах и версиях, доступных в HDInsight.</span><span class="sxs-lookup"><span data-stu-id="c68b8-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="c68b8-118">Интеграция с другими службами Azure, включая веб-приложения и базу данных SQL.</span><span class="sxs-lookup"><span data-stu-id="c68b8-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="c68b8-119">Технологическая платформа Hadoop включает связанные программное обеспечение и служебные программы, включая Apache Hive, HBase, Spark, Kafka и т. д.</span><span class="sxs-lookup"><span data-stu-id="c68b8-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="c68b8-120">Пакет управления</span><span class="sxs-lookup"><span data-stu-id="c68b8-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="c68b8-121">Установка модулей npm</span><span class="sxs-lookup"><span data-stu-id="c68b8-121">Install the npm modules</span></span>

<span data-ttu-id="c68b8-122">Установите модули Azure HDInsight для Node.js с помощью npm.</span><span class="sxs-lookup"><span data-stu-id="c68b8-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="c68b8-123">Пример</span><span class="sxs-lookup"><span data-stu-id="c68b8-123">Example</span></span> 

<span data-ttu-id="c68b8-124">Этот пример создает клиент HD Insight и выводит список всех доступных кластеров.</span><span class="sxs-lookup"><span data-stu-id="c68b8-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="c68b8-125">Примеры</span><span class="sxs-lookup"><span data-stu-id="c68b8-125">Samples</span></span>

<span data-ttu-id="c68b8-126">См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.</span><span class="sxs-lookup"><span data-stu-id="c68b8-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
