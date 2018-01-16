---
title: "クイック スタート: Visual Studio を使用して初めての Python Web アプリを作成する | Microsoft Docs"
ms.custom: 
ms.date: 01/08/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload: python
ms.openlocfilehash: 226f673dbd305f9dabf759cb11c6537a2f3ba637
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>クイック スタート: Visual Studio を使用して初めての Python Web アプリを作成する

ここでは 5 分から 10 分で Visual Studio 統合開発環境 (IDE) の概要を示し、簡単な Python Web アプリケーションを作成します。 まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

## <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio 2017 を開きます。

1. 上部のメニュー バーから、**[ファイル] > [新規作成] > [プロジェクト]** の順に選びます。

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[インストール済み]** を展開し、**[Python]** を選びます。

1. 中央のウィンドウで **[Web プロジェクト]** を選び、"HelloPython" のようなプロジェクト名を指定して、**[OK]** を選びます。

    ![Python Web プロジェクトが選択されている [新しいプロジェクト] ダイアログ](media/quickstart-python-00-web-project.png)

    Python のプロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスを取り消し、上部のメニュー バーから **[ツール] > [ツールと機能を取得]** の順に選んで、Visual Studio インストーラーを開きます。 **[Python 開発]** ワークロードを選び、**[変更]** を選びます。

    ![Visual Studio インストーラーの [Python 開発] ワークロード](../python/media/installation-python-workload.png)

1. 右側のウィンドウの**ソリューション エクスプローラー**で、新しいプロジェクトが開きます。 この時点のプロジェクトは、他のファイルが含まれていないため空です。

    ![新しく作成された空のプロジェクトが表示されているソリューション エクスプローラー](media/quickstart-python-01-empty-project.png)

**質問: Visual Studio で Python アプリケーション用のプロジェクトを作成する利点は何ですか。**

回答: 通常、Python アプリケーションはフォルダーとファイルのみを使って定義されますが、アプリケーションが大きくなり、おそらく自動生成されたファイル、Web アプリケーション用 JavaScript などが含まれるようになると、この構造は複雑になる可能性があります。 Visual Studio のプロジェクトは、このような複雑さを管理するのに役立ちます。 プロジェクト (`.pyproj` ファイル) には、プロジェクトに関連付けられたすべてのソース ファイルとコンテンツ ファイルの識別、各ファイルのビルド情報の格納、ソース管理システムと統合するための情報の保持、論理コンポーネントへのアプリケーションの整理の補助などの機能があります。

## <a name="install-the-falcon-library"></a>Falcon ライブラリをインストールする

Python の Web アプリは、ほぼ常に、Web 要求のルーティングや応答の整形といった低レベルの詳細を処理するために、多くの使用可能な Python ライブラリのいずれかを使います。 Visual Studio ではこの目的のために、Bottle、Flask、および Django のフレームワークを使用する Web アプリ用の各種テンプレートを提供します。

ただし、このクイック スタートでは、Falcon ライブラリを使って、パッケージをインストールして Web アプリを最初から作成するプロセスを見ていきます  (Visual Studio には現時点で Falcon 固有のテンプレートが含まれていません)。わかりやすくするため、以下の手順では既定のグローバル環境に Falcon をインストールします。

1. プロジェクトの **[Python 環境]** ノードを展開して、プロジェクトの既定の環境を表示します。

    ![既定の環境が表示されているソリューション エクスプローラー](media/quickstart-python-02-default-environment.png)

1. 環境を右クリックして、**[Python パッケージのインストール]** を選びます。このコマンドを選ぶと、**[Python 環境]** ウィンドウの **[パッケージ]** タブが開きます。検索フィールドに「falcon」と入力し、**["pip install falcon" from PyPI]\(PyPI から "falcon の pip インストール"\)** を選びます。 管理者特権に関するすべてのプロンプトに同意し、Visual Studio の **[出力]** ウィンドウで進行状況を確認します。 (グローバル環境のパッケージ フォルダーが `c:\program files` のように保護された領域内にある場合は、昇格のプロンプトが表示されます)。

    ![Falcon ライブラリのインストール](media/quickstart-python-03-install-package.png)

1. インストールが済むと、**ソリューション エクスプローラー**の環境にライブラリが表示されます。これは、Python コードでライブラリを使用できることを意味します。

    ![インストールされた Falcon ライブラリ](media/quickstart-python-04-package-installed.png)

Falcon の詳細情報は、[falconframework.org](https://falconframework.org/) をご覧ください。

開発者は通常、グローバル環境にライブラリをインストールするのではなく、特定のプロジェクトのライブラリをインストールする "仮想環境" を作成することに注意してください。 Visual Studio の多くの Python プロジェクト テンプレートには、テンプレートが依存するライブラリの一覧が列記されている `requirements.txt` ファイルが含まれます。 これらのテンプレートの 1 つからプロジェクトを作成すると、ライブラリがインストールされる仮想環境の作成がトリガーされます。 詳しくは、「Python 環境」の「[仮想環境](../python/python-environments.md#virtual-environments)」をご覧ください。

## <a name="add-a-code-file"></a>コード ファイルの追加

最小限の Web アプリを実装するための Python コードを追加する準備ができました。

1. **ソリューション エクスプローラー**でプロジェクトを右クリックして、**[追加] > [新しい項目]** を選びます。

1. 表示されるダイアログ ボックスで、**[空の Python ファイル]** を選び、「`hello.py`」という名前を付けて、**[追加]** を選びます。 エディター ウィンドウでファイルが自動的に開きます  (項目テンプレートは多くの場合に役立つ定型コードを提供するので、一般に、**[追加] > [新しい項目]** コマンドは異なる種類のファイルをプロジェクトに追加する優れた方法です)。

1. 次のコードをコピーして、`hello.py` に貼り付けます。

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. このコードを貼り付けると、Visual Studio で最初の行の `falcon` と 20 行目の `wsgiref.simple.server` の下に、ジグザグ矢印が表示されることがあります。 このようなインジケーターが表示されるのは、Visual Studio がこれらのモジュールの IntelliSense データベースを作成中の場合です。

Falcon について詳しくは、[Falcon のクイック スタート](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io) をご覧ください。

## <a name="run-the-application"></a>アプリケーションの実行

1. **ソリューション エクスプローラー**で `hello.py` を右クリックし、**[スタートアップ ファイルとして設定]** を選びます。 コマンドは、アプリの実行時に Python で起動するコード ファイルを識別します。

    ![ソリューション エクスプローラーでプロジェクトのスタートアップ ファイルを設定](media/quickstart-python-05-set-as-startup-file.png)

1. **ソリューション エクスプローラー**で "Hello Python" プロジェクトを右クリックして、**[プロパティ]** を選びます。 次に、**[デバッグ]** タブを選び、**[ポート番号]** プロパティを `8080` に設定します。 これにより、Visual Studio はランダムなポートを使うのではなく、`localhost:8080` でブラウザーを起動するようになります。

1. **[デバッグ] > [デバッグなしで開始]** (Ctrl + F5) を選び、変更をファイルに保存して、アプリを実行します。

1. コマンド ウィンドウに "Starting web app server" というメッセージが表示された後、`localhost:8080` でブラウザー ウィンドウが開いて、"Hello, Python!" というメッセージが表示されます。 コマンド ウィンドウには GET 要求も表示されます 

    ブラウザーが自動的に開かない場合は、任意のブラウザーを起動して `localhost:8080` に移動します。

    コマンド ウィンドウに Python 対話型シェルのみが表示される場合、または画面でそのウィンドウが短時間点滅する場合は、上記の手順 1 でスタートアップ ファイルとして `hello.py` を設定してあるかどうかを確認してください。

1. コマンド ウィンドウを閉じてアプリを停止してから、ブラウザー ウィンドウを閉じます。

## <a name="next-steps"></a>次の手順

Visual Studio IDE と Python について簡単に学習するこのクイック スタートは以上で完了です。 対話型ウィンドウの使用、デバッグ、データの視覚化、Git の操作など、Visual Studio での Python についての詳細なチュートリアルを続行するには、下のボタンを選んでください。

> [!div class="nextstepaction"]
> [チュートリアル: Visual Studio での Python の概要](../python/vs-tutorial-01-01.md)。

- [Visual Studio での Python Web アプリ テンプレート](../python/template-web.md)について学習する
- [Python のデバッグ](../python/debugging.md)について学習する
- [Visual Studio の IDE](../ide/visual-studio-ide.md) についてさらに学習する
