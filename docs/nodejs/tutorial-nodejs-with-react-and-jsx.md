---
title: Node.js と React のアプリを作成する - Visual Studio | Microsoft Docs
description: このチュートリアルでは Visual Studio で Node.js と React のアプリを作成します
ms.custom: mvc
ms.date: 02/19/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-nodejs
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3c0b387e29df6bc46b8a7c3e79ccb50fa16e3ed6
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>チュートリアル: Visual Studio で Node.js と React のアプリを作成する
Visual Studio では、Node.js プロジェクトを簡単に作成することができ、IntelliSense や、Node.js をサポートする他の組み込み機能を利用できます。 Visual Studio に関するこのチュートリアルでは、Visual Studio のテンプレートから Node.js Web アプリケーション プロジェクトを作成します。 その後、React を使って簡単なアプリを作成します。 

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * Node.js プロジェクトを作成する
> * npm パッケージを追加する
> * アプリに React コードを追加する
> * JSX をトランスパイルする
> * デバッガーをアタッチします。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio および Node.js 開発ワークロードをインストールしている必要があります。

    まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

    ワークロードをインストールする必要があるが、既に Visual Studio を所有している場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **[Node.js 開発]** ワークロードを選択し、**[変更]** を選択します。

* Node.js ランタイムをインストールしている必要があります。

    インストールされていない場合は、LTS バージョンを [Node.js](https://nodejs.org/en/download/) Web サイトからインストールしてください。 一般に、Visual Studio はインストール済みの Node.js ランタイムを自動的に検出します。 インストールされているランタイムが検出されない場合は、プロパティ ページで、インストールされているランタイムを参照するプロジェクトを構成することができます (プロジェクトを作成した後、プロジェクト ノードを右クリックして、**[プロパティ]** を選択します)。

    このチュートリアルは、バージョン 8.9.4 でテストされました。

## <a name="create-a-project"></a>プロジェクトを作成する
まず、Node.js Web アプリケーション プロジェクトを作成します。

1. Visual Studio 2017 を開きます。  

1. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。  

1. **[新しいプロジェクト]** ダイアログ ボックスで、左ウィンドウの **[JavaScript]** を展開し、**[Node.js]** を選択します。 中央のウィンドウで、**[空白の Node.js Web アプリケーション]** を選択し、名前に「**NodejsWebAppBlank**」と入力してから、**[OK]** を選択します。   

     **[空白の Node.js Web アプリケーション]** プロジェクト テンプレートが表示されない場合は、最初に Node.js 開発ワークロードをインストールする必要があります。 

    Visual Studio は新しいソリューションを作成し、プロジェクトを開きます。

    ![ソリューション エクスプローラーでの Node.js プロジェクト](../nodejs/media/tutorial-nodejs-react-project-structure.png)  

    - **[新しいプロジェクト]** ダイアログ ボックスに指定した名前が使用され、太字で強調表示されているのがあなたのプロジェクトです。 ファイル システムでは、このプロジェクトは、プロジェクト フォルダーの *.njsproj* ファイルに該当します。 プロジェクトを右クリックし、**[プロパティ]** を選択することで、プロジェクトに関連付けられたプロパティと環境変数を設定することができます。 プロジェクト ファイルでは Node.js プロジェクト ソースへのカスタム変更が行われないため、他の開発ツールを使用してラウンド トリップを行うことができます。

    - 最上位レベルにあるのは、ソリューションです。既定では、名前はプロジェクトと同じです。 ディスク上の *.sln* ファイルで表されるソリューションは、1 つ以上の関連プロジェクトのコンテナーです。

    - npm ノードには、インストールされているすべての npm パッケージが表示されます。 npm ノードを右クリックし、ダイアログ ボックスを使用して npm パッケージを検索し、インストールすることができます。

    - プロジェクト ノードの下に、*server.js* などのプロジェクト ファイルが表示されます。 *server.js* はプロジェクトのスタートアップ ファイルです。

## <a name="add-npm-packages"></a>npm パッケージを追加する

このアプリを正常に実行するには、複数の npm モジュールが必要です。

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. ソリューション エクスプローラー (右側のウィンドウ) で、プロジェクトの **npm** ノードを右クリックして、**[新しい npm パッケージのインストール]** を選びます。

    **[新しい npm パッケージのインストール]** ダイアログ ボックスでは、最新バージョンのパッケージをインストールするか、バージョンを指定してインストールできます。 最新バージョンのパッケージをインストールして予期しないエラーが発生する場合は、後の手順で説明する厳密なバージョンのパッケージをインストールする必要があります。

1. **[新しい npm パッケージのインストール]** ダイアログ ボックスで、react パッケージを探し、**[パッケージのインストール]** をクリックしてインストールします。

    ![npm パッケージをインストールする](../nodejs/media/tutorial-nodejs-react-install-packages.png)

    **[出力]** ウィンドウに、パッケージのインストールの進行状況が表示されます。 インストールが済むと、**npm** ノードの下にパッケージが表示されます。

    プロジェクトの *package.json* ファイルが、パッケージのバージョンなど、新しいパッケージの情報で更新されます。

1. UI を使って残りのパッケージを 1 つずつ検索して追加する代わりに、次のコードを package.json に貼り付けます。 `dependencies` セクションを次のコードに置き換えます。

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.2.0",
      "react-dom": "16.2.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. プロジェクトで **npm** ノードを右クリックして、**[不足している npm パッケージをインストールする]** を選びます。

    **[出力]** ウィンドウに、パッケージのインストールの進行状況が表示されます。

    npm モジュールがインストールされると、ソリューション エクスプローラーの表示は次のようになります。

    ![npm パッケージ](../nodejs/media/tutorial-nodejs-react-npm-modules.png) 

    > [!NOTE]
    > コマンド ラインを使って npm パッケージをインストールした方がよい場合は、プロジェクト ノードを右クリックし、**[ここでコマンド プロンプトを開く]** を選びます。 Node.js の標準コマンドを使ってパッケージをインストールします。

## <a name="add-project-files"></a>プロジェクト ファイルを追加する

以下の手順では、プロジェクトに 4 つの新しいファイルを追加します。

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

この簡単なアプリでは、プロジェクトのルートに新しいプロジェクト ファイルを追加します (ほとんどのアプリでは、通常、サブフォルダーにファイルを追加し、それに応じて相対パスの参照を調整します)。

1. ソリューション エクスプローラーでプロジェクト **NodejsWebAppBlank** を右クリックし、**[追加]** > **[新しい項目]** を選びます。

1. **[新しい項目の追加]** ダイアログ ボックスで、**[TypeScript JSX ファイル]** を選び、名前に「*app.tsx*」と入力して、**[OK]** をクリックします。

1. 同じ手順を繰り返して *webpack-config.js* を追加します。

1. 同じ手順を繰り返して *index.html* をプロジェクトに追加します。 JavaScript ファイルではなく、**[HTML ファイル]** を選びます。

1. 同じ手順を繰り返して *tsconfig.json* をプロジェクトに追加します。 JavaScript ファイルではなく **[TypeScript JSON 構成ファイル]** を選びます。

## <a name="add-app-code"></a>アプリのコードを追加する

1. *server.js* を開き、コードを次のものと置き換えます。

    ```javascript
    'use strict';
    var http = require('http');
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   上記のコードは、Express を使用し、Web アプリケーション サーバーとして Node.js を起動します。 このコードは、プロジェクトのプロパティで構成されているポート番号にポートを設定します (既定では、ポートはプロパティで 1337 に構成されます)。 プロジェクトのプロパティを開くには、ソリューション エクスプローラーでプロジェクトを右クリックして、**[プロパティ]** を選びます。

1. *app.tsx* を開き、次のコードを追加します。

    ```javascript
    declare var require: any
    
    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    上記のコードは、JSX 構文と React を使って、簡単なメッセージを表示します。

1. *index.html* を開き、**body** セクションを次のコードに置き換えます。

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    この HTML ページは *app-bundle.js* を読み込みます。このファイルには、プレーンな JavaScript にトランスパイルされた JSX と React のコードが含まれます。 現在、*app-bundle.js* ファイルは空です。 次のセクションでは、コードをトランスパイルするためのオプションを構成します。

## <a name="configure-webpack-and-typescript-compiler-options"></a>webpack と TypeScript のコンパイラ オプションを構成する

前の手順では、*webpack-config.js* をプロジェクトに追加しました。 ここでは次に、webpack の構成コードを追加します。 JSX をバンドルしてプレーンな JavaScript にトランスパイルするための入力ファイル (*app.tsx*) と出力ファイル (*app-bundle.js*) を指定する、webpack の簡単な構成を追加します。 トランスパイルについては、TypeScript のコンパイラ オプションもいくつか構成します。 このコードは、webpack と TypeScript コンパイラの概要を説明するための基本的な構成です。

1. ソリューション エクスプローラーで *webpack-config.js* を開き、次のコードを追加します。

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    webpack 構成コードは、TypeScript ローダーを使って JSX をトランスパイルするよう Webpack に指示します。

1. tsconfig.json を開き、TypeScript コンパイラ オプションを指定する次のコードを追加します。

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    app.tsx は、ソース ファイルとして指定されています。

## <a name="transpile-the-jsx"></a>JSX をトランスパイルする

1. ソリューション エクスプローラーで、プロジェクト ノードを右クリックして、**[ここでコマンド プロンプトを開く]** を選びます。

1. コマンド プロンプトに次のコマンドを入力します。

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    コマンド プロンプト ウィンドウに結果が表示されます。

    ![webpack を実行する](../nodejs/media/tutorial-nodejs-react-run-webpack.png) 

    上記の出力ではなく何らかのエラーが表示される場合は、それを解決しないとアプリは動きません。 npm パッケージのバージョンがこのチュートリアルで示されているバージョンと異なる場合は、エラーの原因になる可能性があります。 エラーを修正する方法の 1 つは、前の手順で示されている正確なバージョンを使うことです。 また、これらのパッケージ バージョンの中に使われなくなったものがあるためにエラーが発生する場合は、エラーを修正するにはより新しいバージョンをインストールする必要があります。

1. ソリューション エクスプローラーでプロジェクト ノードを右クリックして、**[追加]** > **[既存のフォルダー]** を選択し、*dist* フォルダーを選んで、**[フォルダーの選択]** をクリックします。

    *dist* フォルダーがプロジェクトに追加されます。このフォルダーには、*app-bundle.js* と *app-bundle.js.map* が含まれます。

1. *app-bundle.js* を開き、トランスパイルされた JavaScript コードを表示します。

1. 外部で変更されたファイルを再度読み込むように求めるメッセージが表示される場合は、**[すべてはい]** をクリックします。

    ![変更されたファイルを読み込む](../nodejs/media/tutorial-nodejs-react-reload-files.png) 

*app.tsx* を変更するたびに、webpack コマンドを再実行する必要があります。

## <a name="run-the-app"></a>アプリを実行する

1. 現在のデバッグ ターゲットとして Chrome が選ばれていることを確認します。

    ![デバッグ ターゲットとして Chrome を選ぶ](../nodejs/media/tutorial-nodejs-react-debug-target.png)  

1. アプリを実行するには、**F5** キーを押すか (**[デバッグ]** > **[デバッグの開始]**)、または緑の矢印ボタンをクリックします。

    Node.js コンソール ウィンドウが開き、デバッガーがリッスンしているポートが示されます。

    Visual Studio は、スタートアップ ファイル *server.js* を起動することにより、アプリを起動します。

    ![ブラウザーで React を実行する](../nodejs/media/tutorial-nodejs-react-running-react.png) 

1. ブラウザー ウィンドウを閉じます。

1. コンソール ウィンドウを閉じます。

## <a name="set-a-breakpoint-and-run-the-app"></a>ブレークポイントを設定してアプリを実行する

1. *server.js* で、`staticPath` 宣言の左側の余白をクリックして、ブレークポイントを設定します。

    ![ブレークポイントの設定](../nodejs/media/tutorial-nodejs-react-set-breakpoint.png) 

    ブレークポイントは、信頼できるデバッグの最も基本的で重要な機能です。 ブレークポイントは、Visual Studio が実行コードを中断する場所を示します。これにより、変数の値またはメモリの動作を確認したり、コードの分岐が実行されるかどうかを確認したりすることができます。 

1. アプリを実行するには、**F5** キー (**[デバッグ]** > **[デバッグの開始]**) を押します。

    設定したブレークポイントでデバッガーが一時停止します (現在のステートメントは黄色でマークされます)。 ここで、**[ローカル]** ウィンドウや **[ウォッチ]** ウィンドウなどのデバッガー ウィンドウを使って、現在スコープ内にある変数をマウスでポイントすることにより、アプリの状態を調べることができます。

1. アプリを続行するには **F5** キーを押します。

1. Chrome の開発者ツールを使う場合は、**F12** キーを押します。 これらのツールでは、DOM を調べたり、JavaScript コンソールを使ってアプリを操作したりできます。

1. Web ブラウザーとコンソールを閉じます。

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>クライアント側の React コードにブレークポイントを設定してヒットする

前のセクションでは、サーバー側の Node.js コードにデバッガーをアタッチしました。 クライアント側の React コードに Visual Studio からデバッガーをアタッチしてブレークポイントをヒットするには、デバッガーが正しいプロセスを識別できるように手助けする必要があります。 ここではその方法の 1 つを示します。

1. Chrome のすべてのウィンドウを閉じます。

1. Windows の **[スタート]** ボタンから **[ファイル名を指定して実行]** コマンドを開き (右クリックして **[ファイル名を指定して実行]** を選択)、次のコマンドを入力します。

    `chrome.exe --remote-debugging-port=9222`

    デバッグが有効な状態で Chrome が起動します。

1. Visual Studio に切り替え、次の図に示すように、*app-bundle.js* のコードの `render()` 関数にブレークポイントを設定します。

    ![ブレークポイントの設定](../nodejs/media/tutorial-nodejs-react-set-breakpoint-client-code.png) 

1. Visual Studio でデバッグ ターゲットとして Chrome を選択し、**Ctrl + F5** キーを押して (**[デバッグ]** > **[デバッグなしで開始]**)、ブラウザーでアプリを実行します。

    アプリがブラウザーの新しいタブで開きます。

1. **[デバッグ]** > **[プロセスにアタッチ]** の順に選びます。

1. **[プロセスにアタッチ]** ダイアログ ボックスの **[アタッチ先]** フィールドで **[Webkit code]\(Webkit コード\)** を選び、フィルター ボックスに「**chrome**」と入力して検索結果をフィルター処理します。

1. 正しいホスト ポート (この例では 1337) の Chrome プロセスを選び、**[アタッチ]** をクリックします。

    ![プロセスにアタッチする](../nodejs/media/tutorial-nodejs-react-attach-to-process.png) 

    Visual Studio で DOM Explorer と JavaScript コンソールが開けば、デバッガーが正しくアタッチしたことがわかります。 これらのデバッグ ツールは、Chrome の開発者ツールや Edge の F12 ツールに似ています。

1. ブレークポイントを設定したコードは既に実行しているので、ブラウザーのページを更新してブレークポイントにヒットします。

    デバッガーで一時停止している間に、変数をマウスでポイントし、デバッガー ウィンドウを使って、アプリの状態を確認できます。 コードをステップ実行することにより (**F5**、**F10**、**F11**)、デバッガーを進めることができます。

    環境とブラウザーの状態に応じて、app-bundle.js 内またはそれにマップされた app.tsx 内の場所で、ブレークポイントにヒットする可能性があります。 どちらの場合も、コードをステップ実行して、変数を確認できます (*.tsx* ファイル内のコードで中断する必要があり、できない場合は、`debugger;` ステートメントを使うか、または Chrome の開発者ツールでブレークポイントを設定してみてください)。

    > [!TIP]
    > 以上の手順に従って初めてプロセスにアタッチした後は、Visual Studio 2017 で **[デバッグ]** > **[プロセスに再アタッチする]** を選ぶことで、同じプロセスにすぐに再アタッチできます。

## <a name="next-steps"></a>次の手順 

このチュートリアルでは、Node.js と React アプリを作成し、JSX をトランスパイルして、デバッグする方法を説明しました。 Node.js Tools for Visual Studio についてさらに学習するには、Wiki のページをご覧ください。

> [!div class="nextstepaction"]
> [Node.js Tools for Visual Studio](https://github.com/Microsoft/nodejstools)