---
title: 'クイック スタート: Visual Studio を使用して初めての Node.js Web アプリを作成する'
description: このクイック スタートでは、Visual Studio で Node.js アプリを作成します
ms.date: 06/27/2018
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f11396527208862428483744bc1ac3b02583f4c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955493"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>クイック スタート: Visual Studio を使用して初めての Node.js Web アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、単純な Node.js Web アプリケーションを作成します。 Visual Studio 2017 をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、Node.js Web アプリケーション プロジェクトを作成します。

1. Node.js ランタイムがまだインストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。

    一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストールされているランタイムが検出されない場合は、プロパティ ページで、インストールされているランタイムを参照するプロジェクトを構成することができます (プロジェクトを作成した後、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します)。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスで、左ウィンドウの **[JavaScript]** を展開し、**[Node.js]** を選択します。 中央のウィンドウで、**[空白の Node.js Web アプリケーション]** を選択してから **[OK]** を選択します。

     **[空白の Node.js Web アプリケーション]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

     ![VS インストーラーの Node.js ワークロード](../ide/media/quickstart-nodejs-workload.png)

    **[空の Node.js Web アプリケーション]** テンプレートを選択し、**[OK]** をクリックすると、Visual Studio は新しいソリューションを作成し、プロジェクトを開きます。 *server.js* が左側のウィンドウのエディターで開きます。

## <a name="explore-the-ide"></a>IDE を探索する

1. 右ウィンドウの**ソリューション エクスプローラー**を見てください。

   ![ソリューション エクスプローラー](../ide/media/quickstart-nodejs-solution-explorer.png)

   - **[新しいプロジェクト]** ダイアログ ボックスに指定した名前が使用され、太字で強調表示されているのがあなたのプロジェクトです。 ディスク上では、このプロジェクトは、プロジェクト フォルダーの *.njsproj* ファイルに該当します。

   - 最上位レベルにあるのは、ソリューションです。既定では、名前はプロジェクトと同じです。 ディスク上の *.sln* ファイルで表されるソリューションは、1 つ以上の関連プロジェクトのコンテナーです。

   - npm ノードには、インストールされているすべての npm パッケージが表示されます。 npm ノードを右クリックし、ダイアログ ボックスを使用して npm パッケージを検索し、インストールすることができます。

1. コマンド プロンプトから npm パッケージまたは Node.js コマンドをインストールする場合は、プロジェクト ノードを右クリックし、**[ここでコマンド プロンプトを開く]** を選択します。

   ![Node.js コマンド プロンプト](../ide/media/quickstart-nodejs-command-prompt.png)

1. エディター (左ウィンドウ) の *server.js* で、`http.createServer` を選択してから **F12 キー**を押すか、コンテキスト (右クリック) メニューから **[定義に移動]** を選択します。 このコマンドで *index.d.ts* の `createServer` 関数の定義が示されます。

   ![[定義に移動] コンテキスト メニュー](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *server.js* に戻り、このコード行の文字列の末尾 `res.end('Hello World\n');` にカーソルを置き、次のように変更します。

    `res.end('Hello World\n' + res.connection.`

    `connection.` と入力すると、IntelliSense によってコード入力をオートコンプリートするオプションが表示されます。

   ![IntelliSense のオートコンプリート](../ide/media/quickstart-nodejs-intellisense.png)

1. **[localPort]** を選択し、`);` と入力して、次のようにステートメントを完成させます。

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>アプリケーションの実行

1. **Ctrl** キーを押しながら **F5** キーを押すか、**[デバッグ]、[デバッグなしで開始]** の順に選択してアプリケーションを実行します。 アプリがブラウザーで開きます。

1. ブラウザー ウィンドウに "Hello World" とローカルのポート番号が表示されます。

1. Web ブラウザーを閉じます。

Visual Studio IDE と Node.js の入門となるこのクイック スタートは以上で完了です。 機能についてさらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [アプリを Linux App Service にデプロイする](../javascript/publish-nodejs-app-azure.md)

- [Node.js と Express のチュートリアル](../javascript/tutorial-nodejs.md)
- [Node.js と React のチュートリアル](../javascript/tutorial-nodejs-with-react-and-jsx.md)