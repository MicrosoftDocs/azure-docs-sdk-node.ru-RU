---
title: Модули Azure HDInsight для Node.js
description: Справочник по модулям Azure HDInsight для Node.js
ms.service: hdinsight
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.topic: article
ms.devlang: nodejs
ms.date: 07/18/2017
ms.openlocfilehash: e35e0d487efce2a591130403f8b72a43c638fdec
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2018
ms.locfileid: "52101729"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a>Модули Azure HDInsight для Node.js

Azure HDInsight является облачным распределением компонентов Hadoop из платформы данных Hortonworks Data Platform (HDP). Первоначально технология Apache Hadoop была платформой с открытым кодом для распределенной обработки и анализа наборов больших данных в кластерах компьютеров.

Благодаря HDInsight технологии Hadoop просты в использовании. Теперь вам доступно следующее:
- Упрощенная настройка и установка. Дополнительные сведения см. в статье о подготовке кластеров Hadoop в HDInsight.
- Максимальная доступность и надежность. Дополнительные сведения см. в статье о доступности и надежности HDInsight.
- Функции безопасности и управления за счет интеграции с Active Directory. Дополнительные сведения см. в статье о присоединенных к домену кластерах.
- Динамическое масштабирование без прерывания заданий.
- Обновление компонентов и доступность текущих версий. Дополнительные сведения см. в статье о компонентах и версиях, доступных в HDInsight.
- Интеграция с другими службами Azure, включая веб-приложения и базу данных SQL.

Технологическая платформа Hadoop включает связанные программное обеспечение и служебные программы, включая Apache Hive, HBase, Spark, Kafka и т. д. 

## <a name="management-package"></a>Пакет управления

### <a name="install-the-npm-modules"></a>Установка модулей npm

Установите модули Azure HDInsight для Node.js с помощью npm.

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>Пример 

Этот пример создает клиент HD Insight и выводит список всех доступных кластеров. 

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

## <a name="samples"></a>Примеры

См. другие [примеры кода Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs), которые можно использовать в приложениях.
