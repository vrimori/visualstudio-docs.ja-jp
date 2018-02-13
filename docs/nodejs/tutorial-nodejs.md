---
title: "Visual Studio の Node.js の概要 | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a8e6c800ef036d0f6e8e5affae745e541a276284
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Visual Studio の Node.js の概要
このチュートリアルでは、Visual Studio を使用して Node.js を開発します。単純な Node.js Web アプリを作成し、いくつかのコードを追加し、IDE の一部の機能を試し、アプリを実行します。 まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。  

## <a name="create-a-project"></a>プロジェクトを作成する
まず、Node.js Web アプリケーション プロジェクトを作成します。

1. Visual Studio 2017 を開きます。  

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。  

3. **[新しいプロジェクト]** ダイアログ ボックスで、左ウィンドウの **[JavaScript]** を展開し、**[Node.js]** を選択します。 真ん中のウィンドウで **[基本の Azure Node.js Express 4 アプリケーション]** を選択し、**[OK]** を選択します。   

     **[基本の Azure Node.js Express 4 アプリケーション]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。 

    Visual Studio は新しいソリューションを作成し、プロジェクトを開きます。 **app.js** プロジェクト ファイルがエディター (左のウィンドウ) で開きます。 Visual Studio のソリューションとプロジェクトについて詳しくない場合、「[Quickstart: Use Visual Studio to create your first Node.js app](../ide/quickstart-nodejs.md)」 (クイックスタート: Visual Studio を使用して最初の Node.js アプリを作成する) を参照してください。

## <a name="add-some-code"></a>何らかのコードを追加する

1. ソリューション エクスプローラー (右のウィンドウ) で、[views] フォルダーを開き、index.pug を開きます。

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

1. ルート フォルダーに index.js を開きます。

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

1. `data` の後に「`: get`」と入力します。IntelliSense が getData 関数を表示します。 `getData` を選択します。

    ![IntelliSense を使用する](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. `"data"` の前のコンマ (`,`) を削除します。式で緑の構文が強調表示されます。 構文の強調表示にカーソルを合わせます。

    ![構文エラーの表示](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    このメッセージの最後の行から、JavaScript インタープリターはコンマ (`,`) を要求していることがわかります。

1. **[エラー一覧]** タブをクリックします。

    ファイル名と行番号と共に警告と説明が表示されます。

    ![エラー一覧の表示](../nodejs/media/tutorial-nodejs-error-list.png)

1. コードを修正します。`"data"` の前にコンマ (`,`) を追加してください。

## <a name="set-a-breakpoint"></a>ブレークポイントの設定

1. index.js で、次のコード行の前にある左の余白をクリックし、ブレークポイントを設定します。

    `res.render('index', { title: 'Express', "data": getData() });`

    ブレークポイントは、信頼できるデバッグの最も基本的で重要な機能です。 ブレークポイントは、Visual Studio が実行コードを中断する場所を示します。これにより、変数の値またはメモリの動作を確認したり、コードの分岐が実行されるかどうかを確認したりすることができます。 

    ![ブレークポイントの設定](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>アプリケーションの実行

1. デバッグ ツール バーでデバッグ ターゲットを選択します。

    ![デバッグ ターゲットを選択する](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. **Ctrl キーを押しながら F5 キーを押して**アプリケーションを実行します。

    設定したブレークポイントのところでデバッガーが一時停止します。 ここで、アプリの状態を確認できます。

1. `getData` の上にカーソルを合わせ、データヒントでそのプロパティを確認する

    ![変数の検査](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. **F5** キーを押して続行します。

    アプリがブラウザーで開きます。

    ブラウザー ウィンドウで、タイトルとして "Express" を、最初の段落で "Welcome to Express" を確認できます。

1. ボタンをクリックすると、さまざま画像が表示されます。

    ![ブラウザーで実行しているアプリ](../nodejs/media/tutorial-nodejs-running-in-browser.png)  

1. Node.js 対話型ウィンドウを開きます。**[表示]、[その他のウィンドウ]、[Node.js 対話型ウィンドウ]** の順に選択してください。

   ![Node.js 対話型ウィンドウを開く](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    対話型ウィンドウは、`require()` ステートメントの使用を含めた、コードでできるすべてのことをサポートします。 次のスクリーンショットのコードは変数を定義し、Node.js インタープリターの場所を表示します。

   ![Node.js 対話型ウィンドウ](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

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

- [Node.js Tools for Visual Studio](https://github.com/Microsoft/nodejstools/wiki) についてさらに学習する  
- [Visual Studio の IDE](../ide/visual-studio-ide.md) についてさらに学習する  