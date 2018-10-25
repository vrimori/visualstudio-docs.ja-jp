---
title: 'クイック スタート: Visual Studio を使用して初めての Vue.js アプリを作成する'
description: このクイック スタートでは、Node.js Tools for Visual Studio を利用し、Visual Studio で Vue.js アプリを作成します
ms.date: 09/24/2018
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
ms.openlocfilehash: 3862f62439bd9b919d3c0534a8c2fe2d3c16fea9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926619"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>クイック スタート: Visual Studio を使用して初めての Vue.js アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、シンプルな Vue.js Web アプリケーションを作成して実行ます。 Visual Studio 2017 をまだインストールしていない場合は、[Visual Studio のダウンロード](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ページに移動し、無料試用版をインストールしてください。

> [!IMPORTANT]
> この記事には、Visual Studio 2017 バージョン 15.8 以降で使用できる Vue.js テンプレートが必要です。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、Vue.js Web アプリケーション プロジェクトを作成します。

1. Node.js ランタイムがまだインストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。

    一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストールされているランタイムが検出されない場合は、プロパティ ページで、インストールされているランタイムを参照するプロジェクトを構成することができます (プロジェクトを作成した後、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します)。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスが開いたら、**[JavaScript]** の **[Node.js]** か **[TypeScript]** の **[Node.js]** で **[基本的な Vue.js Web アプリケーション]** を選択し、プロジェクト名を入力し、**[OK]** をクリックします。

     ![Vue.js テンプレート](../javascript/media/vuejs-template.png)

    Visual Studio によって新しいプロジェクトが作成されます。 ソリューション エクスプローラーで新しいプロジェクトが開きます (右ウィンドウ)。

     **[基本的な Vue.js Web アプリケーション]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

     ![VS インストーラーの Node.js ワークロード](../ide/media/quickstart-nodejs-workload.png)

    Visual Studio は新しいソリューションを作成し、プロジェクトを開きます。

1. アプリケーションに必要な npm パッケージのインストールの進捗状況は [出力] ウィンドウで確認できます (下ウィンドウ)。

1. ソリューション エクスプローラーで **npm** ノードを開き、必要なすべての npm パッケージが存在するかどうかを確認します。

    不足しているパッケージ (感嘆符のアイコン) がある場合は、**npm** ノードを右クリックして、**[不足している npm パッケージをインストールする]** を選択します。

## <a name="explore-the-ide"></a>IDE を探索する

1. 右ウィンドウの**ソリューション エクスプローラー**を見てください。

     ![Vue.js ソリューション](../javascript/media/vuejs-solution.png)

   - **[新しいプロジェクト]** ダイアログ ボックスに指定した名前が使用され、太字で強調表示されているのがあなたのプロジェクトです。 ディスク上では、このプロジェクトは、プロジェクト フォルダーの *.njsproj* ファイルに該当します。

   - 最上位レベルにあるのは、ソリューションです。既定では、名前はプロジェクトと同じです。 ディスク上の *.sln* ファイルで表されるソリューションは、1 つ以上の関連プロジェクトのコンテナーです。

   - **npm** ノードには、インストールされているすべての npm パッケージが表示されます。 npm ノードを右クリックし、ダイアログ ボックスを使用して npm パッケージを検索し、インストールすることができます。

2. コマンド プロンプトから npm パッケージをインストールするか、Node.js コマンドを実行する場合は、プロジェクト ノードを右クリックし、**[ここでコマンド プロンプトを開く]** を選択します。

## <a name="add-a-vue-file-to-the-project"></a>.vue ファイルをプロジェクトに追加する

1. ソリューション エクスプローラーで、*src* フォルダーなどのフォルダーを右クリックし、**[追加]**、**[新しい項目]** の順に選択します。

1. **[JavaScript Vue 単一ファイル コンポーネント]** または **[TypeScript Vue 単一ファイル コンポーネント]** を選択し、**[追加]** をクリックします。

    Visual Studio によって新しいファイルがプロジェクトに追加されます。

## <a name="build-the-project"></a>プロジェクトをビルドする

1. (TypeScript プロジェクトのみ) Visual Studio から **[ビルド]**、**[ソリューションのクリーン]** の順に選択します。

1. 次に、**[ビルド]**、**[ソリューションのビルド]** の順に選択し、プロジェクトをビルドします。 結果を見るには、**出力**ウィンドウを確認します。

    Vue.js プロジェクト テンプレートでは、ビルド後イベントを構成することで、`build` npm スクリプトが使用されます。 この設定を変更する場合、エクスプローラーからプロジェクト ファイル (*\<プロジェクト名\>.njsproj*) を開き、次のコード行を検索します。

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>アプリケーションの実行

1. **Ctrl** キーを押しながら **F5** キーを押すか、**[デバッグ]、[デバッグなしで開始]** の順に選択してアプリケーションを実行します。

   コンソールに "*Starting Development Server*" というメッセージが表示されます。

   その後、アプリがブラウザーで開きます。

   ![ブラウザーで実行されている Vue.js アプリ](../javascript/media/vuejs-running-app.png)

1. Web ブラウザーを閉じます。

このクイック スタートは完了しました。 Visual Studio IDE と Vue.js について少しはご理解いただけたかと思います。 機能についてさらに深く理解したい場合は、目次の**チュートリアル** セクションに示されているチュートリアルを続行してください。

## <a name="next-steps"></a>次の手順

- [Node.js と Express のチュートリアル](../nodejs/tutorial-nodejs.md)を読む
- [Node.js と React のチュートリアル](../nodejs/tutorial-nodejs-with-react-and-jsx.md)を読む
- [アプリを Linux App Service にデプロイする](../javascript/publish-nodejs-app-azure.md)