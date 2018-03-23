---
title: '[タスク] ウィンドウを使用して |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/18/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: ''
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 889c78e17898a8f5f3d84b81c9605761919d7a2e
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="using-the-tasks-window"></a>[タスク] ウィンドウの使用
**タスク**ウィンドウに似ています、**スレッド**ことに関する情報を表示するウィンドウで、 <xref:System.Threading.Tasks.Task?displayProperty=fullName>、 [task_handle](/cpp/parallel/concrt/reference/task-group-class)、または[WinJS.Promise](http://msdn.microsoft.com/library/windows/apps/br211867.aspx)各スレッドではなくオブジェクト。 スレッドと同様、タスクは、同時に実行できる非同期操作を表します。ただし、複数のタスクが同じスレッドで実行される場合もあります。 
  
 マネージ コードで使用することができます、**タスク**を操作するときにウィンドウ<xref:System.Threading.Tasks.Task?displayProperty=fullName>オブジェクト、または、 **await**と**async**キーワード (**のAwait**と**Async** VisualBasic で)。 マネージ コードでのタスクの詳細については、次を参照してください。[の並行プログラミング](/dotnet/standard/parallel-programming/index)です。  
  
 ネイティブ コードで使用することができます、**タスク**を操作するときにウィンドウ[タスク グループ](/cpp/parallel/concrt/task-parallelism-concurrency-runtime)、[並列アルゴリズム](/cpp/parallel/concrt/parallel-algorithms)、[非同期エージェント](/cpp/parallel/concrt/asynchronous-agents)、および[軽量タスク](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)です。 ネイティブ コードでのタスクの詳細については、次を参照してください。[同時実行ランタイム](/cpp/parallel/concrt/concurrency-runtime)です。  
  
 JavaScript では、promise を使用している場合、[タスク] ウィンドウを使用できます`.then`コード。 参照してください[JavaScript (UWP アプリ) で非同期プログラミング](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx)詳細についてはします。   
  
 使用することができます、**タスク**デバッガーを中断する場合は、常にします。 上でアクセスできる、**デバッグ** をクリックしてメニュー **Windows**クリックし、**タスク**です。 次の図は、**タスク** ウィンドウで、既定のモード。  
  
 ![タスク ウィンドウ](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  マネージ コードでは、マネージ スレッドがスリープ状態または結合状態のとき、状態が <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.TaskStatus>、または <xref:System.Threading.Tasks.TaskStatus> の <xref:System.Threading.Tasks.TaskStatus> は [タスク] ウィンドウに表示されないことがあります。  
  
## <a name="tasks-column-information"></a>[タスク] ウィンドウの列の情報  
 内の列、**タスク**ウィンドウは、次の情報を表示します。  
  
|列名|説明|  
|-----------------|-----------------|  
|**フラグ**|どのタスクにフラグが設定されているかを示します。タスクのフラグを設定または解除することができます。|  
|**アイコン**|黄色の矢印は現在のタスクを示します。 現在のタスクは、現在のスレッドの最上位のタスクです。<br /><br /> 白い矢印は中断しているタスク、つまりデバッガーを呼び出したときに現在のタスクだったタスクを示します。<br /><br /> 一時停止アイコンはユーザーによって凍結されているタスクを示します。 一覧でタスクを右クリックして、タスクを凍結したり凍結解除したりすることができます。|  
|**ID**|タスクに対してシステムで指定された番号です。 ネイティブ コードでは、タスクのアドレスになります。|  
|**状態**|タスクの現在の状態 (スケジュールされた、アクティブ、ブロックされている、デッドロック、待機中、または完了)。 スケジュール状態のタスクは、まだ実行されていないため、まだ呼び出し履歴、割り当てられたスレッド、関連情報がないタスクです。<br /><br /> アクティブなタスクは、デバッガーを中断する前にコードを実行していたタスクです。<br /><br /> 待機中またはブロックされているタスクがシグナル状態になるイベント、ロックが解放する、または別のタスクが終了するを待機しているためにブロックされています。<br /><br /> デッドロック状態のタスクは、スレッドが別のスレッドでデッドロックされた待機中のタスクです。<br /><br /> ポインターを合わせる、**ステータス**セルの詳細については、ブロックを表示するデッドロック状態または待機中のタスクをします。 **警告:** 、**タスク**ウィンドウ待機チェーン トラバーサル (WCT) でサポートされる同期プリミティブを使用するブロックされているタスクに関してのみ、デッドロックが報告されます。 、たとえばするデッドロック状態<xref:System.Threading.Tasks.Task>オブジェクトで、デバッガーの報告、WCT を使用して**待機中デッドロック**です。 デバッガーは WCT を使用しない、同時実行ランタイムによって管理されるデッドロック状態のタスクについて報告**待機している**です。 WCT の詳細については、次を参照してください。[待機チェーン トラバーサル](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx)です。|  
|**開始時刻**|タスクがアクティブになった時間です。|  
|**期間**|タスクがアクティブになっている秒数です。|  
|**完了時間**|タスクが完了した時間です。|  
|**場所**|タスクの呼び出し履歴内の現在の位置です。 タスクのすべての呼び出し履歴を表示するには、このセルの上にカーソルを置きます。 スケジュール状態のタスクについては、このセルには値が表示されません。|  
|**Task**|最初のメソッドと、作成時にタスクに渡された引数です。|  
|**AsyncState**|タスクの状態です (マネージ コードの場合)。 既定では、この列は非表示になっています。 この列を表示するには、いずれかの列ヘッダーのコンテキスト メニューを開きます。 選択**列**、 **AsyncState**です。|  
|**Parent**|このタスクを作成したタスクの ID です。 この列が空白のタスクには親はありません。 これは、マネージ プログラムの場合にのみ適用されます。|  
|**スレッドの割り当て**|タスクを実行しているスレッドの ID と名前です。|  
|**AppDomain**|マネージ コード用の情報で、タスクを実行しているアプリケーション ドメインを示します。|  
|**task_group**|ネイティブ コードのアドレスに対して、 [task_group](/cpp/parallel/concrt/reference/task-group-class.mdd)タスクをスケジュールするオブジェクト。 非同期エージェントおよび軽量タスクでは、この列は 0 に設定されます。|  
|**Process**|タスクが実行されているプロセスの ID です。|  
  
 ビューに列を追加するには、列見出しを右クリックし、追加する列を選択します (列を削除するには選択を解除します)。また、列を左右にドラッグして列の順序を変更することもできます。 列のショートカット メニューを次の図に示します。  
  
 ![[タスク] ウィンドウのショートカット ビュー メニュー](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>タスクの並べ替え  
 列を基準にタスクを並べ替えるには、列ヘッダーをクリックします。 たとえばをクリックすると、 **ID**列ヘッダーをタスクをタスク ID を並べ替えることができます: 1,2,3,4,5 というようにします。 並べ替え順序を逆にするには、もう一度列ヘッダーをクリックします。 現在の並べ替え列と並べ替え順序は、列に矢印で示されます。  
  
## <a name="grouping-tasks"></a>タスクのグループ化  
 リスト ビューの任意の列に基づいてタスクをグループ化することができます。 たとえばを右クリックして、**ステータス**列ヘッダーをクリックし、 **Group by** > **[*ステータス*]**、することができます状態が同じすべてのタスクをグループ化します。 たとえば、でしたをすばやく確認がブロックされている理由に専念することができるようにタスクを待機しています。 また、デバッグ セッションでは関係のないグループを折りたたむこともできます。 他の列を基準にしても、同じようにしてグループ化できます。 グループに対しては、グループ ヘッダーの横にあるボタンをクリックするだけで、まとめてフラグを設定したり解除したりすることができます。 次の図は、**タスク**グループ化されたモードでのウィンドウ。  
  
 ![[タスク] ウィンドウのグループ化されたモード](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>親子ビュー  
 このビューは、マネージ コードの場合のみ使用できます。右クリックして、**ステータス**列ヘッダーをクリックし、 **Group by** > **親**での階層ビューにタスクの一覧を変更することができますすべての子タスクは、表示したり、その親の下にある非表示になっているサブ ノードです。 
  
## <a name="flagging-tasks"></a>タスクに対するフラグの設定  
 タスクがタスクを選択して実行されているタスク一覧の項目を選択し、スレッドのフラグを設定することができます**割り当てられているスレッドにフラグ**コンテキスト メニューから、または最初の列のフラグ アイコンをクリックします。 複数のタスクにフラグを設定してそれらだけを集中して確認する場合、フラグ列で並べ替えを行うことで、フラグを設定したすべてのタスクが上に表示されるようにすることができます。 使用することも、**並列スタック**ウィンドウを表示するには、タスクのみフラグが付けられます。 これにより、デバッグには関係のないタスクを除外することができます。 フラグはデバッグ セッション間で保持されません。  
  
## <a name="freezing-and-thawing-tasks"></a>タスクの凍結と凍結解除  
 タスク一覧の項目を右クリックし、をクリックしてタスクを実行するスレッドを凍結したり**割り当てられているスレッドを凍結**です。 (タスクが既に凍結されている場合、コマンドは**割り当てられたスレッドの凍結解除**)。スレッドを凍結すると、現在のブレークポイントの後のコードのステップ実行でそのスレッドが実行されなくなります。 **固定すべてのスレッドが、この 1 つ**コマンドは、タスク一覧の項目を実行している 1 つを除くすべてのスレッドを凍結します。
  
 各タスクのその他のメニュー項目を次の図に示します。  
  
 ![[タスク] ウィンドウのショートカット スレッド メニュー](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")  

## <a name="switching-the-active-task-or-frame"></a>アクティブなタスクまたはフレームの切り替え

**タスクへの切り替え**コマンドは、現在のタスク、アクティブなタスクです。 **フレームに切り替え**コマンドは、選択したスタック フレームをアクティブなスタック フレームを使用します。 デバッガーのコンテキストは、現在のタスクまたは選択したスタック フレームに切り替えられます。

## <a name="see-also"></a>関連項目  
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)   
 [並列プログラミング](/dotnet/standard/parallel-programming/index)   
 [同時実行ランタイム](/cpp/parallel/concrt/concurrency-runtime)   
 [[並列スタック] ウィンドウの使用](../debugger/using-the-parallel-stacks-window.md)   
 [チュートリアル: 並行アプリケーションのデバッグ](../debugger/walkthrough-debugging-a-parallel-application.md)