---
title: "マルチ スレッド アプリケーションのデバッグの開始 |Microsoft ドキュメント"
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 1d4298d60886d8fe8b402b59b1838a4171532ab1
ms.openlocfilehash: 3ffb550707280d76756cbd144ed03f4143ce144b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="get-started-debugging-a-multithreaded-application-in-visual-studio"></a>Visual Studio でのマルチ スレッド アプリケーションのデバッグの開始します。
Visual Studio には、いくつかのツールとマルチ スレッド アプリケーションをデバッグするためのユーザー インターフェイス要素が用意されています。 このチュートリアルでは、スレッド マーカーを使用する方法、**並列スタック** ウィンドウで、**並列ウォッチ**ウィンドウ、条件付きブレークポイントは、およびフィルターのブレークポイント。 このチュートリアルでは、わずか数分が完了することを理解するマルチ スレッド アプリケーションのデバッグの機能とします。

|         |         |
|---------|---------|
| ![ビデオを見る](../install/media/video-icon.png "WatchVideo") | [ビデオを見る](#video)で同様の手順を示しています。 マルチ スレッド デバッグします。 |

その他のトピックでは、その他のマルチ スレッド デバッグ ツールを使用してその他についてを説明します。

- 使用する方法を示すようなトピックの**デバッグの場所**ツールバーと**スレッド**ウィンドウを参照してください[チュートリアル: マルチ スレッド アプリケーションをデバッグ](../debugger/how-to-use-the-threads-window.md)です。

- 使用するサンプルのようなトピックの<xref:System.Threading.Tasks.Task>(マネージ コード) と、同時実行ランタイム (C++) を参照してください[チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)です。 最もマルチ スレッド アプリケーションの種類に適用される一般的なデバッグ ヒント、このトピックの内容とリンク先のトピックを参照します。
  
このチュートリアルを開始するには、マルチ スレッド アプリケーション プロジェクトが必要です。 次の手順に従って、このようなプロジェクトを作成します。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>マルチ スレッド アプリ プロジェクトを作成するには  
  
1.  **ファイル** メニューの 選択**新規** をクリックし、**プロジェクト**です。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **プロジェクトの種類**s ボックスで、任意の言語 をクリックします。 **Visual c#**、 **Visual c**、または**Visual Basic**です。  
  
3.  **テンプレート**ボックスで、選択**コンソール アプリ**です。  
  
4.  **名前**ボックス名前 を入力します。  
  
5.  **[OK]** をクリックします。  
  
     新しいコンソール プロジェクトが表示されます。 プロジェクトが作成されると、ソース ファイルが表示されます。 言語によっては、選択した Program.cs、MyThreadWalkthroughApp.cpp、または Module1.vb、ソース ファイルを呼び出すことがあります。  
  
6.  ソース ファイルに表示されるコードを削除し、次に示す例のコードに置き換えます。

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

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
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
  
7.  **ファイル** メニューのをクリックして**すべて保存**です。  
  
#### <a name="to-begin-the-tutorial"></a>このチュートリアルを開始するには  
  
-   ソース コード エディターで、次のコードを探します。 
  
    ```CSharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>デバッグを開始するには  
  
1.  左側の余白内をクリックして、`Thread.Sleep`または`Thread::Sleep`新しいブレークポイントを挿入するステートメント。  
  
     ソース コード エディターの左側の余白で、赤い円が表示されます。 これは、ブレークポイントがその場所に設定されていることを示します。 
  
2.  **デバッグ** メニューのをクリックして**デバッグの開始** (**f5 キーを押して**)。  
  
     Visual Studio ソリューションをビルドする、アプリは、アタッチされたデバッガーの実行を開始し、アプリがブレークポイントで停止します。  
  
    > [!NOTE]
    > コンソール ウィンドウにフォーカスを移動する場合にクリックして、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ウィンドウにフォーカスを戻す[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
4.  ソース コード エディターで、ブレークポイントを含む行を探します。  
  
    ```CSharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>スレッド マーカーを検出するには  

1.  [デバッグ] ツールバーで、をクリックして、**ソース内のスレッドを表示**ボタン![ソース内のスレッドを表示](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")です。

2. キーを押して**F11**進める 1 行ずつデバッガーのコードを 1 回です。
  
3.  ウィンドウ左端の余白に注目します。 この行に表示されます、*スレッド マーカー*アイコン![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")布の 2 つのスレッドと類似しています。 スレッド マーカーは、スレッドが停止している位置を示します。

    スレッド マーカーを部分的にブレークポイントによって隠さ可能性がありますに注意してください。 
  
4.  スレッド マーカーの上にポインターを置きます。 DataTip が表示されます。 データヒントは、停止したスレッドごとに名前とスレッド ID 番号を表示します。 名前がここでは、おそらくは`<noname>`します。 
  
5.  ショートカット メニューの 利用可能なオプションを表示するスレッド マーカーを右クリックします。
    
## <a name="ParallelStacks"></a>スレッドの場所を表示します。

**並列スタック** ウィンドウに切り替えることができますのタスク ビュー、およびするが各スレッドの呼び出し履歴情報を表示できますスレッド ビュー間および (タスク ベースのプログラミング)。 このアプリは、スレッド ビューを使用できます。

1. 開く、**並列スタック**ウィンドウを選択して**デバッグ > Windows > 並列スタック**です。 次のようなものが表示されます (正確な情報は各スレッド、ハードウェア、および使用するプログラミング言語の現在の場所によって異なるされます)。

    ![並列スタック ウィンドウ](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    この例では左から右へおこの情報を取得します。
    
    - メイン スレッド (左側) が停止しました`Thread.Start`(停止ポイントがスレッド マーカーのアイコンによって示される![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker"))。
    - 2 つのスレッドが入力した、 `ServerClass.InstanceMethod`、うちの 1 つは、現在のスレッド (黄色の矢印) で、他のスレッドが停止している間`Thread.Sleep`です。
    - (右側) で新しいスレッドを開始しても (で停止`ThreadHelper.ThreadStart`)。

2.  内のエントリを右クリックし、**並列スタック**ショートカット メニューの 利用可能なオプションを表示するウィンドウです。

    これらを右クリック メニューからさまざまなアクションを実行できますが、このチュートリアルお表示されますでこれらの詳細の**並列ウォッチ**ウィンドウ ([次へ] セクション)。

    > [!NOTE]
    > 各スレッドに関する情報を含むビューで使用して、一覧の確認興味のある場合、**スレッド**ウィンドウ代わりにします。 参照してください[チュートリアル: マルチ スレッド アプリケーションをデバッグ](../debugger/how-to-use-the-threads-window.md)です。

## <a name="set-a-watch-on-a-variable"></a>変数のウォッチを設定します。

1. 開く、**並列ウォッチ**ウィンドウを選択して**デバッグ > Windows > 並列ウォッチ > 並列ウォッチ 1**です。

2. 表示されているセルをクリックして、`<Add Watch>`テキスト (または、4 番目の列の空のヘッダー セルは) 型`data`、Enter キーを押します。

    スレッドごとに、データ変数の値は、ウィンドウに表示します。

3. 表示されているセルにもう一度クリックして、`<Add Watch>`テキスト (または 5 番目の列の空のヘッダー セルは) 型`count`、Enter キーを押します。

    各スレッドの数の変数の値は、ウィンドウに表示します。 (まだ場合は、しないこの多くの情報を参照して、デバッガー内のスレッドの実行を進めるにさらに数回 f11 キーを押してしてください。)

    ![[並列ウォッチ] ウィンドウ](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 使用可能なオプションを表示するウィンドウ内の行の 1 つを右クリックします。

## <a name="flagging-and-unflagging-threads"></a>スレッドに対するフラグの設定と設定解除  
特に注目するスレッドのフラグを設定することができます。 スレッドに対するフラグの設定は、重要なスレッドを追跡しを気にせずスレッドを無視することをお勧めします。  
  
#### <a name="to-flag-threads"></a>スレッドにフラグを設定するには  

1. **並列ウォッチ**ウィンドウで、SHIFT キーを押しながら、複数の行を選択します。

2. 右クリックし、**フラグ**です。

    ここで、選択したすべてのスレッドがフラグが付けられます。 ここで、フラグが設定されたスレッドのみを表示するフィルター処理することができます。
  
3.  **並列ウォッチ**ウィンドウで、検索、**フラグが設定されたスレッドのみを表示する**ボタン![フラグが設定されたスレッドを表示する](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")です。  
  
4.  クリックして、**フラグが設定されたスレッドのみを表示する**ボタンをクリックします。  
  
    今度は、フラグが設定されたスレッドのみがボックスに表示されます。

    > [!TIP]
    > いくつかのスレッドのフラグを設定したときに、コード エディター内のコード行を右クリックして選択**カーソルにフラグが設定されたスレッドの実行**(コードをすべてフラグが設定されたスレッドが到達に選択することを確認してください)。 これは上での実行の順序を制御しやすく、コードの選択された行のスレッドを一時停止[スレッドの凍結と凍結解除](#bkmk_freeze)です。

5.  をクリックして、**フラグが設定されたスレッドのみを表示する**に切り替わりますボタン**すべてのスレッド**モード。
    
#### <a name="to-unflag-threads"></a>スレッドのフラグを解除するには

スレッドのフラグ解除、内の 1 つまたは複数のフラグが設定されたスレッドを右クリックして、**並列ウォッチ**ウィンドウを選択して**フラグ解除**です。

## <a name="bkmk_freeze"></a>スレッドの実行を凍結と凍結解除 

> [!TIP]
> 凍結および凍結解除することができます (中断および再開) スレッドのスレッドが作業を実行する順序を制御します。 デッドロックなどの同時実行の問題を解決するには、競合状態が役立ちます。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>スレッドを凍結および凍結解除するには  
  
1.  **並列ウォッチ**ウィンドウで、すべての行の選択すると、右クリックして選択**凍結**です。

    2 番目の列で一時停止アイコンが行ごとに表示されます。 一時停止アイコンは、スレッドが固定されていることを示します。

2.  1 つの行をクリックして、行の選択を解除します。

3.  行を右クリックし **凍結解除**です。

    スレッドが不要になった固定されていることを示す、この行で一時停止アイコンはありません。

4.  コード エディターに切り替えるし、をクリックして**F11**です。 固定されていないスレッドのみを実行します。

    アプリは、いくつかの新しいスレッドをインスタンス化も可能性があります。 すべての新しいスレッドはフラグが設定されたでありが固定されていないことに注意してください。

## <a name="bkmk_follow_a_thread"></a>次の条件付きブレークポイントを使用して、1 つのスレッド

場合によっては、デバッガーで 1 つのスレッドの実行を追跡すると役立つができます。 固定するは、スレッドは、1 つの方法を行うことができますが、一部のシナリオで (特定のバグの再現) するには、他のスレッドを凍結することがなく 1 つのスレッドを以下にすることです。 スレッドは、他のスレッドを凍結しないでに従う、興味のあるスレッドで以外のコードに分割を回避する必要があります。 これを行うことができます、[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)です。

スレッド名またはスレッド ID などのさまざまな条件でブレークポイントを設定することができます。 スレッドごとに一意になることがわかっているデータに条件を設定する役に立つ別の方法です。 これは一部の特定のデータ値よりも、特定のスレッドで関心のあるが、一般的なデバッグ シナリオです。

#### <a name="to-follow-a-single-thread"></a>1 つのスレッドを実行するには

1. 以前に作成したブレークポイントを右クリックして選択**条件**です。

2. **ブレークポイントの設定**ウィンドウで、「`data == 5`条件式にします。

    ![条件付きブレークポイント](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 特定のスレッドで必要な場合は、し、スレッド名またはスレッド ID 条件を使用します。 これを実行する、**ブレークポイントの設定**ウィンドウで、**フィルター**の代わりに**条件式**フィルターのヒントに従います。 (デバッガーを再起動すると、スレッド Id が変更) してから、アプリ コードで、スレッドの名前を付けることができます。

3. 閉じる、**ブレークポイントの設定**ウィンドウです。

4. [再起動] をクリックして![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp")デバッグ セッションを再開するボタンをクリックします。

    データ変数の 5 スレッド上のコードに分割されます。 黄色の矢印 (現在のデバッガー コンテキスト) 内で検索、**並列ウォッチ**ことを確認するウィンドウです。

5. ここで、コード (F10) をステップ (F11) コードにステップ インし、および 1 つのスレッドの実行を追跡できます。

    ブレークポイント条件は、スレッドに一意であり、デバッガーが他のスレッドを (それらを無効にする必要があります) で他のブレークポイントにヒットしません、限りコードをステップ インし、他のスレッドを切り替えずにコードにステップ インできます。

    > [!NOTE]
    > デバッガーが進むと、すべてのスレッドが実行されます。 ただし、他のスレッドの 1 つに、ブレークポイントにヒットしない限り、デバッガーが他のスレッドでコードを中断しません。 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>マルチ スレッド デバッグ ウィンドウについて 

#### <a name="to-switch-to-another-thread"></a>別のスレッドに切り替えるには 

- 別のスレッドに切り替えるを参照してください[する方法: 別のスレッド間のデバッグに切り替える。](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

## <a name="video"></a>マルチ スレッドのデバッグに関するビデオを見る

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171" frameborder="0" allowfullscreen></iframe>
</div>

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>並列スタック ウィンドウや 並列ウォッチ ウィンドウの詳細について  
  
- 参照してください[する方法: 並列スタック ウィンドウの使用](../debugger/using-the-parallel-stacks-window.md) 

- 参照してください[する方法: 並列ウォッチ ウィンドウの使用](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法 : デバッグ中に別のスレッドに切り替える](../debugger/how-to-switch-to-another-thread-while-debugging.md)

