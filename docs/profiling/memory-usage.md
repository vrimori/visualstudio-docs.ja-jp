---
title: "メモリ使用量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8a3c6e60d0ea85d93281764ec3a3435538b9baa0
ms.openlocfilehash: b81ce391ad842085f95ff0a4a6e906036406230a
ms.lasthandoff: 02/28/2017

---
# <a name="memory-usage"></a>メモリ使用量
デバッガーに統合された **メモリ使用量** 診断ツールを使用したデバッグ中に、メモリ リークおよび非効率的なメモリを見つけます。 メモリ使用量ツールを使用すると、マネージ メモリ ヒープ、およびネイティブ メモリ ヒープの&1; つまたは複数の *スナップショット* を取得できます。 .NET アプリ、ネイティブ アプリ、または混在モード (.NET とネイティブ) アプリのスナップショットを収集できます。  
  
-   単一のスナップショットを分析することにより、オブジェクト型のメモリ使用に対する相対的な影響を理解し、アプリ内でメモリが効率的に使用されていないコードを検出することができます。  
  
-   アプリの&2; つのスナップショットを比較 (diff) することにより、コード内で時間の経過に伴ってメモリ使用量が増加している箇所を検出することもできます。  
  
 次の図は、**[診断ツール]** ウィンドウ (Visual Studio 2015 Update 1 以降で利用可能) を示しています。  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
 **メモリ使用量** ツールでメモリのスナップショットをいつでも収集できますが、Visual Studio デバッガーを使用すると、パフォーマンスの問題を調査中にアプリケーションの実行方法を制御することができます。 ブレークポイントの設定、ステップ実行、すべて中断、その他のデバッガー アクションは、パフォーマンスの調査を最も関連性の高いコード パスに集中させるのに役立ちます。 アプリの実行中にこれらのアクションを実行することで、目的としていないコードからのノイズを除去することができ、問題の診断にかかる時間を大幅に短縮できます。  
  
 さらに、デバッガーの外部のメモリ ツールも使用できます。 「[ストア アプリのメモリ使用量の分析](../profiling/memory-usage-without-debugging2.md)」を参照してください。  
  
> [!NOTE]
>  **カスタム アロケーター サポート** ネイティブ メモリ プロファイラーは、実行時に生成された割り当て [ETW](https://msdn.microsoft.com/en-us/library/windows/desktop/bb968803\(v=vs.85\).aspx) イベント データを収集して機能します。  CRT および Windows SDK のアロケーターには、割り当てデータをキャプチャできるように、ソース レベルで注釈が付けられています。  独自のアロケーターを作成する場合、新しく割り当てられたヒープ メモリへのポインターを返すすべての関数は、[__declspec](/visual-cpp/cpp/declspec)(アロケーター) で修飾できます。myMalloc での例を次に示します。  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)` 

## <a name="collect-memory-usage-data"></a>メモリ使用量データの収集

1.  Visual Studio でデバッグするプロジェクトを開き、メモリ使用率を調べ始めるポイントでアプリのブレークポイントを設定します。

    メモリの問題があると疑われる領域がある場合は、メモリの問題が発生する前に、最初のブレークポイントを設定します。

    > [!TIP]
    >  アプリがメモリの割り当てと割り当て解除を頻繁に行う場合、目的とする操作のメモリ プロファイルを取得するのが容易ではないため、操作の最初と最後にブレークポイントを設定して (または操作をステップ実行して)、メモリが変更された正確なポイントを見つけます。 

2.  分析するコードの関数またはリージョンの終わりに (または疑わしいメモリの問題が発生したあとに)&2; つ目のブレークポイントを設定します。
  
3.  **[診断ツール]** ウィンドウは、オフにしていない限り自動的に表示されます。 もう一度ウィンドウを表示するには、**[デバッグ] > [ウィンドウ] > [診断ツールの表示]** の順にクリックします。

4.  ツールバーにある **[ツールの選択]** の設定で、**[メモリ使用量]** を選択します。

     ![診断ツールを表示する](../profiling/media/DiagToolsSelectTool.png "DiagToolsSelectTool")

5.  **[デバッグ]、[デバッグの開始]** の順にクリックします (あるいは、ツール バーの **[開始]** をクリックするか、**F5** を押します)。

     アプリケーションが読み込みを完了すると、診断ツールの概要ビューが表示されます。

     ![診断ツールの概要タブ](../profiling/media/DiagToolsSummaryTab.png "DiagToolsSummaryTab")

     > [!NOTE]
     >  メモリ データの収集はネイティブ アプリや混在モードのアプリのパフォーマンスに影響する可能性があるため、既定でメモリのスナップショットは無効になっています。 ネイティブ アプリや混在モードのアプリのスナップショットを有効にするには、デバッグ セッションを開始します (ショートカット キー: **F5**)。 **[診断ツール]** ウィンドウが表示されたら、[メモリ使用量] タブを選択して、**[ヒープのプロファイル]** を選択します。  
     >   
     >  ![スナップショットを有効にする](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
     >   
     >  デバッグを停止 (ショートカット キー: **Shift + F5**) してから再開します。  

6.  デバッグ セッションの開始時にスナップショットを取得するには、**[メモリ使用量]** 概要ツールバーで **[スナップショットの取得]** を選択します。 (ここにもブレークポイントを設定すると役に立つ場合があります。)

    ![スナップショットを取得する](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot") 
     
     > [!TIP]
     >  -   メモリ比較のベースラインを作成するには、デバッグ セッションの開始時に、スナップショットを取得することを検討します。  

6.  最初のブレークポイントにヒットするシナリオを実行します。

7.  デバッガーが最初のブレークポイントで一時停止している間に、**[メモリ使用量]** 概要ツールバーで **[スナップショットの取得]** を選択します。  

8.  F5 キーを押すと、アプリケーションが&2; つ目のブレークポイントまで実行されます。

9.  次に、別のスナップショットを取得しましょう。

     この時点で、データの分析を開始できます。    
  
## <a name="analyze-memory-usage-data"></a>メモリ使用量データの分析
メモリ使用量の概要テーブルの行には、デバッグ セッション中に取得したスナップショットが一覧表示され、より詳細なビューへのリンクが提供されています。

![メモリの概要テーブル](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 列の名前は、プロジェクトのプロパティで選択したデバッグ モード (.NET、ネイティブ、または混合 (.NET とネイティブの両方)) によって決まります。  
  
-   **[オブジェクト (相違)]** および **[割り当て (相違)]** 列には、スナップショット取得時の .NET メモリおよびネイティブ メモリ内のオブジェクト数が表示されます。  
  
-   **[ヒープ サイズ (相違)]** 列には、.NET ヒープおよびネイティブ ヒープのバイト数が表示されます。 

複数のスナップショットを取得した場合、概要テーブルのセルには、行のスナップショットと前のスナップショットの間の値の変化が含まれます。  
  
![メモリの概要テーブル セル](../profiling/media/dbgdiag_mem_summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  

メモリ使用量を分析するには、リンクを&1; つクリックして、メモリ使用量の詳細なレポートを開きます。  

-   現在のスナップショットと前のスナップショットの相違点の詳細を表示するには、矢印の左にある変更リンクを選択します (![メモリ使用量増加](../profiling/media/prof-tour-mem-usage-up-arrow.png "メモリ使用量増加"))。 赤い矢印はメモリ使用量が増加したことを示し、緑の矢印は減少したことを示しています。

    > [!TIP]
    >  より迅速にメモリの問題を識別するために、Diff レポートは、総数が最も増加したオブジェクト型の順 (**[オブジェクト (相違)]** 列の変更リンク) や、総ヒープ サイズが最も増加したオブジェクト型の順 (**[ヒープ サイズ (相違)]** 変更リンク) に並べ替えられています。

-   選択したスナップショットのみの詳細を表示するには、変更リンクではないリンクを選択します。 
  
 レポートが新しいウィンドウに表示されます。   
  
### <a name="managed-types-reports"></a>マネージ型レポート  
 メモリ使用量の概要テーブルで、**[オブジェクト (相違)]** または **[割り当て (相違)]** セルの現在のリンクを選択します。  
  
 ![デバッガーのマネージ型のレポート &#45; ルートへのパス](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 上のウィンドウには、型で参照されているすべてのオブジェクトのサイズ (**包括サイズ**) を含む、スナップショット内の型の総数およびサイズが表示されます。  
  
 下のウィンドウの **[ルートのパス]** ツリーには、上ウィンドウで選択されている型を参照するオブジェクトが表示されます。 .NET Framework のガベージ コレクターがオブジェクトのメモリをクリーンアップするのは、そのオブジェクトを参照する最後の型が解放されたときに限られます。  
  
 **[参照される型]** ツリーには、上のウィンドウで選択されている型に保持されている参照が表示されます。  
  
 ![マネージ参照型のレポート ビュー](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 上のウィンドウで選択した型のインスタンスを表示するには、![[インスタンス] アイコン](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") アイコンを選択します。  
  
 ![インスタンス ビュー](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **[インスタンス]** ビューには、上のウィンドウのスナップショットで選択されているインスタンスが表示されます。 [ルートのパス] および [参照されたオブジェクト] ウィンドウには、選択したインスタンスを参照するオブジェクト、および選択したインスタンスが参照する型が表示されます。 スナップショットが取得された時点でデバッガーを停止すると、[値] セルの上にマウス カーソルを移動して、ツール ヒントにオブジェクトの値を表示することができます。  
  
### <a name="native-type-reports"></a>ネイティブ型のレポート  
 **[診断ツール]** ウィンドウのメモリ使用量の概要テーブルで、**[割り当て (相違)]** または **[ヒープ サイズ (相違)]** セルの現在のリンクを選択します。  
  
 ![ネイティブ型のビュー](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **[型ビュー]** には、スナップショットの型の数およびサイズが表示されます。  
  
-   選択した型のインスタンス アイコン (![[オブジェクト型] 列の [インスタンス] アイコン](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) を選択し、スナップショットの選択した型のオブジェクトに関する情報を表示します。  
  
     **[インスタンス]** ビューには、選択した型の各インスタンスが表示されます。 インスタンスを選択すると呼び出し履歴が表示され、その結果、 **[割り当て呼び出し履歴]** ウィンドウにそのインスタンスが作成されます。  
  
     ![インスタンス ビュー](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   **[表示モード]** の一覧で **[スタック ビュー]** を選択し、選択した型の割り当て履歴を表示します。  
  
     ![スタック ビュー](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>変更 (Diff) レポート  
  
-   **[診断ツール]** ウィンドウの **[メモリ使用量]** タブで、概要テーブルのセルにある変更リンクを選択します。  
  
     ![変更 &#40;差分&#41; レポートの選択](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
-   マネージ レポート、もしくはネイティブ レポートの **[比較対象]** 一覧でスナップショットを選択します。  
  
     ![比較対象の一覧からスナップショットを選択](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
 変更レポートを実行すると、基本のスナップショット値と比較のスナップショットの差分を表示する列 ( **(Diff)**のマークが付けられる) が、基本レポートに追加されます。 ネイティブ型の差分レポート ビューは次のようになります。  
  
 ![ネイティブ型の差分ビュー](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>ブログとビデオ  
 [Visual Studio 2015 の診断ツール [デバッガー] ウィンドウ](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [ブログ: Visual Studio 2015 のデバッグ中のメモリ使用量ツール](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/13/memory-usage-tool-while-debugging-in-visual-studio-2015.aspx)  
  
 [Visual C++ ブログ: VS2015 プレビューでのネイティブ メモリ診断](http://blogs.msdn.com/b/vcblog/archive/2014/11/21/native-memory-diagnostics-in-vs2015-preview.aspx)  
  
 [Visual C++ ブログ: Visual Studio 2015 CTP のネイティブ メモリ診断ツール](http://blogs.msdn.com/b/vcblog/archive/2014/06/04/native-memory-diagnostic-tools-for-visual-studio-14-ctp1.aspx)
