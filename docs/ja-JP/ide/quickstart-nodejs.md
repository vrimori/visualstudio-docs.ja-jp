---
title: 'クイック スタート: Visual Studio を使用して初めての Node.js アプリを作成する'
description: このクイック スタートでは、Visual Studio で Node.js アプリを作成します
ms.date: 11/15/2017
ms.prod: visual-studio-dev15
ms.technology: vs-nodejs
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: afc2accc5572ecacc90222a865230daa9b311044
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>クイック スタート: Visual Studio を使用して初めての Node.js アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、単純な Node.js Web アプリケーションを作成します。 Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する
まず、Node.js Web アプリケーション プロジェクトを作成します。

1. Node.js ランタイムがまだインストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。

    一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストール済みのランタイムが検出されない場合は、インストール済みのランタイムを参照するようにプロジェクトを構成することができます。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスで、左ウィンドウの **[JavaScript]** を展開し、**[Node.js]** を選択します。 中央のウィンドウで、**[空白の Node.js Web アプリケーション]** を選択してから **[OK]** を選択します。

     **[空白の Node.js Web アプリケーション]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

     ![VS インストーラーの Node.js ワークロード](../ide/media/quickstart-nodejs-workload.png)

    Visual Studio は新しいソリューションを作成し、プロジェクトを開きます。 *server.js* が左側のウィンドウのエディターで開きます。

## <a name="explore-the-ide"></a>IDE を探索する

1. 右ウィンドウの**ソリューション エクスプローラー**を見てください。

   ![ソリューション エクスプローラー](../ide/media/quickstart-nodejs-solution-explorer.png)

  - **[新しいプロジェクト]** ダイアログ ボックスに指定した名前が使用され、太字で強調表示されているのがあなたのプロジェクトです。 ディスク上では、このプロジェクトは、プロジェクト フォルダーの *.njsproj* ファイルに該当します。

  - 最上位レベルにあるのは、ソリューションです。既定では、名前はプロジェクトと同じです。 ディスク上の *.sln* ファイルで表されるソリューションは、1 つ以上の関連プロジェクトのコンテナーです。

  - npm ノードには、インストールされているすべての npm パッケージが表示されます。 npm ノードを右クリックし、ダイアログ ボックスを使用して npm パッケージを検索し、インストールすることができます。

1. コマンド プロンプトから npm パッケージまたは node.js コマンドをインストールする場合は、プロジェクト ノードを右クリックし、**[ここでコマンド プロンプトを開く]** を選択します。

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

このクイック スタートは完了しました。 Visual Studio IDE について少しはご理解いただけたかと思います。 機能についてさらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="next-steps"></a>次の手順

- [Node.js と Express のチュートリアル](../nodejs/tutorial-nodejs.md)を読む
- [Node.js と React のチュートリアル](../nodejs/tutorial-nodejs-with-react-and-jsx.md)を読む