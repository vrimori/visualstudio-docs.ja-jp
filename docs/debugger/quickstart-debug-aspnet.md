---
title: ASP.NET をデバッグします。
description: Visual Studio デバッガーを使用して ASP.NET をデバッグします。
ms.custom: mvc
ms.date: 08/06/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 74671401b3e3eaeae5840110dfc37c926266f98a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636988"
---
# <a name="quickstart-debug-aspnet-with-the-visual-studio-debugger"></a>クイック スタート: Visual Studio デバッガーでの ASP.NET をデバッグします。

Visual Studio デバッガーには、アプリのデバッグに役立つ多くの強力な機能が用意されています。 このトピックでは、基本的な機能のいくつかを簡単に紹介します。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#**、選択**Web**、中央のペインの  **ASP.NET Core Web アプリケーション**します。

1. ような名前を入力**MyDbgApp**  をクリック**OK**します。

1. 表示されるダイアログ ボックスで、次のように選択します。 **Web アプリケーション**で中央のウィンドウをクリック**OK**します。

     表示されない場合、 **Web アプリケーション**プロジェクト テンプレートをクリックして、 **Visual Studio インストーラーを開く**の左側のウィンドウで、リンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 **[ASP.NET と Web 開発]** ワークロードを選択してから **[変更]** を選択します。

    ![Web アプリケーションを選択します。](../debugger/media/dbg-qs-aspnet-choose-web-app.png)

    Visual Studio によってプロジェクトが作成されます。

1. ソリューション エクスプ ローラーで about.cshtml.cs (Pages/About.cshtml) を開くし、次のコードに置き換えます

    ```csharp
    public void OnGet()
    {
        Message = "Your application description page.";
    }
    ```

    を、次のコードで置換します。

    ```csharp
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

A*ブレークポイント*コードを参照してください、変数の値またはメモリ、またはコードの分岐が実行を取得するかどうかの動作を行うためにの Visual Studio が、実行を中断する位置を示すマーカーです。 最も基本的な機能は、デバッグすることをお勧めします。

1. ブレークポイントを設定するには、左側の余白 をクリックして、`doWork`関数 (コードとキーを押して行を選択または**F9**)。

    ![ブレークポイントの設定](../debugger/media/dbg-qs-set-breakpoint-aspnet.png)

    左中かっこの左側にブレークポイントを設定 (`{`)。

1. これでキーを押します**F5** (選択または**デバッグ > [デバッグ開始]**)。

1. Web ページが読み込まれると、クリックして、**について**web ページの上部にあるリンクです。

    デバッガーでは、ブレークポイントを設定したが一時停止します。 デバッガーとアプリの実行が一時停止しているステートメントは黄色の矢印で示されます。 左中かっこでは、行 (`{`) した後、`doWork`関数の宣言がまだ実行されていません。

    ![ブレークポイントに到達する](../debugger/media/dbg-qs-hit-breakpoint-aspnet.png)

    > [!TIP]
    > ループまたは再帰では、ブレークポイントを設定または頻繁にステップを実行する多くのブレークポイントがある場合は、使用する場合、[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)を特定の条件が満たされた場合にのみ、コードが中断されているかどうかを確認します。 これにより、時間を節約し、こともできます簡単に再現が難しい問題をデバッグします。

## <a name="navigate-code"></a>コード間の移動

続行するデバッガーに指示するさまざまなコマンドもあります。 有用なコード ナビゲーション コマンドは、Visual Studio 2017 の新機能を説明します。

ブレークポイントで一時停止、中には、ステートメントを合わせる`return c2`緑まで**実行 をクリックする**ボタン![クリックで実行](../debugger/media/dbg-tour-run-to-click.png)が表示されたら、およびキーを押します、**実行 をクリックする**ボタンをクリックします。

![実行をクリックするには](../debugger/media/dbg-qs-run-to-click-aspnet.png)

アプリの実行を継続し、ボタンをクリックするコード行で一時停止します。

使用する一般的なキーボード コマンド コードをステップ実行を含める**F10**と**F11**します。 詳細についての詳細な手順については、次を参照してください。、[初心者向けガイド](../debugger/getting-started-with-the-debugger.md)します。

## <a name="inspect-variables-in-a-datatip"></a>データヒントで変数を検査します。

1. (黄色の実行ポインターによってマークされた) コードの現在の行で合わせます、`c2`データヒントを表示する、マウスでオブジェクト。

    ![データヒントを表示します。](../debugger/media/dbg-qs-data-tip-aspnet.png)

    データヒントには、現在の値が表示されます、`c2`変数、プロパティを確認することができます。 予定がない値を表示する場合は、デバッグ、時におそらく前または呼び出し元の行のコードにバグがあります。 

2. 現在のプロパティ値を確認する [データヒント] を展開し、`c2`オブジェクト。

3. 値を確認するを続行するために、データヒントをピン留めする場合`c2`コードを実行するときに、小規模のピン アイコンをクリックします。 (固定したデータヒントは任意の場所に移動できます)。

## <a name="edit-code-and-continue-debugging"></a>コードを編集してデバッグを続行する

デバッグ セッションの途中で、コードでテストしたい変更を特定する場合をも実行できます。

1. `OnGet`メソッドの 2 番目のインスタンスをクリックします。`result.First.Value`変更と`result.First.Value`に`result.Last.Value`。

1. キーを押して**F10** (または**デバッグ > ステップ オーバー**) 何度か、デバッガーを進めるし、編集済みのコードを実行します。

    ![エディット コンティニュ](../debugger/media/dbg-qs-edit-and-continue-aspnet.png "エディット コンティニュ")

    **F10 キーを押して**(まだをスキップするコードを実行します) それらへのステップ インではなく関数経由でデバッガーの 1 つのステートメント、時間が手順を進めます。

エディット コンティニュを使用して機能の制限の詳細については、次を参照してください。[エディット コンティニュ](../debugger/edit-and-continue.md)します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、コードをステップ実行、デバッガーを起動し、変数を確認する方法を学習できました。 詳細情報へのリンクと共にデバッガー機能の概要を取得することがあります。

> [!div class="nextstepaction"]
> [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)
