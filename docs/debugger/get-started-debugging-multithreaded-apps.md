---
title: マルチ スレッド アプリケーションのデバッグについて理解するには
description: Visual Studio での並列スタック ウィンドウや 並列ウォッチ ウィンドウを使用したデバッグします。
ms.custom: H1HackMay2017
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 95a198213daa90a1370cba056a8c522495e06c94
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54227981"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>マルチ スレッド アプリケーションのデバッグの開始 (C#、Visual Basic、C++)
Visual Studio には、いくつかのツールとマルチ スレッド アプリケーションをデバッグする方法をユーザー インターフェイス要素が用意されています。 このチュートリアルでは、スレッド マーカーを使用する方法、**並列スタック**ウィンドウで、**並列ウォッチ**ウィンドウ、条件付きブレークポイントは、および [フィルター] ブレークポイント。 このチュートリアルを完了に慣れることがするマルチ スレッド アプリケーションをデバッグするための Visual Studio の機能を使用します。

| | |
|---------|---------|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | [ビデオを見る](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171)同様の手順を示しています。 マルチ スレッド デバッグします。 |

これら 2 つのトピックでは、その他のマルチ スレッド デバッグ ツールを使用して追加についてを説明します。

- 使用する、**デバッグの場所**ツールバーと**スレッド**ウィンドウを参照してください[チュートリアル。マルチ スレッド アプリケーションをデバッグ](../debugger/how-to-use-the-threads-window.md)します。

- 使用するサンプルの<xref:System.Threading.Tasks.Task>(マネージ コード) を参照してください (C++)、同時実行ランタイムと[チュートリアル: 並行アプリケーションをデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)します。 最もマルチ スレッド アプリケーションの種類に適用される一般的なデバッグ ヒント、そのトピックと、この 1 つの両方を参照します。
  
まず、マルチ スレッド アプリケーション プロジェクトを必要があります。 以下に例を示します。  
  
## <a name="create-a-multithreaded-app-project"></a>マルチ スレッド アプリ プロジェクトを作成します。  
  
1.  **[ファイル]** メニューで、**[新規作成]** > **[プロジェクト]** の順に選択します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  言語の選択**Visual c#**、 **Visual C**、または**Visual Basic**します。  
  
3.  **Windows デスクトップ**、選択**コンソール アプリ**します。  
  
4.  **名前**フィールドに、MyThreadWalkthroughApp を入力します。  
  
5.  **[OK]** を選択します。  
  
     新しいコンソール プロジェクトが表示されます。 プロジェクトを作成すると、ソース ファイルが表示されます。 選択した言語に応じて、ソース ファイルが呼び出される可能性が*Program.cs*、 *MyThreadWalkthroughApp.cpp*、または*Module1.vb*します。  
  
6.  ソース ファイルに表示されるコードを削除し、以下を一覧表示する適切な例のコードに置き換えます。

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  **[ファイル]** メニューの **[すべてを保存]** をクリックします。  
  
## <a name="debug-the-multithreaded-app"></a>マルチ スレッド アプリをデバッグします。  
  
1. ソース コード エディターで次のコード スニペットのいずれかになります。 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. 左側の余白で左クリックして、`Thread.Sleep`または`this_thread::sleep_for`新しいブレークポイントを挿入するステートメント。  
  
    余白は、赤い円は、この場所にブレークポイントを設定することを示します。 
  
2. **デバッグ**メニューの [**デバッグの開始]** (**F5**)。  
  
    Visual Studio ソリューションをビルド、アタッチされたデバッガーを開始してから、アプリ、アプリがブレークポイントで停止します。  
  
3. ソース コード エディターでは、ブレークポイントを含む行を探します。
  
### <a name="ShowThreadsInSource"></a>スレッド マーカーを見つける  

1.  デバッグ ツールバーで、選択、**ソース スレッドを表示**ボタン![ソース スレッドを表示](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")します。

2. キーを押して**F11**コード デバッガーの 1 つの行に 1 回です。
  
3.  ウィンドウ左端の余白に注目します。 この行に表示されます、*スレッド マーカー*アイコン![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")ツイストの 2 つのスレッドと類似しています。 スレッド マーカーは、スレッドが停止している位置を示します。

    スレッド マーカーは、ブレークポイントによって部分的に非表示に可能性があります。 
  
4.  スレッド マーカーの上にポインターを置きます。 停止したスレッドごとの名前とスレッド ID 番号を示す、データヒントが表示されます。 名前がここでは、おそらくは`<noname>`します。 
  
5.  ショートカット メニューの 利用可能なオプションを表示するスレッド マーカーを選択します。
    
### <a name="ParallelStacks"></a>スレッドの場所を表示します。

**並列スタック** ウィンドウに切り替えることができます、タスクを確認しては、各スレッドの呼び出し履歴情報を表示できますスレッド ビューの間、(タスク ベースのプログラミング)。 このアプリでは、スレッド ビューを使用できます。

1. 開く、**並列スタック**ウィンドウを選択して**デバッグ** > **Windows** > **並列スタック**します。 次のような画面が表示されます。 正確な情報については、各スレッド、ハードウェア、および使用するプログラミング言語の現在の場所によって異なります。

    ![並列スタック ウィンドウ](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    この例では、左から右へのマネージ コードには、この情報のように表示します。
    
    - メイン スレッド (左側) が停止しました`Thread.Start`停止ポイントが、スレッド マーカーのアイコンによって示されます、![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")します。
    - 2 つのスレッドが入力した、 `ServerClass.InstanceMethod`、うちの 1 つは、現在のスレッド (黄色の矢印) で、他のスレッドが停止中に`Thread.Sleep`します。
    - (右) で新しいスレッドが開始されてでが停止した`ThreadHelper.ThreadStart`します。

2.  内のエントリを右クリックし、**並列スタック**ショートカット メニューの 使用可能なオプションを表示するウィンドウ。

    これらの右クリック メニューからさまざまなアクションを実行することができますが、このチュートリアルでこれらの詳細の示しますが、**並列ウォッチ**ウィンドウ (次のセクション)。

    > [!NOTE]
    > リスト ビューを各スレッドの情報を表示する、**スレッド**ウィンドウ代わりにします。 「[チュートリアル:マルチ スレッド アプリケーションをデバッグ](../debugger/how-to-use-the-threads-window.md)します。

### <a name="set-a-watch-on-a-variable"></a>変数のウォッチを設定します。

1. 開く、**並列ウォッチ**ウィンドウを選択して**デバッグ** > **Windows** > **並列ウォッチ** > **並列ウォッチ 1**します。

2. 表示されているセルを選択、`<Add Watch>`テキスト (または 4 番目の列ヘッダーの空のセル) を入力および`data`します。

    スレッドごとに、data 変数の値は、ウィンドウに表示されます。

3. 表示されているセルを選択、`<Add Watch>`テキスト (または 5 日の列の空のヘッダー セル) を入力および`count`します。

    値、`count`スレッドごとの変数が、ウィンドウに表示されます。 まだこの大量の情報が表示されない場合は、キーを押してをお試しください**F11**何度か、デバッガー内のスレッドの実行を進めます。

    ![[並列ウォッチ] ウィンドウ](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 使用可能なオプションを表示するには、ウィンドウ内の行のいずれかを右クリックします。

### <a name="flag-and-unflag-threads"></a>スレッドに対するフラグの設定と設定解除を行う  
重要なスレッドを追跡し、その他のスレッドを無視するスレッドのフラグを設定することができます。  
  
1. **並列ウォッチ**ウィンドウで、キーを押し、 **Shift**キーし、複数の行を選択します。

2. 右クリックして**フラグ**します。

    選択したすべてのスレッドのフラグが設定されます。 ここで、フラグが設定されたスレッドのみを表示するフィルター処理することができます。
  
3.  **並列ウォッチ**ウィンドウで、**フラグが設定されたスレッドのみを表示する**ボタン![フラグが設定されたスレッドを表示する](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")します。  
  
    フラグが設定されたスレッドのみが一覧に表示します。

    > [!TIP]
    > 一部のスレッドのフラグを設定した後は、コード エディターでのコード行を右クリックし、選択**カーソルにフラグが設定されたスレッドの実行**します。 すべてのスレッドのフラグが設定するコードに到達を選択してください。 Visual Studio は、一時停止で選択した行のコードのスレッドによる実行の順序を制御しやすく[スレッドの凍結と凍結解除](#bkmk_freeze)します。

4.  選択、**フラグが設定されたスレッドのみを表示する**ボタンをもう一度に切り替えます**すべてのスレッド**モード。
    
5. スレッドのフラグ解除、内の 1 つまたは複数のフラグが設定されたスレッドを右クリックし、**並列ウォッチ**ウィンドウと選択**フラグ解除**します。

### <a name="bkmk_freeze"></a> 固定およびスレッドの実行を凍結解除 

> [!TIP]
> 停止および再開することができます (中断および再開) スレッドのスレッドが作業を実行する順序を制御します。 デッドロックなどの同時実行の問題を解決し、競合状態が役立ちます。
   
1.  **並列ウォッチ**ウィンドウで、すべての行選択すると、右クリックして選択**固定**します。

    2 番目の列では、行ごとに一時停止アイコンが表示されます。 一時停止アイコンは、スレッドが固定されていることを示します。

2.  1 つの行のみを選択して、その他のすべての行を選択解除します。

3.  行を右クリックして**凍結解除**します。

    一時停止アイコンは、この行は、スレッドが凍結して不要になったことを示すされなくなります。

4.  コード エディターとキーを押して切り替える**F11**します。 固定されたスレッドのみを実行します。

    アプリは、いくつかの新しいスレッドをインスタンス化も可能性があります。 すべての新しいスレッドはフラグが設定されたではなく、保持されていません。

### <a name="bkmk_follow_a_thread"></a> 次の条件付きブレークポイントを 1 つのスレッド

デバッガーでの 1 つのスレッドの実行を追跡ことができます。 そのためには 1 つの方法で必要のないスレッドを凍結ことです。 一部のシナリオでは、特定のバグを再現する例については、他のスレッドを凍結しないで 1 つのスレッドに従う必要があります。 スレッドを他のスレッドをフリーズさせないに従って、興味のあるスレッドで以外のコードに重大なを避ける必要があります。 設定してこれを行う、[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)します。

スレッド名またはスレッド ID などのさまざまな条件でブレークポイントを設定することができます。 ある可能性がありますに有益では各スレッドに一意ですがわかっているデータの条件を設定します。 これは、任意の特定のスレッドよりもいくつかの特定のデータ値に強い関心がする一般的なデバッグ シナリオです。

1. 以前に作成したブレークポイントを右クリックして**条件**します。

2. **ブレークポイントの設定**ウィンドウで、入力`data == 5`の条件付きの式。

    ![条件付きブレークポイント](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 特定のスレッドで必要な場合は、スレッド名またはスレッド ID を使用条件。 この、**ブレークポイントの設定**ウィンドウで、**フィルター**の代わりに**条件式**フィルターのヒントに従います。 デバッガーを再起動したときにスレッド Id を変更すると、アプリのコードで、スレッドの名前をする可能性があります。

3. 閉じる、**ブレークポイントの設定**ウィンドウ。

4. 再起動を選択します。![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp") 、デバッグ セッションを再開するボタンをクリックします。

    データ変数の値が 5 には、スレッドでコードを中断します。 **並列ウォッチ**ウィンドウで、デバッガーの現在のコンテキストを示す黄色の矢印を参照してください。

5. コードをステップするようになりましたが、(**F10**) とコードにステップ イン (**F11**) と 1 つのスレッドの実行を追跡します。

    ブレークポイント条件は、スレッドに一意であり、デバッガーが (無効にする必要があります)、他のスレッドで、他のブレークポイントにヒットしない、限りコードをステップし、他のスレッドを切り替えずにコードにステップ インできます。

    > [!NOTE]
    > デバッガーが進むと、すべてのスレッドが実行されます。 ただし、他のスレッドのいずれかのブレークポイントをヒットしない限り、デバッガーが他のスレッドでコードを中断しません。 
  
## <a name="see-also"></a>関連項目  
[マルチスレッド アプリケーションのデバッグ](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[方法: デバッグ中に別のスレッドに切り替える](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
[方法: 並列スタック ウィンドウを使用します。](../debugger/using-the-parallel-stacks-window.md)  
[方法: [並列ウォッチ] ウィンドウを使用する](../debugger/how-to-use-the-parallel-watch-window.md)  
