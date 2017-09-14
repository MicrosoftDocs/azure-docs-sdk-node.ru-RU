---
title: "Разработка приложений Node.js с помощью Visual Studio Code и Azure"
description: "Выполните инструкции из этого руководства, в котором объясняется, как создать приложение Node.js, поместить его в образ Docker и развернуть в Azure"
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2017
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="445ed-103">Разработка приложений Node.js с помощью Visual Studio Code и Azure</span><span class="sxs-lookup"><span data-stu-id="445ed-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="445ed-104">В этом руководстве объясняется, как контейнезировать существующее приложение Node.js (с помощью Docker) и развернуть его в Azure с помощью Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="445ed-105">В руководстве используется простое приложение со списком задач, созданное и опубликованное [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span><span class="sxs-lookup"><span data-stu-id="445ed-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="445ed-106">Это одностраничное приложение MEAN, которое использует MongoDB в качестве базы данных, Node/Express для API REST/веб-сервера и Angular.js 1.x для внешнего пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="445ed-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="445ed-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="445ed-107">Prerequisites</span></span>

<span data-ttu-id="445ed-108">Чтобы продолжить работу с примером, подготовьте следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="445ed-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="445ed-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="445ed-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="445ed-110">Docker</span><span class="sxs-lookup"><span data-stu-id="445ed-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="445ed-111">Учетная запись DockerHub</span><span class="sxs-lookup"><span data-stu-id="445ed-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="445ed-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="445ed-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="445ed-113">Учетная запись Azure</span><span class="sxs-lookup"><span data-stu-id="445ed-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="445ed-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="445ed-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="445ed-115">[Chrome](https://www.google.com/chrome/browser/desktop/) — требуется для отладки интерфейса примера приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="445ed-116">MongoDB — так как пример приложения использует MongoDB, требуется выполняющийся в локальной среде экземпляр MongoDB, который прослушивает стандартный порт `27017`.</span><span class="sxs-lookup"><span data-stu-id="445ed-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="445ed-117">Чтобы получить этот экземпляр, после установки Docker выполните две команды: сначала `docker pull mongo`, а затем `docker run -it -p 27017:27017 mongo`.</span><span class="sxs-lookup"><span data-stu-id="445ed-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="445ed-118">Настройка проекта</span><span class="sxs-lookup"><span data-stu-id="445ed-118">Project setup</span></span>

<span data-ttu-id="445ed-119">Чтобы приступить к работе, скачайте пример проекта, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="445ed-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="445ed-120">Откройте Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="445ed-121">Нажмите клавишу **&lt;F1>**, чтобы отобразить палитру команд.</span><span class="sxs-lookup"><span data-stu-id="445ed-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="445ed-122">В строке палитры команд введите `gitcl`, выберите команду **Git: Clone** и нажмите клавишу  **&lt;ВВОД>**.</span><span class="sxs-lookup"><span data-stu-id="445ed-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![Команда gitcl в строке командной палитры Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="445ed-124">Если появится запрос ввести **URL-адрес репозитория**, введите `https://github.com/scotch-io/node-todo`, затем нажмите клавишу **&lt;ВВОД>**.</span><span class="sxs-lookup"><span data-stu-id="445ed-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="445ed-125">Выберите (или создайте) локальный каталог, в который нужно клонировать проект.</span><span class="sxs-lookup"><span data-stu-id="445ed-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Обозреватель Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="445ed-127">Встроенный терминал</span><span class="sxs-lookup"><span data-stu-id="445ed-127">Integrated terminal</span></span>

<span data-ttu-id="445ed-128">Так как это проект Node.js, сначала необходимо установить все зависимости проекта из npm.</span><span class="sxs-lookup"><span data-stu-id="445ed-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="445ed-129">Нажмите клавишу **&lt;CTRL>**, чтобы отобразить встроенный терминал Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="445ed-130">Введите `yarn` и нажмите клавишу **&lt;ВВОД>**.</span><span class="sxs-lookup"><span data-stu-id="445ed-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Выполнение команды yarn в Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="445ed-132">Встроенная система управления версиями Git</span><span class="sxs-lookup"><span data-stu-id="445ed-132">Integrated Git version control</span></span>

<span data-ttu-id="445ed-133">После установки зависимостей приложения с помощью Yarn создается файл `yarn.lock`, который позволяет повторно запрашивать эти же зависимости в будущем без сюрпризов со стороны сборок непрерывной интеграции, рабочих развертываний или компьютеров других разработчиков.</span><span class="sxs-lookup"><span data-stu-id="445ed-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="445ed-134">Ниже показано, как добавить файл `yarn.lock` в систему управления версиями:</span><span class="sxs-lookup"><span data-stu-id="445ed-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="445ed-135">В Visual Studio Code откройте вкладку встроенной системы Git (вкладка с эмблемой Git).</span><span class="sxs-lookup"><span data-stu-id="445ed-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="445ed-136">В поле **Сообщение** введите сообщение фиксации и нажмите клавиши **&lt;CTRL>&lt;ВВОД>**.</span><span class="sxs-lookup"><span data-stu-id="445ed-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Добавление файла yarn.lock в Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="445ed-138">Навигация по проекту и коду</span><span class="sxs-lookup"><span data-stu-id="445ed-138">Project and code navigation</span></span>

<span data-ttu-id="445ed-139">Чтобы ориентироваться в базе кода, поэкспериментируем с возможностями навигации в среде Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="445ed-140">Нажмите клавиши **&lt;CTRL>P**.</span><span class="sxs-lookup"><span data-stu-id="445ed-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="445ed-141">Введите `.js`, чтобы отобразить файлы JavaScript/JSON рядом с родительской папкой каждого файла.</span><span class="sxs-lookup"><span data-stu-id="445ed-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![Отображение всех JS-файлов](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="445ed-143">Выберите файл `server.js`, который является скриптом запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="445ed-144">Наведите указатель мыши на переменную **database** (импортирована в строку 6), чтобы просмотреть ее тип.</span><span class="sxs-lookup"><span data-stu-id="445ed-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="445ed-145">Эта возможность быстро проверять переменные, модули и типы в файле очень удобна при разработке проектов.</span><span class="sxs-lookup"><span data-stu-id="445ed-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![Обнаружение типа](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="445ed-147">Нажмите кнопку мыши в пределах диапазона переменной, например **database**, чтобы просмотреть все ссылки на эту переменную в том же файле.</span><span class="sxs-lookup"><span data-stu-id="445ed-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="445ed-148">Чтобы просмотреть все ссылки на переменную в проекте, щелкните переменную правой кнопкой мыши и в контекстном меню выберите **Найти все ссылки**.</span><span class="sxs-lookup"><span data-stu-id="445ed-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![Поиск ссылок на переменную](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="445ed-150">Вы также можете просмотреть определение переменной, даже если оно находится в другом файле.</span><span class="sxs-lookup"><span data-stu-id="445ed-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="445ed-151">Для этого щелкните правой кнопкой мыши **database.localUrl** (строка 12) и в контекстном меню выберите **Показать определение**.</span><span class="sxs-lookup"><span data-stu-id="445ed-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![Отображение определения переменной](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="445ed-153">Изменение кода и использование автозаполнения</span><span class="sxs-lookup"><span data-stu-id="445ed-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="445ed-154">Строка подключения MongoDB программно задана в объявлении **database.localUrl**.</span><span class="sxs-lookup"><span data-stu-id="445ed-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="445ed-155">Выполнив инструкции из этого раздела, вы измените код, чтобы получить строку подключения из переменной среды. Вы также узнаете о функции автозаполнения Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="445ed-156">Откройте файл `server.js`.</span><span class="sxs-lookup"><span data-stu-id="445ed-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="445ed-157">Замените код</span><span class="sxs-lookup"><span data-stu-id="445ed-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="445ed-158">следующим:</span><span class="sxs-lookup"><span data-stu-id="445ed-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="445ed-159">Обратите внимание: если при вводе кода вручную (вместо копирования и вставки) поставить точку после `process`, Visual Studio Code отобразит список доступных элементов глобального API **process** Node.js.</span><span class="sxs-lookup"><span data-stu-id="445ed-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![Автозаполнение автоматически отображает элементы API](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="445ed-161">Автозаполнение работает, потому что Visual Studio Code использует TypeScript в фоновом режиме (даже для JavaScript), чтобы передавать информацию о вводе, которая может передаваться в список завершения при вводе.</span><span class="sxs-lookup"><span data-stu-id="445ed-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="445ed-162">Visual Studio Code может определить, что проект является проектом Node.js, и автоматически скачать файл вводимых элементов TypeScript для [Node.js из NPM](https://www.npmjs.com/package/@types/node).</span><span class="sxs-lookup"><span data-stu-id="445ed-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="445ed-163">Файл вводимых элементов позволяет получить автозаполнение для других глобальных значений Node.js, например **Buffer** и **setTimeout**, а также все встроенные модули, такие как **fs** и **http**.</span><span class="sxs-lookup"><span data-stu-id="445ed-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="445ed-164">Кроме встроенных API-интерфейсов Node.js, функция автоматического получения значений также поддерживает более 2000 модулей сторонних производителей, таких как React, Underscore и Express.</span><span class="sxs-lookup"><span data-stu-id="445ed-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="445ed-165">Например, чтобы не позволить Mongoose аварийно завершать работу приложения, если оно не может подключиться к настроенному экземпляру базы данных MongoDB, вставьте следующую строку кода в строку 13:</span><span class="sxs-lookup"><span data-stu-id="445ed-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="445ed-166">Как и при использовании предыдущего кода, вы получите автозаполнение автоматически.</span><span class="sxs-lookup"><span data-stu-id="445ed-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![Автозаполнение автоматически отображает элементы API](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="445ed-168">Модули, которые поддерживает эта функция автозаполнения, можно увидеть в созданном сообществом проекте [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), который является источником для всех определений типов TypeScript.</span><span class="sxs-lookup"><span data-stu-id="445ed-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="445ed-169">Выполнение приложения</span><span class="sxs-lookup"><span data-stu-id="445ed-169">Running the app</span></span>

<span data-ttu-id="445ed-170">Теперь, когда вы познакомились с кодом, пришло время запустить приложение.</span><span class="sxs-lookup"><span data-stu-id="445ed-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="445ed-171">Чтобы запустить приложение из Visual Studio Code, нажмите клавишу **&lt;F5>**.</span><span class="sxs-lookup"><span data-stu-id="445ed-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="445ed-172">При запуске кода с помощью **&lt;F5>** (режим отладки) Visual Studio Code запускает приложение и показывает окно **консоли отладки**, отображающее StdOut для приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![Мониторинг StdOut приложения в консоли отладки](./media/node-howto-e2e/console.png)

<span data-ttu-id="445ed-174">Кроме того, **консоль отладки** подключается к только что запущенному приложению, чтобы вы могли вводить выражения JavaScript, которые будут обрабатываться в приложении. В этой консоли также есть функция автоматического заполнения.</span><span class="sxs-lookup"><span data-stu-id="445ed-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="445ed-175">Чтобы увидеть, как это работает, введите в консоли `process.env`:</span><span class="sxs-lookup"><span data-stu-id="445ed-175">To see this in action, type `process.env` in the console:</span></span>

![Ввод кода в консоль отладки](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="445ed-177">Вы смогли запустить приложение нажатием клавиши **&lt;F5>**, так как открытый сейчас файл является файлом JavaScript (`server.js`).</span><span class="sxs-lookup"><span data-stu-id="445ed-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="445ed-178">Поэтому Visual Studio Code предполагает, что проект является приложением Node.js.</span><span class="sxs-lookup"><span data-stu-id="445ed-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="445ed-179">Закройте все файлы JavaScript в Visual Studio Code и нажмите клавишу **&lt;F5>**. В Visual Studio Code появится запрос на выбор среды:</span><span class="sxs-lookup"><span data-stu-id="445ed-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![Выбор среды выполнения](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="445ed-181">Откройте браузер и перейдите к `http://localhost:8080`, чтобы просмотреть запущенное приложение.</span><span class="sxs-lookup"><span data-stu-id="445ed-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="445ed-182">Введите сообщение в текстовое поле и добавьте или удалите несколько задач, чтобы понять, как работает приложение.</span><span class="sxs-lookup"><span data-stu-id="445ed-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![Запуск приложения со списком задач](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="445ed-184">Отладка</span><span class="sxs-lookup"><span data-stu-id="445ed-184">Debugging</span></span>

<span data-ttu-id="445ed-185">Кроме того что в Visual Studio Code можно запустить приложение и взаимодействовать с ним через консоль, это средство также позволяет задавать точки останова непосредственно в коде.</span><span class="sxs-lookup"><span data-stu-id="445ed-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="445ed-186">Например, нажмите клавиши **&lt;CTRL>P**, чтобы отобразить средство выбора файлов.</span><span class="sxs-lookup"><span data-stu-id="445ed-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="445ed-187">Когда откроется средство выбора файлов, введите `route` и выберите файл `route.js`.</span><span class="sxs-lookup"><span data-stu-id="445ed-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="445ed-188">Установите точку останова на строке 28, представляющей маршрут Express (вызывается, когда приложение пытается добавить запись из списка задач).</span><span class="sxs-lookup"><span data-stu-id="445ed-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="445ed-189">Чтобы задать точку останова, щелкните область слева от номера строки в редакторе, как показано на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="445ed-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Настройка точки останова в Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="445ed-191">Помимо стандартных точек останова, средство Visual Studio Code поддерживает условные точки останова, которые позволяют указать время остановки приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="445ed-192">Чтобы задать условную точку останова, щелкните правой кнопкой мыши область слева от строки, в которой нужно приостановить выполнение, выберите **Добавить условную точку останова...** и укажите выражение JavaScript (например, `foo = "bar"`) или число операций выполнения, определяющих условие, при котором приложение должно быть остановлено.</span><span class="sxs-lookup"><span data-stu-id="445ed-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="445ed-193">Установив точку останова, вернитесь к выполняемому приложению и добавьте запись из списка задач.</span><span class="sxs-lookup"><span data-stu-id="445ed-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="445ed-194">Добавление такой записи немедленно останавливает выполнение приложения на строке 28, где вы задали точку останова:</span><span class="sxs-lookup"><span data-stu-id="445ed-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Visual Studio Code приостанавливает выполнение на точке останова](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="445ed-196">Когда приложение будет приостановлено, можно навести указатель мыши на выражения кода, чтобы просмотреть их текущие значения, проверить локальные переменные или контрольные значения и стек вызовов, а также использовать панель инструментов отладки для пошагового выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="445ed-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="445ed-197">Нажмите клавишу **&lt;F5>**, чтобы возобновить выполнение приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="445ed-198">Отладка полного стека</span><span class="sxs-lookup"><span data-stu-id="445ed-198">Full-stack debugging</span></span>

<span data-ttu-id="445ed-199">Как упоминалось выше, приложение со списком задач — это приложение MEAN, то есть приложение, интерфейс и серверная часть которого написаны с помощью JavaScript.</span><span class="sxs-lookup"><span data-stu-id="445ed-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="445ed-200">То есть, если вы выполняете отладку серверного кода (Node/Express), в определенный момент может потребоваться отладить код интерфейса (Angular).</span><span class="sxs-lookup"><span data-stu-id="445ed-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="445ed-201">Для этого в Visual Studio Code есть множество расширений, в том числе встроенная отладка Chrome.</span><span class="sxs-lookup"><span data-stu-id="445ed-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="445ed-202">Откройте вкладку **Расширения** и введите `chrome` в поле поиска:</span><span class="sxs-lookup"><span data-stu-id="445ed-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Расширение отладки Chrome для Visual Studio Code](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="445ed-204">Выберите расширение с именем **Отладчик для Chrome** и выберите **Установить**.</span><span class="sxs-lookup"><span data-stu-id="445ed-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="445ed-205">Установив расширение отладки Chrome, щелкните **Перезагрузить**, чтобы закрыть и снова открыть Visual Studio Code для активации расширения.</span><span class="sxs-lookup"><span data-stu-id="445ed-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Перезагрузка Visual Studio Code после установки расширения отладки Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="445ed-207">Хотя вы смогли выполнить и отладить код Node.js без специальной настройки Visual Studio Code, чтобы отладить внешнее веб-приложение, необходимо создать файл `launch.json`, который сообщает Visual Studio Code, как запускать приложение.</span><span class="sxs-lookup"><span data-stu-id="445ed-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="445ed-208">Чтобы создать файл `launch.json`, откройте вкладку **Отладка**, щелкните значок шестеренки (на нем должна быть небольшая красная точка вверху) и выберите среду **node.js**.</span><span class="sxs-lookup"><span data-stu-id="445ed-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![Настройка файла launch.json в Visual Studio Code](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="445ed-210">Созданный файл `launch.json` выглядит, как на снимке экрана ниже. Этот файл сообщает Visual Studio Code, как запустить приложение или как подключиться к нему, чтобы выполнить его отладку.</span><span class="sxs-lookup"><span data-stu-id="445ed-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

<span data-ttu-id="445ed-211">Обратите внимание: средство Visual Studio Code определило, что скриптом запуска приложения является `server.js`.</span><span class="sxs-lookup"><span data-stu-id="445ed-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="445ed-212">Откройте файл `launch.json`, нажмите кнопку **Добавить конфигурацию** (внизу справа) и выберите **Chrome: Launch with userDataDir** (Chrome: запустить с использованием userDataDir).</span><span class="sxs-lookup"><span data-stu-id="445ed-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Добавление конфигурации Chrome в Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="445ed-214">Добавление новой конфигурации запуска для Chrome позволяет отладить внешний код JavaScript.</span><span class="sxs-lookup"><span data-stu-id="445ed-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="445ed-215">Наведите указатель мыши на любой заданный параметр, чтобы увидеть его функцию.</span><span class="sxs-lookup"><span data-stu-id="445ed-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="445ed-216">Кроме того, обратите внимание, что Visual Studio Code автоматически определяет URL-адрес приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="445ed-217">Задайте для свойства **webRoot** значение `${workspaceRoot}/public`, чтобы отладчик Chrome знал, где найти внешние ресурсы приложения:</span><span class="sxs-lookup"><span data-stu-id="445ed-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

<span data-ttu-id="445ed-218">Чтобы запустить или выполнить отладку внешнего и внутреннего кода одновременно, необходимо создать *комплексную* конфигурацию запуска, которая сообщает средству Visual Studio Code, какой набор конфигураций нужно выполнять параллельно.</span><span class="sxs-lookup"><span data-stu-id="445ed-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="445ed-219">Добавьте следующий фрагмент кода в качестве свойства верхнего уровня в файл `launch.json` (как одноуровневое свойство существующего свойства **configurations**).</span><span class="sxs-lookup"><span data-stu-id="445ed-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="445ed-220">Строковые значения, указанные в массиве **compounds.configurations**, ссылаются на **имя** отдельных записей в списке **конфигураций**.</span><span class="sxs-lookup"><span data-stu-id="445ed-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="445ed-221">Если вы уже изменили эти имена, внесите соответствующие изменения в массив.</span><span class="sxs-lookup"><span data-stu-id="445ed-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="445ed-222">Чтобы увидеть, как это работает, перейдите на вкладку "Отладка" и выберите для выбранной конфигурации значение **Полный стек** (имя составного конфигурации) и нажмите клавишу **&lt;F5>** для запуска.</span><span class="sxs-lookup"><span data-stu-id="445ed-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Выполнение конфигурации в Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="445ed-224">Выполнение конфигурации запускает приложение Node.js (это можно увидеть в выходных данных консоли отладки) и Chrome (который настроен для перехода к приложению Node.js по адресу `http://localhost:8080`).</span><span class="sxs-lookup"><span data-stu-id="445ed-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="445ed-225">Нажмите клавиши **&lt;Ctrl>P** и введите (или выберите) значение `todos.js`, которое является основным контроллером Angular внешней части приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="445ed-226">Установите точку останова на строке 11, которая является точкой входа для создаваемой записи из списка задач.</span><span class="sxs-lookup"><span data-stu-id="445ed-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="445ed-227">Вернитесь к выполняемому приложению и добавьте новую запись. Вы увидите, что средство Visual Studio Code приостановило выполнение кода Angular.</span><span class="sxs-lookup"><span data-stu-id="445ed-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Отладка внешнего кода в Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="445ed-229">Как и во время отладки Node.js, можно навести указатель мыши на выражения, просмотреть локальные переменные и контрольные значения, обработать выражения в консоли и т. д.</span><span class="sxs-lookup"><span data-stu-id="445ed-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="445ed-230">Необходимо обратить внимание на два важных момента.</span><span class="sxs-lookup"><span data-stu-id="445ed-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="445ed-231">В области **Стек вызовов** отображаются два разных стека: **Node** и **Chrome**. При этом указано, какой из стеков приостановлен.</span><span class="sxs-lookup"><span data-stu-id="445ed-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="445ed-232">Можно переходить между внутренним и внешним кодом.</span><span class="sxs-lookup"><span data-stu-id="445ed-232">You can step between front and back-end code.</span></span> <span data-ttu-id="445ed-233">Нажмите клавишу **&lt;F5>**, чтобы запустить и активировать точку останова, заданную ранее в маршруте Express.</span><span class="sxs-lookup"><span data-stu-id="445ed-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="445ed-234">После этого вы можете эффективно отладить внешний и внутренний код JavaScript или код полного стека JavaScript непосредственно в Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="445ed-235">Концепция комплексного отладчика не ограничивается только двумя целевыми процессами и кодом JavaScript.</span><span class="sxs-lookup"><span data-stu-id="445ed-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="445ed-236">Поэтому, если вы работаете с приложением-микрослужбой (это может быть polyglot), можно использовать тот же рабочий процесс (после установки соответствующих расширений для языка или платформы).</span><span class="sxs-lookup"><span data-stu-id="445ed-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="445ed-237">Включение приложения в образ Docker</span><span class="sxs-lookup"><span data-stu-id="445ed-237">Dockerizing the app</span></span>

<span data-ttu-id="445ed-238">В этом разделе рассказывается о возможностях Visual Studio Code для разработки с помощью [Docker](https://www.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="445ed-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="445ed-239">Разработчики Node.js используют Docker, чтобы предоставлять развертывания переносимых приложений для сред разработки, непрерывной интеграции и рабочих сред.</span><span class="sxs-lookup"><span data-stu-id="445ed-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="445ed-240">Так как Docker является довольно сложным инструментом, Visual Studio Code предоставляет расширение, которое помогает использовать Docker в приложениях.</span><span class="sxs-lookup"><span data-stu-id="445ed-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="445ed-241">Вернитесь на вкладку **Расширения**, выполните поиск по запросу `docker` и выберите расширение **Docker**.</span><span class="sxs-lookup"><span data-stu-id="445ed-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="445ed-242">Установите расширение Docker, а затем перезагрузите Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Установка расширения Docker для Visual Studio Code](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="445ed-244">Расширение Docker для Visual Studio Code включает команду для создания *Dockerfile* и файла `docker-compose.yml` для существующего проекта.</span><span class="sxs-lookup"><span data-stu-id="445ed-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="445ed-245">Чтобы просмотреть доступные команды Docker, откройте палитру команд. Для этого нажмите клавишу **&lt;F1>** и введите `docker`.</span><span class="sxs-lookup"><span data-stu-id="445ed-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="445ed-246">Команды для Visual Studio, которые поддерживает расширение Docker</span><span class="sxs-lookup"><span data-stu-id="445ed-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="445ed-247">Выберите **Docker: Add docker files to workspace** (Docker: добавление файлов docker в рабочую область), выберите **Node.js** в качестве платформы приложения и укажите, что приложение предоставляет порт `8080`.</span><span class="sxs-lookup"><span data-stu-id="445ed-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="445ed-248">Команда Docker создает полный файл `Dockerfile` и файлы docker-compose, которые вы можете сразу использовать.</span><span class="sxs-lookup"><span data-stu-id="445ed-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![Созданный файл Dockerfile](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="445ed-250">Расширение Docker также обеспечивает автоматическое заполнение для файлов `Dockerfiles` и `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="445ed-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="445ed-251">Чтобы увидеть, как это работает, откройте `Dockerfile` и измените строку 2:</span><span class="sxs-lookup"><span data-stu-id="445ed-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="445ed-252">на:</span><span class="sxs-lookup"><span data-stu-id="445ed-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="445ed-253">Установите курсор после `t` в `mhart`, нажмите клавиши **&lt;CTRL>&lt;Пробел>**, чтобы просмотреть все репозитории образов, которые команда `mhart` опубликовала в DockerHub.</span><span class="sxs-lookup"><span data-stu-id="445ed-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Автоматическое заполнение расширения Docker](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="445ed-255">Выберите команду `mhart/alpine-node`, которая предоставляет все необходимое для приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="445ed-256">Лучше создавать небольшие образы, так как с их помощью приложения можно быстрее построить и развернуть. Это позволяет быстрее распространять их и масштабировать.</span><span class="sxs-lookup"><span data-stu-id="445ed-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="445ed-257">Теперь, когда вы создали файл `Dockerfile`, нужно собрать фактический образ Docker.</span><span class="sxs-lookup"><span data-stu-id="445ed-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="445ed-258">Не забывайте, что можно использовать команду, которую установило расширение Docker в Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="445ed-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="445ed-259">Нажмите клавишу **&lt;F1>**, введите `dockerb` на палитре команд, а затем выберите команду **Docker: Build Image** (Docker: сборка образа).</span><span class="sxs-lookup"><span data-stu-id="445ed-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="445ed-260">Выберите файл `/Dockerfile`, который вы только что создали и изменили.</span><span class="sxs-lookup"><span data-stu-id="445ed-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="445ed-261">Укажите тег, который включает в себя имя пользователя DockerHub (например, `lostintangent/node`).</span><span class="sxs-lookup"><span data-stu-id="445ed-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="445ed-262">Нажмите клавишу **&lt;ВВОД>**, чтобы запустить встроенное окно терминала, в котором отображаются выходные данные создаваемого образа Docker.</span><span class="sxs-lookup"><span data-stu-id="445ed-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![Состояние сборки образа Docker](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="445ed-264">Обратите внимание, что команда автоматизировала процесс выполнения `docker build`. Это еще одна возможность повысить производительность. Либо можно использовать интерфейс командной строки Docker CLI напрямую.</span><span class="sxs-lookup"><span data-stu-id="445ed-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="445ed-265">На этом этапе развернутые приложения могут легко получить этот образ. Достаточно просто передать образ в DockerHub.</span><span class="sxs-lookup"><span data-stu-id="445ed-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="445ed-266">Чтобы сделать это, войдите в DockerHub, запустив `docker login` из интерфейса командной строки и введя учетные данные своей учетной записи.</span><span class="sxs-lookup"><span data-stu-id="445ed-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="445ed-267">Затем можно открыть палитру команд в Visual Studio Code. Для этого введите `dockerpush` и выберите команду `Docker: Push`.</span><span class="sxs-lookup"><span data-stu-id="445ed-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="445ed-268">Выберите только что созданный тег изображения (например, `lostintangent/node`) и нажмите клавишу **&lt;ВВОД>**.</span><span class="sxs-lookup"><span data-stu-id="445ed-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="445ed-269">Команда автоматизирует вызов `docker push` и отображает выходные данные в окне встроенного терминала.</span><span class="sxs-lookup"><span data-stu-id="445ed-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="445ed-270">Развертывание приложения</span><span class="sxs-lookup"><span data-stu-id="445ed-270">Deploying the app</span></span>

<span data-ttu-id="445ed-271">Теперь, когда вы поместили приложение в образ Docker и передали его в DockerHub, необходимо развернуть приложение в облаке, чтобы оно стало доступным для пользователей.</span><span class="sxs-lookup"><span data-stu-id="445ed-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="445ed-272">Для этого используйте службу приложений Azure, которая является предложением Azure PaaS.</span><span class="sxs-lookup"><span data-stu-id="445ed-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="445ed-273">В службе приложений есть две возможности для разработчиков Node.js:</span><span class="sxs-lookup"><span data-stu-id="445ed-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="445ed-274">Поддержка виртуальных машин Linux, минимизирующая несовместимость для приложений, которые созданы с помощью собственных модулей Node, или другие средства, которые могут не поддерживать Windows и (или) вести себя иначе.</span><span class="sxs-lookup"><span data-stu-id="445ed-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="445ed-275">Поддержка развертываний Docker, которая позволяет указать имя образа Docker и дает возможность службе приложений извлекать, развертывать и масштабировать образ автоматически.</span><span class="sxs-lookup"><span data-stu-id="445ed-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="445ed-276">Чтобы приступить к работе, откройте терминал Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="445ed-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="445ed-277">Для управления учетной записью Azure и подготовки инфраструктуры, необходимой для запуска приложения со списком задач, используйте версию Azure CLI 2.0.</span><span class="sxs-lookup"><span data-stu-id="445ed-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="445ed-278">Войдите в учетную запись из интерфейса командной строки с помощью команды `az login` (как указано в предварительных условиях). Выполните следующие действия, чтобы подготовить экземпляр службы приложений и развернуть контейнер приложения со списком задач:</span><span class="sxs-lookup"><span data-stu-id="445ed-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="445ed-279">Создайте группу ресурсов, которую можно будет использовать как *пространство имен* или *каталог* для организации ресурсов Azure.</span><span class="sxs-lookup"><span data-stu-id="445ed-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="445ed-280">С помощью параметра `-n` укажите имя группы.</span><span class="sxs-lookup"><span data-stu-id="445ed-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="445ed-281">Параметр `-l` указывает расположение группы ресурсов.</span><span class="sxs-lookup"><span data-stu-id="445ed-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="445ed-282">В предварительной версии службы приложений для Linux можно было только выбирать регионы.</span><span class="sxs-lookup"><span data-stu-id="445ed-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="445ed-283">Поэтому, если вы не находитесь в западной части США и хотите узнать, какие регионы доступны, выполните в CLI команду `az appservice list-locations --linux-workers-enabled`, чтобы просмотреть варианты выбора центра обработки данных.</span><span class="sxs-lookup"><span data-stu-id="445ed-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="445ed-284">Назначьте созданную группу ресурсов группой ресурсов по умолчанию, чтобы продолжить использовать CLI и не указывать группу ресурсов при каждом вызове CLI:</span><span class="sxs-lookup"><span data-stu-id="445ed-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="445ed-285">Создайте *план* службы приложений, управляющий созданием и масштабированием базовой виртуальной машины, на которой развертывается приложение.</span><span class="sxs-lookup"><span data-stu-id="445ed-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="445ed-286">Еще раз укажите любое значение для параметра `n`.</span><span class="sxs-lookup"><span data-stu-id="445ed-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="445ed-287">Параметр --is-linux указывает, что вы создаете виртуальные машины под управлением Linux.</span><span class="sxs-lookup"><span data-stu-id="445ed-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="445ed-288">Без этого параметра CLI по умолчанию подготавливает виртуальные машины под управлением Windows.</span><span class="sxs-lookup"><span data-stu-id="445ed-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="445ed-289">Создайте веб-приложение, представляющее фактическое приложение со списком задач, которое будет выполняться в плане и группе ресурсов, которые вы только что создали.</span><span class="sxs-lookup"><span data-stu-id="445ed-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="445ed-290">Веб-приложение можно считать процессом или контейнером, а план — виртуальной машиной или узлом контейнера, где выполняется веб-приложение.</span><span class="sxs-lookup"><span data-stu-id="445ed-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="445ed-291">При создании веб-приложения необходимо также настроить его для использования образа Docker, опубликованного в DockerHub:</span><span class="sxs-lookup"><span data-stu-id="445ed-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="445ed-292">Если вместо пользовательского контейнера вы предпочитаете развертывание Git, см. статью о [создании веб-приложения Node.js в Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span><span class="sxs-lookup"><span data-stu-id="445ed-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="445ed-293">Назначьте веб-приложение веб-экземпляром по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="445ed-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="445ed-294">Запустите приложение для просмотра развернутого контейнера, который можно найти по URL-адресу `*.azurewebsites.net`:</span><span class="sxs-lookup"><span data-stu-id="445ed-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![Приложение со списком задач, выполняющееся в браузере](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="445ed-296">Первый запуск приложения может длиться несколько минут, так как служба приложений должна извлечь образ Docker из DockerHub и запустить его.</span><span class="sxs-lookup"><span data-stu-id="445ed-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="445ed-297">На этом этапе вы развернули и запустили приложение со списком задач.</span><span class="sxs-lookup"><span data-stu-id="445ed-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="445ed-298">Теперь у вас есть приложение со списком задач.</span><span class="sxs-lookup"><span data-stu-id="445ed-298">You have now deployed the todo app.</span></span> <span data-ttu-id="445ed-299">Но вращающийся значок означает, что приложение не может подключиться к базе данных.</span><span class="sxs-lookup"><span data-stu-id="445ed-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="445ed-300">Это связано с тем, что во время разработки вы использовали локальный экземпляр MongoDB, который не доступен из центров обработки данных Azure.</span><span class="sxs-lookup"><span data-stu-id="445ed-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="445ed-301">Так как вы изменили приложение, чтобы принимать строку подключения с помощью переменной среды, достаточно запустить сервер MongoDB и повторно настроить экземпляр службы приложений, чтобы она ссылалась на переменную среды.</span><span class="sxs-lookup"><span data-stu-id="445ed-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="445ed-302">В следующем разделе объясняется, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="445ed-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="445ed-303">Подготовка сервера MongoDB</span><span class="sxs-lookup"><span data-stu-id="445ed-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="445ed-304">Вы можете настроить сервер MongoDB или набор реплик и самостоятельно управлять ИТ-инфраструктурой, но вы также можете использовать решение Azure, которое называется [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span><span class="sxs-lookup"><span data-stu-id="445ed-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="445ed-305">Cosmos DB — это полностью управляемая высокопроизводительная база данных NoSQL с функцией георепликации, которая обеспечивает уровень совместимости MongoDB.</span><span class="sxs-lookup"><span data-stu-id="445ed-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="445ed-306">Это означает, что вы можете указать в ней приложение MEAN (или любой клиент либо средство MongoDB, например [Studio 3T](https://studio3t.com/)) и вам не нужно будет ничего изменять, кроме строки подключения.</span><span class="sxs-lookup"><span data-stu-id="445ed-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="445ed-307">Далее объясняется, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="445ed-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="445ed-308">В терминале Visual Studio Code выполните следующую команду, чтобы создать экземпляр службы Cosmos DB, совместимый с MongoDB.</span><span class="sxs-lookup"><span data-stu-id="445ed-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="445ed-309">Замените заполнитель **<NAME>** глобально уникальным значением (Cosmos DB использует это имя для создания URL-адреса сервера базы данных):</span><span class="sxs-lookup"><span data-stu-id="445ed-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="445ed-310">Получите строку подключения MongoDB для этого экземпляра:</span><span class="sxs-lookup"><span data-stu-id="445ed-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="445ed-311">Обновите переменную среды веб-приложения **MONGODB_URL**, чтобы она подключилась к новому экземпляру Cosmos DB и не пыталась подключиться к локальному серверу MongoDB (которого не существует):</span><span class="sxs-lookup"><span data-stu-id="445ed-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="445ed-312">Вернитесь в браузер и обновите его.</span><span class="sxs-lookup"><span data-stu-id="445ed-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="445ed-313">Попробуйте добавить и удалить элемент списка задач, чтобы убедиться, что приложение работает и в нем не нужно ничего менять.</span><span class="sxs-lookup"><span data-stu-id="445ed-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="445ed-314">Задайте для переменной среды созданный экземпляр Cosmos DB, который является полной эмуляцией базы данных MongoDB.</span><span class="sxs-lookup"><span data-stu-id="445ed-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![Демонстрация приложения после подключения к базе данных](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="445ed-316">При необходимости можно переключиться обратно на экземпляр базы данных Cosmos DB и увеличить или уменьшить масштаб зарезервированной пропускной способности, необходимой экземпляру MongoDB. Тогда вы получите дополнительный трафик, изменяя инфраструктуру вручную.</span><span class="sxs-lookup"><span data-stu-id="445ed-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="445ed-317">Cosmos DB автоматически индексирует каждый документ и его свойства.</span><span class="sxs-lookup"><span data-stu-id="445ed-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="445ed-318">Поэтому вам не нужно профилировать медленные запросы или вручную регулировать индексы.</span><span class="sxs-lookup"><span data-stu-id="445ed-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="445ed-319">Просто выполните подготовку и масштабирование, а все остальное сделает Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="445ed-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="445ed-320">Размещение частного реестра Docker</span><span class="sxs-lookup"><span data-stu-id="445ed-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="445ed-321">DockerHub позволяет распространять образы контейнера. Но иногда вам может понадобиться разместить собственный частный реестр Docker, например, чтобы повысить безопасность или производительность либо для более удобного управления.</span><span class="sxs-lookup"><span data-stu-id="445ed-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="445ed-322">Для этого Azure предоставляет [реестр контейнеров Azure](https://azure.microsoft.com/services/container-registry/) (ACR), который позволяет вам создать собственный реестр Docker, резервное хранилище которого находится в том же центре обработки данных, что и ваше веб-приложение (благодаря этому извлечение происходит быстрее).</span><span class="sxs-lookup"><span data-stu-id="445ed-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="445ed-323">ACR также предоставляет полный контроль над содержимым и элементами управления доступом. То есть вы решаете, кто может отправлять и извлекать образы.</span><span class="sxs-lookup"><span data-stu-id="445ed-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="445ed-324">Чтобы подготовить пользовательский реестр, выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="445ed-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="445ed-325">Замените заполнитель **<NAME>** глобальным уникальным значением, которое ACR использует для создания URL-адреса сервера входа в реестр.</span><span class="sxs-lookup"><span data-stu-id="445ed-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="445ed-326">Хотя в этих инструкциях для примера используется **учетная запись администратора**, не рекомендуется использовать ее в рабочих реестрах.</span><span class="sxs-lookup"><span data-stu-id="445ed-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="445ed-327">Команды `az acr create` отображают URL-адрес сервера входа (в столбце `LOGIN SERVER`), используемого для входа с помощью Docker CLI (например, `ninademo.azurecr.io`).</span><span class="sxs-lookup"><span data-stu-id="445ed-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="445ed-328">Кроме того, команда создает учетные данные администратора, которые можно использовать для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="445ed-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="445ed-329">Чтобы получить такие учетные данные, выполните следующую команду и запишите отображаемое имя пользователя и пароль:</span><span class="sxs-lookup"><span data-stu-id="445ed-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="445ed-330">С помощью учетных данных, созданных на предыдущем шаге, и отдельного имени входа сервера вы можете войти в реестр, используя стандартный рабочий процесс Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="445ed-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="445ed-331">Теперь вы можете отметить тегами свой контейнер Docker, чтобы определить связь с частным реестром. Для этого выполните следующую команду (замените `lostintangent/node` именем образа контейнера):</span><span class="sxs-lookup"><span data-stu-id="445ed-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="445ed-332">Отправьте отмеченный тегами образ в свой частный реестр Docker.</span><span class="sxs-lookup"><span data-stu-id="445ed-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="445ed-333">Контейнер теперь хранится в частном реестре. С помощью Docker CLI вы можете продолжать работать с ним, как и при использовании DockerHub.</span><span class="sxs-lookup"><span data-stu-id="445ed-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="445ed-334">Чтобы настроить веб-приложение службы приложений извлекать образ из частного реестра, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="445ed-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="445ed-335">Обязательно добавьте префикс `https://` в начало параметра `-r`.</span><span class="sxs-lookup"><span data-stu-id="445ed-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="445ed-336">Не добавляйте префикс к имени образа контейнера.</span><span class="sxs-lookup"><span data-stu-id="445ed-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="445ed-337">Если обновить приложение в браузере, оно будет выглядеть и работать, как раньше.</span><span class="sxs-lookup"><span data-stu-id="445ed-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="445ed-338">Но теперь приложение работает с использованием вашего частного реестра Docker.</span><span class="sxs-lookup"><span data-stu-id="445ed-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="445ed-339">Обновив приложение, отметьте тегами и отправьте изменения, как показано выше, а также обновите тег в конфигурации контейнера службы приложений.</span><span class="sxs-lookup"><span data-stu-id="445ed-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="445ed-340">Настройка пользовательского доменного имени</span><span class="sxs-lookup"><span data-stu-id="445ed-340">Configuring a custom domain name</span></span>

<span data-ttu-id="445ed-341">Хотя URL-адрес `*.azurewebsites.net` отлично подходит для тестирования, в определенный момент может потребоваться добавить собственное доменное имя для веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="445ed-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="445ed-342">Получив доменное имя у регистратора, вам нужно только добавить запись `A`, которая указывает на внешний IP-адрес веб-приложения (который фактически является подсистемой балансировки нагрузки).</span><span class="sxs-lookup"><span data-stu-id="445ed-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="445ed-343">Чтобы получить этот IP-адрес, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="445ed-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="445ed-344">Кроме добавления записи `A`, добавьте запись `TXT` к своему домену, которая указывает на домен `*.azurewebsites.net`, используемый вами до сих пор.</span><span class="sxs-lookup"><span data-stu-id="445ed-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="445ed-345">Сочетание записей `A` и `TXT` позволяет Azure убедиться в том, что вы являетесь владельцем домена.</span><span class="sxs-lookup"><span data-stu-id="445ed-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="445ed-346">Создав эти записи и распространив изменения DNS, зарегистрируйте пользовательский домен в Azure, чтобы входящий трафик обрабатывался правильно.</span><span class="sxs-lookup"><span data-stu-id="445ed-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="445ed-347">Команда не будет работать, пока не будут распространены изменения в DNS.</span><span class="sxs-lookup"><span data-stu-id="445ed-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="445ed-348">Откройте браузер и перейдите к пользовательскому домену, чтобы увидеть, что он разрешается в развернутое приложение в Azure.</span><span class="sxs-lookup"><span data-stu-id="445ed-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="445ed-349">Увеличение и уменьшение масштаба</span><span class="sxs-lookup"><span data-stu-id="445ed-349">Scaling up and out</span></span>

<span data-ttu-id="445ed-350">Ваше веб-приложение может стать настолько популярным, что его выделенных ресурсов (ЦП и ОЗУ) может не хватать для обработки увеличенного трафика и выполнения операций.</span><span class="sxs-lookup"><span data-stu-id="445ed-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="445ed-351">План службы приложений, который вы создали ранее (**B1**), предоставляет 1 ядро ЦП и 1,75 ГБ ОЗУ. Эти ресурсы можно израсходовать достаточно быстро.</span><span class="sxs-lookup"><span data-stu-id="445ed-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="445ed-352">В плане **В2** можно увеличить объем ЦП и ОЗУ в два раза. Поэтому, если вы заметили, что приложению не хватает одного из ресурсов, можно увеличить масштаб базовой виртуальной машины. Для этого выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="445ed-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="445ed-353">Сведения о ценах и спецификации планов службы приложений Azure см. на странице с [ценами службы приложений](https://azure.microsoft.com/pricing/details/app-service/).</span><span class="sxs-lookup"><span data-stu-id="445ed-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="445ed-354">Через несколько секунд веб-приложение будет перенесено на запрошенное оборудование и начнет использовать соответствующие ресурсы.</span><span class="sxs-lookup"><span data-stu-id="445ed-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="445ed-355">Вы также можете уменьшить масштаб ресурсов. Это можно сделать с помощью той же команды. Только нужно выбрать параметр `--sku`, который предоставляет меньше ресурсов по более низкой цене.</span><span class="sxs-lookup"><span data-stu-id="445ed-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="445ed-356">Если ваше веб-приложение работает без отслеживания состояния, кроме увеличения масштаба спецификаций виртуальной машины, вы также можете *развернуть* рабочую нагрузку, добавив дополнительные экземпляры базовой виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="445ed-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="445ed-357">План службы приложений, созданный ранее, включал только одну виртуальную машину (*рабочая роль*). Поэтому весь входящий трафик ограничивался доступными ресурсами этого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="445ed-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="445ed-358">Если вы хотите добавить второй экземпляр виртуальной машины, выполните ту же команду, которую вы выполняли раньше, но вместо увеличения масштаба SKU увеличьте число рабочих виртуальных машин.</span><span class="sxs-lookup"><span data-stu-id="445ed-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="445ed-359">При развертывании рабочей нагрузки такого веб-приложения входящий трафик будет прозрачно сбалансирован между всеми экземплярами. Это позволит сразу увеличивать производительность, не меняя код или инфраструктуру.</span><span class="sxs-lookup"><span data-stu-id="445ed-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="445ed-360">Веб-приложения без отслеживания состояния рекомендуются для использования, так как они позволяют детерминированно увеличивать и уменьшать масштаб, а также развертывать рабочие нагрузки. Это возможно, так как в такой конфигурации ни виртуальные машины, ни экземпляры приложения не содержат состояние, необходимое для работы.</span><span class="sxs-lookup"><span data-stu-id="445ed-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="445ed-361">Хотя в этой статье приводится пример одного веб-приложения, вы можете создать и развернуть несколько веб-приложений в рамках одного плана службы приложений, чтобы не подготавливать другие планы и не платить за них.</span><span class="sxs-lookup"><span data-stu-id="445ed-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="445ed-362">Очистка</span><span class="sxs-lookup"><span data-stu-id="445ed-362">Clean-up</span></span>

<span data-ttu-id="445ed-363">Чтобы не оплачивать неиспользуемые ресурсы Azure, выполните следующую команду в терминале Visual Studio Code. Так вы удалите все ресурсы, которые были подготовлены при выполнении инструкций из этого руководства.</span><span class="sxs-lookup"><span data-stu-id="445ed-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="445ed-364">Процесс очистки может длиться несколько минут.</span><span class="sxs-lookup"><span data-stu-id="445ed-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="445ed-365">После завершения очистки команда `az group delete` оставит вашу учетную запись Azure в том же состоянии, в котором она была до начала работы с руководством.</span><span class="sxs-lookup"><span data-stu-id="445ed-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="445ed-366">Возможность организовывать, развертывать и удалять ресурсы Azure как единый объект является одним из основных преимуществ групп ресурсов.</span><span class="sxs-lookup"><span data-stu-id="445ed-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="445ed-367">Поэтому рекомендуется группировать ресурсы, для которых вы планируете одинаковое время существования.</span><span class="sxs-lookup"><span data-stu-id="445ed-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>