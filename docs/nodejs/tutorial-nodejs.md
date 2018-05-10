---
title: Node.js と Express のアプリを作成する
description: このチュートリアルでは、Node.js Tools for Visual Studio を使用してアプリを作成します。
ms.custom: ''
ms.date: 03/13/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 259524aa8f4bb20097f5f5504c890ee7f4cc3b78
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>チュートリアル: Visual Studio で Node.js と Express のアプリを作成する
このチュートリアルでは、Node.js と Express を使用して Visual Studio を開発します。単純な Node.js Web アプリを作成し、いくつかのコードを追加し、IDE の一部の機能を試し、アプリを実行します。 まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * Node.js プロジェクトを作成する
> * 何らかのコードを追加する
> * IntelliSense を使用する
> * アプリを実行する
> * ブレークポイントに到達する

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio および Node.js 開発ワークロードをインストールしている必要があります。

    まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

    ワークロードをインストールする必要があるが、既に Visual Studio を所有している場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

* Node.js ランタイムをインストールしている必要があります。

    インストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。 一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストールされているランタイムが検出されない場合は、プロパティ ページで、インストールされているランタイムを参照するプロジェクトを構成することができます (プロジェクトを作成した後、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します)。

    このチュートリアルは、Node.js 8.10.0 でテストされました。

## <a name="create-a-project"></a>プロジェクトを作成する
まず、Node.js Web アプリケーション プロジェクトを作成します。

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスで、左ウィンドウの **[JavaScript]** を展開し、**[Node.js]** を選択します。 真ん中のウィンドウで **[基本の Azure Node.js Express 4 アプリケーション]** を選択し、**[OK]** を選択します。

     **[基本の Azure Node.js Express 4 アプリケーション]** プロジェクト テンプレートが表示されない場合は、最初に **Node.js 開発**ワークロードをインストールする必要があります。

    Visual Studio は新しいソリューションを作成し、プロジェクトを開きます。 *app.js* プロジェクト ファイルがエディター (左のウィンドウ) で開きます。

    - **[新しいプロジェクト]** ダイアログ ボックスに指定した名前が使用され、太字で強調表示されているのがあなたのプロジェクトです。 ファイル システムでは、このプロジェクトは、プロジェクト フォルダーの *.njsproj* ファイルに該当します。 プロジェクトを右クリックし、**[プロパティ]** を選択することで、プロジェクトに関連付けられたプロパティと環境変数を設定することができます。 プロジェクト ファイルでは Node.js プロジェクト ソースへのカスタム変更が行われないため、他の開発ツールを使用してラウンド トリップを行うことができます。

    - 最上位レベルにあるのは、ソリューションです。既定では、名前はプロジェクトと同じです。 ディスク上の *.sln* ファイルで表されるソリューションは、1 つ以上の関連プロジェクトのコンテナーです。

    - npm ノードには、インストールされているすべての npm パッケージが表示されます。 npm ノードを右クリックし、ダイアログ ボックスを使用して npm パッケージを検索し、インストールすることができます。

    - プロジェクト ノードの下に、*app.js* などのプロジェクト ファイルが表示されます。 *app.js* はプロジェクトのスタートアップ ファイルです。

1. **npm** ノードを開き、必要なすべての npm パッケージが存在するかどうかを確認します。

    不足しているパッケージ (感嘆符のアイコン) がある場合は、**npm** ノードを右クリックして、**[不足している npm パッケージをインストールする]** を選択します。

## <a name="add-some-code"></a>何らかのコードを追加する

1. ソリューション エクスプローラー (右のウィンドウ) で、[views] フォルダーを開き、*index.pug* を開きます。

1. 内容を次のマークアップで置換します。

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. ルート フォルダーに *index.js* を開きます。

1. `router.get` の呼び出しの前に次のコードを追加します。

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. `router.get` 関数呼び出しを次のコードで置換します。

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    `res.render` が含まれるコードの行にエラーがあります。 アプリを実行するには、アプリを修正する必要があります。 次のセクションでは、エラーを修正します。

## <a name="use-intellisense"></a>IntelliSense を使用する

1. *index.js* で、`res.render` を含むコードの行に移動します。

1. `data` 文字列の後に「`: get`」と入力します。IntelliSense が `getData` 関数を表示します。 `getData` を選択します。

    ![IntelliSense を使用する](../nodejs/media/tutorial-nodejs-intellisense.png)

1. `"data"` の前のコンマ (`,`) を削除します。式で緑の構文が強調表示されます。 構文の強調表示にカーソルを合わせます。

    ![構文エラーの表示](../nodejs/media/tutorial-nodejs-syntax-checking.png)

    このメッセージの最後の行から、JavaScript インタープリターはコンマ (`,`) を要求していることがわかります。

1. **[エラー一覧]** タブをクリックします。

    ファイル名と行番号と共に警告と説明が表示されます。

    ![エラー一覧の表示](../nodejs/media/tutorial-nodejs-error-list.png)

1. コードを修正します。`"data"` の前にコンマ (`,`) を追加してください。

## <a name="set-a-breakpoint"></a>ブレークポイントの設定

1. *index.js* で、次のコード行の前にある左の余白をクリックし、ブレークポイントを設定します。

    `res.render('index', { title: 'Express', "data": getData() });`

    ブレークポイントは、信頼できるデバッグの最も基本的で重要な機能です。 ブレークポイントは、Visual Studio が実行コードを中断する場所を示します。これにより、変数の値またはメモリの動作を確認したり、コードの分岐が実行されるかどうかを確認したりすることができます。

    ![ブレークポイントの設定](../nodejs/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>アプリケーションの実行

1. デバッグ ツール バーでデバッグ ターゲットを選択します。

    ![デバッグ ターゲットを選択する](../nodejs/media/tutorial-nodejs-deploy-target.png)

1. **F5** キー (**[デバッグ]** > **[デバッグの開始]**) を押してアプリケーションを実行します。

    設定したブレークポイントのところでデバッガーが一時停止します。 ここで、アプリの状態を確認できます。

1. `getData` の上にカーソルを合わせ、データヒントでそのプロパティを確認する

    ![変数の検査](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. **F5** キー (**[デバッグ]** > **[続行]**) を押して続行します。

    アプリがブラウザーで開きます。

    ブラウザー ウィンドウで、タイトルとして "Express" を、最初の段落で "Welcome to Express" を確認できます。

1. ボタンをクリックすると、さまざま画像が表示されます。

    ![ブラウザーで実行しているアプリ](../nodejs/media/tutorial-nodejs-running-in-browser.png)

1. Web ブラウザーを閉じます。

## <a name="optional-publish-to-azure-app-service"></a>(省略可能) Azure App Service に発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

   ![Azure App Service に発行する](../nodejs/media/tutorial-nodejs-publish-to-azure.png)

1. **[Microsoft Azure App Service]** を選択します。

    **[App Service]** ダイアログ サービスで、Azure アカウントにサインインし、既存の Azure サブスクリプションに接続できます。

1. 残りの手順に従い、サブスクリプションを選択し、リソース グループを選択または作成し、App Service プランを選択または作成し、Azure に公開するように求められたらその手順に従います。 詳しい手順については、「[Web 配置を使用して Azure Web サイトに発行する](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)」を参照してください。

1. **[出力]** ウィンドウには、Azure へのデプロイの進捗状況が表示されます。

    デプロイに成功すると、Azure App Service で実行されているアプリがブラウザーで開きます。 ボタンをクリックすると、画像が表示されます。

   ![Azure App Service で実行されているアプリ](../nodejs/media/tutorial-nodejs-running-in-azure.png)

これでこのチュートリアルは完了です。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Express を使用して Node.js アプリを作成して実行し、デバッガーを使用してブレークポイントに到達する方法について学びました。

> [!div class="nextstepaction"]
> [Node.js Tools for Visual Studio](https://github.com/Microsoft/nodejstools)