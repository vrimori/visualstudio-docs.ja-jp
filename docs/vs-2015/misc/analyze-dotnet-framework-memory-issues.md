---
title: .NET Framework のメモリに関する問題の分析 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: susanno
manager: douge
ms.openlocfilehash: 210fb8ced645250789c9c1da0339abe0814656ae
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288393"
---
# <a name="analyze-net-framework-memory-issues"></a>.Net Framework のメモリ分析の問題
Visual Studio マネージド メモリ アナライザーを使用して、.NET Framework コードでのメモリ リークおよび非効率的なメモリの使用を検出します。 対象コードの最低限の .NET Framework バージョンは .NET Framework 4.5 です。  
  
 メモリ分析ツールで情報を分析する*ダンプ ヒープ データ付きファイル*をアプリのメモリ内のオブジェクトのコピー。 ダンプ (.dmp) ファイルは、Visual Studio IDE から収集することも、その他のシステム ツールを使用して収集することもできます。  
  
-   単一のスナップショットを分析することにより、オブジェクト型のメモリ使用に対する相対的な影響を理解し、アプリ内でメモリが効率的に使用されていないコードを検出することができます。  
  
-   比較することもできます (*diff*) が原因で、メモリ、コードの領域を見つけるためのアプリの 2 つのスナップショットを使用して、時間と共に増加します。  
  
 マネージ メモリ アナライザーのチュートリアルは、次を参照してください。 [Visual Studio 2013 に実稼働環境での .NET メモリ問題の診断を使用して](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)、Visual Studio ALM と Team Foundation Server のブログにします。  
  
##  <a name="BKMK_Contents"></a> 目次  
 [.NET Framework アプリでメモリの使用](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [アプリでメモリに関する問題を特定します。](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [メモリのスナップショットを収集します。](#BKMK_Collect_memory_snapshots)  
  
 [メモリ使用量の分析します。](#BKMK_Analyze_memory_use)  
  
##  <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> .NET Framework アプリでメモリの使用  
 .NET Framework はガベージ コレクションが実行されるランタイムであるため、ほとんどのアプリでメモリの使用が問題になりません。 ただし、Web サービスや Web アプリケーションなどの長時間実行されるアプリケーションおよびメモリ量に制限があるデバイスでは、メモリ内にオブジェクトが蓄積されると、アプリのパフォーマンスや、そのアプリを実行するデバイスのパフォーマンスに影響することがあります。 メモリが過剰に使用されると、ガベージ コレクターの実行頻度が高すぎる場合や、オペレーティング システムが RAM とディスクとの間でメモリを移動せざるを得ない場合、アプリケーションやコンピューターのリソースが不足する可能性があります。 最悪の場合、"メモリ不足" 例外によってアプリがクラッシュすることもあります。  
  
 .NET*マネージ ヒープ*は、アプリによって作成された参照オブジェクトが格納されている仮想メモリの領域です。 オブジェクトの有効期間はガベージ コレクター (GC) によって管理されます。 ガベージ コレクターは参照を使用して、メモリ ブロックを占有するオブジェクトを追跡します。 参照は、オブジェクトが作成され変数に割り当てられると、作成されます。 単一のオブジェクトに対して、複数の参照を作成することもできます。 たとえば、クラス、コレクション、またはその他のデータ構造にオブジェクトを追加するか、2 つ目の変数にオブジェクトを割り当てると、オブジェクトへの追加の参照が作成されます。 明示的な方法ではありませんが、あるオブジェクトでイベント ハンドラーを別のオブジェクトのイベントに追加した場合も、参照が作成されます。 この場合、ハンドラーが明示的に削除されるか 2 つ目のオブジェクトが破棄されるまで、最初のオブジェクトへの参照が 2 つ目のオブジェクトに保持されます。  
  
 各アプリケーションについて、GC では、アプリケーションから参照されるオブジェクトを追跡する参照ツリーが管理されます。 *参照ツリー*オブジェクトがインスタンス化、動的に関連付けられているスレッドのスタックと、グローバルと静的のオブジェクトを含む、ルートのセット。 オブジェクトへの参照を持つ 1 つ以上の親オブジェクトがある場合、そのオブジェクトではルートが作成されます。 GC は、アプリケーション内の他のオブジェクトまたは変数から参照されていない場合にのみ、そのオブジェクトのメモリを再利用できます。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> アプリでメモリに関する問題を特定します。  
 メモリに関する問題の最も可視的な兆候は、アプリのパフォーマンスです (特に、時間の経過に伴ってパフォーマンスが低下する場合)。 特定のアプリの実行中に他のアプリのパフォーマンスが低下した場合も、メモリの問題を示している可能性があります。 メモリの問題を疑いがある場合は、タスク マネージャーなどのツールを使用してまたは[Windows パフォーマンス モニター](http://technet.microsoft.com/library/cc749249.aspx)調査を進めます。 たとえば、考えられるメモリ リークの原因として、説明が付かないような合計メモリ サイズの増加がないか確認します。  
  
 ![リソース モニターで一貫性のあるメモリの増加](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 また、コードについて認識しているより明らかに大きいメモリ スパイクに気付くことがあります。このような場合は、プロシージャ内での非効率的なメモリの使用を示している可能性があります。  
  
 ![Resource Manager でのメモリ スパイク](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
##  <a name="BKMK_Collect_memory_snapshots"></a> メモリのスナップショットを収集します。  
 メモリ分析ツールで情報を分析する*ダンプ ファイル*ヒープ情報が含まれています。 Visual Studio でダンプ ファイルを作成するかなどのツールを使用することができます[ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx)から[Windows Sysinternals](http://technet.microsoft.com/sysinternals)します。 参照してください[ダンプは、1 つ作成する方法でしょうか。](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) 、Visual Studio デバッガー チーム ブログ。  
  
> [!NOTE]
>  ほとんどのツールでは、完全なヒープ メモリ データの有無に関係なくダンプ情報を収集できます。 Visual Studio メモリ アナライザーでは、完全なヒープ情報が求められます。  
  
 **Visual Studio からダンプを収集するには**  
  
1.  Visual Studio プロジェクトから開始されたプロセスのダンプ ファイルを作成することも、実行中のプロセスにデバッガーをアタッチすることもできます。 参照してください[実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
2.  実行を停止します。 選択すると、デバッガーが停止**すべて中断**上、**デバッグ**メニュー、または例外またはブレークポイントで  
  
3.  **デバッグ**] メニューの [選択**ダンプを保存**します。 **ダンプを保存** ダイアログ ボックスで、場所を指定し、ことを確認します**ヒープ付きミニダンプ**(既定値) が選択されて、**型として保存**一覧。  
  
 **2 つのメモリ スナップショットを比較するには**  
  
 アプリでのメモリ使用量の増加を分析するには、アプリの単一インスタンスから 2 つのダンプ ファイルを収集します。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
##  <a name="BKMK_Analyze_memory_use"></a> メモリ使用量の分析します。  
 [オブジェクトの一覧をフィルター処理](#BKMK_Filter_the_list_of_objects) **&#124;** [単一スナップショットからのメモリ データを分析](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [2 つのメモリの比較スナップショット](#BKMK_Compare_two_memory_snapshots)  
  
 ダンプ ファイルでメモリ使用に関する問題を分析するには:  
  
1.  Visual Studio で、次のように選択します。**ファイル**、**オープン**ダンプ ファイルを指定します。  
  
2.  **ミニダンプ ファイルの概要**ページで、選択**マネージ メモリのデバッグ**します。  
  
     ![ダンプ ファイル概要ページ](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
 メモリ アナライザーによるデバッグ セッションが開始し、ファイルの分析が行われ、[ヒープの表示] ページに結果が表示されます。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
###  <a name="BKMK_Filter_the_list_of_objects"></a> オブジェクトの一覧をフィルター処理します。  
 メモリ アナライザーの既定では、メモリ スナップショット内のオブジェクト一覧がフィルター処理されます。これにより、ユーザー コードの型とインスタンスのみを対象とし、合計ヒープ サイズのパーセンテージで表したしきい値を超える合計包括サイズの型のみが表示されます。 これらのオプションを変更することができます、**ビュー設定**一覧。  
  
|||  
|-|-|  
|**マイ コードのみを有効にする**|[マイ コードのみ] では、独自に作成した型のみを一覧に表示するために、ほとんどの一般的なシステム オブジェクトが非表示になります。<br /><br /> Visual Studio で、マイ コードのみ オプションを設定することも**オプション** ダイアログ ボックス。 **[デバッグ]** メニューの **[オプションと設定]** をクリックします。 **デバッグ**/**全般** タブを選択またはクリア**マイ コードのみ**します。|  
|**小さいオブジェクトを折りたたむ**|**小さいオブジェクトを折りたたむ**合計包括サイズが合計ヒープ サイズの 0.5% 未満のすべての種類を非表示にします。|  
  
 内の文字列を入力して、種類の一覧をフィルターすることもできます、**検索**ボックス。 一覧には、この文字列が名前に含まれる型のみが表示されます。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
###  <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> 1 つのスナップショットからメモリ データを分析します。  
 Visual Studio による新しいデバッグ セッションが開始し、ファイルの分析が行われ、[ヒープの表示] ページにメモリ データが表示されます。  
  
 ![オブジェクトの種類一覧](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>オブジェクトの型テーブル  
 最上部のテーブルには、メモリ内に保持されているオブジェクトの型が一覧表示されます。  
  
-   **カウント**スナップショットで、型のインスタンスの数が表示されます。  
  
-   **サイズ (バイト)** への参照を保持するオブジェクトのサイズを除く、型のすべてのインスタンスのサイズです。 次に、  
  
-   **包括サイズ (バイト)** の参照先のオブジェクトのサイズが含まれています。  
  
 インスタンスのアイコンを選択することができます (![オブジェクト型列のインスタンス アイコン](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) で、**オブジェクトの種類**のインスタンスの一覧を表示する列、入力します。  
  
#### <a name="instance-table"></a>インスタンス テーブル  
 ![インスタンス テーブル](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
-   **インスタンス**オブジェクトのオブジェクト識別子として機能するオブジェクトのメモリ位置には  
  
-   **値**値型の実際の値が表示されます。 参照される型の名前の上にポインターを合わせると、データヒントでそのデータ値を確認できます。  
  
     ![データ ヒントで値をインスタンス](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
-   **サイズ (バイト)** への参照を保持するオブジェクトのサイズを除く、オブジェクトのサイズです。 次に、  
  
-   **包括サイズ (バイト)** の参照先のオブジェクトのサイズが含まれています。  
  
 既定では、型とインスタンスは並んで**包括サイズ (バイト)** します。 並べ替え順序を変更するには、一覧の列ヘッダーを選択します。  
  
#### <a name="paths-to-root"></a>ルートのパス  
  
-   選択した型に対して、**オブジェクトの種類**、テーブル、**ルートのパス**への参照の数と共に、型のすべてのオブジェクトのルート オブジェクトに固有の型階層を表示するテーブル、階層の上にある型。  
  
-   型のインスタンスから選択したオブジェクトの**ルートのパス**インスタンスへの参照を保持する実際のオブジェクトのグラフを示しています。 オブジェクトの名前の上にポインターを合わせると、データヒントでそのデータ値を確認できます。  
  
#### <a name="referenced-types--referenced-objects"></a>参照される型/参照されるオブジェクト  
  
-   選択した型に対して、**オブジェクトの種類**、テーブル、**参照される型** タブには、選択した種類のすべてのオブジェクトによって保持されている参照先の種類の数とサイズが表示されます。  
  
-   型の選択したインスタンスの**参照されたオブジェクト**選択したインスタンスによって保持されているオブジェクトが表示されます。 名前の上にポインターを合わせると、データヒントでそのデータ値を確認できます。  
  
 **循環参照**  
  
 オブジェクトでは、直接的または間接的に 1 つ目のオブジェクトへの参照を保持する 2 つ目のオブジェクトを参照している可能性があります。 参照パスの展開を中止し、追加メモリ アナライザーには、このような状況が検出されると、 **[循環が検出されました]** 最初のオブジェクトと停止の一覧を注釈。  
  
 **ルートの種類**  
  
 メモリ アナライザーでは、保持されている参照の種類を示す注釈がルート オブジェクトに追加されます。  
  
|注釈|説明|  
|----------------|-----------------|  
|**静的変数** `VariableName`|静的変数。 `VariableName` は変数の名前です。|  
|**終了処理ハンドル**|ファイナライザー キューからの参照。|  
|**ローカル変数**|ローカル変数。|  
|**強力なハンドル**|オブジェクト ハンドル テーブルからの強い参照へのハンドル。|  
|**非同期です。固定ハンドル**|オブジェクト ハンドル テーブルからの非同期固定オブジェクト。|  
|**依存ハンドル**|オブジェクト ハンドル テーブルからの依存オブジェクト。|  
|**固定ハンドル**|オブジェクト ハンドル テーブルからの固定された強い参照。|  
|**RefCount ハンドル**|オブジェクト ハンドル テーブルからの参照カウントされたオブジェクト。|  
|**SizedRef ハンドル**|ガベージ コレクション時に、すべてのオブジェクトおよびオブジェクト ルートの集合的なクロージャの概算サイズを保持する強力なハンドル。|  
|**ピンされたローカル変数**|ピンされたローカル変数。|  
  
###  <a name="BKMK_Compare_two_memory_snapshots"></a> 2 つのメモリ スナップショットを比較します。  
 メモリ リークの原因である可能性のあるオブジェクトを見つけるために、プロセスに関する 2 つのダンプ ファイルを比較できます。 リークしているオブジェクトの数の増加をわかりやすくするために、1 つ目 (1 回目) と 2 つ目 (2 回目) のファイルを収集する時間間隔は十分長くする必要があります。 2 つのファイルを比較するには:  
  
1.  2 つ目のダンプ ファイルを開いて**マネージ メモリのデバッグ**上、**ミニダンプ ファイルの概要**ページ。  
  
2.  メモリ分析レポート ページで、開く、**ベースラインの選択**一覧を選び、**参照**最初のダンプ ファイルを指定します。  
  
 アナライザーは、間の差を表示するレポートの上部ペインに列を追加、**カウント**、**サイズ**、および**包括サイズ**でそれらの値の種類の以前のスナップショット。  
  
 ![型リストの相違点列](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
 A**参照数の相違**に列が追加されても、**ルートのパス**テーブル。  
  
 ![ページのトップへ](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [内容](#BKMK_Contents)  
  
## <a name="see-also"></a>関連項目  
 [VS ALM TFS ブログ: Visual Studio 2013 を使用して実稼働環境での .NET メモリ問題を診断するには](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV&#124;マネージ メモリ分析](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio ツールボックス&#124;マネージ Visual Studio 2013 でのメモリ分析](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)