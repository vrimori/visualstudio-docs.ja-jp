---
title: "CPU 使用率データの分析 (ASP.NET) | Microsoft Docs"
ms.custom: 
ms.date: 12/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 2d92c4fcdbc3c4af3269876836602025a4403463
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Visual Studio での CPU 使用率データの分析 (ASP.NET)

Visual Studio は、アプリケーションのパフォーマンス問題の分析に役立つ高性能な機能をたくさん備えています。 このトピックでは、基本的な機能のいくつかを簡単に紹介します。 今回、高い CPU 使用率に起因するパフォーマンス上のボトルネックを特定するツールを紹介します。 診断ツールは Visual Studio の .NET 開発 (ASP.NET を含む) とネイティブ/C++ 開発で利用できます。

診断ハブでは、診断セッションの実行と管理のために他の多くのオプションを提供しています。 ここで説明する **CPU 使用率**ツールでは必要なデータを得ることができない場合、[他のプロファイリング ツール](../profiling/Profiling-Tools.md)で得られる別の種類の情報が役に立つことがあります。 多くの場合、アプリケーションのパフォーマンス上の問題は CPU 以外の何かが原因になります。メモリ、UI のレンダリング、ネットワークの要求時間などです。

## <a name="create-a-project"></a>プロジェクトを作成する

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **[Visual C#]** の下で **[Web]** を選択し、真ん中のウィンドウで **[ASP.NET Web アプリケーション (.NET Framework)]** を選択します。

    > [!NOTE]
    > CPU 使用率ツールは現在、ASP.NET Core ではサポートされていません。

1. **MyProfilingApp_MVC** のような名前を入力し、**[OK]** をクリックします。

1. ダイアログ ボックスが表示されたら、真ん中のウィンドウで **[MVC]** を選択し、**[OK]** をクリックします。

    Visual Studio によってプロジェクトが作成されます。 ソリューション エクスプローラー (右ウィンドウ) にプロジェクト ファイルが表示されます。

1. ソリューション エクスプローラーで、[Models] フォルダーを右クリックし、**[追加]**、**[クラス]** の順に選択します。

1. 新しいクラスに `Data.cs` という名前を付け、**[追加]** を選択します。

1. ソリューション エクスプローラーで、`Models/Data.cs` を開き、次の `using` ステートメントをファイルの先頭に追加します。

    ```cs
    using System.Threading;
    ```

1. Data.cs で、下記のコード

    ```cs
    public class Data
    {
    }
    ```

    を、次のコードで置換します。

    ```cs
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. ソリューション エクスプローラーで、Controller/HomeControllers.cs を開き、次のコードを

    ```cs
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    を、次のコードで置換します。

    ```cs
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> 手順 1: プロファイリング データを収集する 
  
1.  最初に、`Simple` コンストラクターのこのコード行でアプリのブレークポイントを設定します。

    `for (int i = 0; i < 200; i++)`

    コード行の左の余白をクリックし、ブレークポイントを設定します。

1.  次に、`Simple` コンストラクターの終わりにある閉じかっこに 2 つ目のブレークポイントを設定します。

     ![プロファイリング用のブレークポイントを設定する](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > 2 つのブレークポイントを設定することで、分析するコードの部分にデータ収集を限定できます。
  
1.  **[診断ツール]** ウィンドウは、オフにしていない限り表示されます。 もう一度ウィンドウを表示するには、**[デバッグ] > [ウィンドウ] > [診断ツールの表示]** の順にクリックします。

1.  **[デバッグ]、[デバッグの開始]** の順にクリックします (あるいは、ツール バーの **[開始]** をクリックするか、**F5** を押します)。

1.  アプリが読み込みを終了したら、Web ページの一番上にある **[情報]** リンクをクリックし、新しいコードを実行します。

1.  診断ツールの**概要**ビューを確認します。

1.  デバッガーが一時停止になっているとき、**[CPU プロファイルの記録]** を選択して CPU 使用率データの収集を有効にし、**[CPU 使用率]** タブを開きます。

     ![診断ツールの [CPU プロファイルの有効化]](../profiling/media/quickstart-cpu-usage-summary.png)

     データ収集が有効になると、記録ボタンに赤い円が表示されます。

     **[CPU プロファイルの記録]** を選択すると、Visual Studio は関数とその実行時間の記録を開始します。時系列グラフも生成され、サンプリング セッションの特定のセグメントに注目できます。アプリケーションがブレークポイントで停止したとき、この収集されたデータのみを表示できます。

6.  F5 キーを押すと、アプリケーションが 2 つ目のブレークポイントまで実行されます。

     これで、2 つのブレークポイント間で実行されるコードのリージョンを対象に、アプリケーションのパフォーマンス データが得られました。

     プロファイラーがスレッド データの準備を開始します。 それが完了するまで待ちます。
  
     CPU 使用率ツールの **[CPU 使用率]** タブにレポートが表示されます。

     この時点で、データの分析を開始できます。

## <a name="Step2"></a> 手順 2: CPU 使用率データの分析

データの分析では、最初に CPU 使用率で関数の一覧を調べて最も多くの作業を行っている関数を特定し、それから個々の作業を詳しく調べることをお勧めします。

1. 関数の一覧で、最も多くの作業を行っている関数を調べます。

     ![診断ツールの [CPU 使用率] タブ](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > 関数は、最も多くの作業を行っている順に一覧表示されます (呼び出し順ではありません)。 それにより、最も実行時間の長い関数を簡単に特定できます。

2. 関数の一覧で、`MyProfilingApp_MVC.Models.ServerClass::GetNumber` 関数をダブルクリックします。

    関数をダブルクリックすると、左ウィンドウで **[呼び出し元/呼び出し先]** ビューが開きます。 

    ![診断ツールの [呼び出し元/呼び出し先] ビュー](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    このビューでは、選択した関数が見出しと **[現在の関数]** ボックスに表示されます (この例では、`ServerClass::GetNumber`)。 現在の関数を呼び出した関数が左側の **[呼び出し元の関数]** に表示されます。現在の関数で呼び出された関数があれば、それは右側の **[呼び出される関数]** ボックスに表示されます。 (いずれかのボックスを選択し、現在の関数を変更できます。)

    このビューには、合計時間 (ms) と関数の完了にかかったアプリケーション実行時間全体のパーセンテージが表示されます。

    また、**関数本体**に、呼び出し元の関数と呼び出される関数にかかった時間を除き、関数本体にかかった時間の合計 (と時間のパーセンテージ) が表示されます。 (この図では、2235 ms のうち 2220 ms が関数本体に使用され、残り時間 (<20 ms) がこの関数で呼び出された外部コードで使用されています。) 実際の値は、環境に応じて異なります。

    > [!TIP]
    > **関数本体**の値が高い場合、関数自体の中でパフォーマンス上のボトルネックとなっている可能性があります。

## <a name="next-steps"></a>次の手順

- [メモリ使用量を分析し](../profiling/memory-usage.md)、パフォーマンス上のボトルネックを特定します。
- CPU 使用率ツールで [CPU 使用率を分析し](../profiling/cpu-usage.md)、さらに詳細な情報を取得します。
- デバッガーをアタッチせずに、または実行中のアプリをターゲットにすることで、CPU 使用率を分析します。詳細については、「[デバッガーを使用して、または使用せずにプロファイリング ツールを実行する](../profiling/running-profiling-tools-with-or-without-the-debugger.md)」の「[デバッグなしでプロファイリング データを収集する](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)」をご覧ください。

## <a name="see-also"></a>参照  

 [Visual Studio のプロファイル](../profiling/index.md)  
 [プロファイリング機能ツアー](../profiling/profiling-feature-tour.md)
