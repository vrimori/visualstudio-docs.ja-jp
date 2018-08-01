---
title: アプリの CPU 使用率を測定する
description: デバッガーに統合された診断ツールを使用して、アプリケーションでの CPU パフォーマンスの問題を分析します。
ms.custom: mvc
ms.date: 02/27/2017
ms.technology: vs-ide-debug
ms.topic: tutorial
f1_keywords:
- vs.performance.wizard.intropage
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
- CPU Usage
- Diagnostics Tools
ms.assetid: da2fbf8a-2d41-4654-a509-dd238532d25a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa2751b901323adb6aa17ab553aa2f464d883ebd
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39206852"
---
# <a name="profile-application-performance-in-visual-studio"></a>Visual Studio でのアプリケーション パフォーマンスのプロファイリング
Visual Studio プロファイリング ツールを使用して、アプリケーションでパフォーマンスの問題を分析することができます。 このガイドでは、診断ツールの **[CPU 使用率]** タブを使用し、アプリのパフォーマンス データを取得する方法について説明します。 診断ツールは Visual Studio の .NET 開発 (ASP.NET を含む) とネイティブ/C++ 開発で利用できます。
  
デバッガーが一時停止すると、**CPU 使用率**ツールは、アプリケーションで実行されている関数に関する情報を収集します。 このツールは、作業を実行していた関数を一覧表示し、サンプリング セッションの特定のセグメントに焦点を当てるために使用できるタイムライン グラフを提供します。

診断ハブでは、診断セッションの実行と管理のために他の多くのオプションを提供しています。 **CPU 使用率**では必要なデータを得ることができない場合、[他のプロファイリング ツール](../profiling/profiling-feature-tour.md)が別の種類の情報を提供します。その情報が役に立つ可能性があります。 多くの場合、アプリケーションのパフォーマンス上の問題は CPU 以外の何かが原因になります。メモリ、UI のレンダリング、ネットワークの要求時間などです。 診断ハブには、この種のデータを記録し、分析するためのオプションが他にもいろいろあります。

|         |         |
|---------|---------|
|  ![ビデオのムービー カメラ アイコン](../install/media/video-icon.png "ビデオを見る")  |    CPU 使用率の分析方法とメモリ使用率の分析方法については、診断ツールの使用に関する[こちらのビデオ](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171)をご覧ください。 |

この記事では、通常のデバッグ ワークフローで CPU 使用率を分析する方法について説明します。 デバッガーをアタッチせずに、または実行中のアプリをターゲットにすることで、CPU 使用率を分析することもできます。詳細については、「[デバッガーを使用して、または使用せずにプロファイリング ツールを実行する](../profiling/running-profiling-tools-with-or-without-the-debugger.md)」の「[デバッグなしでプロファイリング データを収集する](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging)」をご覧ください。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * CPU 使用率のデータの収集
> * CPU 使用率データの分析
  
## <a name="step-1-collect-profiling-data"></a>手順 1: プロファイル データを収集する 
  
1.  Visual Studio でデバッグするプロジェクトを開き、CPU 使用率を調べるポイントでアプリのブレークポイントを設定します。

2.  分析するコードの関数またはリージョンの終わりに 2 つ目のブレークポイントを設定します。

    > [!TIP]
    > 2 つのブレークポイントを設定することで、分析するコードの部分にデータ収集を限定できます。
  
3.  **[診断ツール]** ウィンドウは、オフにしていない限り自動的に表示されます。 もう一度ウィンドウを表示するには、**[デバッグ]** > **[ウィンドウ]** > **[診断ツールの表示]** の順にクリックします。

4.  ツールバーにある **[ツールの選択]** の設定で、**CPU 使用率**、[メモリ使用率](../profiling/Memory-Usage.md)、またはその両方を表示するかどうかを選択できます。 Visual Studio Enterprise を実行している場合は、**[ツール]** > **[オプション]** > **[IntelliTrace]** で IntelliTrace を有効または無効にすることもできます。

     ![診断ツールを表示する](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

     CPU 使用率を中心に観察します。**CPU 使用率**が有効になっていることを確認してください (既定では有効になっています)。

5.  **[デバッグ]** > **[デバッグの開始]** の順にクリックします (または、ツール バーの **[開始]** をクリックするか、**F5** キーを押します)。

     アプリケーションが読み込みを完了すると、診断ツールの概要ビューが表示されます。

     ![診断ツールの概要タブ](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     イベントに関する詳細については、「[診断ツール ウィンドウの [イベント検索とフィルター処理] タブ](http://blogs.msdn.com/b/visualstudioalm/archive/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window.aspx)」を参照してください。

6.  最初のブレークポイントにヒットするシナリオを実行します。

7.  デバッガーが一時停止になっているとき、CPU 使用率データの収集を有効にし、**[CPU 使用率]** タブを開きます。

     ![診断ツールの [CPU プロファイルの有効化]](../profiling/media/DiagToolsEnableCPUProfiling.png "DiagToolsEnableCPUProfiling")

     **[CPU プロファイルの記録]** を選択すると、Visual Studio は関数とそれにかかる時間の記録を開始します。 アプリケーションがブレークポイントで停止したとき、この収集されたデータのみを表示できます。

8.  F5 キーを押すと、アプリケーションが 2 つ目のブレークポイントまで実行されます。

     これで、2 つのブレークポイント間で実行されるコードのリージョンを対象に、アプリケーションのパフォーマンス データが得られました。

9.  CPU タイムラインで、分析対象として関心のあるリージョンを選択します (プロファイル データを表示するリージョンにする必要があります)。

     ![診断ツールで時間のセグメントを選択する](../profiling/media/DiagToolsSelectTimeSegment.png "DiagToolsSelectTimeSegment")

     プロファイラーがスレッド データの準備を開始します。 それが完了するまで待ちます。

     ![診断ツールのスレッド準備](../profiling/media/DiagToolsPreparingThreads.png "DiagToolsPreparingThreads")
  
     CPU 使用率ツールの **[CPU 使用率]** タブにレポートが表示されます。
  
     ![診断ツールの [CPU 使用率] タブ](../profiling/media/DiagToolsCPUUsageTab.png "DiagToolsCPUUsageTab")

     この時点で、データの分析を開始できます。

## <a name="step-2-analyze-cpu-usage-data"></a>手順 2: CPU 使用率データを分析する

データの分析では、最初に CPU 使用率で関数の一覧を調べて最も多くの作業を行っている関数を特定し、それから個々の作業を詳しく調べることをお勧めします。

1. 関数の一覧で、最も多くの作業を行っている関数を調べます。

    ![診断ツールの CPU 使用率の関数一覧](../profiling/media/DiagToolsCPUUsageFunctionList.png "DiagToolsCPUUsageFunctionList")

    > [!TIP]
    > 関数は、最も多くの作業を行っている順に一覧表示されます (呼び出し順ではありません)。 それにより、最も実行時間の長い関数を簡単に特定できます。

2. 関数の一覧で、たくさんの作業を行っているアプリケーション関数の 1 つをダブルクリックします。

    関数をダブルクリックすると、左ウィンドウに **[呼び出し元/呼び出し先]** ビューが開きます。 

    ![診断ツールの [呼び出し元/呼び出し先] ビュー](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")

    このビューでは、選択した関数が見出しと **[現在の関数]** ボックスに表示されます (この例では、GetNumber)。 現在の関数を呼び出した関数が左側の **[呼び出し元の関数]** に表示されます。現在の関数で呼び出された関数があれば、それは右側の **[呼び出される関数]** ボックスに表示されます。 (いずれかのボックスを選択し、現在の関数を変更できます。)

    このビューには、合計時間 (ms) と関数の完了にかかったアプリケーション実行時間全体のパーセンテージが表示されます。
    また、**関数本体**に、呼び出し元の関数と呼び出される関数にかかった時間を除き、関数本体にかかった時間の合計 (と時間のパーセンテージ) が表示されます。 (この例では、3729 ms のうち 3713 ms が関数本体に使用され、残りの 16 ms がこの関数で呼び出された外部コードで使用されています。)

    > [!TIP]
    > **関数本体**の値が高い場合、関数自体の中でパフォーマンス上のボトルネックとなっている可能性があります。

3. 関数の呼び出し順を示す上位レベルのビューを表示する場合、ウィンドウの上部にあるドロップダウンから **[コール ツリー]** を選択します。
 
    図中の番号は、前に示した各手順に対応しています。
  
    ![診断ツールのコール ツリー](../profiling/media/DiagToolsCallTree.png "DiagToolsCallTree")
  
|||
|-|-|
|![手順 1](../profiling/media/ProcGuid_1.png "ProcGuid_1")|CPU 使用率コール ツリーのトップ レベルのノードは擬似ノードです。|  
|![手順 2](../profiling/media/ProcGuid_2.png "ProcGuid_2")|ほとんどのアプリでは、 [[外部コードの表示]](#view-external-code) オプションをオフにすると、セカンド レベルのノードは **[外部コード]** ノードとなります。このノードに含まれるシステムおよびフレームワーク コードは、アプリの開始と停止、UI の描画、スレッド スケジュールの制御、およびアプリへの他の低レベル サービスの提供を行います。|  
|![手順 3](../profiling/media/ProcGuid_3.png "ProcGuid_3")|セカンド レベル ノードの子はユーザー コード メソッドおよび非同期ルーチンで、セカンド レベル システムとフレームワーク コードによって呼び出される、または作成されます。|
|![手順 4](../profiling/media/ProcGuid_4.png "ProcGuid_4")|メソッドの子ノードには、親メソッドの呼び出しのみのデータが含まれます。 **[外部コードの表示]** がオフのとき、アプリ メソッドには **[外部コード]** ノードが含まれる場合もあります。|

列値の詳細は次のようになります。

- **[合計 CPU]** は、その関数、およびその関数によって呼び出された関数によって実行された作業の量を示します。 合計 CPU 値が高い関数は、全体的に見て最も負荷の高い関数です。
  
- **[セルフ CPU]** は、関数本体内のコードによって実行された作業の量を示しますが、その関数から呼び出された関数によって実行された作業は含まれません。 **セルフ CPU 値**が高い部分は、関数自体の中でパフォーマンス上のボトルネックとなっている可能性があります。

- **モジュール** 関数が含まれるモジュールの名前です。あるいは、[外部コード] ノード内の関数が含まれるモジュールの数です。

## <a name="view-external-code"></a>外部コードの表示

外部コードは、作成したコードによって実行されるシステムおよびフレームワーク コンポーネント内の関数です。 外部コードには、アプリの開始と停止、UI の描画、スレッドの制御、およびアプリへの他の低レベル サービスの提供を行う関数が含まれます。 外部コードを確認することはほとんどないため、CPU 使用率ツールはユーザー メソッドの外部関数を 1 つの **[外部コード]** ノードにまとめます。
  
外部コードのコール パスを表示する場合、 **[フィルター ビュー]** リストから **[外部コードの表示]** をクリックし、 **[適用]** をクリックします。  
  
![[フィルター表示]、[外部コードの表示] の順に選択します](../profiling/media/DiagToolsShowExternalCode.png "DiagToolsShowExternalCode")  
  
多くの外部コードの呼び出しチェーンは複雑な入れ子になっているため、関数名列の幅は、一部の大型コンピューター モニターを除いてディスプレイの幅に収まりきらない可能性があります。 その場合、関数名は **[...]** と表示されます。
  
検索ボックスを使って目的のノードを探した後、水平スクロール バーを使ってデータを表示させます。

> [!TIP]
> Windows 関数を呼び出す外部コードをプロファイリングする場合は、最新の .*pdb* ファイルがあることを確認する必要があります。 これらのファイルがない場合、レポート ビューに暗号のようなわかりにくい Windows 関数名が一覧表示されます。 必要なファイルがあることを確認する方法の詳細については、「[Specify symbol (.pdb) and source files in the debugger](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)」(デバッガーにシンボル (.pdb) とソース ファイルを指定する) を参照してください。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、CPU 使用率のデータを収集し、分析する方法について学習しました。 「[クイック スタート: プロファイリング ツールの概要](../profiling/profiling-feature-tour.md)」を既に完了している場合、自分のアプリのメモリ使用量を分析する方法を一読しておくことをお勧めします。

> [!div class="nextstepaction"]
> [Visual Studio でのメモリ使用のプロファイリング](../profiling/memory-usage.md) 
