---
title: ASP.NET の Visual Studio のデバッグ |Microsoft ドキュメント
ms.custom: mvc
ms.date: 03/16/2018
ms.technology:
- vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 27072fda7535db5cd7307523c7e1732fef79c9e2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debug-aspnet-with-the-visual-studio-debugger"></a>Visual Studio デバッガーでの ASP.NET をデバッグします。

Visual Studio デバッガーでは、アプリのデバッグに役立つ多くの強力な機能を提供します。 このトピックでは、基本的な機能のいくつかを簡単に紹介します。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#**、選択**Web**、中央のペインの  **ASP.NET Core Web アプリケーション**です。

1. ような名前を入力**MyDbgApp**  をクリック**OK**です。

1. ダイアログ ボックスが表示されますが、選択**Web アプリケーション**をクリックして中央のペイン**OK**。

     表示されない場合、 **Web アプリケーション**プロジェクト テンプレートをクリックして、**開いている Visual Studio インストーラー**の左側のウィンドウ内のリンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 選択、 **ASP.NET**と**.NET Core**ワークロード、順に選択**変更**です。

    ![Web アプリケーションを選択します。](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio によってプロジェクトが作成されます。

1. ソリューション エクスプ ローラーで、(Pages/About.cshtml) の下の About.cshtml.cs を開き、次のコードを置き換えます

    ```c#
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    を、次のコードで置換します。

    ```c#
    public void OnGet()
    {
        LinkedList<int> result = doWork();
        Message = "Result of work: " + result.First.Value + ", " + result.First.Value;
    }

    private static LinkedList<int> doWork()
    {
        LinkedList<int> c1 = new LinkedList<int>();

        c1.AddLast(10);
        c1.AddLast(20);

        LinkedList<int> c2 = new LinkedList<int>(c1);

        return c2;

    }
    ```

## <a name="set-a-breakpoint"></a>ブレークポイントの設定

A*ブレークポイント*は Visual Studio が、実行を中断する位置を示すマーカー コードのために、変数の値またはメモリ、またはコードの分岐が実行を取得するかどうかの動作を確認することができます。 デバッグの最も基本的な機能することをお勧めします。

1. 左側の余白をクリックして、ブレークポイントを設定するには`doWork`関数 (コードとキーを押して行を選択または**F9**)。

    ![ブレークポイントの設定](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    左中かっこの左側にブレークポイントを設定 (`{`)。

1. これでキーを押します**f5 キーを押して**(かを選択して**デバッグ > [デバッグ開始]**)。

1. Web ページが読み込まれると、クリックして、**に関する**web ページの上部にあるリンクします。

    デバッガーでは、ブレークポイントを設定するが一時停止します。 デバッガーとアプリの実行が一時停止して、ステートメントは黄色の矢印で示されます。 左中かっこでは、行 (`{`) した後、`doWork`関数宣言がまだ実行されていません。

    ![ブレークポイントに到達する](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > ループまたは再帰では、ブレークポイントまたは頻繁にステップを実行する多くのブレークポイントがある場合を使用した場合、[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)を特定の条件が満たされた場合にのみ、コードが中断されるかどうかを確認します。 これは、時間を節約できますもやすくしたり再現が困難な問題をデバッグします。

## <a name="navigate-code"></a>コード間の移動

続行する、デバッガーに指示するさまざまなコマンドがあります。 有用なコード ナビゲーション コマンドは、Visual Studio 2017 の新機能を説明します。

ブレークポイントで一時停止、中には、ステートメントを合わせる`return c2`緑まで**をクリックして実行**ボタン![実行 をクリックする](../debugger/media/dbg-tour-run-to-click.png)が表示され、キーを押し、**をクリックして実行**ボタンをクリックします。

![クリックして実行します。](../debugger/media/dbg-qs-run-to-click-aspnet.png)

アプリでは、実行が続けられ、ボタンをクリックしたコードの行で一時停止します。

使用される共通のキーボード コマンド コードのステップ実行を含める**F10**と**F11**です。 複数の詳細な手順については、次を参照してください。、[ビギナーズ ガイド](../debugger/getting-started-with-the-debugger.md)です。

## <a name="inspect-variables-in-a-datatip"></a>データヒントで変数を検査します。

1. 現在のコード行 (黄色実行ポインターによってマーク) を合わせると、`c2`データヒントを表示する、マウスを持つオブジェクト。

    ![データヒントを表示します。](../debugger/media/dbg-qs-data-tip-aspnet.png)

    データヒントは、の現在の値を表示、`c2`変数のプロパティを検査することができます。 デバッグする場合、予期しない値を表示する場合、おそらく前または呼び出し元の行のコードでバグがあります。 

2. 現在のプロパティ値を見てにデータヒントを展開し、`c2`オブジェクト。

3. 値を表示する継続できるように、データヒントをピン留めする場合`c2`コードを実行するときに、小規模のピン アイコンをクリックします。 (固定したデータヒントは任意の場所に移動できます)。

## <a name="edit-code-and-continue-debugging"></a>コードを編集およびデバッグを続行

デバッグ セッションの途中で、コードでテストを実行する変更を識別する場合、行うことができます、すぎます。

1. `OnGet`メソッドの 2 つ目のインスタンスをクリックして`result.First.Value`変更と`result.First.Value`に`result.Last.Value`です。

1. キーを押して**F10** (または**デバッグ > ステップ オーバー**) 何度か、デバッガーを進めるし、編集済みのコードを実行します。

    ![エディット コンティニュ](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "エディット コンティニュ")

    **F10 キーを押して**(まだをスキップする、コードが実行される) それらへのステップ インではなく関数経由で、時間が手順デバッガー 1 つのステートメントを進めます。

エディット コンティニュを使用して機能の制限の詳細については、次を参照してください。[エディット コンティニュ](../debugger/edit-and-continue.md)です。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、コードをステップ実行、デバッガーを起動し、変数を検査する方法を学びました。 詳細情報へのリンクと共にデバッガーの機能について詳しく説明を取得することがあります。

> [!div class="nextstepaction"]
> [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)
