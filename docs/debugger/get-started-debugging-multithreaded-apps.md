---
title: マルチ スレッド アプリケーションのデバッグについて理解するには
description: Visual Studio での並列スタック ウィンドウや 並列ウォッチ ウィンドウを使用したデバッグします。
ms.custom: H1HackMay2017
ms.date: 08/01/2018
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 66239362e454d5ab333214c444aeee3fa54b1b8a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936861"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Visual Studio でマルチ スレッド アプリケーションのデバッグの開始します。
Visual Studio には、いくつかのツールとマルチ スレッド アプリケーションをデバッグする方法をユーザー インターフェイス要素が用意されています。 このチュートリアルでは、スレッド マーカーを使用する方法、**並列スタック**ウィンドウで、**並列ウォッチ**ウィンドウ、条件付きブレークポイントは、および [フィルター] ブレークポイント。 このチュートリアルでは、わずか数分ですが、完了に慣れることがするマルチ スレッド アプリケーションのデバッグ機能を使用します。

| | |
|---------|---------|
| ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る") | [ビデオを見る](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171)同様の手順を示しています。 マルチ スレッド デバッグします。 |

その他のトピックでは、その他のマルチ スレッド デバッグ ツールを使用して追加についてを説明します。

- 使用する方法を示すようなトピックの**デバッグの場所**ツールバーと**スレッド**ウィンドウを参照してください[チュートリアル: マルチ スレッド アプリケーションをデバッグ](../debugger/how-to-use-the-threads-window.md)します。

- 使用するサンプルのようなトピックの<xref:System.Threading.Tasks.Task>(マネージ コード) を参照してください (C++)、同時実行ランタイムと[チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)します。 一般的なデバッグのヒントは、このトピックの「とリンクされたトピック両方を読み取る最もマルチ スレッド アプリケーション種類に適用されます。
  
このチュートリアルを開始するには、マルチ スレッド アプリケーション プロジェクトが必要です。 次の手順に従って、このようなプロジェクトを作成します。  
  
#### <a name="to-create-the-multithreaded-app-project"></a>マルチ スレッド アプリ プロジェクトを作成するには  
  
1.  **ファイル** メニューの 選択**新規** をクリックし、**プロジェクト**します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  好みの言語をクリックします。 **Visual c#**、 **Visual c**、または**Visual Basic**します。  
  
3.  **Windows デスクトップ**、選択**コンソール アプリ**します。  
  
4.  **名前**ボックスの [名前] を入力します。  
  
5.  **[OK]** をクリックします。  
  
     新しいコンソール プロジェクトが表示されます。 プロジェクトが作成されると、ソース ファイルが表示されます。 選択した言語に応じて、ソース ファイルは Program.cs、MyThreadWalkthroughApp.cpp、または Module1.vb という可能性があります。  
  
6.  ソース ファイルに表示されるコードを削除し、ここで示す例のコードに置き換えます。

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
  
7.  **ファイル** メニューのをクリックして**すべて保存**します。  
  
#### <a name="to-begin-the-tutorial"></a>このチュートリアルを開始するには  
  
-   ソース コード エディターでは、次のコードを探します。 
  
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
  
#### <a name="to-start-debugging"></a>デバッグを開始するには  
  
1. 左側の余白内をクリックして、`Thread.Sleep`または`this_thread::sleep_for`新しいブレークポイントを挿入するステートメント。  
  
    ソース コード エディターの左側にある余白、赤い円が表示されます。 これは、ブレークポイントがその場所に設定されていることを示します。 
  
2. **デバッグ** メニューのをクリックして**デバッグの開始** (**F5**)。  
  
    Visual Studio ソリューションをビルド、アタッチされたデバッガーを開始してから、アプリ、アプリがブレークポイントで停止します。  
  
   > [!NOTE]
   > コンソール ウィンドウにフォーカスを移動する場合のクリックして、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ウィンドウにフォーカスが戻って[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
3. ソース コード エディターでは、ブレークポイントを含む行を見つけます。  
  
   ```csharp  
   Thread.Sleep(3000);  
   ```  
  
   ```C++  
   this_thread::sleep_for(chrono::seconds(3)); 
   ```

   ```VB
   Thread.Sleep(3000)
   ```    
  
#### <a name="ShowThreadsInSource"></a>スレッド マーカーを検出するには  

1.  [デバッグ] ツールバーをクリックして、**ソース スレッドを表示**ボタン![ソース スレッドを表示](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")します。

2. キーを押して**F11**コード デバッガーの 1 つの行に 1 回です。
  
3.  ウィンドウ左端の余白に注目します。 この行に表示されます、*スレッド マーカー*アイコン![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")布の 2 つのスレッドと類似しています。 スレッド マーカーは、スレッドが停止している位置を示します。

    スレッド マーカーを部分的にブレークポイントによって隠さ可能性がありますに注意してください。 
  
4.  スレッド マーカーの上にポインターを置きます。 DataTip が表示されます。 データヒントは、停止したスレッドごとに名前とスレッド ID 番号を表示します。 名前がここでは、おそらくは`<noname>`します。 
  
5.  ショートカット メニューの 利用可能なオプションを表示するスレッド マーカーを右クリックします。
    
## <a name="ParallelStacks"></a>スレッドの場所を表示します。

**並列スタック** ウィンドウに切り替えることができます、タスクを確認しては、各スレッドの呼び出し履歴情報を表示できますスレッド ビューの間、(タスク ベースのプログラミング)。 このアプリでは、スレッド ビューを使用できます。

1. 開く、**並列スタック**ウィンドウを選択して**デバッグ > Windows > 並列スタック**します。 このような画面が表示されます (正確な情報は各スレッド、ハードウェア、および使用するプログラミング言語の現在の場所によって異なるなります)。

    ![並列スタック ウィンドウ](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    この例では、左から右にマネージ コードのこの情報取得します。
    
    - メイン スレッド (左側) が停止しました`Thread.Start`(停止ポイントは、スレッド マーカーのアイコンによって示されます![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker"))。
    - 2 つのスレッドが入力した、 `ServerClass.InstanceMethod`、うちの 1 つは、現在のスレッド (黄色の矢印) で、他のスレッドが停止中に`Thread.Sleep`します。
    - (右) で新しいスレッドが開始されても (停止`ThreadHelper.ThreadStart`)。

2.  内のエントリを右クリックし、**並列スタック**ショートカット メニューの 使用可能なオプションを表示するウィンドウ。

    これらの右クリック メニューからさまざまなアクションを実行することができますが、このチュートリアルでこれらの詳細の示しますが、**並列ウォッチ**ウィンドウ (次のセクション)。

    > [!NOTE]
    > 各スレッドに関する情報を表示を使用して、一覧の確認に関心がある場合、**スレッド**ウィンドウ代わりにします。 参照してください[チュートリアル: マルチ スレッド アプリケーションをデバッグ](../debugger/how-to-use-the-threads-window.md)します。

## <a name="set-a-watch-on-a-variable"></a>変数のウォッチを設定します。

1. 開く、**並列ウォッチ**ウィンドウを選択して**デバッグ > Windows > 並列ウォッチ > 並列ウォッチ 1**します。

2. 表示されているセルをクリックして、`<Add Watch>`テキスト (または、4 番目の列ヘッダーの空のセル) 型`data`、Enter キーを押します。

    スレッドごとに、data 変数の値は、ウィンドウに表示されます。

3. 表示されているセルをもう一度クリックして、`<Add Watch>`テキスト (または、5 番目の列で空のヘッダー セル) 型`count`、Enter キーを押します。

    スレッドごとに count 変数の値は、ウィンドウに表示されます。 (しないこの多くの情報を参照してください。 まだ場合、デバッガー内のスレッドの実行を進めるにさらに数回 f11 キーを押してしてください。)

    ![[並列ウォッチ] ウィンドウ](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 使用可能なオプションを表示するには、ウィンドウ内の行の 1 つを右クリックします。

## <a name="flagging-and-unflagging-threads"></a>スレッドに対するフラグの設定と設定解除  
特に注目するスレッドのフラグを設定することができます。 スレッドに対するフラグの設定は、重要なスレッドを追跡するのには気いないスレッドを無視して良い方法です。  
  
#### <a name="to-flag-threads"></a>スレッドにフラグを設定するには  

1. **並列ウォッチ**ウィンドウで、SHIFT キーを押しながら、複数の行を選択します。

2. 右クリックし、**フラグ**します。

    ここで、選択したすべてのスレッドがフラグが設定されます。 ここで、フラグが設定されたスレッドのみを表示するフィルター処理することができます。
  
3.  **並列ウォッチ**ウィンドウで、検索、**フラグが設定されたスレッドのみを表示する**ボタン![フラグが設定されたスレッドを表示する](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")します。  
  
4.  をクリックして、**フラグが設定されたスレッドのみを表示する**ボタンをクリックします。  
  
    今度は、フラグが設定されたスレッドのみがボックスに表示されます。

    > [!TIP]
    > 一部のスレッドのフラグを設定したときに、コード エディターでのコード行を右クリックし、選択**カーソルにフラグが設定されたスレッドの実行**(フラグ付きのスレッドがすべてのコードに到達に選択することを確認してください)。 これは、選択した線による実行の順序を制御しやすく、コードのスレッドを一時停止[スレッドの凍結と凍結解除](#bkmk_freeze)します。

5.  をクリックして、**フラグが設定されたスレッドのみを表示する**に戻すにはボタン**すべてのスレッド**モード。
    
#### <a name="to-unflag-threads"></a>スレッドのフラグを解除するには

スレッドのフラグを解除することができます、内の 1 つまたは複数のフラグが設定されたスレッドを右クリックして、**並列ウォッチ**ウィンドウ選択**フラグ解除**します。

## <a name="bkmk_freeze"></a> スレッドの実行を凍結と凍結解除 

> [!TIP]
> 停止および再開することができます (中断および再開) スレッドのスレッドが作業を実行する順序を制御します。 デッドロックなどの同時実行の問題を解決し、競合状態が役立ちます。
  
#### <a name="to-freeze-and-unfreeze-threads"></a>スレッドを凍結および凍結解除するには  
  
1.  **並列ウォッチ**ウィンドウで、すべての行選択すると、右クリックして選択**固定**します。

    2 番目の列の一時停止アイコンが行ごとに表示されます。 一時停止アイコンは、スレッドが固定されていることを示します。

2.  1 つの行のみをクリックして、行の選択を解除します。

3.  行を右クリックして**凍結解除**します。

    一時停止アイコンは、この行は、スレッドが凍結して不要になったことを示すされなくなります。

4.  コード エディターに切り替え、をクリックして**F11**します。 固定されたスレッドのみを実行します。

    アプリは、いくつかの新しいスレッドをインスタンス化も可能性があります。 すべての新しいスレッドはフラグが設定されたとが固定されていないことに注意してください。

## <a name="bkmk_follow_a_thread"></a> 次の条件付きブレークポイントを使用して 1 つのスレッド

デバッガーでの 1 つのスレッドの実行を追跡する便利な場合あります。 行うことができます 1 つの方法で、必要のないスレッドを凍結することですが、一部のシナリオでは、(特定のバグの再現コード) を他のスレッドを凍結しないで 1 つのスレッドに従うする可能性があります。 スレッドを他のスレッドをフリーズさせないに従って、興味のあるスレッドで以外のコードに重大なを避ける必要があります。 設定してこれを行う、[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)します。

スレッド名またはスレッド ID などのさまざまな条件でブレークポイントを設定することができます。 各スレッドを一意になることがわかっているデータに、条件を設定する役立つと思われるもう 1 つの方法です。 これは、任意の特定のスレッドよりもいくつかの特定のデータ値に強い関心がする一般的なデバッグ シナリオです。

#### <a name="to-follow-a-single-thread"></a>1 つのスレッドを実行するには

1. 以前に作成したブレークポイントを右クリックし **条件**します。

2. **ブレークポイントの設定**ウィンドウで、「`data == 5`の条件付きの式。

    ![条件付きブレークポイント](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 特定のスレッドで必要な場合は、スレッド名またはスレッド ID を使用条件。 この、**ブレークポイントの設定**ウィンドウで、**フィルター**の代わりに**条件式**フィルターのヒントに従います。 (デバッガーを再起動すると、スレッド Id が変更) してから、アプリのコードでスレッドを名前たい場合があります。

3. 閉じる、**ブレークポイントの設定**ウィンドウ。

4. [再起動] をクリックして![アプリの再起動](../debugger/media/dbg-tour-restart.png "RestartApp")デバッグ セッションを再開するボタンをクリックします。

    データ変数は 5 スレッド上のコードに分割されます。 黄色の矢印 (現在のデバッガー コンテキスト) 内で検索、**並列ウォッチ**ことを確認するウィンドウ。

5. ここで、ステップ オーバー (F10) のコード (F11) コードにステップ インとし、1 つのスレッドの実行を追跡できます。

    ブレークポイント条件は、スレッドに一意であり、デバッガーが (無効にする必要があります)、他のスレッドで、他のブレークポイントにヒットしない、限りは、コードをステップし、他のスレッドを切り替えずにコードにステップ インします。

    > [!NOTE]
    > デバッガーが進むと、すべてのスレッドが実行されます。 ただし、他のスレッドのいずれかのブレークポイントをヒットしない限り、デバッガーが他のスレッドでコードを中断しません。 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>詳細については、マルチ スレッド デバッグ ウィンドウ 

#### <a name="to-switch-to-another-thread"></a>別のスレッドに切り替える 

- 別のスレッドに切り替えるを参照してください[方法: 別のスレッド デバッグ中に切り替える。](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>並列スタック ウィンドウや 並列ウォッチ ウィンドウの詳細について  
  
- 参照してください[方法: 並列スタック ウィンドウを使用](../debugger/using-the-parallel-stacks-window.md) 

- 参照してください[方法: 並列ウォッチ ウィンドウの使用](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>関連項目  
 [マルチ スレッド アプリケーションをデバッグします。](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [方法 : デバッグ中に別のスレッドに切り替える](../debugger/how-to-switch-to-another-thread-while-debugging.md)
