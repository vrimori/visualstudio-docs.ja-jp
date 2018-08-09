---
title: マネージ コードのデバッグ |Microsoft Docs
description: C# または Visual Studio デバッガーを使用して Visual Basic をデバッグします。
ms.custom: mvc
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: f4cea2e1-08dc-47ac-aba2-3b8c338e607f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2ba06156a8fa44a61b489deba6104673e8fb08ce
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637524"
---
# <a name="quickstart-debug-with-managed-code-using-the-visual-studio-debugger"></a>Visual Studio デバッガーを使用してマネージ コードでのクイック スタート: デバッグします。

Visual Studio デバッガーには、アプリのデバッグに役立つ多くの強力な機能が用意されています。 このトピックでは、基本的な機能のいくつかを簡単に紹介します。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

2. **Visual c#** または**Visual Basic**、選択 **.NET Core**、中央のペインの **コンソール アプリ (.NET Core)** します。

     **[Console App (.NET Core)]** プロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 選択、 **.NET デスクトップ開発**と **.NET Core**ワークロードを選択し、**変更**します。

3. ような名前を入力**MyDbgApp**  をクリック**OK**します。

    Visual Studio によってプロジェクトが作成されます。

4. *Program.cs*または*Module1.vb*、次のコードに置き換えます

    ```csharp
    class Program
    {
        static void Main(string[] args)
        {
        }
    }
    ```

    ```vb
    Module Module1
        Sub Main()
        End Sub
    End Module
    ```

    を、次のコードで置換します。

    ```csharp
    class Program
    {
        private static void doWork()
        {
            LinkedList<int> c1 = new LinkedList<int>();

            c1.AddLast(10);
            c1.AddLast(20);

            LinkedList<int> c2 = new LinkedList<int>(c1);
            int i = c2.First.Value;
            int j = c2.First.Value;
            Console.Write("The first element is ");
            Console.Write(i);
            Console.Write("\n");
            Console.Write("The second element is ");
            Console.Write(j);
            Console.Write("\n");

        }

        static int Main()
        {
            // using namespace std;
            doWork();
            return 0;

        }
    }
    ```

    ```vb
    Imports System.Collections.Generic

    Namespace MyDbgApp
        Class Program
            Private Shared Sub doWork()
                Dim c1 As New LinkedList(Of Integer)()

                c1.AddLast(10)
                c1.AddLast(20)

                Dim c2 As New LinkedList(Of Integer)(c1)
                Dim i As Integer = c2.First.Value
                Dim j As Integer = c2.First.Value
                Console.Write("The first element is ")
                Console.Write(i)
                Console.Write(vbLf)
                Console.Write("The second element is ")
                Console.Write(j)
                Console.Write(vbLf)

            End Sub

            Public Shared Function Main() As Integer
                ' using namespace std;
                doWork()
                Return 0

            End Function
        End Class
    End Namespace
    ```

    > [!NOTE]
    > Visual Basic で、スタートアップ オブジェクトが `Sub Main` に設定されていることを確認します (**[プロパティ]、[アプリケーション]、[スタートアップ オブジェクト]**)。

## <a name="set-a-breakpoint"></a>ブレークポイントの設定

A*ブレークポイント*コードを参照してください、変数の値またはメモリ、またはコードの分岐が実行を取得するかどうかの動作を行うためにの Visual Studio が、実行を中断する位置を示すマーカーです。 最も基本的な機能は、デバッグすることをお勧めします。

1. ブレークポイントを設定するには、左側の余白 をクリックして、`doWork`関数呼び出し (コードとキーを押して行を選択または**F9**)。

    ![ブレークポイントを設定する](../debugger/media/dbg-qs-set-breakpoint-csharp.png "ブレークポイントを設定します。")

2. これでキーを押します**F5** (選択または**デバッグ > [デバッグ開始]**)。

    ![ブレークポイントにヒット](../debugger/media/dbg-qs-hit-breakpoint-csharp.png "ブレークポイントにヒット")

    デバッガーでは、ブレークポイントを設定したが一時停止します。 デバッガーとアプリの実行が一時停止しているステートメントは黄色の矢印で示されます。 は、行、`doWork`関数呼び出しがまだ実行されていません。

    > [!TIP]
    > ループまたは再帰では、ブレークポイントを設定または頻繁にステップを実行する多くのブレークポイントがある場合は、使用する場合、[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)を特定の条件が満たされた場合にのみ、コードが中断されているかどうかを確認します。 条件付きブレークポイントは、時間を節約でき、そのこともできます簡単に再現が難しい問題をデバッグします。

## <a name="navigate-code"></a>コード間の移動

続行するデバッガーに指示するさまざまなコマンドもあります。 有用なコード ナビゲーション コマンドは、Visual Studio 2017 の新機能を説明します。

ブレークポイントで一時停止、中には、ステートメントを合わせる`c1.AddLast(20)`緑まで**実行 をクリックする**ボタン![クリックで実行](../debugger/media/dbg-tour-run-to-click.png "RunToClick")が表示されたら、およびキーを押します、**実行 をクリックする**ボタンをクリックします。

![クリックする実行](../debugger/media/dbg-qs-run-to-click-csharp.png "実行 をクリックするには")

アプリの実行を継続を呼び出す`doWork`、し、ボタンをクリックしたコード行で一時停止します。

使用する一般的なキーボード コマンド コードをステップ実行を含める**F10**と**F11**します。 詳細についての詳細な手順については、次を参照してください。、[初心者向けガイド](../debugger/getting-started-with-the-debugger.md)します。

## <a name="inspect-variables-in-a-datatip"></a>データヒントで変数を検査します。

1. (黄色の実行ポインターによってマークされた) コードの現在の行で合わせます、`c1`データヒントを表示する、マウスでオブジェクト。

    ![データヒントを表示](../debugger/media/dbg-qs-data-tip-csharp.png "データヒントを表示")

    データヒントには、現在の値が表示されます、`c1`変数、プロパティを確認することができます。 予定がない値を表示する場合は、デバッグ、時におそらく前または呼び出し元の行のコードにバグがあります。 

2. 現在のプロパティ値を確認する [データヒント] を展開し、`c1`オブジェクト。

3. 値を確認するを続行するために、データヒントをピン留めする場合`c1`コードを実行するときに、小規模のピン アイコンをクリックします。 (固定したデータヒントは任意の場所に移動できます)。

## <a name="edit-code-and-continue-debugging"></a>コードを編集してデバッグを続行する

デバッグ セッションの途中で、コードでテストしたい変更を特定する場合をも実行できます。

1. 2 番目のインスタンスをクリックします。`c2.First.Value`変更と`c2.First.Value`に`c2.Last.Value`します。

2. キーを押して**F10** (または**デバッグ > ステップ オーバー**) 何度か、デバッガーを進めるし、編集済みのコードを実行します。

    ![エディット コンティニュ](../debugger/media/dbg-qs-edit-and-continue-csharp.gif "エディット コンティニュ")

    **F10 キーを押して**(まだをスキップするコードを実行します) それらへのステップ インではなく関数経由でデバッガーの 1 つのステートメント、時間が手順を進めます。

エディット コンティニュを使用して機能の制限の詳細については、次を参照してください。[エディット コンティニュ](../debugger/edit-and-continue.md)します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、コードをステップ実行、デバッガーを起動し、変数を確認する方法を学習できました。 詳細情報へのリンクと共にデバッガー機能の概要を取得することがあります。

> [!div class="nextstepaction"]
> [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)
